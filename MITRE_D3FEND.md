# MITRE D3FEND 六大戰術

# MITRE D3FEND| DETECT 戰術
### MITRE D3FEND| DETECT | 網路流量分析戰技 網路流量分析Network Traffic Analysis
- 管理網路活動分析Administrative Network Activity Analysis
- 位元組序列模擬Byte Sequence Emulation
- 憑證分析Certificate Analysis
- 主動憑證分析Active Certificate Analysis
- 被動憑證分析Passive Certificate Analysis
- 用戶端-伺服器負載分析Client-server Payload Profiling
- 連線嘗試分析Connection Attempt Analysis
- DNS 流量分析DNS Traffic Analysis
- 檔案雕刻File Carving
- 入站會話量分析Inbound Session Volume Analysis
- IPC 流量分析IPC Traffic Analysis
- 網路流量社群偏差Network Traffic Community Deviation
- 每台主機下載上傳比率分析Per Host Download-Upload Ratio Analysis
- 協定元資料異常檢測 Protocol Metadata Anomaly Detection
- 中繼模式分析 Relay Pattern Analysis
- 遠端終端會話偵測 Remote Terminal Session Detection
- RPC 流量分析(RPC Traffic Analysis)



### 管理網路活動分析Administrative Network Activity Analysis
```
Definition
Detection of unauthorized use of administrative network protocols by analyzing network activity against a baseline.

How it works
Network protocols such as RDP, IPMI, SSH, SNMP, VNC, MOSH, NX, TeamViewer, SPICE, PCoIP, and others are used by system administrators to remotely manage servers. Defenders monitor administrative network activity to determine if the use of remote protocols is malicious. Attackers can abuse administrative protocols and leverage them for initial access to various endpoints. For example, an attacker with valid credentials will remotely SSH or RDP into a server and attempt to blend in with existing traffic from system administrators. By monitoring the traffic activity, it is possible to detect when the protocols are behaving differently from a known baseline of system administration activity.

Considerations
Administrative traffic can be encrypted, making network protocol analysis a challenge
False alarms can be mitigated by integration with inventory management systems

定義
透過根據基線分析網路活動來偵測未經授權的管理網路協定使用。

怎麼運作的
系統管理員使用 RDP、IPMI、SSH、SNMP、VNC、MOSH、NX、TeamViewer、SPICE、PCoIP 等網路協定來遠端管理伺服器。防禦者監視管理網路活動，以確定遠端協定的使用是否是惡意的。攻擊者可以濫用管理協定並利用它們來初始存取各種端點。例如，擁有有效憑證的攻擊者將透過 SSH 或 RDP 遠端連接到伺服器，並嘗試與系統管理員的現有流量混合。透過監視流量活動，可以偵測協定的行為何時與系統管理活動的已知基線不同。

注意事項
管理流量可以加密，使網路協定分析成為一項挑戰
透過與庫存管理系統整合可以減少誤報
數位工件關係：
這種防禦技術與特定的數位製品有關。點擊工件節點以獲取更多資訊。
```


### 位元組序列模擬Byte Sequence Emulation
```
Definition
Analyzing sequences of bytes and determining if they likely represent malicious shellcode.

Synonyms: Shellcode Transmission Detection .
How it works
Bytes are analyzed as if they are machine code instructions, and such instructions that are a common component of known shellcode are noted, such as stack pivots, reads from a Memory Address Table, and system calls for functions that disable protections or execute code. For example, the x86 instruction b0 0b: mov $11, %ax, with no further alterations to the %ax register, followed by cd 80: syscall executes the system call execve() in the Linux kernel, which replaces the current process with another one specified -- this is a common action in shellcode, so this sequence would be flagged.

This technique detects shellcode despite whether or not it would cause a buffer overflow in the target binary.

If the sequence of bytes contains a sequence similar to that used in malicious shellcode, the entire byte sequence is flagged and a follow-on technique may be invoked.

Considerations
False Negatives
If the shellcode instructions are far apart, simple implementations might not detect the shellcode.

Due to the nature of assembly instructions not having a defined start or end, implementations which do not process all start sequences (for example, when they a find byte sequence of interest, continue scanning forwards from the end of it) might not detect the shellcode.

This technique might not detect more complex or obfuscated instructions. For that purpose, Dynamic Analysis or Emulated File Analysis could assist by analyzing the actual instruction function.

This technique may not detect self-modifying code. To make it harder for a process to modify itself, Process Segment Execution Prevention should be used, while noting its considerations.

This technique might not detect malicious shellcode which reuses instructions in the target binary for malicious effect, as memory references in the presumed assembly code are not dereferenced. Dynamic Analysis and Emulated File Analysis, when set up properly to fork from the running target binary, might detect this. Process Segment Execution Prevention combined with Segment Address Offset Randomization frequently makes introduction of shellcode through overwriting a saved return pointer more difficult. Call stack depth analysis might detect excessive reuse of instructions in the target binary. Shadow Stack Frames might detect that a stack frame's return address has changed and Stack Frame Canary Verification might detect that the stack frame's return address was overwritten. Other heuristic methods might detect jump-oriented programming shellcode.

With inserting code directly, that it is not a buffer overflow, and just some place where code is executed either to a file or a write-what-where, the buffer overflow mitigations do not help. Behavioral analysis could detect this, or proper access control could mitigate this.

False Positives
Byte sequences containing code that is never used as machine code are still analyzed and flagged for anomalies, and eventually, it is likely that an attack sequence will arise from the sheer volume of bytes transmitted.
```
```
定義
分析位元組序列並確定它們是否可能代表惡意 shellcode。

同義詞： Shellcode 傳輸偵測 。
怎麼運作的
對位元組進行分析，就好像它們是機器碼指令一樣，並記錄已知 shellcode 的常見元件的指令，例如堆疊樞軸、從記憶體位址表讀取以及禁用保護或執行程式碼的函數的系統呼叫。例如，x86 指令b0 0b: mov $11, %ax，無需進一步更改寄存器%ax，然後執行Linux 內核中的cd 80: syscall系統調用，該系統execve()

該技術可以檢測 shellcode，無論它是否會導致目標二進位檔案中的緩衝區溢位。

如果位元組序列包含與惡意 shellcode 中使用的序列類似的序列，則整個位元組序列將被標記，並且可以呼叫後續技術​​。

注意事項
假陰性
如果 shellcode 指令相距較遠，簡單的實作可能無法偵測到 shellcode。

由於彙編指令的性質沒有定義開始或結束，因此不處理所有開始序列的實作（例如，當它們找到感興趣的位元組序列時，從其末尾繼續向前掃描）可能無法偵測到 shellcode 。

此技術可能無法偵測更複雜或混淆的指令。為此，動態分析或模擬檔案分析可以透過分析實際指令功能來提供幫助。

此技術可能無法偵測自修改程式碼。為了使進程更難修改自身，應使用進程段執行保護，同時注意其註意事項。

此技術可能無法偵測到重複使用目標二進位檔案中的指令以達到惡意效果的惡意 shellcode，因為假定的彙編程式碼中的記憶體參考不會被取消引用。當動態分析和模擬檔案分析正確設定為從運行的目標二進位檔案派生時，可能會偵測到這一點。進程段執行預防與段位址偏移隨機化相結合經常使透過覆蓋保存的返回指標來引入 shellcode 變得更加困難。呼叫堆疊深度分析可能會偵測到目標二進位檔案中指令的過度重複使用。影子堆疊幀可能會檢測到堆疊幀的返回地址已更改，而堆疊幀金絲雀驗證可能會檢測到堆疊幀的返回地址已被覆蓋。其他啟發式方法可能會偵測面向跳轉的程式設計 shellcode。

透過直接插入程式碼，這不是緩衝區溢出，而只是在檔案或寫入內容中執行程式碼的某個地方，緩衝區溢出緩解措施沒有幫助。行為分析可以檢測到這一點，或者適當的存取控制可以緩解這一點。

誤報
包含從未用作機器代碼的程式碼的位元組序列仍會被分析並標記異常，最終，傳輸的大量位元組可能會產生攻擊序列。
```

### 憑證分析Certificate Analysis
```
Definition
Analyzing Public Key Infrastructure certificates to detect if they have been misconfigured or spoofed using both network traffic, certificate fields and third-party logs.

How it works
Certificate Analysis ensures that the data elements of the certificate are current and anchored in a known trust model. Certificate authorities, revocation lists, and third-party secure logs are used in the analysis. Analysis includes detection of server impersonation, phishing domains, and forged certificates.

TLS certificates are designed to expire to ensure that the cryptographic keys are forced to be changed on a regular basis. The certificates in the trust path also expire and can cause a break in the trust chain. This means that even if a server certificate is updated correctly, intermediate certificates can expire and the trust chain is not maintained. This can cause services to become unavailable.

Digital Artifact Relationships:
```
```
定義
使用網路流量、證書欄位和第三方日誌分析公鑰基礎設施證書，以偵測它們是否配置錯誤或被欺騙。

怎麼運作的
憑證分析可確保憑證的資料元素是最新的並錨定在已知的信任模型中。
分析中使用憑證授權單位、撤銷清單和第三方安全日誌。
分析包括偵測伺服器模擬、網路釣魚網域和偽造憑證。

TLS 憑證設計為會過期，以確保強制定期變更加密金鑰。信任路徑中的憑證也會過期，並可能導致信任鏈中斷。
這意味著即使伺服器憑證已正確更新，中間憑證也可能會過期並且信任鏈不會得到維護。
這可能會導致服務不可用。

數位工件關係：
這種防禦技術與特定的數位製品有關。點擊工件節點以獲取更多資訊。
```
### 主動憑證分析Active Certificate Analysis
```
Definition
Actively collecting PKI certificates by connecting to the server and downloading its server certificates for analysis.

How it works
Analysis of server certificates using active methods to detect if certificates have been misconfigured or spoofed by using elements of the certificate, certificate authorities and signatures.

Certificate validity analysis
This can be accomplished by verifying the digital signature on certificate.

Certificate path analysis
The client's browser can perform path verification to ensure that the server's certificate contains a valid trust anchor.

Certificate configuration analysis
Some browsers can be configured to implement the key-usage extensions contained certificates. This can help to prevent a certificate from being misused.

Certificate revocation status analysis
Using either Certificate Revocation Lists (CRLs) or Online Certificate Status Protocol (OCSP) to determine the revocation status. OCSP Stapling, binding the status with the certificate, helps to mitigate potential delay in status verifications.

Considerations
Management of the PKI across the enterprise typically requires automation to maintain scalability and flexibility
If the certificate authority, issuing the certificate, is compromised then all of the certificates issued by the CA are suspect
There may be delays associated with updates to certificates
Revoked certificates give the appearance of valid certificates until they are published to a trusted revocation service (OCSP or CRL)
The revocation service (OCSP or CRL) may be down during our connection and a browser will need to make a decision will need to be made about trusting the connection
```

```
定義
透過連接伺服器並下載其伺服器憑證進行分析，主動收集PKI憑證。

怎麼運作的
使用主動方法分析伺服器證書，透過使用證書、證書頒發機構和簽名等元素來檢測證書是否配置錯誤或被欺騙。

證書有效性分析
這可以透過驗證證書上的數位簽章來完成。

證書路徑分析
客戶端的瀏覽器可以執行路徑驗證，以確保伺服器的憑證包含有效的信任錨。

證書配置分析
某些瀏覽器可以設定為實作包含憑證的金鑰使用擴充功能。這有助於防止證書被濫用。

憑證吊銷狀態分析
使用憑證撤銷清單 (CRL) 或線上憑證狀態協定 (OCSP) 來確定撤銷狀態。OCSP 裝訂將狀態與憑證綁定在一起，有助於減少狀態驗證中潛在的延遲。

注意事項
整個企業的 PKI 管理通常需要自動化以保持可擴展性和靈活性
如果頒發憑證的憑證授權單位受到損害，則 CA 頒發的所有憑證都值得懷疑
證書更新可能會出現延遲
撤銷的憑證在發佈到可信任撤銷服務（OCSP 或 CRL）之前會顯示為有效憑證
吊銷服務（OCSP 或 CRL）可能在我們的連線期間關閉，瀏覽器需要做出信任連線的決定
數位工件關係：
這種防禦技術與特定的數位製品有關。點擊工件節點以獲取更多資訊。
```
### 被動憑證分析Passive Certificate Analysis
```
Definition
["Collecting host certificates from network traffic or other passive sources like a certificate transparency log and analyzing them for unauthorized activity.","Passively collecting certificates and analyzing them."]
How it works
Certificates are analyzed outside of a TLS server connection using third-party secure update logs, domain name analysis and analytics.

Secure update certificate logs
Certificate Logs The key enabling feature is a secure service that maintains record logs of certificate activities. The logs allow users to only append certificates and never to delete or modify the log entries. The logs use Merkle Tree Hashes to ensure they have not been tampered with. The logging service also allows for public auditing by any user.
The logging service, upon receipt of a certificate to log, will respond with a signed certificate timestamp (SCT). The SCT guarantees the certificate will be added to the log within the time specified. The SCT must be present with the certificate during a TLS handshake.

Certificate Monitoring Certificate monitoring, of the logs, is typically done by the CA and they watch for suspicious certificate logging and unusual certificates or extensions or permissions. Monitors are also responsible for verifying the logs are accurate and public.

Certificate Auditors Log integrity is verified by log auditors. Auditors make use of log proofs are used to validate the cryptographic hashes (Merkle Trees) that the log employs are consistent. In order to ensure consistency throughout multiple monitors and auditors, sharing a common logging service, gossip protocol is employed.

Phishing domain name analysis
A curated corpus of known benign domains and phishing domain names is used as training text for machine learning. Through the use of feature set extraction, vectors labels are created with scoring to indicated if they are considered benign or phishing domains.

A stream of new or updated SSL certificates with fully qualified domain names (FQDN) is analyzed against the feature vectors and a predictive model determines a score for the domains. The scoring considers distance measures such as Levenshtein distance to help in determining the final label score. Supervised learning is also employed using the curated domains of benign and phishing domains.

Subdomain phishing analysis, prepending a trusted domain to a phishing domain, and regular expression comparisons are also used in the label scoring model. A tunable measure is used to determine the threshold for alerting. This measure helps to balance between precision and recall measures.

Considerations
Some entity will need to run the logging service and a trusted entity is preferred.
Certificate Authorities will likely need to monitor the logging service for consistency.
Certificate revocation is unchanged and remains outside of Certificate Transparency, but certificates needing to be revoked are visible.
Technique dependent of reliable feed of new and updated certificates
Some certificate authorities allow for certificates to be registered with wildcards in the FQDN and thus will fail some of the subdomain scoring
Phishing HTTP domains will not be discovered
```
```
定義
[“從網路流量或其他被動來源（例如證書透明度日誌）收集主機證書，並分析它們是否存在未經授權的活動。”，“被動收集證書並分析它們。”]
怎麼運作的
使用第三方安全性更新日誌、網域分析和分析在 TLS 伺服器連線之外對憑證進行分析。

安全性更新憑證日誌
憑證日誌 關鍵的啟用功能是維護憑證活動記錄日誌的安全服務。日誌允許使用者僅附加證書，而不能刪除或修改日誌條目。日誌使用 Merkle 樹哈希來確保它們不被篡改。日誌記錄服務也允許任何使用者進行公開審計。
日誌記錄服務在收到要記錄的憑證後，將使用簽署憑證時間戳記 (SCT) 回應。SCT 保證證書將在指定的時間內新增至日誌中。在 TLS 握手期間，SCT 必須與憑證一起出現。

證書監控 日誌的證書監控通常由 CA 完成，他們監視可疑的證書日誌記錄以及異常的證書或擴充功能或權限。監控人員也負責驗證日誌的準確性和公開性。

證書審核員 日誌完整性由日誌審核員驗證。稽核人員利用日誌證明來驗證日誌使用的加密雜湊（Merkle 樹）是否一致。為了確保共享公共日誌服務的多個監視器和審計員的一致性，採用了八卦協議。

釣魚域名分析
已知良性域名和網路釣魚域名的精選語料庫用作機器學習的訓練文本。透過使用特徵集提取，建立向量標籤並進行評分，以指示它們是否被視為良性領域或網路釣魚域。

根據特徵向量分析具有完全限定網域名稱 (FQDN) 的新的或更新的 SSL 憑證流，並透過預測模型確定域的分數。評分會考慮編輯距離等距離測量，以幫助確定最終的標籤分數。也使用良性域和網路釣魚域的策劃域來採用監督式學習。

子網域網路釣魚分析、在網路釣魚網域前面新增可信任網域以及正規表示式比較也用於標籤評分模型。可調測量用於確定警報閾值。此措施有助於平衡精確度和召回率措施之間的平衡。

注意事項
某些實體需要執行日誌記錄服務，並且首選受信任的實體。
證書頒發機構可能需要監控日誌記錄服務的一致性。
憑證撤銷未發生變化，且仍處於憑證透明度之外，但需要撤銷的憑證是可見的。
技術依賴新證書和更新證書的可靠饋送
某些證書頒發機構允許在 FQDN 中使用通配符註冊證書，因此某些子網域評分會失敗
網路釣魚 HTTP 網域不會被發現
數位工件關係：
這種防禦技術與特定的數位製品有關。點擊工件節點以獲取更多資訊。
```
### 用戶端-伺服器負載分析Client-server Payload Profiling
```
Definition
Comparing client-server request and response payloads to a baseline profile to identify outliers.

How it works
Profiling request and response payloads across multiple clients to a single server to develop a baseline of their characteristics. May take into account request/response sizes, entropy, frequency, and rhythm. Finally, identify outliers as they may indicate a malicious payload delivery and subsequent server exploitation.

Considerations
Collecting metrics to establish a profile can be challenging since user behavior can change easily.
Employees may work different hours or inconsistent schedules which will cause false positives.
Collection of network activity to generate metrics is a computationally intensive process.
Users may log into different workstations which may cause false positives.
Digital Artifact Relationships:
This defensive technique is related to specific digital artifacts. Click the artifact node for more information.
```
```
定義
將客戶端-伺服器請求和回應負載與基準設定檔進行比較，以識別異常值。

怎麼運作的
分析多個客戶端到單一伺服器的請求和回應負載，以建立其特徵的基線。可以考慮請求/回應大小、熵、頻率和節奏。最後，識別異常值，因為它們可能表明惡意負載傳輸和隨後的伺服器利用。

注意事項
收集指標來建立檔案可能具有挑戰性，因為使用者行為很容易改變。
員工可能會工作不同的時間或不一致的時間表，這會導致誤報。
收集網路活動以產生指標是一個計算密集型過程。
使用者可能會登入不同的工作站，這可能會導致誤報。
數位工件關係：
這種防禦技術與特定的數位製品有關。點擊工件節點以獲取更多資訊。
```
### 連線嘗試分析Connection Attempt Analysis
```

```
```

```
### DNS 流量分析DNS Traffic Analysis
```

```
```

```
### 檔案雕刻File Carving
```

```
```

```
### 入站會話量分析Inbound Session Volume Analysis
```

```
```

```
### IPC 流量分析IPC Traffic Analysis
```

```
```

```
### 網路流量社群偏差Network Traffic Community Deviation
```

```
```

```
### 每台主機下載上傳比率分析Per Host Download-Upload Ratio Analysis
```

```
```

```
### 協定元資料異常檢測 Protocol Metadata Anomaly Detection
```

```
```

```
### 中繼模式分析 Relay Pattern Analysis
```

```
```

```
### 遠端終端會話偵測 Remote Terminal Session Detection
```

```
```

```
### RPC 流量分析(RPC Traffic Analysis)
```

```
```

```
