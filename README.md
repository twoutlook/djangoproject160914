# 開發和正式環境的詳細調試，參考, [這裡](DEV-PROD.md)


# hicloud VM 規格
    Standard Mini-Promotions(Linux)
    ubuntu 14.04 eng, 64bit
    LAMP(Apache2.4+MySQL5.5+PHP5.5) with Webmin
    1 virtual core [equivalent to 1GHz CPU capacity] ,1 GB RAM
    30 GB
    
[210.65.11.216](http://210.65.11.216)

# Github
https://github.com/twoutlook/djangoproject160914

# c9.io
為方便自動上傳更新，在左邊的
Repositories, 先選 Github 項目, 再 clone to edit 

可以開多個，目前使用這個
- https://ide.c9.io/twoutlook/djangoproject160914-dev2

# Hostmonster


將域名 [twcloudwebapp.com](http://www.twcloudapp.com) 指向 hicloud 給的 IP, 
- 2016-12-18 到期, type: Unassigned, 因此沒有預設網站。
- DNS Zone Editor, 單一修改 A (Host) $, 其它不動。  

