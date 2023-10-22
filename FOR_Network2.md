# FOR_Network2
- https://www.packtpub.com/product/hands-on-network-forensics/9781789344523
- https://github.com/nipunjaswal/networkforensics/tree/master
- https://github.com/chrissanders/packets

## 

## 核心技術
- Deep Packet Inspection (DPI) ch5
- Statistical Flow Analysis ch6
- Combatting Tunneling and Encryption ch7
## Section 3: Conducting Network Forensics
- Chapter 6, Investigating Good, Known, and Ugly Malware
- Chapter 7, Investigating C2 Servers
- Chapter 8, Investigating and Analyzing Logs
- Chapter 9, WLAN Forensics
- Chapter 10, Automated Evidence Aggregation and Analysis

### CH5.Deep Packet Inspection (DPI)
- DPI is the process of looking beyond the generic TCP/IP headers and involves analyzing the payload itself.
- DPI is widely used in the following fields and services:
  - Traffic shapers: Blocking malicious traffic/limiting traffic.
  - Service assurance: Network admins can ensure that high-priority traffic is carefully dealt with and services do not go down for them.
  - Identification of fake applications: Applications that make use of non-standard ports to leverage standard protocol data are easily identified with DPI.
  - Malware Detection: Since DPI allows viewing the payload itself, malware detection is much easier to perform.
  - Intrusion detection: Not only malware, but also the DPI-enabled system can uncover hack attempts and exploit attempts, backdoors, and much more.
  - Data Leakage Prevention (DLP): With DPI, we can identify critical data traveling out of the network as well, making it an ideal choice for DLP systems.
- 案例探討:ICMP Flood or something else
- https://is.muni.cz/th/ql57c/dp-svoboda.pdf

## ch 6 Statistical Flow Analysis
  - 工具
    - Yet Another Flowmeter (YAF)
      - YAF - CERT NetSA Security Suite
      - https://tools.netsa.cert.org/yaf/ 
    - System for Internet-Level Knowledge (SiLK)
    - iSiLK
    - Argus
    - Wireshark
    - Bro
  - YAF (https://tools.netsa.cert.org/yaf/libyaf/yaf_silk.html)
  - SiLK (https://tools.netsa.cert.org/silk/download.html) 
### YAF - CERT NetSA Security Suite
- https://www.youtube.com/watch?v=7ZQG8zDEf7c
- 本課程由 Mike McFail 和 Ben Actis 教授，重點在於從安全營運中心角度進行網路分析和惡意活動追蹤。
- 我們將深入探討 Netflow 的優勢、Netflow 的操作限制、建議的感測器放置、Netflow 工具、
- 網路資料的視覺化、網路態勢感知的分析貿易技術和網路狩獵場景。
- 課程目標： * 提供對 Netflow 資料格式的理解 *
- 描述常見的 NetFlow 收集、分析和視覺化工具 *
- 涵蓋態勢感知和狩獵分析技巧 *
- 將 NetFlow 與其他資料來源融合
- 案例探討:

## Combatting Tunneling and Encryption ch7
- Decrypting TLS using browsers
- Decoding a malicious DNS tunnel
  - 樣本: https://github.com/ctfhacker/ctf-writeups/blob/master/holidayhack-2015/part1/gnome.pcap 
- Decrypting 802.11 packets
  - 樣本:https://github.com/ctfs/write-ups-2015/raw/master/codegate-ctf-2015/programming/good-crypto/file.xz 
- Decoding keyboard captures
  -  https://github.com/dbaser/CTF-Write-ups/blob/master/picoCTF-2017/for80-just_keyp_trying/data.pcap 
- https://github.com/nipunjaswal/networkforensics/tree/master/Ch5
- 案例探討: 

## 網路流量中的惡意程式  Investigating Good, Known, and Ugly Malware
- Hidden Tear Decryptor (https://github.com/goliate/hidden-tear)
- PyLocky Decryptor (https://github.com/Cisco-Talos/pylocky_decryptor)
- 案例探討 1: Lokibot
- 案例探討 2: PyLocky ransomware
  - Hybrid-Analysis website (https://www.hybrid-analysis.com/)
  - https://www.virustotal.com/gui/file/04cf54c95b58f15a2d06ad805a49b20233408737eb417190a817fd189bcf2329/relations
- 案例探討 3: a banking Trojan on the network   Emotet
  - https://www.fortinet.com/blog/threat-research/analysis-of-a-fresh-variant-of-the-emotet-malware
  - https://www.malware-traffic-analysis.net/training-exercises.html
- 案例探討 4:
- 案例探討 1: Lokibot
  - 樣本:https://github.com/R3MRUM/loki-parse/tree/master  ==> loki-bot_network_traffic.pcap
  - https://www.ithome.com.tw/news/151655
  - https://www.ithome.com.tw/tags/lockbit-30
  - 新版LokiBot惡意軟體正透過Windows Office文件檔案傳播 2023 / 07 / 17
  - LockBit 模仿犯使用外洩的程式碼發展新勒索軟體進行攻擊 2023 / 10 / 20
  - AI、持續性威脅暴露管理列Gartner 2024年十大戰略技術趨勢 2023 / 10 / 20 
  - https://attack.mitre.org/versions/v7/software/S0447/
  - https://www.cisa.gov/news-events/cybersecurity-advisories/aa20-266a#:~:text=LokiBot%E2%80%94also%20known%20as%20Lokibot,cryptocurrency%20wallets%2C%20and%20other%20credentials.
  - https://forums.juniper.net/t5/Security/A-look-into-LokiBot-infostealer/ba-p/315265 
  - https://r3mrum.wordpress.com/2017/07/13/loki-bot-inside-out/
  - MITRE ATT&CK enterprise techniques used by LokiBot
  - https://community.juniper.net/blogs/elevate-member/2020/12/22/a-look-into-lokibot-infostealer
  - https://www.blackberry.com/us/en/solutions/endpoint-security/ransomware-protection/lokibot
  - LokiBot 於 2015 年首次被報導，被歸類為憑證收集器、資訊竊取者和遠端存取木馬 (RAT)。
  - LokiBot 是一種流行的資訊竊取程序，因為它易於使用且能夠有效地獲得對目標系統的初始存取權限。
  - LokiBot 也是一種惡意軟體即服務 (MaaS)，有兩個不同的版本。正品版本在地下市場出售，起價 300 美元；破解版售價約 80 美元。
  - 2020 年，LokiBot 的活動激增，控制了全球最大的殭屍網絡，隨後被列入 CISA 2021 年十大惡意軟體菌株名單。
  - 雖然 LokiBot 的最終功能清單相對較短，專注於資訊竊取和憑證收集，但它確實提供遠端程式碼執行 (RCE) 功能，允許攻擊者輕鬆導入其他工具，包括勒索軟體。
  - 僅此 RCE 功能就使 LokiBot 成為高風險惡意軟體。但LokiBot 的最大優勢在於其高度通用且複雜的第一階段交付和解包方法，這使得它經常被用作導入惡意軟體的暫存器，而該惡意軟體在第二階段策略（即更深層次的網絡滲透和橫向移動）方面表現出色。
  - LokiBot 武器庫中的另一個武器是它能夠危害 Android 裝置和基於 Windows 的系統。
  - LokiBot 的活動時好時壞，使用量急劇上升，隨後進入休眠停機階段，導致一些人得出結論，大規模 LokiBot 活動的時機需要經過仔細考慮。
  - Top 11 Malware Strains of 2021 — And How to Stop Them
    -  https://blogs.blackberry.com/en/2022/08/top-11-malware-strains-of-2021-and-how-to-stop-them

- 案例探討 2: PyLocky ransomware
- 案例探討 3:
- 案例探討 4:
##
-
- 案例探討:

##
-
- 案例探討:

##
-
- 案例探討:

##
-
- 案例探討:

##
-
- 案例探討:

##
-
- 案例探討:

##
-
- 案例探討:

##
-
- 案例探討:
