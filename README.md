# ICMP
ARP-alike for IPv6

對於 IPv4 而言，ICMP 可能僅僅作用於確認網路的健全狀態如此罷了！然而 IPv6 版本的 ICMP 功能遠遠超過這些，新功能包含 IGMP 將多點傳送 multicast 的群組併入至 ICMPv6 ; 也包含 ARP/RARP，能將 MAC 和 IP 位置相互映射 ; 除此之外，尚有 ND (Neighbour Discovery) 網路芳鄰，讓 ICMPv6 能夠確認相同 Link-Layer 的路由，保持追蹤可觸及的 Neightbour Routers。

# Check Network Status using ICMP

倘若封包無法適切的處理並傳送網路狀態相關資訊，將回報錯誤。例如，若路由因為封包太大而無法傳送至另一個網路而無法執行轉發，則會回傳 ICMP 訊息給初始傳送的主機。

來源主機可利用 ICMP 訊息決定好重設封包的大小（MTU）， 再行傳送即可。

# ICMP

128, Echo Request

129, Echo Reply

# Error Msg

* 1, DES Unreacheachable

     0 無法路由至目的地
     
     1 管理禁止與目的地通訊
     
     2 來源位置超出範圍
     
     3 位址無法抵達
     
     4 通訊阜無法抵達
     
     5 來源位址不符進/出政策
     
     6 拒絕路由至目的地
     
     7 來源路由標頭錯誤

* 2, Packet too Big

     0 預設值

* 3, Time Exceeded

     0 超越傳輸跳點 hop 限制
     
     1 分段重組逾時

* 4, Param Problem

     0 錯誤標頭欄位
     
     1 下一標頭狀態尚未認可
     
     2 選項尚未認可

# Neighbour Discovering

https://datatracker.ietf.org/doc/rfc4861/

* 133, Router Solicitate (探索)

* 134, Router Advertisement (廣告)

* 135, Neighbour Solicitate

* 136, Neightbour Advertisement

* 137, Redirect Msg (重新導向訊息)

# Multicast Listening

* 130, query

* 131, report

* 132, done
