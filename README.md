HITwh NSCSCC Team | 哈尔滨工业大学（威海）全国大学生计算机系统能力培养大赛小组

# 知识版权 Copyright

文档：版权 ® [哈尔滨工业大学（威海）全国大学生计算机系统能力培养大赛小组](https://github.com/hitwh-nscscc)  2019

Documents: Copyright ® [HITwh NSCSCC Team](https://github.com/hitwh-nscscc)  2019 

## 版权许可 - 中文

本作品文档采用知识共享 署名-非商业性使用-相同方式共享 4.0 国际 许可协议进行许可。

要查看该许可协议，可访问 http://creativecommons.org/licenses/by-nc-sa/4.0/ 或者写信到 Creative Commons, PO Box 1866, Mountain View, CA 94042, USA。

## Copyright License - English

Documents containing in this work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. 

To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.



# 跟我一步一步实现简单的五级流水MIPS

作为体系结构实验课前的一次讲解，本系列文档参考《自己动手写 CPU》一书中的实现步骤，将体系结构课程教授的知识具体化，让同学们完全靠自己实现一个简单的五级流水架构以深入理解课本中的理论知识，将其运用到实际，并最终独立地完成此次实验。

## 基本提纲

本文档将用以下的顺序，层层深入，一步一步指导同学们实现一个**最简单的（ORI指令）、带数据前推及流水线暂停的32位静态五级流水MIPS**，之后大家举一反三来完成这次体系结构实验：

1. 单周期、多周期和流水线处理器；
2. 浅析计组课设中制作的CPU；
3. 什么是五级流水、数据前推、流水线暂停；
4. 一个静态五级流水MIPS的最基本架构；
5. 第一条指令 ORI 的实现：
   1. 一个原始的五级流水线结构；
   2. IF / ID / EX / MEM / WB 阶段的分别实现；
   3. VIVADO 行为仿真；
   4. 再次拿出 5.1 提及的原始的五级流水线结构，回顾所学内容。
6. 流水线数据相关问题；
7. ORI 的数据相关；
8. 数据相关的解决办法介绍：
   1. 流水线暂停；
   2. 数据前推；
   3. 编译器调度（仅提及）；
9. **ORI 指令数据相关的解决办法 1 - 数据前推：**
   1. 针对 ORI 指令的数据前推的原理；
   2. 修改相应模块；
   3. VIVADO 行为仿真；
   4. 修改后的五级流水线结构（与原始的五级流水线结构对比）；
10. **ORI 指令数据相关的解决办法 2 - 流水线暂停：**
   1. 针对 ORI 指令的流水线暂停的原理；
   2. 修改相应模块；
   3. VIVADO 行为仿真；
   4. 修改后的五级流水线结构（与原始的五级流水线结构对比）；
11. MIPS 交叉编译环境的搭建指南。

## 参考资料

《自己动手写 CPU》 - 雷思磊