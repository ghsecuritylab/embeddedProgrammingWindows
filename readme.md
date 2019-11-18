# 使用 Visual Studio 2019 Community 在 Win10 下进行 STM32 嵌入式编程

作者：武汉大学计算机学院 胡继承

时间：2019年11月18日

----



多年来由于经济因素，中国的大学生及广大的小公司通常使用盗版软件进行嵌入式编程。在开源风暴的席卷下，时至今日终于有机会使用开源工具链在 Win10 下进行嵌入式编程，而且方便性及稳定性完全不亚于商业软件。想想商用数据库软件在中华日益没落的历史，可以想象嵌入式开发的开源时代已经到来，该花点时间捋捋了。本文以 STM32 系列的 ARM 芯片嵌入式开发为例子来展现开源嵌入式开发的流程，如果使用 mbed 的话也容易类推到其它 ARM 芯片的嵌入式开发。

微软在 VS2017 中便引入了嵌入式编程，经过几年的发展已经越来越成熟了。本文介绍如何使用 VS2019 社区版来进行嵌入式编程。使用 VS code 也能完成该项工作，配置方法基本类似。

基本步骤如下：
1. 使用开源工具生成框架程序
2. 使用 VS 2019 Community 进行编码和编译
3. 使用 ST-LINK/V2-1 将程序下载到电路板
4. 使用 VS 2019 Community 调试程序


## ST-LINK/V2-1引脚定义

**ST-LINK/V2-1 只能调试 STM32 系列芯片**
       
| foot | CN4 | description |
| :---: | --- | --- |
| 1 | VDD_TARGET | target VDD |
| $\color{red}{2}$ | **SWCLK SWD** | clock |
| 3 | GND | ground |
| 4 | SWDIO SWD | data I/O |
| 5 | NRST | target MCU RESET |
| 6 | SWO | reserved |

![ST-LINK_V2-1.png](ST-LINK_V2-1.png)

**调试外接电路板时需要将 CN2 两个跳线悬空**


如果不接1、3脚，会对目标MCU板的电源造成很剧烈的干扰。

![connOtherBoard.png](connOtherBoard.png)


