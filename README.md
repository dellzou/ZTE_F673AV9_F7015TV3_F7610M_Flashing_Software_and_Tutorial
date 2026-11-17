# 中兴 F673AV9 / F7015TV3 / F7610M 工具包

配套文章：[中兴 F673AV9 / F7015TV3 / F7610M 开 Telnet 与改码](https://xiaozou123.cn/zte-f673av9-f7015tv3-f7610m-telnet/)

三台机器共用同一套中兴命令体系：工厂模式开临时 Telnet → 固化 → 改地区 → 改码 / 取超密。

## 目录

- `factorymode_crack.exe`：命令行开工厂模式，F673AV9 用这条
- `putty.exe`：Telnet 客户端
- `tftpd64.exe`：TFTP，导配置文件用
- `common/`：ZTelnet、zte_factroymode、ztecfg，以及老版 TelnetONU 1.5.0
- `中兴 ZXHN F673AV9教程.txt`、`F7610M_开telnet与取超密方法.txt`：原始教程，保留文本以便对照

## 两份教程的可信度不一样

- F7610M 那份是**实操记录**：临时 Telnet → 固化（root / 系列号）→ 改地区 → TFTP 取 `db_user_cfg.xml` → `ztecfg -d AESCBC` 解密，步骤和命令能对上。
- F673AV9 那份来源不明，里面「`setmac 1 512` 改 SN」与 `512` 字段的实际含义冲突；正确写法是先 `setmac show2` 看 ID 再动手。原文照录，不要照抄。

## 文件与 SHA256

| 文件 | 字节 |
|---|---|
| `F7610M_开telnet与取超密方法.txt` | 1,914 |
| `common/ZTelnet v1.0.5.exe` | 9,729,169 |
| `common/telnetonu_1.5.0/2022.lic` | 752 |
| `common/telnetonu_1.5.0/Cmd_Onu.txt` | 5,376 |
| `common/telnetonu_1.5.0/TelnetONU_1.5.0.exe` | 81,920 |
| `common/telnetonu_1.5.0/date.dll` | 13 |
| `common/telnetonu_1.5.0/decrypt.exe` | 53,248 |
| `common/telnetonu_1.5.0/factorymode.exe` | 872,448 |
| `common/telnetonu_1.5.0/getinfo.exe` | 36,864 |
| `common/telnetonu_1.5.0/reg.dll` | 29 |
| `common/telnetonu_1.5.0/指令.txt` | 255 |
| `common/zte_factroymode.exe` | 9,840,829 |
| `common/ztecfg.exe` | 7,037,223 |
| `common/说明.txt` | 453 |
| `factorymode_crack.exe` | 872,448 |
| `putty.exe` | 524,288 |
| `tftpd64.exe` | 346,112 |
| `中兴 ZXHN F673AV9教程.txt` | 2,538 |

```
1ba52b4caa28b35f0f939b66970e74e52f9cc76d1fc779ccc6e9fbbbd0618984  F7610M_开telnet与取超密方法.txt
c6b0fc3056864024ab0b153cc1f8aabd2d60ef4d61a3abde19adf1d122b5743f  common/ZTelnet v1.0.5.exe
906432d722ac04f3adef9208561dcb68f0b9cb36959e4d4dee01f5268fbac78f  common/telnetonu_1.5.0/2022.lic
e90ae2757686fb8837226209244e3579a44a2482ed1b8a83f8e7945e0f8c7160  common/telnetonu_1.5.0/Cmd_Onu.txt
952c8be8bf878e87a795472945ec77a77658c5a55dce84951d60e2213237be68  common/telnetonu_1.5.0/TelnetONU_1.5.0.exe
a09d07f8bdf6d3d9b2f6412fd99969750925bd457f788129682913d43ec262ed  common/telnetonu_1.5.0/date.dll
d9e46a77a566b511fb154327637da91546086e34e02ba41c82b1f86c6746beb6  common/telnetonu_1.5.0/decrypt.exe
d100ae9e1a7bc25a360122d6e7d658b498078c0fbf7635d8c5ad3a839d0772c2  common/telnetonu_1.5.0/factorymode.exe
607ed6be8bc8e05a1e5ee2b726732e74fa0b8849b5cc247348cc7aec8343f0cd  common/telnetonu_1.5.0/getinfo.exe
7de624cbdf1d570b6c061c89b852823733630cfb8ca506a0309d73e139da312f  common/telnetonu_1.5.0/reg.dll
385a3669421a4cf853677075b153faa4787ff7c8f273de340a1b460c627b0fb9  common/telnetonu_1.5.0/指令.txt
7fae6d52429eca484d75f51d9d3a2fcb03b790a8cd40c6885685b7d8e34926b8  common/zte_factroymode.exe
a14be5d00516fc8ca950e97347e4f6e3f535f354254542f746739407aa9e3f46  common/ztecfg.exe
8a18dd722a3d4a2249f97e7b128a3cf4a03639e3ef396d8b48ba774c1e752691  common/说明.txt
e5fa3ca8a74a768c58abe7a0e552bbd66276353804604cbaa6c2479b95b9d702  factorymode_crack.exe
8aafc0858cb440910b9b7f237124f373389591a488a77d3d367da56bbf462678  putty.exe
058db9a905bea6683717e4d5dcf99a94f7303963cad624afb140d9ed1ee5b83e  tftpd64.exe
9b4c7bb031c73e3d0f5cd44366f1c51c226caa9d87a606d5d0779bc7311dd3ee  中兴 ZXHN F673AV9教程.txt
```

## 相关仓库

同品牌其它机型，命令体系或刷机思路相近，排障时可以互相参照；每个仓库开头都对应一篇文章：

- [中兴 F650 / F1855V2 工具包](https://github.com/dellzou/ZTE_F650_F1855V2_Flashing_Software_and_Tutorial)：天翼网关 4.0 开 Telnet
- [中兴 F7607P 工具包](https://github.com/dellzou/ZTE_F7607P_Flashing_Software_and_Tutorial)：改地区与电信版固件
- [中兴 G7610 工具包](https://github.com/dellzou/ZTE_G7610_Flashing_Software_and_Tutorial)：工厂模式、setmac 改码、配置解密
- [中兴 G7615 / G7611 工具包](https://github.com/dellzou/ZTE_G7615_G7611_Flashing_Software_and_Tutorial)：改地区与分区刷写

## 免责声明

工具与固件均来自公开维修资料，仅供自有设备维修与学习使用。刷机有风险，操作前先备份，后果自负。
