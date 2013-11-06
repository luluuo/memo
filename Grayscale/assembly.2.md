ԭ��������: http://www.agner.org/optimize/
# 2 ��ʼ֮ǰ

## 2.1 ��ʼ���֮ǰҪ����������

ʹ�û�࿪ʼ���֮ǰ, ��úú�����Ϊʲô��Ҫʹ�û������, ��ĳ�����Ĳ�����Ҫʹ�û�������, �Լ�ʹ��ʲô���ı�̷���. Ҫ�ǿ������Ի�������, �ܿ���ͻᷢ���Լ����˷�ʱ��, �Ż������д���Ĳ���, ʹ�û�����ɱ���������c++�ɵ��¶�, �����Ż����������Ż��Ķ���, д��һ��һ������ά���Ĵ���, ���߳���Ŵ�������޷����ԵĴ���. 

�����г��˿�ʼ���֮ǰ��Ҫ���ǵļ�����: 

* Never make the whole program in assembly. That is a waste of time. Assembly code
should be used only where speed is critical and where a significant improvement in
speed can be obtained. Most of the program should be made in C or C++. These are
the programming languages that are most easily combined with assembly code.

+ ��Ҫ�û��д��������. �ǻ��˷�ʱ��. ֻӦ����׷���ٶȶ��ҿ���ȡ�ô���ٶ������ĵط�ʹ�û�����. Ҫ��c����c++ʵ�ִ󲿷ֵĳ���. �����������׺ͻ�������ʹ�õ�������. 

* If the purpose of using assembly is to make system code or use special instructions
that are not available in standard C++ then you should isolate the part of the
program that needs these instructions in a separate function or class with a well
defined functionality. Use intrinsic functions (see p. 34) if possible.

+ ���ʹ�û���Ŀ�������ϵͳ�������ʹ��ĳЩ��׼c++���ṩ��ָ��, Ӧʹ�ú������߹����걸����ѻ�����ͳ�����������ָ��뿪��. ���ܵĻ�ʹ��αָ���(��34ҳ)

* If the purpose of using assembly is to optimize for speed then you have to identify
the part of the program that consumes the most CPU time, possibly with the use of a
**profiler**. Check if the bottleneck is file access, memory access, CPU instructions, or
something else, as described in manual 1: "Optimizing software in C++". Isolate the
critical part of the program into a function or class with a well-defined functionality.

+ ���ʹ�û���Ŀ�����Ż��ٶȾ͵��ȶ�λ���������һ����������cpuʱ��, ���ܵ���**profiler** .����ƿ���Ƿ����ļ�, �����ڴ�, CPUָ��Ǳ��ʲô, �����ֲ�1: "�Ż�c++����" �н�������. �ѳ���Ĺؼ������ú������߹����걸����������.  

* If the purpose of using assembly is to make a function library then you should clearly
define the functionality of the library. Decide whether to make a function library or a
class library. Decide whether to use static linking (.lib in Windows, .a in Linux) or
dynamic linking (.dll in Windows, .so in Linux). Static linking is usually more
efficient, but dynamic linking may be necessary if the library is called from languages
such as C# and Visual Basic. You may possibly make both a static and a dynamic
link version of the library.

+ ���ʹ�û����Ϊ����ɺ�����, Ҫ����ض����Ĺ���. �ȶ�����Ҫ��ɺ����⻹�����. �ٶ�����Ҫʹ�þ�̬����(Windows��.lib, Linux��.a)���Ƕ�̬����(Windows��.dll, Linux��.so). ��̬���Ӹ���Ч, ���Ǵ�C#����VB���õĻ�ֻ���ö�̬���ӿ���. ���ܶ�̬�;�̬�İ汾��Ҫ����. 

* If the purpose of using assembly is to optimize an embedded application for size or
speed then find a development tool that supports both C/C++ and assembly and
make as much as possible in C or C++.

+ ���ʹ�û����Ϊ���Ż�Ƕ��ʽӦ�õĿռ���ٶ�, �Ҹ�֧��C/C++�ͻ��Ŀ�������, ���Ҿ�������C/C++ʵ��. 

* Decide if the code is reusable or application-specific. Spending time on careful
optimization is more justified if the code is reusable. A reusable code is most
appropriately implemented as a function library or class library.

+ �����ǿ����õĻ���Ӧ�ö��е�. �����Ż������ô��������. �����ô�������ʵ�ʵ�ַ�ʽ�Ǻ�����������. 

* Decide if the code should support multithreading. A multithreading application can
take advantage of microprocessors with multiple cores. **Any data that must be
preserved from one function call to the next on a per-thread basis should be stored
in a C++ class or a per-thread buffer supplied by the calling program**.

+ �����Ƿ�֧�ֶ��߳�. ���߳�Ӧ�ÿ���ʹ�ö��΢������. **���߳�֮����Ҫ�����Ժ�������֮�䴫�ݵ�����Ӧ���ɵ��ó��򱣴���C++������̻߳�������**

* Decide if portability is important for your application. Should the application work in
both Windows, Linux and Intel-based Mac OS? Should it work in both 32 bit and 64
bit mode? Should it work on non-x86 platforms? This is important for the choice of
compiler, assembler and programming method.

+ ����ֲ�Զ�Ӧ�������Ƿ���Ҫ. ����Ҫ��Windows, Linux��Intel-based Mac OS�¶�������? 32λ��64λģʽ��Ҫ֧����? ��x86ƽ̨��? ��Щ����Ա�������ѡ��, ����������ѡ��ͱ�̷���������Ҫ. 

* Decide if your application should work on old microprocessors. If so, then you may
make one version for microprocessors with, for example, the SSE2 instruction set,
and another version which is compatible with old microprocessors. You may even
make several versions, each optimized for a particular CPU. It is recommended to
make **automatic CPU dispatching** (see page 137).

+ �����Ƿ�Ҫ֧�־ɵ�΢������? ����ǵĻ�, �����Ҫʵ��һ��SSE2ָ�֮��İ汾��΢��������, ��һ���汾�����;�΢����������. ��������Ϊÿ�������CPU��ʵ��һ���Ż��汾. ����ʹ��**�Զ�CPU����**(��137ҳ). 

* There are three assembly programming methods to choose between: (1) Use
intrinsic functions and vector classes in a C++ compiler. (2) Use inline assembly in a
C++ compiler. (3) Use an assembler. These three methods and their relative
advantages and disadvantages are described in chapter 5, 6 and 7 respectively
(page 34, 36 and 45 respectively).

+ �����ֻ���̷�����ѡ: (1) ��C++��������ʹ��αָ�����������. (2) ��C++��������ʹ���������. (3)ʹ�û�������. �����ַ��������ǵ���ȱ���ڵ�5, 6, 7�½���(��34, 36, 45ҳ). 

* If you are using an assembler then you have to choose between different syntax
dialects. It may be preferred to use an assembler that is compatible with the
assembly code that your C++ compiler can generate.

+ ʹ�û��������Ļ���Ҫ�ڲ�ͬ���﷨��ѡ��. (����?)����ʹ�ú����C++���������ɵĻ�������ݵĻ�������. 

* Make your code in C++ first and optimize it as much as you can, using the methods
described in manual 1: "Optimizing software in C++". Make the compiler translate
the code to assembly. Look at the compiler-generated code and see if there are any
possibilities for improvement in the code.

+ ��ʹ��C++ʵ�ֲ��Ҿ��������ֲ�1: "�Ż�C++����"�н��ܵķ����Ż���. �ñ������Ѵ��뷭��ɻ�����. �������������ɵĻ�����, �������(C++)�����Ƿ��иĽ����. 

* Highly optimized code tends to be very difficult to read and understand for others
and even for yourself when you get back to it after some time. In order to make it
possible to maintain the code, it is important that you organize it into small logical
units (procedures or macros) with a well-defined interface and calling convention and
appropriate comments. Decide on a consistent strategy for code comments and
documentation.

+ �߶��Ż��Ĵ������������˵�Ǻ����Ķ��������,��ʹ���Լ�����ʱ�������Ҳ����. Ϊ���ô����ά��, �ѻ�������֯��СһЩ���߼���λ(���̻��ߺ�), ��ѭ���õĽӿڶ���͵��ù淶, �ʵ���ע�Ͷ��Ǻ���Ҫ��. �ƶ�һ���ɳ�������ע�ͺ��ĵ�����. 

* Save the compiler, assembler and all other development tools together with the
source code and project files for later maintenance. Compatible tools may not be
available in a few years when updates and modifications in the code are needed.

+ ���������, �������������п�������, ��ͬԴ�������Ŀ�ļ�, �Ա�����ά������. ����֮����Ҫ���º��޸Ĵ����ʱ��, ���ݵĹ��߿��ܾ�û����. (����?)

## 2.2 Make a test strategy
Assembly code is error prone, difficult to debug, difficult to make in a clearly structured way,
difficult to read, and difficult to maintain, as I have already mentioned. A consistent test
strategy can ameliorate some of these problems and save you a lot of time.

## 2.2 �ƶ����Բ���

����ǰ������, �����밮����, �ѵ���, ��д����������, �Ѷ�, ����ά��. �����Ĳ��Բ��Կ��Ը�����Щ����, ��ʡ�ܶ�ʱ��. 

My recommendation is to make the assembly code as an isolated module, function, class or
library with a well-defined interface to the calling program. Make it all in C++ first. Then
make a test program which can test all aspects of the code you want to optimize. It is easier
and safer to use a test program than to test the module in the final application.

�ҵĽ������û������Գ�һ��, ģ��, ����, ����߽ӿڶԵ��������õĿ�. ��ȫ��C++ʵ��. Ȼ��дһ���������д��Ż�����Ĳ��Գ���. ʹ�ò��Գ���������ղ�Ʒ�в���ģ����ȸ���ȫҲ������. 

The test program has two purposes. The first purpose is to verify that the assembly code
works correctly in all situations. And the second purpose is to test the speed of the
assembly code without invoking the user interface, file access and other parts of the final
application program that may make the speed measurements less accurate and less
reproducible.

���Գ���������Ŀ��. ��һ����֤�����������з�֧�¶���������. ����ǲ��Ի�������ٶ�ʱ, ���Բ���������, �������ļ�, Ҳ������Ӧ�ó������������, �������Խ����׼ȷ���ҿ�����. 

You should use the test program repeatedly after each step in the development process and
after each modification of the code.

���������е�ÿһ��, ÿһ�ζԴ�����޸�֮��, ��Ӧ��ʹ�ò��Գ���. 

Make sure the test program works correctly. It is quite common to spend a lot of time
looking for an error in the code under test when in fact the error is in the test program.
There are different test methods that can be used for verifying that the code works correctly.
A white box test supplies a carefully chosen series of different sets of input data to make
sure that all branches, paths and special cases in the code are tested. A black box test
supplies a series of random input data and verifies that the output is correct. A very long
series of random data from a good random number generator can sometimes find rarely
occurring errors that the white box test hasn't found.

��֤���Գ�����ȷ�ع���. ���ܶ�ʱ����ݲ��Խ���ڴ��������Ҵ���, ���ʵ�����ǲ��Գ������������������Ҳ����. 

�и��ֲ��Է�������������֤�����Ƿ�������. �׺в����ṩһϵ�о���ϸѡ���������ݼ��ϱ�֤�����еĸ�����֧·�����������ᱻ���Ե�. �ںв����ṩһϵ������������ݲ���֤�������Ƿ���ȷ. ���㲢���㹻����������ɻ�����ʱ���Է��ְ׺в��Է��ֲ��˵ļ�С���ʴ���.

The test program may compare the output of the assembly code with the output of a C++
implementation to verify that it is correct. The test should cover all boundary cases and
preferably also illegal input data to see if the code generates the correct error responses.
The speed test should supply a realistic set of input data. A significant part of the CPU time
may be spent on branch mispredictions in code that contains a lot of branches. The amount
of branch mispredictions depends on the degree of randomness in the input data. You may
experiment with the degree of randomness in the input data to see how much it influences
the computation time, and then decide on a realistic degree of randomness that matches a
typical real application.

���Գ������ͨ���ԱȻ����������C++�����������֤�Ƿ���ȷ. ����Ӧ�������б߽��������������һЩ�Ƿ���������֤�������ɵĴ������Ƿ���ȷ. 

�ٶȲ���Ӧ�ṩ��ʵ��������. �ڰ����ܶ��֧�Ĵ�����, CPU��ʱ��ܴ�һ���ֿ��������ڴ���ķ�֧Ԥ����. ����ķ�֧Ԥ������ȡ�����������ݵ�����̶�. �����������һ���������ݵ�����̶ȶԼ���ʱ���Ӱ��, Ȼ����һ�����ϵ�����ʵӦ��(����)�������. 

An automatic test program that supplies a long stream of test data will typically find more
errors and find them much faster than testing the code in the final application. A good test
program will find most errors, but you cannot be sure that it finds all errors. It is possible that
some errors show up only in combination with the final application.

�ṩ���������������Զ������Գ���ͨ���������������в��Ը��������ҵ�����. �õĲ��Գ�������ҵ��󲿷ִ���, �����㲻�ܱ�֤���ҵ����д���. �п�����Щ����ֻ�������ղ�Ʒ��(ģ��)�������ʱ�Ż����. 

2.3 Common coding pitfalls
The following list points out some of the most common programming errors in assembly
code.
1. Forgetting to save registers. Some registers have callee-save status, for example
`EBX`. These registers must be saved in the prolog of a function and restored in the
epilog if they are modified inside the function. Remember that the order of `POP`
instructions must be the opposite of the order of `PUSH` instructions. See page 28 for a
list of callee-save registers.

## 2.3 �����������
�����г���һЩ�����ʱ������Ĵ���.
1. ���Ǳ���Ĵ���. ��Щ�Ĵ������������״̬, ����`EBX`. ����������޸�����Щ�Ĵ�����״̬, ��Ҫ�ں�����ʼʱ��������, ���˳�ǰ�ظ�����. ��ס`POP`ָ���˳��Ҫ��`PUSH`ָ���˳�������෴. �����߻ᱣ��ļĴ����б���28ҳ. 

2. Unmatched PUSH and POP instructions. The number of PUSH and POP instructions
must be equal for all possible paths through a function. Example:

Example 2.1. Unmatched push/pop
	<pre><code>
	push ebx
	test ecx, ecx
	jz Finished
	...
	pop ebx
	Finished: ; ����! ���Ҫ��pop ebx֮ǰ��ת. 
	ret
	</code></pre>
Here, the value of EBX that is pushed is not popped again if ECX is zero. The result is
that the RET instruction will pop the former value of EBX and jump to a wrong
address.

2. ����Ե�`PUSH`��`POP`ָ��. �ڷ��������п���·����, `PUSH`��`POP`ָ�����Ŀ���������. ����:

����2.1. ����Ե� push/pop
	<pre><code>
	push ebx
	test ecx, ecx
	jz Finished
	...
	pop ebx
	Finished: ; ����! ���Ҫ��pop ebx֮ǰ��ת. 
	ret
	</code></pre>
�˴���`ECX`��ֵΪ0��ѹջ��`EBX`û�г�ջ. �������`RET`�ᵯ��`EBX`֮ǰ��ֵ�Ӷ���������ĵ�ַȥ. 

3. Using a register that is reserved for another purpose. Some compilers reserve the
use of EBP or EBX for a **frame** pointer or other purpose. Using these registers for a
different purpose in inline assembly can cause errors.

3. �����������õļĴ���. ��Щ����������`EBX`��`EBP`����**֡**ָ����������ô�. �����������ʹ����Щ�Ĵ��������������ܻ��������. 

4. Stack-relative addressing after push. When addressing a variable relative to the
stack pointer, you must take into account all preceding instructions that modify the
stack pointer. Example:
Example 2.2. Stack-relative addressing
	</code></pre>
		mov [esp+4], edi
		push ebp
		push ebx
		cmp esi, [esp+4] ; Probably wrong!
	</code></pre>
Here, the programmer probably intended to compare ESI with EDI, but the value of
ESP that is used for addressing has been changed by the two PUSH instructions, so
that ESI is in fact compared with EBP instead.

4. ѹջ������ջȡַ. ���ջָ��Ա���ȡַʱ, �����֮ǰ�޸�ջָ��Ĳ��������ǽ�ȥ. ����:

�� 2.2. ���ջȡַ
	</code></pre>
		mov [esp+4], edi
		push ebp
		push ebx
		cmp esi, [esp+4] ; ���ܳ���!
	</code></pre>
�ڴ˳���Ա������ͼ�Ƚ�`ESI`��`EDI`, ����`ESP`�Ĵ�����ֵ�Ѿ�������`PUSH`�����޸���, ����`ESI`ʵ�����ں�`EBP`���Ƚ�. 

5. Confusing value and address of a variable. Example:
Example 2.3. Value versus address (MASM syntax)
	<pre><code>
	.data
	MyVariable DD 0 ; Define variable
	.code
	mov eax, MyVariable ; Gets value of MyVariable
	mov eax, offset MyVariable; Gets address of MyVariable
	lea eax, MyVariable ; Gets address of MyVariable
	mov ebx, [eax] ; Gets value of MyVariable through pointer
	mov ebx, [100] ; Gets the constant 100 despite brackets
	mov ebx, ds:[100] ; Gets value from address 100
	</code></pre>

5. ����������ֵ�͵�ַ. ����: 
�� 2.3. ֵ���ַ(MASM�﷨)
	<pre><code>
	.data
	MyVariable DD 0 ; �������
	.code
	mov eax, MyVariable ; ��ȡ����MyVariable��ֵ
	mov eax, offset MyVariable; ��ȡMyVariable�ĵ�ַ
	lea eax, MyVariable ; ��ȡMyVariable�ĵ�ַ
	mov ebx, [eax] ; ͨ��ָ���ȡMyVariable��ֵ
	mov ebx, [100] ; ��������, ��ȡ����100
	mov ebx, ds:[100] ; �ӵ�ַ100��ȡ����
	</code></pre>

6. Ignoring calling conventions. It is important to observe the calling conventions for
functions, such as the order of parameters, whether parameters are transferred on
the stack or in registers, and whether the stack is cleaned up by the caller or the
called function. See page 27.

6. ���Ե��ù���. ���ص��ù����Ǻ���Ҫ��, ���������˳��, ������ͨ��ջ���ǼĴ�������, �Լ��������߻��߱����ú�����û�����ջ. ��27ҳ. 

7. Function name **mangling**. A C++ code that calls an assembly function should use
extern "C" to avoid name mangling. Some systems require that an underscore (_)
is put in front of the name in the assembly code. See page 30.

7. ��������**ѹ��**. C++������û�ຯ��Ҫʹ��extern "C"��������ѹ��. ��ЩϵͳҪ���ຯ������ǰ���»���`_`. ��30ҳ. 

8. Forgetting return. A function declaration must end with both RET and ENDP. Using
one of these is not enough. The execution will continue in the code after the
procedure if there is no RET.

8. ���Ƿ���. ��������������`RET`��`ENDP`��β. ֻʹ��һ���ǲ�����. û��`RET`�Ļ����̵���֮�����������ڴ�����ִ��. 

9. Forgetting stack alignment. The stack pointer must point to an address divisible by
16 before any call statement, except in 16-bit systems and 32-bit Windows. See
page 27.

9. ����ջ����. ���κε���֮ǰջָ�����ָ����Ա�16�����ĵ�ַ, ������16λ����32λWindows��. ��27ҳ. 

10. Forgetting **shadow space** in 64-bit Windows. It is required to reserve 32 bytes of
empty stack space before any function call in 64-bit Windows. See page 30.

10. ����64λWindows��**shadow space**. ��64λWindows���κκ�������֮ǰ��Ҫ����32 ���ֽڵĿ�ջ�ؼ�. ��30ҳ. 

11. Mixing calling conventions. The calling conventions in 64-bit Windows and 64-bit
Linux are different. See page 27.

11. ���õ��ù���. 64λWindows��64λLinux�ĵ��ù����ǲ�ͬ��. ��27ҳ. 

12. Forgetting to clean up floating point register stack. All floating point stack registers
that are used by a function must be cleared, typically with FSTP ST(0), before the
function returns, except for ST(0) if it is used for return value. It is necessary to keep
track of exactly how many floating point registers are in use. If a functions pushes
more values on the floating point register stack than it pops, then the register stack
will grow each time the function is called. An exception is generated when the stack
is full. This exception may occur somewhere else in the program.

12. ������ո���Ĵ���ջ. ���к������õ��ĸ���ջ�Ĵ�����Ҫ�����, ͨ��ͨ���ڷ���ǰ����ָ��`FSTP ST(0)`�����, ����`ST(0)`, �������������ŷ���ֵ�Ļ�. �б�Ҫ��¼�ж��ٸ�����Ĵ�����ʹ��. ���һ������ѹջ������Ĵ���ջ�Ĵ����ȳ�ջ�Ĵ�����, �Ĵ���ջ�ͻ�ÿ�κ������ö�����. ջ�����ʱ��ͻ�����쳣. ����쳣�����ڳ��������ط�ð����. 

13. Forgetting to clear MMX state. A function that uses MMX registers must clear these
with the EMMS instruction before any call or return.

13. �������MMX״̬. ʹ��MMx�Ĵ����ĺ�����Ҫ��`EMMS`ָ���ڵ��û򷵻�ǰ�������. 

14. Forgetting to clear YMM state. A function that uses YMM registers must clear these
with the VZEROUPPER or VZEROALL instruction before any call or return.

14. �������YMM״̬. ʹ��YMM�Ĵ����ĺ���Ҫ�ڵ��û򷵻�ǰʹ��`VZEROUPPER`��`VZEROALL`�������. 

15. Forgetting to clear direction flag. Any function that sets the direction flag with STD
must clear it with CLD before any call or return.

15. ������շ�����λ. �κ�ʹ��`STD`���÷�����λ�ĺ�����Ҫ�ڵ��û򷵻�ǰʹ��`CLD`�����. 

16. Mixing signed and unsigned integers. Unsigned integers are compared using the JB
and JA instructions. Signed integers are compared using the JL and JG instructions.
Mixing signed and unsigned integers can have unintended consequences.

16. �����з��ź��޷�������. �޷�������ͨ��`JB`��`JA`���Ƚ�. �з�������ͨ��`JL`��`JG`. �����з��ź��޷����������������벻���ĺ��. 

17. Forgetting to scale array index. An array index must be multiplied by the size of one
array element. For example mov eax, MyIntegerArray[ebx*4].

17. ���ǰ�����������������. ��������Ҫ��������Ԫ�صĴ�С. ����`mov eax, MyIntegerArray[ebx*4]`. 

18. Exceeding array bounds. An array with n elements is indexed from 0 to n - 1, not
from 1 to n. A defective loop writing outside the bounds of an array can cause errors
elsewhere in the program that are hard to find.

18. ����Խ��. n��Ԫ�ص�����������0��n-1, ����1��n. �������ѭ����������Խ��д��, ���ڳ����������ط���������, �����ҵ�. 

19. Loop with ECX = 0. A loop that ends with the LOOP instruction will repeat 232 times if
ECX is zero. Be sure to check if ECX is zero before the loop.

19. ��`ECX=0`����ѭ��. `ECX`����0�Ļ���`LOOP`ָ���β��ѭ���ᱻִ��232��. ȷ����ѭ������֮ǰ`ECX`����0. 

20. Reading carry flag after INC or DEC. The INC and DEC instructions do not change the
carry flag. Do not use instructions that read the carry flag, such as ADC, SBB, JC, JBE,
SETA, etc. after INC or DEC. Use ADD and SUB instead of INC and DEC to avoid this problem. 

20. ��`INC`��`DEC`֮���**carry**���λ. `INC`��`DEC`ָ����޸�**carry** ���λ. ��Ҫ�ڵ�������֮��ʹ������`ADC`, `SBB`, `JC`, `JBE`, `SETA`��ָ���ȡ**carry**���λ. ʹ��`ADD`��`SUB`����`INC`��`DEC��������������. 