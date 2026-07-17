# 🧬 醫療廢棄物暨資源管理系統整合應用
## 基於 Django 5.1.6 與物聯網全流程勾稽之智慧化醫療廢棄物安全管理系統

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.12+-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python Version">
  <img src="https://img.shields.io/badge/Django-5.1.6-092E20?style=for-the-badge&logo=django&logoColor=white" alt="Django">
  <img src="https://img.shields.io/badge/Platform-Ubuntu%20%7C%20Windows%2011-0078d4?style=for-the-badge&logo=windows&logoColor=white" alt="Platform">
  <img src="https://img.shields.io/badge/Architecture-RBAC%20Compliant-orange?style=for-the-badge" alt="Architecture">
  <img src="https://img.shields.io/badge/Security-SSL%20Protected-red?style=for-the-badge" alt="Security">
</p>

## 📌 專案與作者資訊

| 項目 | 詳細資訊 |
| :--- | :--- |
| **專案名稱** | 醫療廢棄物暨資源管理系統整合應用 |
| **獲獎榮譽** | 大三年度實務專題（獲獎項目） |
| **開發團隊** | 國立高雄科技大學 電腦與通訊工程系（電通三甲） <br> 王俊龍 (C112110149)、劉志凌 (C112110130)、張福榮 (C112110160) |
| **專案定位** | 大三實務專題開發成果 |
| **製作日期** | 民國 114 年 9 月 — 115 年 6 月 |

---

## 📖 專案簡介

本系統是一套專為醫療機構設計的**智慧化醫療廢棄物數位追蹤與安全管理系統**。醫療廢棄物（如感染性廢棄物）因具備高生物危害性，其處理流程受到嚴格的法律規範。

系統基於 Django 5.1.6 框架開發，整合了實體硬體感測器（如藍牙電子磅秤與 QR Code 條碼列印）導入數位追蹤工作流。本系統編制排除基礎帳號與部門管理模組之贅述，全功能聚焦於獨創之**「異常即時警報與智慧審計機制」**。透過在秤重、運送、清運各階段進行精密數位勾稽，徹底杜絕醫療廢棄物非法外流之風險，為現代化智慧醫院提供全方位的技術保障。

---

## 📁 專案檔案架構

本專案之目錄樹狀結構與檔案配置如下：

~~~text
├── .claude/                  # Claude 開發設定與歷史上下文快取
├── .git/                     # Git 版本控制核心資料夾
├── access_control/           # 基於角色型存取控制 (RBAC) 權限模組
├── dashboard_extension/      # 數據儀表板核心擴充與圖表分析模組
├── logs/                     # 系統日誌儲存資料夾 (自動化歸檔目錄)
├── Main/                     # Django 系統主路由與專案核心載入點
├── MedicalWasteManagementSystem/ # 專案組態設定與全域伺服器設定
├── static/                   # 靜態資源原始檔案 (CSS, JavaScript, Images)
├── staticfiles/              # 生產環境收集彙整後之靜態檔案目錄
├── templates/                # 系統前端整合 HTML 頁面模板
├── waste_system_django-main/ # 醫療廢棄物底層主要子系統模組
├── WasteManagement/          # 醫療廢棄物申報、入庫、出庫核心邏輯
├── WastePrediction/          # 廢棄物生成量預測與趨勢分析模組
├── WasteTransportation/      # 清運車隊物流追蹤與載運車次管理
├── .env                      # 環境變數設定檔 (已排除於版本控制，保護機密私鑰)
├── .gitignore                # Git 排除追蹤規則配置檔
├── CLAUDE.md                 # 開發維護指令指引指南
├── DATABASE_SCHEMA.md        # 系統資料庫 Schema 結構定義說明書
├── db.sqlite3                # 本地開發資料庫 (WAL 效能模式)
├── db.sqlite3-shm            # SQLite 共享記憶體暫存檔
├── db.sqlite3-wal            # SQLite 預寫式日誌 (Write-Ahead Log) 暫存檔
├── field_config.json         # 動態欄位配置定義檔
├── initialize.sh             # 生產環境一鍵自動化部署腳本
├── logrotate.conf            # 日誌備份與檔案輪替配置規則檔
├── manage.py                 # Django 命令列工具管理入口
├── MANUAL_SETUP.txt          # 系統手動建置與設定參考手冊
├── README.txt                # 部署與維護備忘錄 (原始說明檔)
├── requirements.txt          # Python 環境依賴套件清單
├── start-server.sh           # 生產環境 Gunicorn 伺服器啟動控制腳本
├── stop-server.sh            # 生產環境服務優雅關閉控制腳本
└── 系統規格書.md              # 醫療廢棄物管理系統規格與詳細分析文件
~~~

---

## 🛠️ 系統環境需求

本專案在相容性與運作效能上，支援以下硬體與軟體部署規範：

### 1. 硬體規格建議
* **中央處理器 (CPU)：** 2 核心以上 (Production 建議); 本地端測試於 AMD Ryzen 7 4800H 運行流暢。
* **隨機存取記憶體 (RAM)：** 4GB 以上 (建議使用 8GB DDR4 以上，以保障 Nginx 及 Gunicorn 高併發負載)。
* **硬碟空間 (Disk Space)：** 最少 20GB 固態硬碟 (SSD) 空間。

### 2. 軟體環境相容
* **開發與測試環境：** Windows 11 (64位元)
* **生產部署環境：** Ubuntu 22.04 LTS 或更新版本 (建議 22.04 或 24.04)
* **Python 版本：** Python 3.12+ (若部署環境低於 3.12，自動化腳本將自動安裝補足)
* **網頁伺服器：** Nginx 1.18 或更新版本
* **資料庫引擎：** SQLite 3.37+ (具備 WAL mode 效能調優)

---

## 👥 使用者角色權限設計 (RBAC)

系統規劃了完整的 **6 大使用者身分組**，各角色具備嚴格的權限劃分與對應可用功能：

1. **根帳號 (root)**：
   * 系統最高權限管理員。
   * 獨佔可管理 Django Administration（本系統帳號管理底層框架）。
   * 唯有具備伺服器管理權限的使用者，才能動態管理一般事業廢棄物之欄位資訊。
2. **管理者 (manager)**：
   * 負責系統營運配置與高階審核，可操作【後台管理】與所有基本配置物件設定。
3. **行政人員 (staff)**：
   * 負責院內日常行政作業，包括過磅與載運紀錄查詢、結算載運單、生成統計報表。
4. **登錄者 (loginer)**：
   * 日常資料維護人員，協助處理基礎系統資料登記。
5. **匯入者 (importer)**：
   * 負責批次外部數據與歷史資料匯入系統。
6. **外部人員 (outer)**：
   * 現場實體清運與作業人員。
   * 負責在現場操作【行動裝置登記】與【QR code列印】。

---

## ⚙️ 系統核心功能介紹

### 系統帳號管理
* **連動式檢視**：點擊左側角色群組與使用者列表，右側詳細資料即時連動呈現。
* **動態新增與權限分組**：提供完整表單輸入使用者帳號、密碼及指定權限等級（身分組）。
* **列表管理**：列表依身分組清晰歸類，支援一鍵刪除。

### 廢棄物種類和部門管理
* **雙欄整合配置**：左欄管理廢棄物種類（名稱、單位），右欄管理部門資訊（代碼、名稱）。
* **行內新增**：點擊【新增】提供空白輸入列，支援使用「分號」一次輸入多個物件資訊，再點擊打勾儲存。
* **行內編輯/刪除**：提供一鍵切換可更改狀態、保存、取消或單筆垃圾桶刪除。
* **批次刪除**：勾選複數項目後，上方按鈕會動態切換為「批次刪除」。
* **關鍵字查詢**：提供頂部查詢列，輸入代號或名稱即可即時模糊篩選。

### 定點和機構管理
* **實體定點維護**：左欄管理院內所有實體過磅定點（代碼、定點名稱，如醫療大樓一樓之一）。
* **外部合作機構**：右欄管理委外清除機構與處理機構，支援行內編輯、批次勾選刪除及關鍵字即時檢索。

### 警報紀錄管理
* **主動式異常警報**：即時追蹤過磅流程產生的重量異常與申報頻率異常。
* **複合條件篩選**：支援依發生日期（起/迄）、警報名稱、警報類型及產出部門進行複合式查詢，並提供一鍵「↺」重置功能。
* **定位追蹤與標記**：檢視警報詳情時，點擊【定位紀錄】按鈕，系統會自動跳轉至對應過磅頁面，並對該異常紀錄實施「黃色高亮閃爍 3 秒」的精準追蹤。
* **警報條件設定門檻**：可動態設定「廢棄物產出量監控」的上下限重量閥值，及各部門的「過秤頻率監控」（每日過秤次數下限）。
* **趨勢折線圖**：可自由切換特定年份或月份，顯示警報次數的時間軸走勢。
* **進度條監控**：展示各部門昨日應過磅與實際過磅完成次數的比例，支援輸入關鍵字過濾部門進度條。
* **資料匯出與列印**：支援將警報趨勢圖表直接匯出為 PDF、PNG、Excel 檔，或呼叫系統原生直接列印。

### QR code 列印
* **標籤即時預覽**：左側預覽區可隨右側設定連動更新，即時顯示包含操作人員、廢棄物種類、部門及列印時間的貼紙樣式。
* **藍牙無線配對**：支援透過瀏覽器 Web Bluetooth 技術，搜尋並無線配對市售藍牙標籤機。
* **自訂列印設定**：調整所需部門、廢棄物類型及列印張數後，一鍵派送至實體標籤機產出專屬二維條碼，完成打包。

### 行動裝置登記
* **相機條碼解碼**：整合行動裝置鏡頭，一鍵喚起相機掃描廢棄物袋上的 QR code，自動解碼並在畫面上秒速帶出部門、種類、人員與打包時間。
* **藍牙連線**：透過網頁端直接配對自行組裝的 ESP34 實體電子磅秤裝置。
* **重量讀取**：點擊【重量紀錄】按鈕即時從磅秤硬體獲取重量並呈現在畫面上。
* **遠端控制功能**：支援「秤盤一鍵歸零」、「多點參數校正（輸入已知公克重量重新計算校正因子）」、「單位動態切換（公斤 KG / 公克 G）」以及「遠端修改磅秤裝置名稱（限 20 字元內）」。
* **一鍵安全上傳**：確認無誤後，點擊【送出紀錄】即可將完整的重量、條碼、定點資訊整合封包上傳資料庫，並自動重置表單。

### 過磅紀錄管理
* **全局看板**：頂部區塊顯示總過磅筆數、昨日過磅重量(kg)、已載運重量(kg)與未載運重量(kg)等營運指標。
* **刪除防護鎖定**：操作欄設有安全隔離鎖。
* **狀態辨識**：已關聯載運單（已清運）的過磅紀錄顯示鎖頭圖示禁止刪除；未載運的過磅紀錄方顯示垃圾桶允許刪除。
* **一鍵結算載運**：勾選複數未載運過磅紀錄，點擊【建立載運單(結算)】，可在懸浮視窗中選擇合作的清理公司與處理公司，一鍵打包轉換成載運單。
* **多元匯出與列印**：支援將篩選後或手動勾選的過磅資料，即時轉存為高解析度 PDF、PNG 或標準 Excel 表單，並支援直接呼叫列印預覽。

### 載運紀錄管理
* **複合式回溯**：提供載運日期區間、清理/處理機構名稱的複合查詢。
* **安全反結算**：如載運有誤，可勾選該載運紀錄點擊【取消載運】，將其整單作廢，並自動將該批過磅紀錄狀態還原至「未載運」狀態以供重新分配，安全機制嚴密。
* **嵌套明細檢視**：點擊【查看】可開啟懸浮視窗，顯示該載運單打包的所有子過磅紀錄明細。

### 報表管理 (部門)
* **動態自訂圖表**：提供視覺化自訂報表產生器。
* **版面拖曳**：使用者可自訂建立多個圖表，並支援在畫面上以拖拉式調整圖表的排列與匯出順序。
* **線段疊加**：在單個圖表中，點擊【新增線段】可自由疊加不同的資料源、時間區段及廢棄物種類。
* **細部渲染**：提供「顯示圖表數值」、「顯示完整表格格線」與「顯示原始資料表格」等功能開關。
* **多檔案匯出**：圖表渲染生成後，支援單鍵匯出為高畫質 PNG 圖片、PDF 技術文件、或是含有完整原始資料分頁的 Excel 試算表。

---

## 🚀 生產環境部署指南

### 1. 一鍵自動化部署
為簡化上線流程，系統附帶 `initialize.sh` 部署指令，可全自動化完成依賴建置：

~~~bash
# 賦予部署腳本執行權限
chmod +x initialize.sh

# 執行部署腳本
./initialize.sh
~~~

**部署腳本執行細節：**
1. 偵測 Python 版本，低於 3.12 則自動啟用 PPA 安裝最新 Python 3.12。
2. 安裝生產環境所需軟體元件 (Nginx, Gunicorn 等)。
3. 使用適當的 Python 版本自動建立本地獨立虛擬環境。
4. 自動安裝所有專案依賴套件 (`requirements.txt`)。
5. 配置系統環境變數，並自動建立 SQLite 資料庫。
6. 設定 Nginx 網頁伺服器設定，並在備妥 SSL 憑證下自動套用。
7. 自動初始化資料庫（寫入 43 個預設科室部門與感染性廢棄物類型）。
8. 設定 logrotate 日誌自動輪替與歸檔機制。

---

### 2. SSL/HTTPS 安全憑證配置
為確保醫療資料在網路傳輸中不被竊聽，系統預置 SSL 安全導向支援：

#### A. 憑證檔案放置
將資訊室或憑證授權機構 (CA) 核發的憑證檔案手動置於系統安全路徑：

~~~bash
# 建立系統專用 SSL 安全目錄
sudo mkdir -p /etc/ssl/mwms
sudo chmod 700 /etc/ssl/mwms

# 複製憑證並鎖定權限 (保護私鑰不外流)
sudo cp cert.pem /etc/ssl/mwms/cert.pem
sudo cp key.key /etc/ssl/mwms/key.key
sudo chmod 640 /etc/ssl/mwms/cert.pem /etc/ssl/mwms/key.key
sudo chown root:www-data /etc/ssl/mwms/cert.pem /etc/ssl/mwms/key.key
~~~

#### B. 配置 Nginx 憑證指向
編輯 Nginx 設定檔 `/etc/nginx/sites-available/mwms`，確認包含以下設定：

~~~nginx
ssl_certificate /etc/ssl/mwms/cert.pem;
ssl_certificate_key /etc/ssl/mwms/key.key;
~~~

測試 Nginx 設定並重新載入：

~~~bash
sudo nginx -t
sudo systemctl reload nginx
~~~

#### C. 啟用 Django 生產環境安全參數
編輯生產環境之 `.env.production`，將以下變數設為 `True` 以啟用嚴格瀏覽器安全政策：

~~~properties
SECURE_SSL_REDIRECT=True
SESSION_COOKIE_SECURE=True
CSRF_COOKIE_SECURE=True
~~~

---

### 3. 智慧日誌系統與自動歸檔
系統內置高規格審計日誌，所有日誌皆採用高標準統一格式記錄：
`YYYY/MM/DD hh:mm:ss.SSS Z+0800 | [類型] | 詳細訊息`

* **實時操作日誌**：`logs/latest.log` (記錄使用者在系統內進行的所有勾稽、警報確認與操作審計)
* **調試詳細日誌**：`logs/debug.log` (僅開發模式下寫入詳細偵錯日誌)
* **錯誤追蹤日誌**：`logs/error.log` (記錄系統拋出之非預期例外或錯誤)

#### 日誌歸檔與輪替控制 (`logrotate`)
為防止日誌檔案無限制增長導致伺服器磁碟空間耗盡，系統設有以下自動輪替機制：
* 每次伺服器重新啟動時，會自動打包舊有日誌：命名格式 `YYYY-MM-DD-N.tar.gz`。
* 系統中每日最大保留 7 個歸檔封包，避免儲存溢出。

---

### 4. 伺服器效能調優
為因應大型醫療機構中多科室同時上線申報、秤重的高併發量負荷，系統進行了以下調優：

#### A. Gunicorn Worker 數量最佳化
編輯 `gunicorn.conf.py` 調整 Worker 執行緒數量，建議配比公式：`(CPU 核心數 × 2) + 1`

~~~python
# 範例：若伺服器 CPU 為 4 核心，建議調整 workers = 9
workers = 9
~~~

#### B. SQLite (WAL mode) 最佳化
資料庫雖預置 SQLite，但已自動啟用 **WAL (Write-Ahead Log) 預寫日誌模式**。
* **極大化併發效能**：實作讀、寫分離，使讀取與寫入操作能並行不悖，適合 50 人以下之中小型醫療院所高頻率秤重登錄。

---

## 🛠️ 常用系統維護指令表

### Django 系統維護
~~~bash
source .venv/bin/activate             # 啟動 Python 虛擬環境
python manage.py migrate              # 執行資料庫遷移
python manage.py init_system          # 初始化預設系統設定與科室資料
python manage.py collectstatic        # 彙整前端靜態網頁檔案
~~~

### 服務生命週期控制
~~~bash
./start-server.sh                     # 啟動 Gunicorn 及背景服務 (含重複啟動防護)
./stop-server.sh                      # 安全且優雅關閉伺服器 (附10秒優雅退場緩衝)
sudo systemctl restart nginx          # 重新啟動 Nginx 網頁伺服器
~~~

### 監控與日誌檢視
~~~bash
tail -f logs/latest.log               # 即時監看使用者操作與警報軌跡
tail -f logs/error.log                # 追蹤即時系統錯誤
ls -lh logs/*.tar.gz                  # 檢視已歸檔打包之歷史日誌
~~~

### 資料庫備份與還原
~~~bash
# 建立備份
mkdir -p backups
cp db.sqlite3 backups/db_$(date +%Y%m%d_%H%M%S).sqlite3
cp db.sqlite3-wal backups/ 2>/dev/null || true

# 還原備份
./stop-server.sh
cp backups/db_目標日期_時間.sqlite3 db.sqlite3
./start-server.sh
~~~

---

## 📋 上線前安全檢查清單 (Pre-launch Checklist)

- [ ] **DEBUG 模式關閉：** 確認 `.env.production` 中 `DEBUG=False`。
- [ ] **金鑰保密：** `SECRET_KEY` 已重構為強隨機高強度金鑰，且 `.env.production` 權限已設為 `600`。
- [ ] **主機名保護：** `ALLOWED_HOSTS` 僅允許設定之醫院網域或指定生產 IP。
- [ ] **防火牆鎖定：** 防火牆僅開放 `80` (HTTP), `443` (HTTPS) 連線，後端 `8000` 連接埠已設為外部不可直接連線。
- [ ] **SSL 加密就緒：** HTTPS 安全憑證安裝無誤，瀏覽器鎖頭正確顯示且支援強導向（HTTP 自動跳轉 HTTPS）。
- [ ] **資料庫 WAL 啟用：** 資料庫讀寫測試正常，備份排程已加入 crontab。

---

## 🔍 常見問題與排除 (FAQ)

### 無法訪問網站（Nginx 沒反應）
1. 檢查 Gunicorn 本地服務是否正常運作：
   `ps aux | grep gunicorn`
2. 確認 Nginx 伺服器端狀態：
   `sudo systemctl status nginx`
3. 查看伺服器防火牆配置，是否正確放行 HTTP/HTTPS 埠口：
   `sudo ufw status`

### 502 Bad Gateway 錯誤
* **原因分析**：網頁伺服器 Nginx 無法連上後端運行的 Django Gunicorn 服務。
* **排除步驟**：
  1. 確認 Gunicorn 是否監聽本地 `8000` port：
     `netstat -tlnp | grep 8000`
  2. 檢查 `logs/error.log` 查看 Django 崩潰原因。
  3. 重啟系統服務：
     `./stop-server.sh && ./start-server.sh`

### 資料庫發生 Lock 鎖定錯誤
* **原因分析**：因多人頻繁寫入，或前次連線異常中斷導致 SQLite 程序併發鎖定。
* **排除步驟**：優雅關閉所有進程，待解鎖後重啟即可恢復：
  `./stop-server.sh`，確認完全無殘留 `gunicorn` 或 `python` 程序後，重啟 `./start-server.sh`。

### 忘記最高管理員密碼
1. 登入伺服器端並啟用虛擬環境，進入 Django Shell：
   `source .venv/bin/activate` ➔ `python manage.py shell`
2. 輸入以下 Python 語法重設密碼：
   ```python
   from django.contrib.auth.models import User
   user = User.objects.get(username='root')
   user.set_password('您的新密碼')
   user.save()
   exit()

### 秤重數據檔案或照片上傳因過大遭阻擋
* **排除步驟**：編輯 Nginx 站點設定 /etc/nginx/sites-available/mwms，在 server 區塊中放寬上傳大小限制：
client_max_body_size 500M;
設定完後重新載入：sudo systemctl reload nginx。
