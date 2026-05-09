# LOYU 羅鈺室內設計 — Design System
**版本：** 2026-04-26 v2.0  
**適用範圍：** Claude Design 視覺調整 + 後續頁面設計

---

## Claude Design 設定說明

### Step 1 — Link code from your computer
連結資料夾：`/Users/aizhuli/Desktop/羅鈺官網-prototype/`

包含：
- `index.html` — 首頁 prototype
- `portfolio.html` — 作品集 prototype
- `羅鈺網站/LOYU/` — 所有圖片素材（LOGO / HERO / 作品集 / 團隊照片）

### Step 2 — Add fonts, logos and assets（上傳以下 LOGO 及品牌文件）

LOGO 檔案來源：`/Users/aizhuli/Desktop/羅鈺官網-prototype/羅鈺網站/LOYU/LOGO/`

| 檔案 | 說明 | 目前使用位置 |
|------|------|-------------|
| `logo-PNG_去背.png` | 圖標 + LOYU 英文橫式（深色底） | Nav 右側 |
| `LOGO01_去背.png` | 圖標 + LOYU INTERIOR DESIGN（深色底） | Hero 置中 |
| `LOGO02_去背.png` | 圖標 + 羅鈺室內裝修工程有限公司（淺色底） | Footer |
| `LOGO03_去背.png` | 其他 LOGO 變體（待確認用途） | 備用 |
| `logo4-PNG_去背.png` | 其他 LOGO 變體 | 備用 |
| `logo5-PNG_去背.png` | 其他 LOGO 變體 | 備用 |
| `logo6-PNG_去背.png` | 其他 LOGO 變體 | 備用 |
| `LOYU Interior Design-VIS.pdf` | 品牌 VIS 完整設計規範（含色彩/字型/使用規則） | 背景參考 |

> **上傳建議：** 至少上傳 `logo-PNG_去背.png`、`LOGO01_去背.png`、`LOGO02_去背.png`，以及 VIS PDF。其餘 LOGO 變體按需求上傳。

### Step 3 — 貼入此 Design System 作為 context

---

## 品牌設計規格

### 色彩系統（依據 VIS 官方規範 2026-04-26 更新）

| 名稱 | HEX | 說明 | PANTONE |
|------|-----|------|---------|
| LOYU Red | `#B40014` | 主色：CTA、強調線、分隔線 | 7621C |
| LOYU Dark Red | `#91000A` | Hover 加深版 | 7624C |
| LOYU Gray | `#717071` | 次要文字、標籤、icon | Cool Gray 9C |
| LOYU Light Gray | `#D2D2D2` | 淺灰邊線 | Cool Gray 1C |
| LOYU White | `#ffffff` | 背景 | — |
| LOYU Black | `#000000` | 深色底背景 | — |

```css
--red:        #B40014   /* LOYU Red - 主色（VIS 官方） */
--dark-red:   #91000A   /* LOYU Dark Red - hover 用 */
--dark:       #1E1E1E   /* 主要文字（近 LOYU Black） */
--mid:        #717071   /* LOYU Gray（VIS 官方） */
--light:      #F7F6F4   /* 暖白背景（設計選擇，VIS 外） */
--light-gray: #D2D2D2   /* LOYU Light Gray */
--border:     #D2D2D2   /* 分隔線（LOYU Light Gray） */
```
其他背景色：`#EEEDE9`（公司簡介灰框）、`#2A2A2A`（team grid label 格子，比 `--dark` 略淺以形成層次）

**Hero 遮罩規則（確定）：**
- 首頁 Hero：`rgba(255,255,255,0.6)` — 白色遮罩，降低照片飽和度，LOYU 紅色 Logo 突出
- 其他頁 Hero（設計團隊、工作機會等）：`background: #1E1E1E`（純色深底，無照片）

**字型（VIS 官方）：** Noto Sans（中文）/ Roboto（數字）/ Gill Sans（英文）  
**網站額外字型：** Cormorant Garamond（editorial 標題，設計選擇）/ Inter（UI）

### 字型系統
```
Noto Sans TC       — 主文、UI 文字（300/400/500/700）
Cormorant Garamond — 標題、引言、案名（300/400/600 + italic）
Inter              — 次要 UI（300/400/500）
```
Google Fonts CDN 已在兩個 HTML 中載入。

### 排版規格
| 樣式 | 規格 |
|------|------|
| 標籤（EYEBROW） | 9–11px, letter-spacing 3–5px, UPPERCASE, color: mid |
| 標題（H2） | Cormorant Garamond, 28–32px, weight 300 |
| 內文 | 13px, line-height 2, color #555 |
| 篩選/按鈕文字 | 11px, letter-spacing 3–4px, UPPERCASE |

---

## 版面系統

### 響應式邏輯（WAA 置中縮放）
所有 Section 使用 `max(最小留白, calc((100% - 最大內容寬) / 2))` 作為左右 padding，確保：
- 大螢幕：內容置中，左右等寬留白
- 縮放時：左右留白同步縮小，內容始終居中
- `@media (max-width: 760px)`：Works 兩欄切單欄、About grid 切單欄

### 首頁
- Works Section：`padding: 100px max(40px, calc((100% - 720px) / 2))`
- About Section：`padding: 60px max(40px, calc((100% - 720px) / 2))`
- Footer：`padding: 60px max(24px, calc((100% - 1100px) / 2)) 36px`
- Nav：初始透明，scrollY ≥ hero 高度 - 70px 後轉白底

### 作品集
- Grid：`repeat(4, 1fr)`，gap 2px，background #bbb（gap 顯色）
- 圖片：aspect-ratio 4/3
- Nav 高度：64px 固定
- 展開面板：`grid-column: 1/-1`，height 72vh，左右 62%/38%

---

## 元件規格

### Works Section Category Label（首頁作品區分類標籤）
- 元素：`.service-intro .cat`
- Font: Noto Sans TC / 24px / weight 500 / letter-spacing 4.32px
- Color: `var(--red)` (#B40014)
- Border-bottom: `1px solid var(--red)`，padding-bottom 10px，margin-bottom 14px
- 說明：此標籤為獨立規格，不套用 H2 或 eyebrow 規則，定位為 category divider

### Nav — 首頁版
- 透明背景：漢堡（左）+ `logo-PNG_去背.png`（右），漢堡線條白色
- 滾過 hero 後：`background:#fff; box-shadow: 0 1px 20px rgba(0,0,0,0.07)`，漢堡線條轉 `--dark`
- padding: 22px 36px

### Nav — 作品集版
- 白底 + `border-bottom: 1px solid var(--border)`
- 3欄 grid：`80px 1fr 80px`，height 64px，padding 0 24px
- 中欄：篩選 tab（全部/商辦空間/住宅空間/其他空間），active 狀態：紅色 + border-bottom 2px red

### Sidebar
- 觸發：漢堡按鈕，slide-in from left
- 寬度：33vw, min 480px, max 580px
- 結構（flex-direction: column）：
  - `sidebar-header`（flex 橫行，border-bottom）：`✕` | 羅鈺室內設計（flex:1）| EN
  - `sidebar-body`（flex 橫行）：左 38% 選單 | 右 62% 聯絡
- 選單組：作品集 / 關於我們 / 加入我們（各含子項目）
- 聯絡區：台中 / 高雄 tab 切換 + 表單（select + inputs + 送出）

### Hero
- 100vh 滿版，8張背景輪播（3秒切換，1.4s 淡入淡出）
- 遮罩：`rgba(0,0,0,0.42)`
- LOGO01 置中：`width: clamp(260px, 36vw, 468px)`
- 底部：↓ 細線 + "SCROLL" 文字
- 滾動效果：LOGO + SCROLL 向上淡出（前 50% hero 高度內完成），背景視差 0.25x
- 直立圖（Hero04）：`background-size: contain; background-color: #8a8a8a`（兩側顯灰底）

#### HERO 圖片清單（`羅鈺網站/LOYU/HERO/`）
| 檔案 | 尺寸 | 類型 |
|------|------|------|
| Hero01.jpg | 1920×950 | 橫式 |
| Hero02.jpg | 1920×800 | 橫式 |
| Hero03.jpg | 1920×800 | 橫式 |
| Hero04.jpg | 500×762 | **直立（灰底效果）** |
| Hero05.jpg | 1920×800 | 橫式 |
| Hero06.jpg | 1920×800 | 橫式 |
| Hero07.jpg | 1920×800 | 橫式 |
| Hero08.jpg | 1920×950 | 橫式 |

### Works Section（首頁作品區）
- 兩欄 flex（50/50），gap 24px，`align-items: flex-start`
- 左欄：直立圖(3/4) → 橫式(16/9) → 其他空間 intro → 橫式(16/9)
- 右欄：商辦空間 intro → 橫式(16/9)×2 → 住宅空間 intro → 橫式(16/9)×2
- hover 效果：`scale(1.05)` + 半透明黑底 + 白色文字淡入
- 底部：「所有作品」border 按鈕 → portfolio.html
- **Scroll 淡入**：IntersectionObserver，`.work-item` 和 `.service-intro` 向上淡入（opacity 0→1, translateY 28px→0, 0.7s ease）

### About Section
- `padding: 60px max(40px, calc((100% - 720px) / 2))`，`background: var(--light)`
- 兩欄 grid（1fr 1fr），`align-items: end`（灰框底部對齊照片底部）
- 左：照片，align-self: stretch，object-fit: cover，object-position: top center
- 右：`background:#EEEDE9; padding:48px 44px`，flex-col
  - eyebrow → Cormorant h2 → 3段內文 → 紅底按鈕「聯絡我們」

### Footer
- `background: var(--light); border-top: 1px solid var(--border)`
- `padding: 60px max(24px, calc((100% - 1100px) / 2)) 36px`
- 5欄 grid：`auto 1fr 1fr auto auto`，gap 48px，align-items start
  - `LOGO02_去背.png`（align-self: center, height 38px）
  - 台中：地址/電話/傳真/信箱
  - 高雄：地址/電話/傳真/信箱
  - FOLLOW：FB + IG svg icon（22px）
  - 諮詢：紅框按鈕「填寫需求表 →」
- 底部：copyright 文字

---

## 素材資料夾結構

所有素材路徑均相對於 `羅鈺官網-prototype/`：

```
羅鈺網站/LOYU/
├── LOGO/
│   ├── logo-PNG_去背.png          ← Nav
│   ├── LOGO01_去背.png            ← Hero
│   ├── LOGO02_去背.png            ← Footer
│   ├── LOGO03_去背.png            ← 備用
│   ├── logo4-PNG_去背.png         ← 備用
│   ├── logo5-PNG_去背.png         ← 備用
│   ├── logo6-PNG_去背.png         ← 備用
│   └── LOYU Interior Design-VIS.pdf  ← 品牌 VIS
├── HERO/
│   └── Hero01.jpg ~ Hero08.jpg
├── 作品集/
│   ├── 01_辦公空間/   （32 案）
│   ├── 02_住宅空間/   （7 案）
│   ├── 03_其他空間/   （5 案）
│   └── 04_團隊照片/   （24 張）
```

---

## 頁面清單

### 已完成（prototype）
| 頁面 | 檔案 | 狀態 |
|------|------|------|
| 首頁 | index.html | prototype 定稿，待 Claude Design 視覺精修 |
| 作品集 | portfolio.html | prototype 定稿，44案填入，待視覺精修 |

### 待設計（優先順序）
| 優先 | 頁面 | 路徑 | 說明 |
|------|------|------|------|
| 1 | 關於我們 | about.html | 公司理念、沿革、數字摘要 |
| 2 | 設計團隊 | team.html | 成員介紹（04_團隊照片可用） |
| 3 | 獲獎記錄 | awards.html | 歷年獎項（時間軸或格狀） |
| 4 | 專欄文章（列表） | articles.html | 文章列表 |
| 5 | 專欄文章（單篇） | article.html | 文章閱讀頁 |
| 6 | 夥伴與客戶群 | clients.html | Logo 牆 + 客戶見證 |
| 7 | 工作機會 | careers.html | 職缺列表 + 申請說明 |
| 8 | 公司環境 | office.html | 辦公室照片 gallery |

---

## 作品集圖片資料庫（44 個案子）

**圖片根目錄（相對路徑）：** `羅鈺網站/LOYU/作品集/`

### 商辦空間（data-cat="commercial"，32案）
| 案名 | 資料夾 | 封面圖檔名 |
|------|--------|-----------|
| 代宇電子 | 01_辦公空間/代宇電子 | projects_image_2018-12-27_loyu_2ea6962595b4711e79a2d7653ab299e5.jpg |
| 來永實業 | 01_辦公空間/來永實業 | projects_image_2019-01-10_loyu_4de4114c192de2cced05df57554db8a8.jpg |
| 健和興端子 | 01_辦公空間/健和興端子 | projects_image_2021-08-09_loyu_0447ec824348cb934db7cca0422b9c73.jpg |
| 克瑞電子 | 01_辦公空間/克瑞電子 | projects_image_2019-01-10_loyu_02c805132cb37d6f6a4d626f2cca7f05.jpg |
| 台中精機 | 01_辦公空間/台中精機 | projects_image_2021-07-05_loyu_1ecdc6defff79f1fd97381a982ed711b.jpg |
| 台灣百和 | 01_辦公空間/台灣百和 | projects_image_2019-01-10_loyu_18a641b8309840bd44deb80037519ec6.jpg |
| 品茂塑膠 | 01_辦公空間/品茂塑膠 | projects_image_2024-11-29_loyu_0480d3cac9095699a52e894d696d0e19.jpg |
| 鼎霖國際 | 01_辦公空間/鼎霖國際 | projects_image_2022-05-25_loyu_001aecac6364ac0311aa2256b0f40f73.jpg |
| 大江生醫 | 01_辦公空間/大江生醫 | projects_image_2019-01-08_loyu_d514cf26acf4c8f2fa428eb31d2d3be0.jpg |
| 宏全國際員工宿舍 | 01_辦公空間/宏全國際 員工宿舍 | projects_image_2024-11-27_loyu_0a158d064d28cd2fd8d330204ce5f538.jpg |
| 宏全國際 | 01_辦公空間/宏全國際 | projects_image_2019-01-10_loyu_1ab7c86e6be48708eb90ade07beb8f82.jpg |
| 宏諦實業 | 01_辦公空間/宏諦實業 | projects_image_2018-05-09_loyu_020d802d3bf74b440b7cf76e07ddac7b.jpg |
| 宏恩塑膠 | 01_辦公空間/宏恩塑膠 | projects_image_2021-07-05_loyu_1421799a8d900a0172f4dfaa9d62bf4a.jpg |
| 儷寶化妝品 | 01_辦公空間/儷寶化妝品 | projects_image_2019-01-11_loyu_02cef7849ef71155da12201e50bc123a.jpg |
| 彰茂企業 | 01_辦公空間/彰茂企業 | projects_image_2019-01-11_loyu_0021d383b11778417262de004645c4a2.jpg |
| 日益電機 | 01_辦公空間/日益電機 | projects_image_2020-08-07_loyu_0100834109ee86ac6fa178ea1169c04b.jpg |
| 普家康興業 | 01_辦公空間/普家康興業 | projects_image_2018-05-09_loyu_19e1cadf3de9328d7769e3430f3f5583.jpg |
| 朝嘉興業 | 01_辦公空間/朝嘉興業 | projects_image_2020-08-11_loyu_03820f8305b335267b95e7ec1cb5c778.jpg |
| 糖村 | 01_辦公空間/糖村 | projects_image_2020-08-11_loyu_164c06f33eb6e0cc7005ca018daf441d.jpg |
| 東台精機 | 01_辦公空間/東台精機 | projects_image_2019-01-10_loyu_449835b1579c1106b107afaa90814384.jpg |
| 松之門控 | 01_辦公空間/松之門控 | projects_image_2022-05-25_loyu_0779c7de3d78d0df2008dc98b257c75d.jpg |
| 橋椿金屬 | 01_辦公空間/橋椿金屬 | projects_image_2018-05-09_loyu_0122a9252bc3da4a1b229cb20d7a7423.jpg |
| 正瀚生技 | 01_辦公空間/正瀚生技 | projects_image_2022-05-25_loyu_18dfc0d006ca2ff49fd4f3114620bb57.jpg |
| 油順精密 | 01_辦公空間/油順精密 | projects_image_2019-01-10_loyu_1cc6f68ab23bd32b6d60f33ba847e894.jpg |
| 皇家NTC商務中心 | 01_辦公空間/皇家NTC商務中心 (設計規劃) | projects_image_2019-01-15_loyu_135a1c971fe97da24b8d4d25224a666f.jpg |
| 羅力衛浴 | 01_辦公空間/羅力衛浴 | projects_image_2021-07-05_loyu_19364aae66b7d021bcfae94def6483a6.jpg |
| 聯合骨科器材 | 01_辦公空間/聯合骨科器材 | projects_image_2018-05-09_loyu_19a5f1a9fd161a0875a73cc1149da917.jpg |
| 野寶科技 | 01_辦公空間/野寶科技 | projects_image_2018-05-09_loyu_1e55adbd5e58fe932cf9edb8f2059244.jpg |
| 金可眼鏡 | 01_辦公空間/金可眼鏡 | projects_image_2019-01-11_loyu_0c5ef9605d784f2ee7e38e6b794d8638.jpg |
| 金器工業 | 01_辦公空間/金器工業 | projects_image_2020-08-07_loyu_06a97591bf674b8ab62cd57c078a4153.jpg |
| 鍵瑋企業 | 01_辦公空間/鍵瑋企業 | projects_image_2019-01-11_loyu_6883da275e5401cc0154ee570e622ebf.jpg |
| 雷尼紹 | 01_辦公空間/雷尼紹 | projects_image_2019-01-11_loyu_0d47bbab5faf3c3f1ad6b655234675b6.jpg |

### 住宅空間（data-cat="residential"，7案）
| 案名 | 資料夾 | 封面圖檔名 |
|------|--------|-----------|
| 張公館 | 02_住宅空間/張公館 | projects_image_2021-07-05_loyu_0dd60896b1bba9b9adf86f1bc906cd19.jpg |
| 接待會館 | 02_住宅空間/接待會館 | projects_image_2020-08-07_loyu_09bb92f0c3179ca8af1efa33707345d9.jpg |
| 林公館 | 02_住宅空間/林公館 | projects_image_2021-07-05_loyu_0fca47e41d0fde615cb6d4ebc23e5733.jpg |
| 江宅 | 02_住宅空間/江宅 | projects_image_2018-05-08_loyu_30bbd5f735107ca4c7b9d204061ee7a7.jpg |
| 田公館 | 02_住宅空間/田公館 | projects_image_2021-07-05_loyu_187936017b3f47115be24631732ec4eb.jpg |
| 羅公館 | 02_住宅空間/羅公館 | projects_image_2018-05-09_loyu_0c300b14b50ab4fcd3848cbd8205c76a.jpg |
| 許公館 | 02_住宅空間/許公館 | projects_image_2019-01-11_loyu_0d322a2695e1dd9fddea20ea953fce27.jpg |

### 其他空間（data-cat="others"，5案）
| 案名 | 資料夾 | 封面圖檔名 |
|------|--------|-----------|
| 六家國小－上銀卓永統紀念圖書館 | 03_其他空間/六家國小 - 上銀卓永統紀念圖書館 | projects_image_2019-01-11_loyu_0a55a5cd63af0cf1474c9bf18f0d353d.jpg |
| 極鮮火鍋－岡山館 | 03_其他空間/極鮮火鍋 - 岡山館 | projects_image_2021-07-08_loyu_0bba771ec779b904438fd41b0cd987d6.jpg |
| 永記造漆－彩虹文史館展覽館 | 03_其他空間/永記造漆－彩虹文史館_展覽館 | projects_image_2018-05-09_loyu_013a3d5c05916c05792ca2cc15280fca.jpg |
| 永記造漆－彩虹文史館文物館 | 03_其他空間/永記造漆－彩虹文史館_文物館 | projects_image_2018-05-09_loyu_10880afdcaf0148535329a3297c9987f.jpg |
| 燒肉神保町－岡山館 | 03_其他空間/燒肉神保町 - 岡山館 | projects_image_2021-07-08_loyu_1506886f41b8a845938f48caecb53b94.jpg |

### 團隊照片（04_團隊照片，24張）
路徑：`羅鈺網站/LOYU/作品集/04_團隊照片/`  
用途：設計團隊頁（team.html）、關於我們頁（about.html）

---

## HTML → Claude Design 轉移流程

1. Claude Code 主對話確認設計（版面、元件、內容）
2. Claude Code 整理規格 → 派 **瑪儂 Agent** 寫/修改 HTML
3. 瀏覽器用 `file://` 本地確認視覺
4. **進入 Claude Design：**
   - Link code → 選 `羅鈺官網-prototype/` 資料夾
   - Upload assets → 上傳 LOGO 去背 PNG + VIS PDF
   - 貼上此 Design System 文件
   - 告知要微調的具體項目（字距、間距、顏色等）
   - Claude Design 輸出 → 確認 → 取代 .html 檔
5. 每一新頁面都重複同樣流程

---

## 設計工作流程（永久規則）

```
Claude Code（主對話）
  ↓ 設計溝通、需求確認
  ↓ 確認後整理規格 → 召喚 瑪儂 Agent
瑪儂 Agent
  ↓ 寫/修改 HTML、CSS、JS
  ↓ 完成回報
Claude Code 驗收
  ↓ 通知 James 瀏覽器確認
  ↓ 需視覺精修 → 進 Claude Design
Claude Design
  ↓ 依本文件調整
  ↓ 輸出 HTML → 取代 .html 檔
```

**重要：主對話不直接寫大量 HTML/CSS，避免 context 堆積與 compact 截斷。**
