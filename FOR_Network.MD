### 歐盟ENISA 
- https://www.enisa.europa.eu/topics/training-and-exercises/trainings-for-cybersecurity-specialists/online-training-material/documents/introduction-to-network-forensics-handbook.pdf

- 三個案例分析
- 案例1:能源領域 ICS/SCADA 攻擊流量分析
  - 鑑識情境
    - 此案例將處理對能源領域 ICS/SCADA 攻擊流量分析
    - 此案例將教導學生如何設定和配置網路安全監控環境，包括常規（非惡意）流量的基線(the baselining of regular (non-malicious) traffic)，最後成功分析網路上的多階段攻擊。
    - 在練習過程中，學生將必須處理以前未見過的網路架構，並熟悉用於控制工業環境的未知協議
  - 測試環境:ENISA_INF _5.1.ova 
- 案例2:資料外洩
  - 鑑識情境:
    - IT 安全團隊在幾乎每個公司環境中面臨的威脅之一是內部資料被盜並滲透到第三方伺服器的風險。這可能會導致許多法律問題、巨額罰款、聲譽損失或洩露公司機密和戰略文件。
    - 通常，可以使用各種方法和技術來完成資料外洩。從攻擊者的角度來看，盡可能長時間地逃避偵測非常重要。因此，攻擊者必須在滲透速度和使用通常較慢但更隱密的技術之間取得平衡。
    - 本節由兩部分組成，涵蓋兩種不同的資料外洩方法。
      - 在第一部分中，學生將學習如何使用 Web 代理程式日誌和其他安全系統來偵測 HTTP(s) 通道上的外洩。在本部分中，學生將學習： 如何安裝和設定具有 TLS/SSL 流量攔截功能的 Web 代理，  如何使用惡意軟體資訊共享平台 (MISP) 輔助分析，  如何執行 Web 代理日誌分析。
      - 第二部分介紹了當洩漏的資料在 DNS 查詢中進行編碼時，使用 DNS 協定進行資料外洩的稍微隱密且不太常見的方法。在這一部分中，學生將學習：  如何執行基本統計分析，  如何在通常龐大的 DNS 日誌檔案中搜尋異常 DNS 查詢。
  - 測試環境: ENISA_INF_Squid_Server_5.2.ova   + ENISA_INF_Squid_Client_5.2.ova
- 案例3:
  - 鑑識情境
  - 測試環境: Caine_ENISA__INF _5.3.ova

One of the threats that IT security teams are facing in almost every corporation environment is a risk of
internal data being stolen and exfiltrated to third party servers. This might lead to many legal problems,
huge fines, loss of reputation or disclosing company secrets and strategic documents.
Typically, data exfiltration can be done using various approaches and techniques. From the attacker point of
view, it is important to evade detection for as long as possible. Thus, attackers must balance between
exfiltration speed and using often slower but more concealed techniques.
This section consists of two parts covering two different approaches to data exfiltration. In the first part
students will learn how to use web proxy logs and other security systems to detect exfiltration over HTTP(s)
channel. In this part students will learn:
 How to install and configure web proxy with TLS/SSL traffic interception capability,
 How to use Malware Information Sharing Platform (MISP) to aid analysis,
 How to perform web proxy logs analysis.
The second part covers slightly more concealed and less common approach to data exfiltration using DNS
protocol when exfiltrated data is encoded among DNS queries. In this part students will learn:
 How to perform basic statistical analysis,
 How to search for anomalous DNS queries in often huge DNS log files.

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



