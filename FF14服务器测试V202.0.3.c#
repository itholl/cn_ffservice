#include <GUIConstantsEx.au3>
#include <MsgBoxConstants.au3>
#include <WinAPIFiles.au3>
#include <IE.au3>


Global $sip = "", $ip = ""
$sock = ""
$Form1 = GUICreate("FF14服务器测试V202.0.3", 328, 165, 193, 125)
$IPin = GUICtrlCreateCombo("", 60, 2, 110, 21) ;下拉框
GUICtrlCreateLabel("服务器:", 5, 4, 50, 17)
$History = GUICtrlCreateEdit("", 2, 82, 321, 40)
$Go = GUICtrlCreateCheckbox("启动检测", 260, -2, 75, 25, 0)
$jichen = GUICtrlCreateLabel("FF14客户端:", 5, 135, 70, 17)
$zt = GUICtrlCreateLabel("", 80, 135, 80, 17)
;;设置背景颜色
;;GUICtrlSetBkColor(-1, 0x009933)
GUICtrlCreateLabel("Port", 175, 4, 23, 17)
$Portin = GUICtrlCreateInput("自动选择", 200, 2, 55, 21)
$Button1 = GUICtrlCreateButton("程序说明", 248, 130, 65, 20)
GUICtrlCreateLabel("连接信息", 4, 62, 200, 17)
$Gstatus = GUICtrlCreateLabel("---------", 74, 30, 196, 41)
GUICtrlSetColor($Gstatus, 0xFF4500)
GUICtrlSetFont(-1, 26, 400, 0, "MS Sans Serif")
GUISetState(@SW_SHOW)
;----------------------------下拉框测试-----------------------------------------------------------------------------
Local Const $sFilePath = @ScriptDir & "\servicelist.ini";文件名
Local $aArray = IniReadSection($sFilePath, "servicename");字段名
Local $sComboTxt ;= "Infomation"
Local $cbDatab
; 检查是否发生错误.
If Not @error Then
	; 枚举显示数组中关键字及其各自的值.
	For $i = 1 To $aArray[0][0]
		$totalini = $aArray[$i][1]
		If Not StringInStr($sComboTxt, $totalini) Then $sComboTxt &= "|" & $totalini
	Next
EndIf
GUICtrlSetData($IPin, "")
GUICtrlSetData($IPin, $sComboTxt, "");下拉框值


;-------------------------------------------------------------------------------------------------------------------
TCPStartup()

While 1
	$msgb = GUIGetMsg()
	Switch $msgb
		Case $GUI_EVENT_CLOSE
			TCPCloseSocket($sock)
			TCPShutdown()
			Exit

		Case BitAND(GUICtrlRead($Go), $GUI_CHECKED)

		Case BitAND(GUICtrlRead($Go), $GUI_UNCHECKED)
			$dx11 = ProcessExists("ffxiv_dx11.exe")
			$dx9 = ProcessExists("ffxiv.exe")
			If $dx11 = 0 Or $dx9 = 0 Then
				GUICtrlSetData($zt, "游戏未启动")
			Else
				GUICtrlSetData($zt, "游戏正在运行")
			EndIf
			$sComboRead = GUICtrlRead($IPin) ;读取 下拉框的值
			;登录大厅
			If $sComboRead = "陆行鸟登录大厅" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "陆行鸟登录大厅", "default"))
			If $sComboRead = "陆行鸟登录大厅" Then $sip = IniRead($sFilePath, "servicelist", "陆行鸟登录大厅", "default") ;将下拉框内容转换为IP，IP为$sip
			If $sComboRead = "莫古力登录大厅" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "莫古力登录大厅", "default"))
			If $sComboRead = "莫古力登录大厅" Then $sip = IniRead($sFilePath, "servicelist", "莫古力登录大厅", "default")
			If $sComboRead = "猫小胖登录大厅" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "猫小胖登录大厅", "default"))
			If $sComboRead = "猫小胖登录大厅" Then $sip = IniRead($sFilePath, "servicelist", "猫小胖登录大厅", "default")
			;陆行鸟大区服务器 all=8
			If $sComboRead = "拉诺西亚" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "拉诺西亚", "default"))
			If $sComboRead = "拉诺西亚" Then $sip = IniRead($sFilePath, "servicelist", "拉诺西亚", "default")
			If $sComboRead = "幻影群岛" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "幻影群岛", "default"))
			If $sComboRead = "幻影群岛" Then $sip = IniRead($sFilePath, "servicelist", "幻影群岛", "default")
			If $sComboRead = "红玉海" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "红玉海", "default"))
			If $sComboRead = "红玉海" Then $sip = IniRead($sFilePath, "servicelist", "红玉海", "default")
			If $sComboRead = "宇宙和音" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "宇宙和音", "default"))
			If $sComboRead = "宇宙和音" Then $sip = IniRead($sFilePath, "servicelist", "宇宙和音", "default")
			If $sComboRead = "晨曦王座" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "晨曦王座", "default"))
			If $sComboRead = "晨曦王座" Then $sip = IniRead($sFilePath, "servicelist", "晨曦王座", "default")
			If $sComboRead = "沃仙曦染" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "沃仙曦染", "default"))
			If $sComboRead = "沃仙曦染" Then $sip = IniRead($sFilePath, "servicelist", "沃仙曦染", "default")
			If $sComboRead = "萌芽池" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "萌芽池", "default"))
			If $sComboRead = "萌芽池" Then $sip = IniRead($sFilePath, "servicelist", "萌芽池", "default")
			If $sComboRead = "神意之地" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "神意之地", "default"))
			If $sComboRead = "神意之地" Then $sip = IniRead($sFilePath, "servicelist", "神意之地", "default")
			;莫古力大区服务器 all=8
			If $sComboRead = "白银乡" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "白银乡", "default"))
			If $sComboRead = "白银乡" Then $sip = IniRead($sFilePath, "servicelist", "白银乡", "default")
			If $sComboRead = "白金幻象" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "白金幻象", "default"))
			If $sComboRead = "白金幻象" Then $sip = IniRead($sFilePath, "servicelist", "白金幻象", "default")
			If $sComboRead = "神拳痕" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "神拳痕", "default"))
			If $sComboRead = "神拳痕" Then $sip = IniRead($sFilePath, "servicelist", "神拳痕", "default")
			If $sComboRead = "潮风亭" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "潮风亭", "default"))
			If $sComboRead = "潮风亭" Then $sip = IniRead($sFilePath, "servicelist", "潮风亭", "default")
			If $sComboRead = "旅人栈桥" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "旅人栈桥", "default"))
			If $sComboRead = "旅人栈桥" Then $sip = IniRead($sFilePath, "servicelist", "旅人栈桥", "default")
			If $sComboRead = "拂晓之间" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "拂晓之间", "default"))
			If $sComboRead = "拂晓之间" Then $sip = IniRead($sFilePath, "servicelist", "拂晓之间", "default")
			If $sComboRead = "龙巢神殿" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "龙巢神殿", "default"))
			If $sComboRead = "龙巢神殿" Then $sip = IniRead($sFilePath, "servicelist", "龙巢神殿", "default")
			If $sComboRead = "梦羽宝境" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "梦羽宝境", "default"))
			If $sComboRead = "梦羽宝境" Then $sip = IniRead($sFilePath, "servicelist", "梦羽宝境", "default")
			;猫小胖大区服务器 all=7
			If $sComboRead = "紫水栈桥" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "紫水栈桥", "default"))
			If $sComboRead = "紫水栈桥" Then $sip = IniRead($sFilePath, "servicelist", "紫水栈桥", "default")
			If $sComboRead = "延夏" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "延夏", "default"))
			If $sComboRead = "延夏" Then $sip = IniRead($sFilePath, "servicelist", "延夏", "default")
			If $sComboRead = "静语庄园" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "静语庄园", "default"))
			If $sComboRead = "静语庄园" Then $sip = IniRead($sFilePath, "servicelist", "静语庄园", "default")
			If $sComboRead = "摩杜纳" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "摩杜纳", "default"))
			If $sComboRead = "摩杜纳" Then $sip = IniRead($sFilePath, "servicelist", "摩杜纳", "default")
			If $sComboRead = "海猫茶屋" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "海猫茶屋", "default"))
			If $sComboRead = "海猫茶屋" Then $sip = IniRead($sFilePath, "servicelist", "海猫茶屋", "default")
			If $sComboRead = "柔风海湾" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "柔风海湾", "default"))
			If $sComboRead = "柔风海湾" Then $sip = IniRead($sFilePath, "servicelist", "柔风海湾", "default")
			If $sComboRead = "琥珀原" Then GUICtrlSetData($Portin, IniRead($sFilePath, "serviceport", "琥珀原", "default"))
			If $sComboRead = "琥珀原" Then $sip = IniRead($sFilePath, "servicelist", "琥珀原", "default")
			$ip = $sip
			$port = GUICtrlRead($Portin, 1)
			If $ip = "" Or $port = "" Then
			Else
				$ip = TCPNameToIP($ip)
				Sleep(1000)
				$start = TimerInit()
				$sock = TCPConnect($ip, $port)
				If @error = 1 Then
					MsgBox(0, "错误", "无效的IP输入！")
					GUICtrlSetState($Go, $GUI_UNCHECKED)
				ElseIf @error = 2 Then
					MsgBox(0, "错误", "无效/关闭的端口输入！")
					GUICtrlSetState($Go, $GUI_UNCHECKED)
				ElseIf $sock = -1 Then
					GUICtrlSetData($Gstatus, "服务器离线!")
					GUICtrlSetFont($Gstatus, 18)
					GUICtrlSetColor($Gstatus, 0xFF0093)
					GUICtrlSetData($History, "[" & @HOUR & ":" & @MIN & ":" & @SEC & "] 离线, " & $ip & ":" & $port & @CRLF, GUICtrlRead($History))
				Else
					$Stop = Round(TimerDiff($start), 2)

					GUICtrlSetData($Gstatus, "注意：服务器在线")
					If IniRead($sFilePath, "Beep", "蜂鸣声提示", "default") = 1 Then Beep(500, 1000)
					GUICtrlSetData($History, "")
					

					GUICtrlSetFont($Gstatus, 18)
					GUICtrlSetColor($Gstatus, 0x009933)
					GUICtrlSetData($History, "[" & @HOUR & ":" & @MIN & ":" & @SEC & "] 在线, " & $ip & ":" & $port & " 延时:" & $Stop & @CRLF, GUICtrlRead($History))
					TCPCloseSocket($sock)



				EndIf
			EndIf
		Case $Button1
			$url = Run(@ComSpec & " /k " & 'start ' & 'https://github.com/itholl/cn_ffservice', "", @SW_HIDE)
			If $url = 0 Then _IECreate("https://github.com/itholl/cn_ffservice", 0)
			
	EndSwitch
WEnd
