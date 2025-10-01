# PERT/CPM 圖
![PERT/CPM 圖](PERT.png)
# 甘特圖
``` mermaid
gantt
    title 專案甘特圖
    dateFormat  YYYY-MM-DD
    section 分析與設計
    需求分析與規劃          :done, task1, 2025-10-01, 2025-10-02
    設計系統架構            :done, task2, 2025-10-03, 2025-10-06

    section 資料庫與前端
    資料庫設計              :active, task3, 2025-10-07, 2025-10-13
    前端UI/UX設計與開發     :active, task8, 2025-10-07, 2025-10-26

    section 功能開發
    開發使用者註冊與登入功能 :active, task4, 2025-10-14, 2025-10-20
    開發書籍刊登功能         :active, task5, 2025-10-14, 2025-11-07
    開發書籍篩選與搜尋功能   :active, task6, 2025-11-08, 2025-11-17
    開發降價通知功能         :active, task7, 2025-11-18, 2025-11-29

    section 測試與部署
    系統整合測試            :active, task9, 2025-11-30, 2025-12-14
    使用者測試              :active, task10, 2025-12-15, 2025-12-19
    文件統整                :active, task11, 2025-12-20, 2025-12-22

```

