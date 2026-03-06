# Tutoref Backend - 履歷用專案摘要

## 系統簡介
Tutoref 是一個山地服務社團為了有系統性地進行教案管理與搜尋系統，目標是讓大學生或內容管理者可以更有效率地上傳、整理、搜尋與維護教案資料。

這套後端主要提供三個核心能力：
- 教案生命週期管理：包含教案 CRUD、收藏、個人教案管理與欄位擴充（如排序與瀏覽次數）
- 搜尋與內容處理：結合 Elasticsearch 與文件前處理流程，提升教案搜尋的精準度與可用性
- 平台整合與穩定運行：整合 Google 登入/帳號關聯、Google Drive 檔案流程、Celery 非同步任務與 Docker 化部署

整體上，這是一個從 API 設計、資料模型、搜尋流程到部署維運都已串起來的實務型 Django 後端專案。

## 專案連結
- Repository: https://github.com/sksmaed/tutoref_backend
- README: https://github.com/sksmaed/tutoref_backend/blob/main/README.md

## 後端在做什麼
`tutoref_backend` 是 `tutoref.tw` 的 Django 後端，主要負責教案資料管理、身份驗證、搜尋能力、檔案上傳流程、背景任務處理，以及可部署到正式環境的 API 服務。

## 技術棧
- Python, Django
- PostgreSQL, Elasticsearch
- Celery (背景任務)
- Docker / Docker Compose
- Google Drive 整合

## 我做過的內容

### 登入與帳號整合
- 建立驗證 API 基礎並修正帳號流程問題（PR #4, #18）
- 處理 Google 登入 callback 與 Google/Django 帳號狀態同步（PR #24, #25）

### 部署與環境治理
- 建立/優化開發環境設定與環境參數處理（PR #3, #7）
- 補齊 Vultr 相關部署設定，提升上線可用性（PR #17）

## 屬於我的 PR
以下依 `git log --all --merges` 與各 PR 合併時帶入的 commit 訊息整理，不直接列連結。

- 2025-09-24 | PR #19 `feat/api`: 整理核心 API 與設定/路由，修正設定檔與 schema、model 對齊問題，提升整體 API 一致性。
- 2025-09-21 | PR #18 `fix/createsuperuser`: 修正 email-based 自訂使用者管理器，改善 `createsuperuser` 流程與帳號建立行為。
- 2025-09-17 | PR #13 `feat/teaching-plna-management-api`: 新增「我的教案」API，並優化多個教案 API 回傳欄位。
- 2025-09-14 | PR #12 `feat/teaching-plna-management-api`: 完成教案 CRUD、收藏 API，並在搜尋流程加入學年/學期解析邏輯。
- 2025-09-13 | PR #11 `refact/upload-api`: 重構上傳 API 與處理流程，調整教案 schema/migration，並更新 PDF 前處理與搜尋流程。
- 2025-09-06 | PR #8 `refact/search-api`: 重構搜尋 API 實作與 workflow，將部分教案服務由 FastAPI 逐步移轉到 Django。
- 2025-08-25 | PR #5 `refact/core-api`: 重構驗證相關 API，包含登入、註冊與重設密碼流程。
- 2025-08-24 | PR #4 `feat/auth-api`: 建立完整驗證系統初版，含 Google login 與共用驗證元件。
