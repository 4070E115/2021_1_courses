# objd2.c
```
// objd2.c
#include <stdio.h>

int main()
{
   printf("Hello CTFer\n");
   return 0;
}
```

```
gcc -g objd2.c -o objd2
```

```
objdump -S  -j .text -M intel objd2 --no-show-raw-insn

objd2:     file format elf64-x86-64


Disassembly of section .text:

0000000000001050 <_start>:
    1050:	xor    ebp,ebp
    1052:	mov    r9,rdx
    1055:	pop    rsi
    1056:	mov    rdx,rsp
    1059:	and    rsp,0xfffffffffffffff0
    105d:	push   rax
    105e:	push   rsp
    105f:	lea    r8,[rip+0x14a]        # 11b0 <__libc_csu_fini>
    1066:	lea    rcx,[rip+0xe3]        # 1150 <__libc_csu_init>
    106d:	lea    rdi,[rip+0xc1]        # 1135 <main>
    1074:	call   QWORD PTR [rip+0x2f66]        # 3fe0 <__libc_start_main@GLIBC_2.2.5>
    107a:	hlt    
    107b:	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001080 <deregister_tm_clones>:
    1080:	lea    rdi,[rip+0x2fa9]        # 4030 <__TMC_END__>
    1087:	lea    rax,[rip+0x2fa2]        # 4030 <__TMC_END__>
    108e:	cmp    rax,rdi
    1091:	je     10a8 <deregister_tm_clones+0x28>
    1093:	mov    rax,QWORD PTR [rip+0x2f3e]        # 3fd8 <_ITM_deregisterTMCloneTable>
    109a:	test   rax,rax
    109d:	je     10a8 <deregister_tm_clones+0x28>
    109f:	jmp    rax
    10a1:	nop    DWORD PTR [rax+0x0]
    10a8:	ret    
    10a9:	nop    DWORD PTR [rax+0x0]

00000000000010b0 <register_tm_clones>:
    10b0:	lea    rdi,[rip+0x2f79]        # 4030 <__TMC_END__>
    10b7:	lea    rsi,[rip+0x2f72]        # 4030 <__TMC_END__>
    10be:	sub    rsi,rdi
    10c1:	sar    rsi,0x3
    10c5:	mov    rax,rsi
    10c8:	shr    rax,0x3f
    10cc:	add    rsi,rax
    10cf:	sar    rsi,1
    10d2:	je     10e8 <register_tm_clones+0x38>
    10d4:	mov    rax,QWORD PTR [rip+0x2f15]        # 3ff0 <_ITM_registerTMCloneTable>
    10db:	test   rax,rax
    10de:	je     10e8 <register_tm_clones+0x38>
    10e0:	jmp    rax
    10e2:	nop    WORD PTR [rax+rax*1+0x0]
    10e8:	ret    
    10e9:	nop    DWORD PTR [rax+0x0]

00000000000010f0 <__do_global_dtors_aux>:
    10f0:	cmp    BYTE PTR [rip+0x2f39],0x0        # 4030 <__TMC_END__>
    10f7:	jne    1128 <__do_global_dtors_aux+0x38>
    10f9:	push   rbp
    10fa:	cmp    QWORD PTR [rip+0x2ef6],0x0        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1102:	mov    rbp,rsp
    1105:	je     1113 <__do_global_dtors_aux+0x23>
    1107:	mov    rdi,QWORD PTR [rip+0x2f1a]        # 4028 <__dso_handle>
    110e:	call   1040 <__cxa_finalize@plt>
    1113:	call   1080 <deregister_tm_clones>
    1118:	mov    BYTE PTR [rip+0x2f11],0x1        # 4030 <__TMC_END__>
    111f:	pop    rbp
    1120:	ret    
    1121:	nop    DWORD PTR [rax+0x0]
    1128:	ret    
    1129:	nop    DWORD PTR [rax+0x0]

0000000000001130 <frame_dummy>:
    1130:	jmp    10b0 <register_tm_clones>

0000000000001135 <main>:
// objd2.c
#include <stdio.h>

int main()
{
    1135:	push   rbp
    1136:	mov    rbp,rsp
   printf("Hello CTFer\n");
    1139:	lea    rdi,[rip+0xec4]        # 2004 <_IO_stdin_used+0x4>
    1140:	call   1030 <puts@plt>
   return 0;
    1145:	mov    eax,0x0
}
    114a:	pop    rbp
    114b:	ret    
    114c:	nop    DWORD PTR [rax+0x0]

0000000000001150 <__libc_csu_init>:
    1150:	push   r15
    1152:	mov    r15,rdx
    1155:	push   r14
    1157:	mov    r14,rsi
    115a:	push   r13
    115c:	mov    r13d,edi
    115f:	push   r12
    1161:	lea    r12,[rip+0x2c80]        # 3de8 <__frame_dummy_init_array_entry>
    1168:	push   rbp
    1169:	lea    rbp,[rip+0x2c80]        # 3df0 <__init_array_end>
    1170:	push   rbx
    1171:	sub    rbp,r12
    1174:	sub    rsp,0x8
    1178:	call   1000 <_init>
    117d:	sar    rbp,0x3
    1181:	je     119e <__libc_csu_init+0x4e>
    1183:	xor    ebx,ebx
    1185:	nop    DWORD PTR [rax]
    1188:	mov    rdx,r15
    118b:	mov    rsi,r14
    118e:	mov    edi,r13d
    1191:	call   QWORD PTR [r12+rbx*8]
    1195:	add    rbx,0x1
    1199:	cmp    rbp,rbx
    119c:	jne    1188 <__libc_csu_init+0x38>
    119e:	add    rsp,0x8
    11a2:	pop    rbx
    11a3:	pop    rbp
    11a4:	pop    r12
    11a6:	pop    r13
    11a8:	pop    r14
    11aa:	pop    r15
    11ac:	ret    
    11ad:	nop    DWORD PTR [rax]

00000000000011b0 <__libc_csu_fini>:
    11b0:	ret    

```
```
objdump -S  -j .text -M intel objd2

objd2:     file format elf64-x86-64


Disassembly of section .text:

0000000000001050 <_start>:
    1050:	31 ed                	xor    ebp,ebp
    1052:	49 89 d1             	mov    r9,rdx
    1055:	5e                   	pop    rsi
    1056:	48 89 e2             	mov    rdx,rsp
    1059:	48 83 e4 f0          	and    rsp,0xfffffffffffffff0
    105d:	50                   	push   rax
    105e:	54                   	push   rsp
    105f:	4c 8d 05 4a 01 00 00 	lea    r8,[rip+0x14a]        # 11b0 <__libc_csu_fini>
    1066:	48 8d 0d e3 00 00 00 	lea    rcx,[rip+0xe3]        # 1150 <__libc_csu_init>
    106d:	48 8d 3d c1 00 00 00 	lea    rdi,[rip+0xc1]        # 1135 <main>
    1074:	ff 15 66 2f 00 00    	call   QWORD PTR [rip+0x2f66]        # 3fe0 <__libc_start_main@GLIBC_2.2.5>
    107a:	f4                   	hlt    
    107b:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001080 <deregister_tm_clones>:
    1080:	48 8d 3d a9 2f 00 00 	lea    rdi,[rip+0x2fa9]        # 4030 <__TMC_END__>
    1087:	48 8d 05 a2 2f 00 00 	lea    rax,[rip+0x2fa2]        # 4030 <__TMC_END__>
    108e:	48 39 f8             	cmp    rax,rdi
    1091:	74 15                	je     10a8 <deregister_tm_clones+0x28>
    1093:	48 8b 05 3e 2f 00 00 	mov    rax,QWORD PTR [rip+0x2f3e]        # 3fd8 <_ITM_deregisterTMCloneTable>
    109a:	48 85 c0             	test   rax,rax
    109d:	74 09                	je     10a8 <deregister_tm_clones+0x28>
    109f:	ff e0                	jmp    rax
    10a1:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]
    10a8:	c3                   	ret    
    10a9:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

00000000000010b0 <register_tm_clones>:
    10b0:	48 8d 3d 79 2f 00 00 	lea    rdi,[rip+0x2f79]        # 4030 <__TMC_END__>
    10b7:	48 8d 35 72 2f 00 00 	lea    rsi,[rip+0x2f72]        # 4030 <__TMC_END__>
    10be:	48 29 fe             	sub    rsi,rdi
    10c1:	48 c1 fe 03          	sar    rsi,0x3
    10c5:	48 89 f0             	mov    rax,rsi
    10c8:	48 c1 e8 3f          	shr    rax,0x3f
    10cc:	48 01 c6             	add    rsi,rax
    10cf:	48 d1 fe             	sar    rsi,1
    10d2:	74 14                	je     10e8 <register_tm_clones+0x38>
    10d4:	48 8b 05 15 2f 00 00 	mov    rax,QWORD PTR [rip+0x2f15]        # 3ff0 <_ITM_registerTMCloneTable>
    10db:	48 85 c0             	test   rax,rax
    10de:	74 08                	je     10e8 <register_tm_clones+0x38>
    10e0:	ff e0                	jmp    rax
    10e2:	66 0f 1f 44 00 00    	nop    WORD PTR [rax+rax*1+0x0]
    10e8:	c3                   	ret    
    10e9:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

00000000000010f0 <__do_global_dtors_aux>:
    10f0:	80 3d 39 2f 00 00 00 	cmp    BYTE PTR [rip+0x2f39],0x0        # 4030 <__TMC_END__>
    10f7:	75 2f                	jne    1128 <__do_global_dtors_aux+0x38>
    10f9:	55                   	push   rbp
    10fa:	48 83 3d f6 2e 00 00 	cmp    QWORD PTR [rip+0x2ef6],0x0        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1101:	00 
    1102:	48 89 e5             	mov    rbp,rsp
    1105:	74 0c                	je     1113 <__do_global_dtors_aux+0x23>
    1107:	48 8b 3d 1a 2f 00 00 	mov    rdi,QWORD PTR [rip+0x2f1a]        # 4028 <__dso_handle>
    110e:	e8 2d ff ff ff       	call   1040 <__cxa_finalize@plt>
    1113:	e8 68 ff ff ff       	call   1080 <deregister_tm_clones>
    1118:	c6 05 11 2f 00 00 01 	mov    BYTE PTR [rip+0x2f11],0x1        # 4030 <__TMC_END__>
    111f:	5d                   	pop    rbp
    1120:	c3                   	ret    
    1121:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]
    1128:	c3                   	ret    
    1129:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

0000000000001130 <frame_dummy>:
    1130:	e9 7b ff ff ff       	jmp    10b0 <register_tm_clones>

0000000000001135 <main>:
// objd2.c
#include <stdio.h>

int main()
{
    1135:	55                   	push   rbp
    1136:	48 89 e5             	mov    rbp,rsp
   printf("Hello CTFer\n");
    1139:	48 8d 3d c4 0e 00 00 	lea    rdi,[rip+0xec4]        # 2004 <_IO_stdin_used+0x4>
    1140:	e8 eb fe ff ff       	call   1030 <puts@plt>
   return 0;
    1145:	b8 00 00 00 00       	mov    eax,0x0
}
    114a:	5d                   	pop    rbp
    114b:	c3                   	ret    
    114c:	0f 1f 40 00          	nop    DWORD PTR [rax+0x0]

0000000000001150 <__libc_csu_init>:
    1150:	41 57                	push   r15
    1152:	49 89 d7             	mov    r15,rdx
    1155:	41 56                	push   r14
    1157:	49 89 f6             	mov    r14,rsi
    115a:	41 55                	push   r13
    115c:	41 89 fd             	mov    r13d,edi
    115f:	41 54                	push   r12
    1161:	4c 8d 25 80 2c 00 00 	lea    r12,[rip+0x2c80]        # 3de8 <__frame_dummy_init_array_entry>
    1168:	55                   	push   rbp
    1169:	48 8d 2d 80 2c 00 00 	lea    rbp,[rip+0x2c80]        # 3df0 <__init_array_end>
    1170:	53                   	push   rbx
    1171:	4c 29 e5             	sub    rbp,r12
    1174:	48 83 ec 08          	sub    rsp,0x8
    1178:	e8 83 fe ff ff       	call   1000 <_init>
    117d:	48 c1 fd 03          	sar    rbp,0x3
    1181:	74 1b                	je     119e <__libc_csu_init+0x4e>
    1183:	31 db                	xor    ebx,ebx
    1185:	0f 1f 00             	nop    DWORD PTR [rax]
    1188:	4c 89 fa             	mov    rdx,r15
    118b:	4c 89 f6             	mov    rsi,r14
    118e:	44 89 ef             	mov    edi,r13d
    1191:	41 ff 14 dc          	call   QWORD PTR [r12+rbx*8]
    1195:	48 83 c3 01          	add    rbx,0x1
    1199:	48 39 dd             	cmp    rbp,rbx
    119c:	75 ea                	jne    1188 <__libc_csu_init+0x38>
    119e:	48 83 c4 08          	add    rsp,0x8
    11a2:	5b                   	pop    rbx
    11a3:	5d                   	pop    rbp
    11a4:	41 5c                	pop    r12
    11a6:	41 5d                	pop    r13
    11a8:	41 5e                	pop    r14
    11aa:	41 5f                	pop    r15
    11ac:	c3                   	ret    
    11ad:	0f 1f 00             	nop    DWORD PTR [rax]

00000000000011b0 <__libc_csu_fini>:
    11b0:	c3                   	ret  
```
