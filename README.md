## 写在前边
由于是在受不了公司提供的256G硬盘的MacBook Pro   
便动了安装一台黑苹果的念头，加上有同事之前的安利 这事情也顺理成章的进行起来了  
本文记录了整个黑苹果的装机步骤，踩坑，以及一些知识点，仅当笔记参考  

## 2022年更新
EFI_Monterey 支持macos 12.1 的EFI  
自己折腾不动了 淘宝找人装的 199 解决你的忧愁  
另外M1芯片出来之后 黑苹果 且行且珍惜  

## 黑苹果装机步骤
### 前置准备
#### 硬件准备 
        cpu Intel i5 10400
        主板 华擎B460M Pro4
        显卡 蓝宝石RX 580 8G 2048sp 白金版（巨坑～～）
        内存 金士顿 16G*2 
        硬盘 西部数据 蓝盘 1T
        无线网卡 fenvi BCM94360CD 黑苹果免驱动
        机箱 鱼巢S5
        电源 全汉450w SFX电源
        另外还需要准备 可以上网的windows电脑一台 16G以上U盘一个
 

#### 软件准备 
        windows 安装程序  非必须
        macOS Cataline 10.15.6 镜像
        DiskGenius      硬盘分区工具
        BalenaEtcher    用于将黑苹果镜像写入U盘    
        GPU-Z           用于查看显卡具体信息
        AMDVbFlash      用于刷显卡Bios
        适合自己的EFI     

[win10安装 官网](https://www.microsoft.com/zh-hk/software-download/windows10ISO)  
[黑果小兵 macOS Cataline 10.15.6](https://blog.daliansky.net/macOS-Catalina-10.15.6-19G73-Release-version-with-Clover-5119-original-image-Double-EFI-Version-UEFI-and-MBR.html)  
[DiskGenius](https://www.diskgenius.cn/)  
[GPU-Z](https://www.techpowerup.com/gpuz/)  
[AMDVbFlash](https://www.techpowerup.com/download/ati-atiflash/)  


### 装机过程
        0. 组装好机器 成功点亮Bios
        1. 在windows上 提前下载好镜像 以及相关软件
        2. 格式化U盘 使用BalenaEtcher 将镜像写入U盘 （注意管理员身份运行，U盘提前格式化好）
        3. 使用DiskGenius将适合自己的EFI文件 替换 引导U盘中 的EFI文件（我使用的是OC 就将OC替换 并改名）
        4. 插入U盘 修改主板Bios启动项为U盘 顺理的话 可以看到OC的启动项选择
        5. 一路执行下去 先使用DiskUtil 将目标盘抹掉 然后再安装
        6. 顺利的话 可以一路安装成功
        7. 安装完成后将U盘的EFI拷贝到硬盘上
           diskutil list 
           diskutil mount <disk0s1>
           diskutil mount <disk1s1>
           挂载完毕之后 手动拷贝即可
        8. 关机 拔掉U盘 重启之后 可以正常进入系统 就表示成功
        9. 使用oc config 生成三码 生成之后 登陆icloud 等云服务可以正常使用
           建议断网生成 并且不要轻易改变 不然存在被封账号的风险
具体装机参考视频

### 遇到的坑
    1. win10 安装 如何通过命令格式化硬盘
    https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-setup-installing-using-the-mbr-or-gpt-partition-style
    2. macOS 安装 如何通过命令格式化硬盘
    3. 黑苹果安装过后 显卡7MB 不识别 原因很多 我的原因是 RX580-8G-2028sp 驱动不支持 
    只能通过 将显卡的Bios刷成 Rx570才可以识别

#### Rx-580-8G-2048 刷570Bios 
    1. 使用GPU-Z 查看自己显卡的具体信息 关注两个点 显存类型 颗粒类型（我的是三星）
    2. 在xxx上查找类似的型号
    3. 使用AMDVbFlash 通过命令 刷Bios 
    4. 刷完成之后 重启一下 再通过GPU-Z 查看 是否显示的显存类型、大小 是否跟目标一致
       不一致一般启动会失败 
    5. 刷显卡Bios必须在win上进行 建议在机器上装两块硬盘 一块win 一块mac 通过控制启动项 来切换系统 
    6. 刷完成之后 可以切到mac系统上看 显卡类型可以正常显示出来 就表示成功了

### 知识资料
    1. 黑果小兵
    2. 为什么黑苹果主流 intel cpu + amd 显卡
    3. xclient 
    4. 显卡查询
    5. 黑苹果配置推荐表





