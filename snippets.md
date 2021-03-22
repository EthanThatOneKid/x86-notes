# x86 Snippets

> [x86 Instructions List](https://en.wikipedia.org/wiki/X86_instruction_listings)

## Toggle Sign

This snippet allows you to change a negative number to a positive number or a positive number to a negative.

```asm
mov rax, 0x8000 0000 0000 0000
push rax
movsd xmm3, [rsp]
xorpd xmm0, xmm3
```
