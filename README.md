# ICMP
ARP-alike for IPv6

對於 IPv4 而言，ICMP 可能僅僅作用於確認網路的健全狀態如此罷了！然而 IPv6 版本的 ICMP 功能遠遠超過這些，新功能包含 IGMP 將多點傳送 multicast 的群組併入至 ICMPv6 ; 也包含 ARP/RARP，能將 MAC 和 IP 位置相互映射 ; 除此之外，尚有 ND (Neighbour Discovery) 網路芳鄰，讓 ICMPv6 能夠確認相同 Link-Layer 的路由，保持追蹤可觸及的 Neightbour Routers。

# Neighbour Discovering

https://datatracker.ietf.org/doc/rfc4861/
