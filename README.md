# Secure Memory with Kotlin/Java and NDK

Added Clear memory button, that clear the used memory for the structure. Similar approach can be used for security storage of sensitive information. (keys, secret, Credit Card data) that way you make sure it is removed from device memory after usage.


Java objects do not have a fixed location in memory on the opposite to C++ objects. They may be moved during their life me. It means Credit Card can by anywhere until Garbage collected and the memory allocation would be use by another object.

Solution for maximum security would be to hande Credit Card data input with NDK (C/C++) and clean the object after use.

For examle, here I stored int 123 (hex 0x7b)

(lldb) x/10x 0xd7bfb040
0xd7bfb040: 0xec6a3c00 0x00000002 0x0000007b 0x00000000
0xd7bfb050: 0x00000000 0x00000000 0x00000000 0x00000000
0xd7bfb060: 0x00000000 0x00000000

After clearing (Clear button) the whoe struct is gone:


(lldb) x/10x 0xd7bfb040
0xd7bfb040: 0x00000000 0x00000000 0x00000000 0x00000000
0xd7bfb050: 0x00000000 0x00000000 0x00000000 0x00000000
0xd7bfb060: 0x00000000 0x00000000




![](/secure-memory.png)


Based on this:

https://yalantis.com/blog/android-ndk-the-interaction-between-kotlin-and-c-c-plus-plus/

https://github.com/KucherenkoIhor/KotlinWithAndroidNdk


