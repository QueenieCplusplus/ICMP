# ICMP
ARP-alike for IPv6

對於 IPv4 而言，ICMP 可能僅僅作用於確認網路的健全狀態如此罷了！然而 IPv6 版本的 ICMP 功能遠遠超過這些，新功能包含 IGMP 將多點傳送 multicast 的群組併入至 ICMPv6 ; 也包含 ARP/RARP，能將 MAC 和 IP 位置相互映射 ; 除此之外，尚有 ND (Neighbour Discovery) 網路芳鄰，讓 ICMPv6 能夠確認相同 Link-Layer 的路由，保持追蹤可觸及的 Neightbour Routers。

# Ping & TraceRoute

# Check Network Status using ICMP

倘若封包無法適切的處理並傳送網路狀態相關資訊，將回報錯誤。例如，若路由因為封包太大而無法傳送至另一個網路而無法執行轉發，則會回傳 ICMP 訊息給初始傳送的主機。

來源主機可利用 ICMP 訊息決定好重設封包的大小（MTU）， 再行傳送即可。

# ICMP

127, reserved for extension

128, Echo Request (Multicast)

129, Echo Reply (Unicast)

# Error Msg

* 1, DES Unreacheachable

     0 No Route to DES, 無法路由至目的地
     
     1 Communication with DES admin prohibited, 管理禁止與目的地通訊 (防火牆過濾封包)
     
     2 Beyond scope of addr, 來源位置超出範圍
     
       封包擁有 link-local 的 source addr 和 global 的 des addr。
     
     3 Addr Unreachable, 位址無法抵達
     
       目的地位址無法還原成正確的網路位址所致，或是 link-layer 出現問題阻止節點觸及目的地網路。  
     
     4 通訊阜無法抵達
     
       UDP 沒有聆聽者時，例如目標伺服器沒有正在執行狀態時。
     
     5 SRC addr failed ingress/egree policy, 來源位址不符進/出政策
     
     6 Reject Route to DES, 拒絕路由至目的地
     
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
     
# Why Error occurs?

1) 超時或逾時的狀況：

路由轉送 forward 封包時，必須將 Hop 跳點減去 1。 Hop Count 確保了封包不至於在網路中漫無目的的無遠弗屆的毫無限制地自由飄渺地...旅行，倘若封包已經減至 0，卻尚未送達，則將拋棄封包，此程式碼將帶著 payload of value 為 0，而程式設計將 0 值定義為 “Time Exceed”，回傳也告知來源主機 Source Host。

2) 封包太大的例外：

封包太大，以至於 next hop 的 MTU 根本不支援的話，那麼就會產生例外錯誤。此時來源主機將接收到所建議的那個下一跳點的 MTU 大小。

3) 目的地無法抵達：

則 ICMP 根本不會產生回應，來源主機不會收到任何回傳訊息...。此時來源主機通報『上層』處理程序。

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
