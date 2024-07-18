當然，這裡是您的繁體中文版本的README：

---

# 伺服器端應用程式 README

本README提供了伺服器端應用程式結構、端點和設置說明的概述。

## 目錄

1. [介紹](#介紹)
2. [使用的技術](#使用的技術)
3. [設置說明](#設置說明)
4. [資料夾結構](#資料夾結構)
5. [API 文件](#API-文件)
   - [認證路由](#認證路由)
   - [課程路由](#課程路由)
6. [附加說明](#附加說明)

## 介紹

此伺服器端應用程式提供了管理使用者身份驗證和課程操作的RESTful API。包括用戶註冊、登錄、JWT身份驗證，以及課程的CRUD操作。

## 使用的技術

- **Node.js**：JavaScript執行環境。
- **Express**：構建Web應用程式和API的框架。
- **MongoDB**：用於存儲應用程式數據的NoSQL數據庫。
- **Mongoose**：MongoDB和Node.js的對象數據建模（ODM）庫。
- **Passport.js**：Node.js的身份驗證中間件。
- **bcrypt**：用於雜湊密碼的庫。
- **jsonwebtoken（JWT）**：生成JSON Web Token用於用戶身份驗證的庫。
- **cors**：啟用跨源資源共享的中間件。

## 設置說明

要在本地運行伺服器端應用程式，請按照以下步驟操作：

1. **克隆存儲庫：**

   ```bash
   git clone <存儲庫URL>
   cd <存儲庫目錄>
   ```

2. **安裝依賴項：**

   ```bash
   npm install
   ```

3. **設置環境變量：**

   在根目錄下創建 `.env` 文件並添加以下變量：

   ```plaintext
   PASSPORT_SECRET=您的JWT密鑰
   ```

   將 `您的JWT密鑰` 替換為您選擇的JWT密鑰。

4. **啟動伺服器：**

   ```bash
   npm start
   ```

   伺服器將在 `http://localhost:8080` 上運行。

## 資料夾結構

應用程式的資料夾結構如下：

```
- /config             # 配置文件（例如：Passport.js配置）
- /models             # MongoDB模型（例如：User、Course）
- /routes             # 路由模組（例如：auth.js、course-route.js）
- /validation         # 請求數據驗證函數
- server.js           # 伺服器應用程式的入口點
- .env                # 環境變量配置文件
- README.md           # 伺服器端應用程式的README
```

## API 文件

### 認證路由

- **基本URL：** `/api/user`

| 方法   | 端點             | 說明                             | 需要的角色  |
|--------|------------------|----------------------------------|-------------|
| POST   | `/register`      | 註冊新用戶                        | 無          |
| POST   | `/login`         | 用戶登錄                          | 無          |

### 課程路由

- **基本URL：** `/api/courses`

| 方法   | 端點                            | 說明                             | 需要的角色  |
|--------|---------------------------------|----------------------------------|-------------|
| GET    | `/`                             | 獲取所有課程                      | 講師        |
| GET    | `/instructor/:_instructor_id`   | 根據講師ID獲取課程               | 講師        |
| GET    | `/student/:_student_id`         | 根據學生ID獲取註冊過的課程       | 學生        |
| GET    | `/findByName/:name`             | 根據課程名稱獲取課程             | 講師        |
| GET    | `/:_id`                         | 根據課程ID獲取課程               | 講師        |
| POST   | `/`                             | 創建新課程                        | 講師        |
| POST   | `/enroll/:_id`                  | 根據課程ID註冊新課程             | 學生        |
| PATCH  | `/:_id`                         | 更新課程                          | 講師        |
| DELETE | `/:_id`                         | 刪除課程                          | 講師        |

## 附加說明

此README提供了如何設置、運行和使用伺服器端應用程式的詳細信息，並描述了每個API端點的功能和所需角色。
