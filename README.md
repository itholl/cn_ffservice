#V202.0.2-测试版
 作者提示：此版本为测试版未完善
 由于需要每个服务器都有角色才能拿到具体IP和port，作者资源有限大部分服务器IP+port无法获取
 需要使用者自行补全“servicelist.ini”信息后才能测试全部服务器连接


一、 应用程序使用说明 “FF14服务器测试V202.0.2.exe”
 1.使用前请关闭杀毒软件，部分杀毒软件会随着病毒库升级产生误报
 2.下载应用包：FF14服务器测试V202.0.2.zip
 3.选择 “服务器” 点击 “启动检测” 即可正常检测服务是否开服


二、#ini配置文件使用说明 “servicelist.ini”
;必须填写和游戏内一样的服务器名称
;服务器名需要完整准确 如："拉诺西亚"，不可直接写"拉诺"
;服务器IP->服务器mane->服务器port  3个对应必填,如下例1
;例1：   服务器IP  ->    "拉诺西亚=109.244.5.43"
;        服务器name->    "01=拉诺西亚"
;        服务器port->    "拉诺西亚=55021"

---------------------------------------------------------
实例：

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
 猫小胖登录大厅=54994
---------------------------------------------------------
备注: [servicename] 编号是根据大区服务器分配的，陆行鸟总共8个大区，00为登录大厅 01-08 可以填写游戏服务器信息
     [servicelist][serviceport] 填写无规则，根据游戏内实际服务器名称和获取到的ip+port填写即可

 bug反馈：QQ1361825893  验证说明来意 
 by：拉诺西亚->北府太郎   asura-Big taro
