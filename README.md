# V202.0.2-测试版  
 作者提示：此版本为测试版未完善
 由于需要每个服务器都有角色才能拿到具体IP和port，作者资源有限大部分服务器IP+port无法获取，需要使用者自行补全“servicelist.ini”信息后才能测试全部服务器连接  


#### 一、 应用程序使用说明 “FF14服务器测试V202.0.2.exe”  
 1.使用前请关闭杀毒软件，部分杀毒软件会随着病毒库升级产生误报  
 2.下载应用包：FF14服务器测试V202.0.2.zip  
 3.选择 “服务器” 点击 “启动检测” 即可正常检测服务是否开服  


#### 二、ini配置文件使用说明 “servicelist.ini”
;必须填写和游戏内一样的服务器名称  
;服务器名需要完整准确 如："拉诺西亚"，不可直接写"拉诺"  
;服务器IP->服务器mane->服务器port  3个对应必填,如下例1  
;例1：   服务器IP  ->    "拉诺西亚=109.244.5.43"  
;        服务器name->    "01=拉诺西亚"  
;        服务器port->    "拉诺西亚=55021"  

---------------------------------------------------------  
#### 实例：

[Beep]  
 蜂鸣声提示=1 ;该功能是增加提示音，如不需要声音提示 将“1”改为“0”， 默认值为“1”

[servicelist]  
 陆行鸟登录大厅=109.244.5.5  
 拉诺西亚=109.244.5.43  
 幻影群岛=109.244.5.45  
 红玉海=109.244.5.41  
 莫古力登录大厅=109.244.5.162  
 猫小胖登录大厅=116.211.8.5  

[servicename]  
 00=陆行鸟登录大厅  
 01=拉诺西亚  
 02=幻影群岛  
 03=红玉海  
 09=莫古力登录大厅  
 16=猫小胖登录大厅  

[serviceport]  
 陆行鸟登录大厅=54994  
 拉诺西亚=55021  
 幻影群岛=55025  
 红玉海=55028  
 莫古力登录大厅=54993  
 猫小胖登录大厅=116.211.8.5
 
---------------------------------------------------------  
备注: [servicename] 编号是根据大区服务器分配的，陆行鸟总共8个大区，00为登录大厅 01-08 可以填写游戏服务器信息  
     [servicelist] [serviceport] 填写无规则，根据游戏内实际服务器名称和获取到的ip+port填写即可  
原理：采用Socket网络发包       
     
建议测试方法：最终测试结果仅供参考  
 1：全区维护->测登录大区  
 2：个别服务器维护->测该服务器  
 假如游戏服务器和游戏大厅通信后，还无法通过游戏大厅进入游戏服务器，可能是SQ官方内部人员在测试正式机，未开放大厅与服务器关联，这种时候只供数据参考  
 
关于IP-Port说明  
FF14连接工作工程：  
（用户客户端）->(ISP网络)->(启动器三大区启动path独立3个地址)->(登录服务器sdlogin)->(游戏大厅)->(分流服务器：映射到各个服务器独立IP+端口)  
例：  
（用户本机）->(广东电信)->（ffxivlobby01.ff14.sdo.com:54994）->（101.227.2.6:80）->(109.244.5.5:54994)->(109.244.5.4:54992:109.244.5.43:55021)  
注：分流服务器作为底层数据连接支持服务器，数据映射到各大服务器IP后，每个服务器实际使用的都是自身IP+独立端口，对外侦测到的IP是 服务器IP：54992
实际端口是来自分流服务器的54992关联端口，并非大区自身端口。  
服务器软连接成功后使用的游戏服务器IP+分流服务器端口，即：109.244.5.43:54992  
外联实际数据连接过程是大区IP+分流服务器映射到游戏服务器端口：109.244.5.43:55021  

54992:仅为底层数据支持端口，并非对外服务端口  
54993:暂未知作用，目测只测到晨曦王座映射端口->莫古力登录大厅服务端口  
54994:为陆行鸟-猫小胖登录大厅服务端口  
验证方式：作者通过模拟拒绝IP+port通信，实现了模拟游戏开关服操作，暂时验证了原理过程（仅供参考）。  

 bug反馈：QQ1361825893  说明来意   
 by：拉诺西亚->北府太郎 | asura-Big taro  
