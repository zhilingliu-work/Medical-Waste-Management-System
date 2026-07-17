# 🧬 醫療廢棄物暨資源管理系統整合應用
## 基於 Django 5.1.6 與物聯網物聯勾稽之智慧化醫療廢棄物主動式追蹤安全管理系統

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
| **開發團隊** | 國立高雄科技大學 電腦與通訊工程系（電通三甲）<br>王俊龍 (C112110149)、劉志凌 (C112110130)、張福榮 (C112110160) |
| **專案定位** | 大三實務專題開發成果 |
| **製作日期** | 民國 114 年 9 月 — 115 年 6 月 |

---

## 📖 專案簡介與設計思維

本系統是一套專為醫療機構量身打造的**智慧化醫療廢棄物數位追蹤與安全管理系統**。因醫療生物危害廢棄物（如感染性廢棄物）具備極高的生物危害風險，其處理與清運流程受到法律嚴格控管。

本專案採取務實主義工程導向，將核心研發精力完全聚焦於**物聯網硬體整合、資料勾稽一致性維護、主動式資安防禦與異常警報機制**。系統編制排除基礎帳號與部門管理模組之贅述，全功能聚焦於獨創之**「異常即時警報與智慧審計機制」**。透過在科室登記、磅秤秤重、轉運、清運各階段進行精密數位勾稽，徹底杜絕醫療廢棄物非法外流之風險，為現代化智慧醫院提供全方位的技術保障。

---

## 📁 儲存庫檔案架構 (Repository Structure)

本專案之目錄樹狀結構與檔案配置如下：

```text
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
