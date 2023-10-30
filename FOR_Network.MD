### 歐盟ENISA 
- https://www.enisa.europa.eu/topics/training-and-exercises/trainings-for-cybersecurity-specialists/online-training-material/documents/introduction-to-network-forensics-handbook.pdf

- 三個案例分析
- 案例1:能源領域 ICS/SCADA 攻擊流量分析
  - 鑑識情境
    - 此案例將處理對能源領域 ICS/SCADA 攻擊流量分析
    - 此案例將教導學生如何設定和配置網路安全監控環境，包括常規（非惡意）流量的基線(the baselining of regular (non-malicious) traffic)，最後成功分析網路上的多階段攻擊。
    - 在練習過程中，學生將必須處理以前未見過的網路架構，並熟悉用於控制工業環境的未知協議
  - 測試環境:ENISA_INF _5.1.ova 
- 案例2:大型金融環境的資料外洩分析(Detecting exfiltration on a large finance corporation environment)
  - 鑑識情境:
    - IT 安全團隊在幾乎每個公司環境中面臨的威脅之一是內部資料被盜並滲透到第三方伺服器的風險。這可能會導致許多法律問題、巨額罰款、聲譽損失或洩露公司機密和戰略文件。
    - 通常，可以使用各種方法和技術來完成資料外洩。從攻擊者的角度來看，盡可能長時間地逃避偵測非常重要。因此，攻擊者必須在滲透速度和使用通常較慢但更隱密的技術之間取得平衡。
    - 本節由兩部分組成，涵蓋兩種不同的資料外洩方法。
      - 在第一部分中，學生將學習如何使用 Web 代理程式日誌和其他安全系統來偵測 HTTP(s) 通道上的外洩。在本部分中，學生將學習： 如何安裝和設定具有 TLS/SSL 流量攔截功能的 Web 代理，  如何使用`惡意軟體資訊共享平台 (MISP, Malware Information Sharing Platform)` 輔助分析，  如何執行 Web 代理日誌分析。
      - 第二部分介紹了當洩漏的資料在 DNS 查詢中進行編碼時，使用 DNS 協定進行資料外洩的稍微隱密且不太常見的方法。在這一部分中，學生將學習：  如何執行基本統計分析(statistical analysis,)，  如何在通常龐大的 DNS 日誌檔案中搜尋異常 DNS 查詢。
  - 測試環境: ENISA_INF_Squid_Server_5.2.ova   + ENISA_INF_Squid_Client_5.2.ova
- 案例3:
  - 鑑識情境
    - 越來越多的公司將 IT 環境外包。基於成本考量、可用性或專業知識。整個 IT 環境可以外包，也可以只外包一部分。應用程式可以完全外包，而維護和託管則由第三方完成。或者，例如，在業務關鍵型應用程式中，應用程式由公司本身託管，而只有應用程式的維護由第三方完成。在IT環境仍然在公司自己所在地，僅外包應用程式的維護的情況下，需要第三方從外部存取。
    - 為此使用 VPN 連線（虛擬私人網路）。透過使用此VPN連接，維護方可以存取需要管理的應用程式。就 IT 安全而言，這並非沒有風險。這種結構的一個問題可能是外部管理員電腦的安全等級。外部管理員可以存取公司資料中心中的應用程式和伺服器。來自外部管理員的受感染電腦可能會對公司的應用程式和伺服器造成損害。
  - 測試環境: Caine_ENISA__INF _5.3.ova


A growing number of companies outsource their IT environment. Based on cost considerations, availability
or expertise. The entire IT environment can be outsourced or only a part. An application can be outsourced
completely whereas maintenance and hosting being done by a third party. Or, for example, in businesscritical applications, the application is hosted by the company itself, whereas only the maintenance of the
application is done by a third party.
In the situation that the IT environment remains at the company's own location, and only the maintenance
of an application is outsourced, the third party needs access from outside. A VPN connection (Virtual Private
Network) is used for this. By using this VPN connection, the maintenance party can access the applications
that need to be managed.
In terms of IT security this is not without risk. One problem with this construction may be the security level
of the external administrator's computer. The external administrators have access to the applications and
servers in the company's datacenter. An infected computer from the external administrator can cause
damage to the company's applications and servers.


### 網路日誌分析

### Wireshark:SampleCaptures
- https://wiki.wireshark.org/SampleCaptures
### Challenge 2 Haystack
- https://ctfacademy.github.io/network/challenge2/answer.htm

### tshark
- tshark: Basic Tutorial with Practical Examples 
  - https://allabouttesting.org/tshark-basic-tutorial-with-practical-examples/
- TShark TryHackMe Writeup
  - https://overide.medium.com/tshark-tryhackme-writeup-5ddf121c133e
- https://ctf-wiki.org/misc/traffic/data/
- tshark(1) Manual Page
  - https://www.wireshark.org/docs/man-pages/tshark.html
- Introduction to TShark
  - https://infosecwriteups.com/introduction-to-tshark-b425fc86ef0d



