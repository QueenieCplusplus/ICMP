# ICMP
ARP-alike for IPv6

對於 IPv4 而言，ICMP 可能僅僅作用於確認網路的健全狀態如此罷了！然而 IPv6 版本的 ICMP 功能遠遠超過這些，新功能包含 IGMP 將多點傳送 multicast 的群組併入至 ICMPv6 ; 也包含 ARP/RARP，能將 MAC 和 IP 位置相互映射 ; 除此之外，尚有 ND (Neighbour Discovery) 網路芳鄰，讓 ICMPv6 能夠確認相同 Link-Layer 的路由，保持追蹤可觸及的 Neightbour Routers。

# Check Network Status using ICMP

倘若封包無法適切的處理並傳送網路狀態相關資訊，將回報錯誤。例如，若路由因為封包太大而無法傳送至另一個網路而無法執行轉發，則會回傳 ICMP 訊息給初始傳送的主機。

來源主機可利用 ICMP 訊息決定好重設封包的大小（MTU）， 再行傳送即可。

# ICMP

Echo Request

Echo Reply

# Error Msg

* 1, DES Unreacheachable

* 2, Packet too Big

* 3, Time Exceeded

* 4, Param Problem

# Neighbour Discovering

https://datatracker.ietf.org/doc/rfc4861/
