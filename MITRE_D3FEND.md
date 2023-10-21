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

Definition
Detection of unauthorized use of administrative network protocols by analyzing network activity against a baseline.

How it works
Network protocols such as RDP, IPMI, SSH, SNMP, VNC, MOSH, NX, TeamViewer, SPICE, PCoIP, and others are used by system administrators to remotely manage servers. Defenders monitor administrative network activity to determine if the use of remote protocols is malicious. Attackers can abuse administrative protocols and leverage them for initial access to various endpoints. For example, an attacker with valid credentials will remotely SSH or RDP into a server and attempt to blend in with existing traffic from system administrators. By monitoring the traffic activity, it is possible to detect when the protocols are behaving differently from a known baseline of system administration activity.

Considerations
Administrative traffic can be encrypted, making network protocol analysis a challenge
False alarms can be mitigated by integration with inventory management systems


### 位元組序列模擬Byte Sequence Emulation


### 憑證分析Certificate Analysis

### 主動憑證分析Active Certificate Analysis

### 被動憑證分析Passive Certificate Analysis

### 用戶端-伺服器負載分析Client-server Payload Profiling

### 連線嘗試分析Connection Attempt Analysis

### DNS 流量分析DNS Traffic Analysis

### 檔案雕刻File Carving

### 入站會話量分析Inbound Session Volume Analysis

### IPC 流量分析IPC Traffic Analysis

### 網路流量社群偏差Network Traffic Community Deviation

### 每台主機下載上傳比率分析Per Host Download-Upload Ratio Analysis

### 協定元資料異常檢測 Protocol Metadata Anomaly Detection

### 中繼模式分析 Relay Pattern Analysis

### 遠端終端會話偵測 Remote Terminal Session Detection

### RPC 流量分析(RPC Traffic Analysis)
