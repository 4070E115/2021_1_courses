# Professional Assembly Language
```
Professional Assembly Language
Richard Blum

ISBN: 978-0-764-57901-1 February 2005 576 Pages
https://book.douban.com/subject/1446250//
https://www.wiley.com/en-us/Professional+Assembly+Language-p-9780764579011
原始碼可由網站下載  code.tgz

課程大綱
http://www.hzcourse.com/web/teachRes/detail/1804/210
```
```
第一部分 組合語言程式設計環境基礎
第1章 什麼是組合語言
第2章 IA-32平臺
第3章 相關的工具
第4章 組合語言程式範例

第二部分 組合語言程式設計基礎
第5章 傳送資料
第6章 控制執行流程
第7章 使用數位
第8章 基本數學功能
第9章 高級數學功能
第10章 處理字串
第11章 使用函數
第12章 使用Linux系統調用

第三部分 高級組合語言技術
第13章 使用內聯彙編
第14章 調用彙編庫
第15章 優化常式
第16章 使用檔
第17章 使用高級IA-32特性
```
```
第一部分 組合語言程式設計環境基礎
第1章 什麼是組合語言
1.1 處理器指令
1.1.1 指令碼處理
1.1.2 指令碼格式
1.2 高階語言
1.2.1 高階語言的種類
1.2.2 高階語言的特性
1.3 組合語言
1.3.1 操作碼助記符
1.3.2 定義資料
1.3.3 命令
1.4 小結
第2章 IA-32平臺
2.1 IA-32處理器的核心部分
2.1.1 控制單元
2.1.2 執行單元
2.1.3 寄存器
2.1.4 標誌
2.2 IA-32的高級特性
2.2.1 x87浮點單元
2.2.2 多媒體擴展
2.2.3 流化SIMD擴展
2.2.4 超執行緒
2.3 IA-32處理器系列
2.3.1 Intel處理器
2.3.2 非Intel處理器
2.4 小結
第3章 相關的工具
3.1 開發工具
3.1.1 彙編器
3.1.2 連接器
3.1.3 調試器
3.1.4 編譯器
3.1.5 目標代碼反彙編器
3.1.6 簡檔器
3.2 GNU彙編器
3.2.1 安裝彙編器
3.2.2 使用彙編器
3.2.3 關於操作碼語法
3.3 GNU連接器
3.4 GNU編譯器
3.4.1 下載和安裝gcc
3.4.2 使用gcc
3.5 GNU調試器程式
3.5.1 下載和安裝gdb
3.5.2 使用gdb
3.6 KDE調試器
3.6.1 下載和安裝kdbg
3.6.2 使用kdbg
3.7 GNU objdump程式
3.7.1 使用objdump
3.7.2 objdump範例
3.8 GNU簡檔器程式
3.8.1 使用簡檔器
3.8.2 簡檔範例
3.9 完整的彙編開發系統
3.9.1 Linux基礎
3.9.2 下載和運行MEPIS
3.9.3 新的開發系統
3.10 小結
第4章 組合語言程式範例
4.1 程式的組成
4.1.1 定義段
4.1.2 定義起始點
4.2 創建簡單程式
4.2.1 CPUID指令
4.2.2 範例程式
4.2.3 構建可執行程式
4.2.4 運行可執行程式
4.2.5 使用編譯器進行彙編
4.3 偵錯工具
4.4 在組合語言中使用C庫函數
4.4.1 使用printf
4.4.2 連接C庫函數
4.5 小結
```

# 
```
#cpuid.s Sample program to extract the processor Vendor ID
.section .data
output:
   .ascii "The processor Vendor ID is 'xxxxxxxxxxxx'\n"
.section .text
.globl _start
_start:
   movl $0, %eax
   cpuid
   movl $output, %edi
   movl %ebx, 28(%edi)
   movl %edx, 32(%edi)
   movl %ecx, 36(%edi)
   movl $4, %eax
   movl $1, %ebx
   movl $output, %ecx
   movl $42, %edx
   int $0x80
   movl $1, %eax
   movl $0, %ebx
   int $0x80
```
```
#cpuid2.s View the CPUID Vendor ID string using C library calls
.section .data
output:
    .asciz "The processor Vendor ID is '%s'\n"
.section .bss
    .lcomm buffer, 12
.section .text
.globl _start
_start:
    movl $0, %eax
    cpuid
    movl $buffer, %edi
    movl %ebx, (%edi)
    movl %edx, 4(%edi)
    movl %ecx, 8(%edi)
    pushl $buffer
    pushl $output
    call printf
    addl $8, %esp
    pushl $0
    call exit
```
