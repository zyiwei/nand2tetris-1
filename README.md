# 计算机系统要素，从零开始构建现代计算机（nand2tetris）
课程官网：https://www.nand2tetris.org//

相关评论：https://book.douban.com/review/7115224/

搬运的课程【中字】：https://www.bilibili.com/video/av80737268

Coursera课程：https://www.coursera.org/learn/build-a-computer/home/welcome

CSDN关于实现的具体介绍：https://blog.csdn.net/qq_41634283/article/details/103991353

课程论坛：http://nand2tetris-questions-and-answers-forum.32033.n3.nabble.com/
## 课程简介
本书通过展现简单但功能强大的计算机系统之构建过程，为读者呈现了一幅完整、严格的计算机应用科学大图景。本书作者认为，理解计算机工作原理的最好方法就是亲自动手，从零开始构建计算机系统。 通过12个章节和项目来引领读者从头开始，本书逐步地构建一个基本的硬件平台和现代软件阶层体系。在这个过程中，读者能够获得关于硬件体系结构、操作系统、编程语言、编译器、数据结构、算法以及软件工程的详实知识。通过这种逐步构造的方法，本书揭示了计算机科学知识中的重要成分，并展示其它课程中所介绍的理论和应用技术如何融入这幅全局大图景当中去。
全书基于“先抽象再实现”的阐述模式，每一章都介绍一个关键的硬件或软件抽象，一种实现方式以及一个实际的项目。完成这些项目所必要的计算机科学知识在本书中都有涵盖，只要求读者具备程序设计经验。本书配套的支持网站提供了书中描述的用于构建所有硬件和软件系统所必需的工具和资料，以及用于12个项目的200个测试程序。
全书内容广泛、涉猎全面，适合计算机及相关专业本科生、研究生、技术开发人员、教师以及技术爱好者参考和学习
## 章节内容简介
#### 1、布尔逻辑
本章需要实现一下基本逻辑门电路，了解一些数字电路内容即可完成项目。都是基于Nand门（与非门）来实现的，当然在实现其他门电路的时候，可以使用已经实现的门电路。使用其他方式实现也可以<br/>
- and and16 （与门，16位按位与）
- or or16 or8way （或门，16位按位或，8位全或）
- not not16 （非门，16位按位非）
- xor （异或）
- mux mux16 mux4way16 mux8way16 （2选1选择器，16位2选1选择器，16位4选1选择器，16位8选1选择器）
- dmux dmux4way dmux8way （解复用器，解4路复用，解8路复用）

#### 2、布尔运算<br/>
- 16位加法器，半加器，全加器
- 增量器
- ALU

#### 3、时序逻辑<br/
- 1bit寄存器，16bit寄存器
- RAM8，RAM64，RAM512，RAM4K，RAM16K
- 程序计数器PC

#### 4、机器语言<br/>
- 乘法程序：该程序的输入值存储在R0和R1中。程序计算R0*R1的值并将其存入R2。
- I/O处理程序

#### 5、计算机体系结构<br/>
- CPU：构建一个简单的CPU
- Memory：构建一个简单的内存单元
- Computer：将CPU和Memory连接起来，完成一个完整的计算机平台

#### 6、汇编编译器<br/>
- 用高级语言完成一个汇编编译器

本项目中使用Java实现，但是在进行编译汇编程序文件的时候，需要手动在Assembler类中修改文件路径，并没有提供命令行式的使用方式

#### 7、虚拟机I：堆栈运算<br/>
- 用高级语言完成一个虚拟机语言翻译器，该翻译器能够将高级语言的中间代码翻译成汇编语言。本章主要完成的命令有算术逻辑命令和内存访问命令

本项目中使用Java实现，但是在进行翻译程序文件的时候，需要手动在VMTranslator类中修改文件路径，并没有提供命令行式的使用方式

#### 8、虚拟机II：程序控制<br/>
- 用高级语言完成一个较完善的虚拟机语言翻译器，该翻译器可以支持的命令有算术逻辑命令，内存访问命令，程序控制和函数调用命令

本项目使用Java实现，但是在形成程序翻译的时候，需要手动在VMTranslator类中修改文件路径（可以是指定的汇编语言文件，也可以是包含多个相关的汇编语言文件的文件夹），并没有提供命令行式的使用方式。预计在完成本课程后，创建加载引擎，使得该编译器可以在cmd下使用命令来进行操作。

#### 9、高级语言<br/>

本章重点介绍了Jack语言的语法和特性。项目是演示Jack语言的运行，并没有难度。

#### 10、编译器I：语法分析<br/>

- 用高级语言完成一个编译器的语法分析部分。主要使用Java来完成，在使用的时候需要手动修改类中的文件路径，计划在之后进行优化，提供命令式调用。
- 该编译器目前还只是在实现的层面上，也就是未进行优化。在模块之间的解耦，对象的封装，以及加载引擎，输出路径方面还未做处理，需要手动的进行修改
- 优化目标：
  - 提高各方法之间的独立性。在目前设计的类中，比如`compileDo`方法，在进入该方法时，do语句的第一个token已经被获取到，而实际上，应该通过该方法进行获取第一个token。在前期写的一些方法都是这么做的，后期写的一些处理犯法都比较好些。
  - 减少代码冗余。目前写的文件中只在比较明显的地方考虑了代码的重用，在一些复杂的地方并未考虑代码的重用，比如`compileTerm`方法非常复杂。里面的逻辑也非常的混乱
  - 写清注释。目前的注释只是简单的提示，阅读起来不易理解。
- 关于.xml文件的说明：
  - 项目源文件可能存在错误。expressionList和parameterList的起止标签不在一行，进行比较的时候可能会出问题。但本项目中的文件都已修改好。
  - xxxG.xml是由Java代码生成的xml文件，G取自generate。
  - 本项目并没有对tokens做xxxT.xml的输出，因为，这一步比较简单，而且tokens有问题会直接反映在后面的处理中。如果你想将错误分治处理，那么最好做一下这个的比较。

另外的一点经验是，要快速的实现一个可运行的程序，然后在调式中改进，这样会非常的高效。最后可以放心的是，本项目的所有文件都以通过测试。

11、编译器II：代码生成<br/>
12、操作系统<br/>
13、后续挖掘
