# 功能性需求
### 1. 用戶註冊與安全（買賣家）
* 用戶必須為高科大學生，須持有學校電子郵件，方可註冊。
* 註冊時需提供用戶名、密碼、高科大電子郵件。
* 系統會驗證電子郵件是否為高科大使用信箱（即為「nkust.edu.tw」)。
* 若忘記密碼，需重新輸入高科大電子信箱，收取驗證碼，重設密碼。

### 2. 書籍刊登/編輯/刪除（賣家）
* **OCR 快速刊登**：賣家可使用 OCR 技術掃描書籍封面或 ISBN 碼，系統需自動識別並填入書籍相關資訊。
* **資訊手動補充與編輯**：當 OCR 辨識失敗或資訊不完整時，允許賣家手動輸入或修改書籍資訊。
* **設定書籍資訊**：賣家可設定書本的售價、上架狀態、商品描述等。
* **上傳書籍圖片**：允許賣家上傳書籍的實體照片。

### 3. 書籍搜尋與瀏覽資訊（買家）
* **關鍵字搜尋**： 買家可輸入書名等資訊進行搜尋。
* **多維度標籤篩選**： 提供如「科系」、「上架時間遠近」、「價錢高低」等標籤進行篩選。
* **書籍詳情頁面**： 買家可查看書籍的所有詳細資訊、圖片。

### 4. 互動與通知（買家）
* **降價通知提醒**：買家可針對特定書籍設定降價通知，當價格低於設定值時，系統應發送提醒。
* **加入追蹤/收藏**：買家可將有興趣的書籍加入收藏清單。

### 5. 聊天室（買賣家）
* 提供「上傳圖片」、「輸入文字」功能

# 非功能性需求
### 1. 效能
* **響應速度**：大多數面載入時間（例如書籍列表、搜尋結果頁）應在 3 秒內完成。
* **OCR 識別速度**：OCR 掃描並自動填充書籍資訊的過程應在 10 秒內完成。

### 2. 可用性與易用性
* **操作簡單**：APP 介面設計需直觀，首次使用者無需複雜說明即可快速完成書籍刊登和購買流程（特別是 OCR 輔助的刊登流程）。
* **介面一致性**：整個 APP 的設計風格、導航和操作流程應保持一致性。
* **錯誤訊息清晰**：系統錯誤（如網路連線問題、OCR 辨識失敗）應以使用者容易理解的方式呈現，並提供解決建議。
* **行動裝置適應性**：介面應能良好地適應不同尺寸和解析度的手機螢幕。

### 3. 安全性
* **身份驗證安全**：學校身份驗證機制應能有效防止非本校人員冒充。
* **隱私保護**：買賣家用戶名稱採取匿名方式。

# 功能分解圖

```mermaid
graph TD
  A[二手書交易平台] --> B[用戶註冊與安全]
  A --> C[書籍管理]
  A --> D[書籍搜尋與瀏覽]
  
  %% 用戶註冊與安全
  B --> B1[用戶註冊]
  B --> B2[身份驗證]
  B --> B3[密碼管理]
  
  
  %% 書籍管理
  C --> C1[書籍刊登]
  C --> C2[書籍編輯]
  C --> C3[書籍刪除]
  
  
  %% 書籍搜尋與瀏覽
  D --> D1[搜尋功能]
  D --> D2[篩選功能]
  D --> D3[詳情查看]
  
  
  
  %% 樣式設定
  classDef mainFunction fill:#e1f5fe,stroke:#01579b,stroke-width:3px
  classDef subFunction fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
  classDef detailFunction fill:#e8f5e8,stroke:#1b5e20,stroke-width:1px
  
  class A mainFunction
  class B,C,D subFunction
  class B1,B2,B3,C1,C2,C3,D1,D2,D3 detailFunction
```

```mermaid
graph TD
  A[二手書交易平台] --> E[互動與通知]
  A --> F[聊天室]

  %% 互動與通知
  E --> E1[降價通知]
  E --> E2[收藏功能]
  
  
  %% 聊天室
  F --> F1[文字溝通]
  F --> F2[圖片分享]

  %% 樣式設定
  classDef mainFunction fill:#e1f5fe,stroke:#01579b,stroke-width:3px
  classDef subFunction fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
  classDef detailFunction fill:#e8f5e8,stroke:#1b5e20,stroke-width:1px
  
  class A mainFunction
  class E,F subFunction
  class E1,E2,F1,F2 detailFunction
```  

# 使用案例圖
### 1. 用戶註冊與安全
```mermaid
flowchart TD
    subgraph 系統
        UC1(["註冊帳號"])
        UC2(["驗證高科大信箱"])
        UC3(["登入"])
        UC4(["忘記密碼"])
        UC5(["重設密碼"])
    end

    買家((買家)) --> UC1
    賣家((賣家)) --> UC1
    UC1 --> UC2
    買家 --> UC3
    賣家 --> UC3
    買家 --> UC4
    賣家 --> UC4
    UC4 --> UC5

```

```mermaid
flowchart TD
    %% 參與者
    Student[高科大學生]
    System[系統]
    EmailServer[電子郵件伺服器]
    
    %% 使用案例
    UC1((用戶註冊))
    UC2((電子郵件驗證))
    UC3((忘記密碼))
    UC4((重設密碼))
    UC5((登入系統))
    
    %% 關聯
    Student --> UC1
    Student --> UC3
    Student --> UC5
    
    UC1 --> System
    UC2 --> System
    UC3 --> System
    UC4 --> System
    UC5 --> System
    
    UC2 --> EmailServer
    UC4 --> EmailServer
    
    %% 包含關係
    UC1 -.->|<<include>>| UC2
    UC3 -.->|<<include>>| UC4
    
    %% 樣式
    classDef actor fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef usecase fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef system fill:#e8f5e8,stroke:#1b5e20,stroke-width:2px
    
    class Student actor
    class UC1,UC2,UC3,UC4,UC5 usecase
    class System,EmailServer system
```

### 2. 書籍刊登/編輯/刪除
```mermaid
flowchart TD
    subgraph 書籍管理系統
        UC1(["OCR 快速刊登"])
        UC2(["手動輸入 / 編輯書籍資訊"])
        UC3(["設定售價與狀態"])
        UC4(["上傳書籍圖片"])
        UC5(["刪除書籍"])
    end

    賣家((賣家)) --> UC1
    賣家 --> UC2
    賣家 --> UC3
    賣家 --> UC4
    賣家 --> UC5
    UC1 --> UC2

```


```mermaid
flowchart TD
    %% 參與者
    Seller[賣家]
    OCRService[OCR服務]
    Database[資料庫]
    
    %% 使用案例
    UC1((OCR快速刊登))
    UC2((手動輸入書籍資訊))
    UC3((編輯書籍資訊))
    UC4((設定售價與狀態))
    UC5((上傳書籍圖片))
    UC6((刪除書籍))
    UC7((管理書籍清單))
    
    %% 關聯
    Seller --> UC1
    Seller --> UC2
    Seller --> UC3
    Seller --> UC4
    Seller --> UC5
    Seller --> UC6
    Seller --> UC7
    
    UC1 --> OCRService
    UC1 --> Database
    UC2 --> Database
    UC3 --> Database
    UC4 --> Database
    UC5 --> Database
    UC6 --> Database
    UC7 --> Database
    
    %% 擴展關係
    UC1 -.->|<<extend>>| UC2
    UC3 -.->|<<include>>| UC4
    UC3 -.->|<<include>>| UC5
    
    %% 樣式
    classDef actor fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef usecase fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef system fill:#e8f5e8,stroke:#1b5e20,stroke-width:2px
    
    class Seller actor
    class UC1,UC2,UC3,UC4,UC5,UC6,UC7 usecase
    class OCRService,Database system
```

### 3. 書籍搜尋與瀏覽資訊
```mermaid
flowchart TD
    subgraph 書籍搜尋系統
        UC1(["關鍵字搜尋"])
        UC2(["多維度標籤篩選"])
        UC3(["查看書籍詳情"])
        UC4(["瀏覽書籍圖片"])
    end

    買家((買家)) --> UC1
    買家 --> UC2
    買家 --> UC3
    UC3 --> UC4


```


```mermaid
flowchart TD
    %% 參與者
    Buyer[買家]
    SearchEngine[搜尋引擎]
    Database[資料庫]
    
    %% 使用案例
    UC1((關鍵字搜尋))
    UC2((多維度篩選))
    UC3((瀏覽書籍清單))
    UC4((查看書籍詳情))
    UC5((查看書籍圖片))
    UC6((科系篩選))
    UC7((時間排序))
    UC8((價格排序))
    
    %% 關聯
    Buyer --> UC1
    Buyer --> UC2
    Buyer --> UC3
    Buyer --> UC4
    
    UC1 --> SearchEngine
    UC2 --> SearchEngine
    UC3 --> Database
    UC4 --> Database
    UC5 --> Database
    
    %% 包含和擴展關係
    UC2 -.->|<<include>>| UC6
    UC2 -.->|<<include>>| UC7
    UC2 -.->|<<include>>| UC8
    UC4 -.->|<<include>>| UC5
    
    %% 樣式
    classDef actor fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef usecase fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef system fill:#e8f5e8,stroke:#1b5e20,stroke-width:2px
    
    class Buyer actor
    class UC1,UC2,UC3,UC4,UC5,UC6,UC7,UC8 usecase
    class SearchEngine,Database system
```

### 4. 互動與通知
```mermaid
flowchart TD
    subgraph 通知系統
        UC1(["設定降價通知"])
        UC2(["接收降價提醒"])
        UC3(["加入追蹤 / 收藏"])
    end

    買家((買家)) --> UC1
    買家 --> UC3
    UC1 --> UC2

```

```mermaid
flowchart TD
    %% 參與者
    Buyer[買家]
    NotificationSystem[通知系統]
    Database[資料庫]
    
    %% 使用案例
    UC1((設定降價通知))
    UC2((接收降價提醒))
    UC3((加入收藏清單))
    UC4((管理收藏清單))
    UC5((移除收藏))
    UC6((查看通知歷史))
    
    %% 關聯
    Buyer --> UC1
    Buyer --> UC2
    Buyer --> UC3
    Buyer --> UC4
    Buyer --> UC5
    Buyer --> UC6
    
    UC1 --> Database
    UC2 --> NotificationSystem
    UC3 --> Database
    UC4 --> Database
    UC5 --> Database
    UC6 --> Database
    
    %% 包含關係
    UC1 -.->|<<trigger>>| UC2
    UC4 -.->|<<include>>| UC5
    
    %% 樣式
    classDef actor fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef usecase fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef system fill:#e8f5e8,stroke:#1b5e20,stroke-width:2px
    
    class Buyer actor
    class UC1,UC2,UC3,UC4,UC5,UC6 usecase
    class NotificationSystem,Database system
```

### 5. 聊天室
```mermaid
flowchart TD
    subgraph 聊天系統
        UC1(["發送文字訊息"])
        UC2(["上傳圖片"])
        UC3(["接收訊息"])
    end

    買家((買家)) --> UC1
    賣家((賣家)) --> UC1
    買家 --> UC2
    賣家 --> UC2
    UC1 --> UC3
    UC2 --> UC3

```


```mermaid
flowchart TD
    %% 參與者
    Buyer[買家]
    Seller[賣家]
    ChatServer[聊天伺服器]
    FileServer[檔案伺服器]
    
    %% 使用案例
    UC1((發送文字訊息))
    UC2((接收文字訊息))
    UC3((上傳圖片))
    UC4((接收圖片))
    UC5((查看聊天記錄))
    UC6((建立聊天室))
    
    %% 關聯
    Buyer --> UC1
    Buyer --> UC2
    Buyer --> UC3
    Buyer --> UC4
    Buyer --> UC5
    Buyer --> UC6
    
    Seller --> UC1
    Seller --> UC2
    Seller --> UC3
    Seller --> UC4
    Seller --> UC5
    
    UC1 --> ChatServer
    UC2 --> ChatServer
    UC3 --> FileServer
    UC4 --> FileServer
    UC5 --> ChatServer
    UC6 --> ChatServer
    
    %% 樣式
    classDef actor fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef usecase fill:#f3e5f5,stroke:#4a148c,stroke-width:2px
    classDef system fill:#e8f5e8,stroke:#1b5e20,stroke-width:2px
    
    class Buyer,Seller actor
    class UC1,UC2,UC3,UC4,UC5,UC6 usecase
    class ChatServer,FileServer system
```


# 使用案例說明
