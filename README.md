# opencore-hackintosh-hasee-k610c-i7-4702mq-hd4600-vt1802
## 电脑型号及其配置
- 神舟k610c
- i7-4702mq
- 显卡: 核显hd4600, 独显gt750m（已屏蔽）
- 声卡: VIA VT1802P
- 无线网卡: Intel(R) Dual Band Wireless AC 7260

## 相关情况
- 本EFI目前使用的是OC0.7.3，使用[国光黑苹果教程](https://apple.sqlsec.com)一步步配置的，系统是BigSur11.7.9，小版本已试验过能正常升级。
- CPU变频正常。
- 睡眠有点问题。
- 核显已驱动，独显已屏蔽。核显刚开始有开机花屏，需要合上显示器再打开才正常，然后通过注入EDID修复了。但是又发现打开vscode和谷歌浏览器等软件会闪屏和花屏，然后通过增加WhateverGreend驱动教程中，针对[移动端h4600的核显布丁](https://github.com/acidanthera/WhateverGreen/blob/master/Manual/AzulPatcher4600_equivalent.plist)相关的修补参数，才成功完美驱动。
- 声卡驱动了一半，有声音，但是没有麦克风。通过`AppleALC.kext`来驱动，启动参数增加`alcid=33`（也可以尝试其他id，具体请查看`AppleALC.kext`的官方建议），而且根据OC教程[修复IRQ冲突 (SSDT-HPET + OC_Patches.plist)](https://sumingyd.github.io/Getting-Started-With-ACPI/Universal/irq.html)自己生成IRQ的SSDT，并且在`ACPI->patch`中增加了相关补丁，才有的声音，麦克风暂时没需求，后续再研究。
- 无线网卡wifi和蓝牙都正常，但是无法使用隔空投送。
- USB端口是自己通过国光教程中用`USBToolBox`在windows下定制的，大家需要自己根据教程定制自己的端口。
