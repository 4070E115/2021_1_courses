#
```


```


```
objdump -S -j .text adder 

adder:     file format elf64-x86-64


Disassembly of section .text:

0000000000400860 <_start>:
  400860:	31 ed                	xor    %ebp,%ebp
  400862:	49 89 d1             	mov    %rdx,%r9
  400865:	5e                   	pop    %rsi
  400866:	48 89 e2             	mov    %rsp,%rdx
  400869:	48 83 e4 f0          	and    $0xfffffffffffffff0,%rsp
  40086d:	50                   	push   %rax
  40086e:	54                   	push   %rsp
  40086f:	49 c7 c0 b0 0c 40 00 	mov    $0x400cb0,%r8
  400876:	48 c7 c1 40 0c 40 00 	mov    $0x400c40,%rcx
  40087d:	48 c7 c7 1e 0b 40 00 	mov    $0x400b1e,%rdi
  400884:	e8 77 ff ff ff       	callq  400800 <__libc_start_main@plt>
  400889:	f4                   	hlt    
  40088a:	66 0f 1f 44 00 00    	nopw   0x0(%rax,%rax,1)

0000000000400890 <deregister_tm_clones>:
  400890:	b8 7f 20 60 00       	mov    $0x60207f,%eax
  400895:	55                   	push   %rbp
  400896:	48 2d 78 20 60 00    	sub    $0x602078,%rax
  40089c:	48 83 f8 0e          	cmp    $0xe,%rax
  4008a0:	48 89 e5             	mov    %rsp,%rbp
  4008a3:	77 02                	ja     4008a7 <deregister_tm_clones+0x17>
  4008a5:	5d                   	pop    %rbp
  4008a6:	c3                   	retq   
  4008a7:	b8 00 00 00 00       	mov    $0x0,%eax
  4008ac:	48 85 c0             	test   %rax,%rax
  4008af:	74 f4                	je     4008a5 <deregister_tm_clones+0x15>
  4008b1:	5d                   	pop    %rbp
  4008b2:	bf 78 20 60 00       	mov    $0x602078,%edi
  4008b7:	ff e0                	jmpq   *%rax
  4008b9:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)

00000000004008c0 <register_tm_clones>:
  4008c0:	b8 78 20 60 00       	mov    $0x602078,%eax
  4008c5:	55                   	push   %rbp
  4008c6:	48 2d 78 20 60 00    	sub    $0x602078,%rax
  4008cc:	48 c1 f8 03          	sar    $0x3,%rax
  4008d0:	48 89 e5             	mov    %rsp,%rbp
  4008d3:	48 89 c2             	mov    %rax,%rdx
  4008d6:	48 c1 ea 3f          	shr    $0x3f,%rdx
  4008da:	48 01 d0             	add    %rdx,%rax
  4008dd:	48 d1 f8             	sar    %rax
  4008e0:	75 02                	jne    4008e4 <register_tm_clones+0x24>
  4008e2:	5d                   	pop    %rbp
  4008e3:	c3                   	retq   
  4008e4:	ba 00 00 00 00       	mov    $0x0,%edx
  4008e9:	48 85 d2             	test   %rdx,%rdx
  4008ec:	74 f4                	je     4008e2 <register_tm_clones+0x22>
  4008ee:	5d                   	pop    %rbp
  4008ef:	48 89 c6             	mov    %rax,%rsi
  4008f2:	bf 78 20 60 00       	mov    $0x602078,%edi
  4008f7:	ff e2                	jmpq   *%rdx
  4008f9:	0f 1f 80 00 00 00 00 	nopl   0x0(%rax)

0000000000400900 <__do_global_dtors_aux>:
  400900:	80 3d a9 19 20 00 00 	cmpb   $0x0,0x2019a9(%rip)        # 6022b0 <completed.6345>
  400907:	75 11                	jne    40091a <__do_global_dtors_aux+0x1a>
  400909:	55                   	push   %rbp
  40090a:	48 89 e5             	mov    %rsp,%rbp
  40090d:	e8 7e ff ff ff       	callq  400890 <deregister_tm_clones>
  400912:	5d                   	pop    %rbp
  400913:	c6 05 96 19 20 00 01 	movb   $0x1,0x201996(%rip)        # 6022b0 <completed.6345>
  40091a:	f3 c3                	repz retq 
  40091c:	0f 1f 40 00          	nopl   0x0(%rax)

0000000000400920 <frame_dummy>:
  400920:	48 83 3d c8 14 20 00 	cmpq   $0x0,0x2014c8(%rip)        # 601df0 <__JCR_END__>
  400927:	00 
  400928:	74 1e                	je     400948 <frame_dummy+0x28>
  40092a:	b8 00 00 00 00       	mov    $0x0,%eax
  40092f:	48 85 c0             	test   %rax,%rax
  400932:	74 14                	je     400948 <frame_dummy+0x28>
  400934:	55                   	push   %rbp
  400935:	bf f0 1d 60 00       	mov    $0x601df0,%edi
  40093a:	48 89 e5             	mov    %rsp,%rbp
  40093d:	ff d0                	callq  *%rax
  40093f:	5d                   	pop    %rbp
  400940:	e9 7b ff ff ff       	jmpq   4008c0 <register_tm_clones>
  400945:	0f 1f 00             	nopl   (%rax)
  400948:	e9 73 ff ff ff       	jmpq   4008c0 <register_tm_clones>

000000000040094d <_Z3geni>:
  40094d:	55                   	push   %rbp
  40094e:	48 89 e5             	mov    %rsp,%rbp
  400951:	48 83 ec 20          	sub    $0x20,%rsp
  400955:	89 7d ec             	mov    %edi,-0x14(%rbp)
  400958:	b8 16 00 00 00       	mov    $0x16,%eax
  40095d:	48 89 c7             	mov    %rax,%rdi
  400960:	e8 8b fe ff ff       	callq  4007f0 <malloc@plt>
  400965:	48 89 45 f8          	mov    %rax,-0x8(%rbp)
  400969:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  40096d:	c6 00 79             	movb   $0x79,(%rax)
  400970:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400974:	48 8d 70 01          	lea    0x1(%rax),%rsi
  400978:	8b 4d ec             	mov    -0x14(%rbp),%ecx
  40097b:	ba 93 24 49 92       	mov    $0x92492493,%edx
  400980:	89 c8                	mov    %ecx,%eax
  400982:	f7 ea                	imul   %edx
  400984:	8d 04 0a             	lea    (%rdx,%rcx,1),%eax
  400987:	c1 f8 02             	sar    $0x2,%eax
  40098a:	89 c2                	mov    %eax,%edx
  40098c:	89 c8                	mov    %ecx,%eax
  40098e:	c1 f8 1f             	sar    $0x1f,%eax
  400991:	29 c2                	sub    %eax,%edx
  400993:	89 d0                	mov    %edx,%eax
  400995:	c1 e0 03             	shl    $0x3,%eax
  400998:	29 d0                	sub    %edx,%eax
  40099a:	29 c1                	sub    %eax,%ecx
  40099c:	89 ca                	mov    %ecx,%edx
  40099e:	89 d0                	mov    %edx,%eax
  4009a0:	83 c0 30             	add    $0x30,%eax
  4009a3:	88 06                	mov    %al,(%rsi)
  4009a5:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  4009a9:	48 8d 50 02          	lea    0x2(%rax),%rdx
  4009ad:	8b 45 ec             	mov    -0x14(%rbp),%eax
  4009b0:	83 c0 3c             	add    $0x3c,%eax
  4009b3:	88 02                	mov    %al,(%rdx)
  4009b5:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  4009b9:	48 83 c0 03          	add    $0x3,%rax
  4009bd:	c6 00 5f             	movb   $0x5f,(%rax)
  4009c0:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  4009c4:	48 8d 50 04          	lea    0x4(%rax),%rdx
  4009c8:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  4009cc:	48 83 c0 02          	add    $0x2,%rax
  4009d0:	0f b6 00             	movzbl (%rax),%eax
  4009d3:	83 e8 14             	sub    $0x14,%eax
  4009d6:	88 02                	mov    %al,(%rdx)
  4009d8:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  4009dc:	48 8d 50 05          	lea    0x5(%rax),%rdx
  4009e0:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  4009e4:	48 83 c0 04          	add    $0x4,%rax
  4009e8:	0f b6 00             	movzbl (%rax),%eax
  4009eb:	83 c0 03             	add    $0x3,%eax
  4009ee:	88 02                	mov    %al,(%rdx)
  4009f0:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  4009f4:	48 8d 50 06          	lea    0x6(%rax),%rdx
  4009f8:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  4009fc:	0f b6 40 05          	movzbl 0x5(%rax),%eax
  400a00:	88 02                	mov    %al,(%rdx)
  400a02:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a06:	48 83 c0 07          	add    $0x7,%rax
  400a0a:	c6 00 65             	movb   $0x65,(%rax)
  400a0d:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a11:	48 8d 50 08          	lea    0x8(%rax),%rdx
  400a15:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a19:	0f b6 40 06          	movzbl 0x6(%rax),%eax
  400a1d:	88 02                	mov    %al,(%rdx)
  400a1f:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a23:	48 8d 50 09          	lea    0x9(%rax),%rdx
  400a27:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a2b:	0f b6 40 03          	movzbl 0x3(%rax),%eax
  400a2f:	88 02                	mov    %al,(%rdx)
  400a31:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a35:	48 83 c0 0a          	add    $0xa,%rax
  400a39:	c6 00 74             	movb   $0x74,(%rax)
  400a3c:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a40:	48 8d 50 0b          	lea    0xb(%rax),%rdx
  400a44:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a48:	48 83 c0 0a          	add    $0xa,%rax
  400a4c:	0f b6 00             	movzbl (%rax),%eax
  400a4f:	83 e8 0c             	sub    $0xc,%eax
  400a52:	88 02                	mov    %al,(%rdx)
  400a54:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a58:	48 83 c0 0c          	add    $0xc,%rax
  400a5c:	c6 00 72             	movb   $0x72,(%rax)
  400a5f:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a63:	48 83 c0 0d          	add    $0xd,%rax
  400a67:	c6 00 33             	movb   $0x33,(%rax)
  400a6a:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a6e:	48 83 c0 0e          	add    $0xe,%rax
  400a72:	c6 00 33             	movb   $0x33,(%rax)
  400a75:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a79:	48 8d 50 0f          	lea    0xf(%rax),%rdx
  400a7d:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a81:	0f b6 40 03          	movzbl 0x3(%rax),%eax
  400a85:	88 02                	mov    %al,(%rdx)
  400a87:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a8b:	48 83 c0 10          	add    $0x10,%rax
  400a8f:	c6 00 6e             	movb   $0x6e,(%rax)
  400a92:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a96:	48 8d 50 11          	lea    0x11(%rax),%rdx
  400a9a:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400a9e:	0f b6 40 02          	movzbl 0x2(%rax),%eax
  400aa2:	88 02                	mov    %al,(%rdx)
  400aa4:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400aa8:	48 8d 50 12          	lea    0x12(%rax),%rdx
  400aac:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400ab0:	48 83 c0 10          	add    $0x10,%rax
  400ab4:	0f b6 00             	movzbl (%rax),%eax
  400ab7:	83 e8 01             	sub    $0x1,%eax
  400aba:	88 02                	mov    %al,(%rdx)
  400abc:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400ac0:	48 83 c0 13          	add    $0x13,%rax
  400ac4:	c6 00 73             	movb   $0x73,(%rax)
  400ac7:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400acb:	48 83 c0 14          	add    $0x14,%rax
  400acf:	c6 00 21             	movb   $0x21,(%rax)
  400ad2:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400ad6:	48 83 c0 15          	add    $0x15,%rax
  400ada:	c6 00 0a             	movb   $0xa,(%rax)
  400add:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400ae1:	c9                   	leaveq 
  400ae2:	c3                   	retq   

0000000000400ae3 <_Z9print_ptrPc>:
  400ae3:	55                   	push   %rbp
  400ae4:	48 89 e5             	mov    %rsp,%rbp
  400ae7:	48 83 ec 20          	sub    $0x20,%rsp
  400aeb:	48 89 7d e8          	mov    %rdi,-0x18(%rbp)
  400aef:	c7 45 fc 00 00 00 00 	movl   $0x0,-0x4(%rbp)
  400af6:	eb 1e                	jmp    400b16 <_Z9print_ptrPc+0x33>
  400af8:	8b 45 fc             	mov    -0x4(%rbp),%eax
  400afb:	48 63 d0             	movslq %eax,%rdx
  400afe:	48 8b 45 e8          	mov    -0x18(%rbp),%rax
  400b02:	48 01 d0             	add    %rdx,%rax
  400b05:	0f b6 00             	movzbl (%rax),%eax
  400b08:	0f be c0             	movsbl %al,%eax
  400b0b:	89 c7                	mov    %eax,%edi
  400b0d:	e8 be fc ff ff       	callq  4007d0 <putchar@plt>
  400b12:	83 45 fc 01          	addl   $0x1,-0x4(%rbp)
  400b16:	83 7d fc 14          	cmpl   $0x14,-0x4(%rbp)
  400b1a:	7e dc                	jle    400af8 <_Z9print_ptrPc+0x15>
  400b1c:	c9                   	leaveq 
  400b1d:	c3                   	retq   

0000000000400b1e <main>:
  400b1e:	55                   	push   %rbp
  400b1f:	48 89 e5             	mov    %rsp,%rbp
  400b22:	48 83 ec 20          	sub    $0x20,%rsp
  400b26:	c7 45 f4 00 00 00 00 	movl   $0x0,-0xc(%rbp)
  400b2d:	c7 45 f0 00 00 00 00 	movl   $0x0,-0x10(%rbp)
  400b34:	c7 45 ec 00 00 00 00 	movl   $0x0,-0x14(%rbp)
  400b3b:	be d0 0c 40 00       	mov    $0x400cd0,%esi
  400b40:	bf a0 21 60 00       	mov    $0x6021a0,%edi
  400b45:	e8 e6 fc ff ff       	callq  400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400b4a:	48 8d 45 f4          	lea    -0xc(%rbp),%rax
  400b4e:	48 89 c6             	mov    %rax,%rsi
  400b51:	bf 80 20 60 00       	mov    $0x602080,%edi
  400b56:	e8 f5 fc ff ff       	callq  400850 <_ZNSirsERi@plt>
  400b5b:	48 8d 55 f0          	lea    -0x10(%rbp),%rdx
  400b5f:	48 89 d6             	mov    %rdx,%rsi
  400b62:	48 89 c7             	mov    %rax,%rdi
  400b65:	e8 e6 fc ff ff       	callq  400850 <_ZNSirsERi@plt>
  400b6a:	48 8d 55 ec          	lea    -0x14(%rbp),%rdx
  400b6e:	48 89 d6             	mov    %rdx,%rsi
  400b71:	48 89 c7             	mov    %rax,%rdi
  400b74:	e8 d7 fc ff ff       	callq  400850 <_ZNSirsERi@plt>
  400b79:	8b 55 f4             	mov    -0xc(%rbp),%edx
  400b7c:	8b 45 f0             	mov    -0x10(%rbp),%eax
  400b7f:	01 c2                	add    %eax,%edx
  400b81:	8b 45 ec             	mov    -0x14(%rbp),%eax
  400b84:	01 d0                	add    %edx,%eax
  400b86:	89 c7                	mov    %eax,%edi
  400b88:	e8 c0 fd ff ff       	callq  40094d <_Z3geni>
  400b8d:	48 89 45 f8          	mov    %rax,-0x8(%rbp)
  400b91:	8b 55 f4             	mov    -0xc(%rbp),%edx
  400b94:	8b 45 f0             	mov    -0x10(%rbp),%eax
  400b97:	01 c2                	add    %eax,%edx
  400b99:	8b 45 ec             	mov    -0x14(%rbp),%eax
  400b9c:	01 d0                	add    %edx,%eax
  400b9e:	3d 39 05 00 00       	cmp    $0x539,%eax
  400ba3:	75 27                	jne    400bcc <main+0xae>
  400ba5:	be e6 0c 40 00       	mov    $0x400ce6,%esi
  400baa:	bf a0 21 60 00       	mov    $0x6021a0,%edi
  400baf:	e8 7c fc ff ff       	callq  400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400bb4:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400bb8:	48 89 c7             	mov    %rax,%rdi
  400bbb:	e8 23 ff ff ff       	callq  400ae3 <_Z9print_ptrPc>
  400bc0:	bf ef 0c 40 00       	mov    $0x400cef,%edi
  400bc5:	e8 f6 fb ff ff       	callq  4007c0 <puts@plt>
  400bca:	eb 0f                	jmp    400bdb <main+0xbd>
  400bcc:	be f1 0c 40 00       	mov    $0x400cf1,%esi
  400bd1:	bf a0 21 60 00       	mov    $0x6021a0,%edi
  400bd6:	e8 55 fc ff ff       	callq  400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400bdb:	48 8b 45 f8          	mov    -0x8(%rbp),%rax
  400bdf:	48 89 c7             	mov    %rax,%rdi
  400be2:	e8 59 fc ff ff       	callq  400840 <free@plt>
  400be7:	b8 00 00 00 00       	mov    $0x0,%eax
  400bec:	c9                   	leaveq 
  400bed:	c3                   	retq   

0000000000400bee <_Z41__static_initialization_and_destruction_0ii>:
  400bee:	55                   	push   %rbp
  400bef:	48 89 e5             	mov    %rsp,%rbp
  400bf2:	48 83 ec 10          	sub    $0x10,%rsp
  400bf6:	89 7d fc             	mov    %edi,-0x4(%rbp)
  400bf9:	89 75 f8             	mov    %esi,-0x8(%rbp)
  400bfc:	83 7d fc 01          	cmpl   $0x1,-0x4(%rbp)
  400c00:	75 27                	jne    400c29 <_Z41__static_initialization_and_destruction_0ii+0x3b>
  400c02:	81 7d f8 ff ff 00 00 	cmpl   $0xffff,-0x8(%rbp)
  400c09:	75 1e                	jne    400c29 <_Z41__static_initialization_and_destruction_0ii+0x3b>
  400c0b:	bf b1 22 60 00       	mov    $0x6022b1,%edi
  400c10:	e8 cb fb ff ff       	callq  4007e0 <_ZNSt8ios_base4InitC1Ev@plt>
  400c15:	ba c8 0c 40 00       	mov    $0x400cc8,%edx
  400c1a:	be b1 22 60 00       	mov    $0x6022b1,%esi
  400c1f:	bf 20 08 40 00       	mov    $0x400820,%edi
  400c24:	e8 e7 fb ff ff       	callq  400810 <__cxa_atexit@plt>
  400c29:	c9                   	leaveq 
  400c2a:	c3                   	retq   

0000000000400c2b <_GLOBAL__sub_I__Z3geni>:
  400c2b:	55                   	push   %rbp
  400c2c:	48 89 e5             	mov    %rsp,%rbp
  400c2f:	be ff ff 00 00       	mov    $0xffff,%esi
  400c34:	bf 01 00 00 00       	mov    $0x1,%edi
  400c39:	e8 b0 ff ff ff       	callq  400bee <_Z41__static_initialization_and_destruction_0ii>
  400c3e:	5d                   	pop    %rbp
  400c3f:	c3                   	retq   

0000000000400c40 <__libc_csu_init>:
  400c40:	41 57                	push   %r15
  400c42:	41 89 ff             	mov    %edi,%r15d
  400c45:	41 56                	push   %r14
  400c47:	49 89 f6             	mov    %rsi,%r14
  400c4a:	41 55                	push   %r13
  400c4c:	49 89 d5             	mov    %rdx,%r13
  400c4f:	41 54                	push   %r12
  400c51:	4c 8d 25 80 11 20 00 	lea    0x201180(%rip),%r12        # 601dd8 <__frame_dummy_init_array_entry>
  400c58:	55                   	push   %rbp
  400c59:	48 8d 2d 88 11 20 00 	lea    0x201188(%rip),%rbp        # 601de8 <__init_array_end>
  400c60:	53                   	push   %rbx
  400c61:	4c 29 e5             	sub    %r12,%rbp
  400c64:	31 db                	xor    %ebx,%ebx
  400c66:	48 c1 fd 03          	sar    $0x3,%rbp
  400c6a:	48 83 ec 08          	sub    $0x8,%rsp
  400c6e:	e8 05 fb ff ff       	callq  400778 <_init>
  400c73:	48 85 ed             	test   %rbp,%rbp
  400c76:	74 1e                	je     400c96 <__libc_csu_init+0x56>
  400c78:	0f 1f 84 00 00 00 00 	nopl   0x0(%rax,%rax,1)
  400c7f:	00 
  400c80:	4c 89 ea             	mov    %r13,%rdx
  400c83:	4c 89 f6             	mov    %r14,%rsi
  400c86:	44 89 ff             	mov    %r15d,%edi
  400c89:	41 ff 14 dc          	callq  *(%r12,%rbx,8)
  400c8d:	48 83 c3 01          	add    $0x1,%rbx
  400c91:	48 39 eb             	cmp    %rbp,%rbx
  400c94:	75 ea                	jne    400c80 <__libc_csu_init+0x40>
  400c96:	48 83 c4 08          	add    $0x8,%rsp
  400c9a:	5b                   	pop    %rbx
  400c9b:	5d                   	pop    %rbp
  400c9c:	41 5c                	pop    %r12
  400c9e:	41 5d                	pop    %r13
  400ca0:	41 5e                	pop    %r14
  400ca2:	41 5f                	pop    %r15
  400ca4:	c3                   	retq   
  400ca5:	90                   	nop
  400ca6:	66 2e 0f 1f 84 00 00 	nopw   %cs:0x0(%rax,%rax,1)
  400cad:	00 00 00 

0000000000400cb0 <__libc_csu_fini>:
  400cb0:	f3 c3                	repz retq 

```
```
找出關鍵程式 ==> cmp  
  400b9e:	3d 39 05 00 00       	cmp    $0x539,%eax
  400ba3:	75 27                	jne    400bcc <main+0xae>
  
  $0x539 =5*16*16 + 3*16 + 9 = 1337
```
