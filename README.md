# 胖打注音 — 台語衍生詞表（方音符號）

本儲存庫是 **胖打注音（Panda Zhuyin）** iOS 注音輸入法的**台語詞庫衍生資料**，以方音符號格式提供，供公開取用、研究與再利用。

## 為何有這個儲存庫

胖打注音的台語詞庫合併了以 **CC BY-SA 4.0** 授權的來源（台華線頂對照典）。CC BY-SA 的 **ShareAlike** 條款要求：衍生資料須以相同授權、且未受技術措施限制的可取得形式釋出。胖打注音主程式閉源，App Store 二進位受 DRM 保護，故在此以未加密、可改的形式公開衍生詞表，以履行 ShareAlike 的 availability 義務。

## 版本對應

本儲存庫的 git tag 與 app 版本一一對應（例如 tag `v2.0.0` = App Store 上的 2.0.0 版詞庫）。每次 app 發版打 tag 時，由 CI 自動比對出貨詞庫並同步推送至此，公開內容永遠反映**已上架版本**。

## 逐檔授權

| 檔案 | 內容 | 授權 |
|---|---|---|
| `phrases-taigi.txt` | 台語詞庫（詞＋頻次＋方音音節） | **CC BY-SA 4.0**（整體，含台華線頂衍生內容） |
| `char-taigi.txt` | 單字讀音頻次 | **CC BY-SA 4.0**（同上） |
| `lexicon-taigi-romanization.txt` | 詞條羅馬字（詞＋方音音節＋臺羅＋白話字）；臺羅為來源辭典**原文逐字保留**，白話字自臺羅轉出 | **CC BY-SA 4.0**（同上） |
| `emoji-annotations-taigi.txt` | 台語詞 → emoji 對應 | 混合血緣：台語詞取自 iTaigi（**CC0**）、emoji 對應衍生自 [rime-emoji](https://github.com/rime/rime-emoji)（**LGPL-3.0**）；**不含**台華線頂內容，無 BY-SA 約束 |

`LICENSE` 為 CC BY-SA 4.0 全文，適用於 `phrases-taigi.txt`、`char-taigi.txt` 與 `lexicon-taigi-romanization.txt`。再利用這三檔時請**標示來源**並以**相同授權**釋出你的衍生作品；再利用 emoji 表時請依其血緣分別標示。

`lexicon-taigi-romanization.txt` 首行為 App 端 mmap 用的 pragma（`# panda-lexicon-v1 romanization`），其後為授權註解，再其後為 tab 分隔資料（按 UTF-8 byte order 排序）。以 `#` 開頭的行皆為註解。

## 資料來源與各自授權

| 來源 | 收錄條數* | 授權 |
|---|---|---|
| iTaigi 華台對照典（ChhoeTaigi） | ~16.7K | CC0 |
| 教育部臺灣台語常用詞辭典（[kemdict-data-ministry-of-education](https://github.com/kemdict/kemdict-data-ministry-of-education) 鏡像） | ~29.5K | CC BY-ND 3.0 TW |
| 公視台語台《台語新詞辭庫》 | ~2.3K | CC BY 4.0 |
| **台華線頂對照典（ChhoeTaigi）** | ~65.3K | **CC BY-SA 4.0** |
| **台灣植物名彙 1928（佐佐木舜一，ChhoeTaigi）** | ~0.7K（植物名） | **CC BY-SA 4.0** |
| 教育部學科術語臺灣台語／臺灣客語對譯查詢 | ~2.7K（學科術語，淨新增） | 政府網站資料開放宣告（CC BY 等價） |
| **iCorpus 臺華平行新聞語料庫漢字臺羅版** | 詞頻（真實語料次數，非詞條） | CC BY 4.0 |

\* 通過品質過濾後併入本詞表的條數，隨版本演進。iCorpus 提供的是**詞頻**（非詞條），故無「收錄條數」。

- **台華線頂對照典** © [ChhoeTaigi 找台語](https://github.com/ChhoeTaigi/ChhoeTaigiDatabase)，CC BY-SA 4.0。本詞表含其衍生內容，故整體以 CC BY-SA 4.0 釋出。
- **台灣植物名彙 1928**（佐佐木舜一）© [ChhoeTaigi 找台語](https://github.com/ChhoeTaigi/ChhoeTaigiDatabase)，CC BY-SA 4.0。本詞表含其植物名衍生內容，同以 CC BY-SA 4.0 釋出。
- **教育部辭典**部分依 CC BY-ND 3.0 TW 重製並標示出處。臺羅→方音符號為規則驅動的機械式標音系統轉換，無創作性投入，屬**重製**而非改作；CC BY-ND 3.0 TW 第 3 條明文授權重製、散布與公開傳輸，且不限商業用途。
- **iTaigi**（CC0）、**公視新詞**（CC BY 4.0）向上相容併入 CC BY-SA。
- **教育部學科術語臺灣台語／臺灣客語對譯查詢**依政府網站資料開放宣告釋出（無償、得再授權、可改作、可商用，須註明出處＝CC BY 等價），向上相容併入 CC BY-SA。
- **iCorpus 臺華平行新聞語料庫漢字臺羅版** © 薛丞宏，CC BY 4.0（向上相容併入 CC BY-SA）。提供真實語料**詞頻**（非詞條），為頻次項的 count 來源（見「修改說明」）。
- 臺羅→方音符號轉換規則移植自 g0v `trs2bpmf`（CC0）。

## 修改說明

（依 CC BY-SA 4.0 §3(a)(1)(B) 標示已對原始素材所做之修改）

- **格式轉換**：臺羅拼音 → 方音符號（g0v trs2bpmf 規則的忠實移植）
- **四源合併去重**：以（詞, 讀音）為鍵
- **詞頻（Dirichlet 混合偽頻次）**：`頻次 = 票數(prior) + iCorpus 真實語料次數 / μ`（μ=50）。
  - 票數 prior：原始三源各 2 票、台華線頂與台灣植物名彙各 1 票（fallback 源，獨有詞落尾段、不搶常用詞首位）；帶小數 ε 作來源優先度 tie-break（如 `凹 1.01 ㄠ`）。
  - iCorpus count：真實新聞語料的（詞, 讀音）出現次數，經臺羅→方音轉換後 join。**未命中語料的詞維持票數 prior 原值**（零證據詞排序不變）；c=1 單次觀測不翻越票數層（μ 護欄）。
- **單字頻次（char 層 standalone 注入）**：`頻次 = 來源覆蓋數(prior) + round(iCorpus 獨立單字詞次數 / 5)`。只計語料中**單獨成詞**的出現（複合詞構成字不灌入）；整數量化下微量觀測（c≤2）歸零；含少量新聞語體排除項（translationese，如被動句「被」）。
- **品質過濾**：剔除整句/諺語（≥7 漢字）、漢羅混寫、非法音節

## 檔案格式

| 檔案 | 格式 |
|---|---|
| `phrases-taigi.txt` | 每行 `詞 頻次 方音音節…`（空白分隔；頻次＝Dirichlet 混合偽頻次） |
| `char-taigi.txt` | 每行 `字 ⇥ 0 ⇥ 頻 ⇥ 讀音`（tab 分隔） |
| `emoji-annotations-taigi.txt` | 每行 `台語詞 ⇥ emoji1,emoji2…`（tab 分隔） |

詞庫檔檔頭註解列出各源授權。

## 產出方式

由胖打注音的 `Scripts/taigi-lexicon/` 與 `Scripts/taigi-emoji-overlay/` build pipeline 自動產出。本儲存庫為該產出的**公開鏡像**，app 發版時由 CI 自動同步。

## 相關連結

- 胖打注音官網／說明書：<https://github.com/yintzuyuan/panda-zhuyin>
