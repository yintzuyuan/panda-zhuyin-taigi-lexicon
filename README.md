# 胖打注音 — 台語衍生詞表（方音符號）

本儲存庫是 **胖打注音（Panda Zhuyin）** iOS 注音輸入法的**台語詞庫衍生資料**，以方音符號格式提供，供公開取用、研究與再利用。

## 為何有這個儲存庫

胖打注音的台語詞庫合併了以 **CC BY-SA 4.0** 授權的來源（台華線頂對照典）。CC BY-SA 的 **ShareAlike** 條款要求：衍生資料須以相同授權、且未受技術措施限制的可取得形式釋出。胖打注音主程式閉源，App Store 二進位受 DRM 保護，故在此以未加密、可改的形式公開衍生詞表，以履行 ShareAlike 的 availability 義務。

## 版本對應

本儲存庫的 git tag 與 app 版本一一對應（例如 tag `v2.0.0` = App Store 上的 2.0.0 版詞庫）。每次 app 發版打 tag 時，由 CI 自動比對出貨詞庫並同步推送至此，公開內容永遠反映**已上架版本**。

## 逐檔授權

| 檔案 | 內容 | 授權 |
|---|---|---|
| `phrases-taigi.txt` | 台語詞庫（詞＋票數＋方音音節） | **CC BY-SA 4.0**（整體，含台華線頂衍生內容） |
| `char-taigi.txt` | 單字讀音頻次 | **CC BY-SA 4.0**（同上） |
| `emoji-annotations-taigi.txt` | 台語詞 → emoji 對應 | 混合血緣：台語詞取自 iTaigi（**CC0**）、emoji 對應衍生自 [rime-emoji](https://github.com/rime/rime-emoji)（**LGPL-3.0**）；**不含**台華線頂內容，無 BY-SA 約束 |

`LICENSE` 為 CC BY-SA 4.0 全文，適用於 `phrases-taigi.txt` 與 `char-taigi.txt`。再利用這兩檔時請**標示來源**並以**相同授權**釋出你的衍生作品；再利用 emoji 表時請依其血緣分別標示。

## 資料來源與各自授權

| 來源 | 收錄條數* | 授權 |
|---|---|---|
| iTaigi 華台對照典（ChhoeTaigi） | ~16.7K | CC0 |
| 教育部臺灣台語常用詞辭典（[kemdict-data-ministry-of-education](https://github.com/kemdict/kemdict-data-ministry-of-education) 鏡像） | ~29.5K | CC BY-ND 3.0 TW |
| 公視台語台《台語新詞辭庫》 | ~2.3K | CC BY 4.0 |
| **台華線頂對照典（ChhoeTaigi）** | ~65.3K | **CC BY-SA 4.0** |

\* 通過品質過濾後併入本詞表的條數，隨版本演進。

- **台華線頂對照典** © [ChhoeTaigi 找台語](https://github.com/ChhoeTaigi/ChhoeTaigiDatabase)，CC BY-SA 4.0。本詞表含其衍生內容，故整體以 CC BY-SA 4.0 釋出。
- **教育部辭典**部分依 CC BY-ND 3.0 TW，以「格式轉換（臺羅→方音符號）非改作」立場重製並標示出處。
- **iTaigi**（CC0）、**公視新詞**（CC BY 4.0）向上相容併入 CC BY-SA。
- 臺羅→方音符號轉換規則移植自 g0v `trs2bpmf`（CC0）。

## 修改說明

（依 CC BY-SA 4.0 §3(a)(1)(B) 標示已對原始素材所做之修改）

- **格式轉換**：臺羅拼音 → 方音符號（g0v trs2bpmf 規則的忠實移植）
- **四源合併去重**：以（詞, 讀音）為鍵
- **來源票數加權**：原始三源各 2 票、台華線頂 1 票（使台華獨有詞落尾段當 fallback）；票數帶小數 ε 作來源優先度 tie-break（如 `凹 1.01 ㄠ`）
- **品質過濾**：剔除整句/諺語（≥7 漢字）、漢羅混寫、非法音節

## 檔案格式

| 檔案 | 格式 |
|---|---|
| `phrases-taigi.txt` | 每行 `詞 票數 方音音節…`（空白分隔） |
| `char-taigi.txt` | 每行 `字 ⇥ 0 ⇥ 頻 ⇥ 讀音`（tab 分隔） |
| `emoji-annotations-taigi.txt` | 每行 `台語詞 ⇥ emoji1,emoji2…`（tab 分隔） |

詞庫檔檔頭註解列出各源授權。

## 產出方式

由胖打注音的 `Scripts/taigi-lexicon/` 與 `Scripts/taigi-emoji-overlay/` build pipeline 自動產出。本儲存庫為該產出的**公開鏡像**，app 發版時由 CI 自動同步。

## 相關連結

- 胖打注音官網／說明書：<https://github.com/yintzuyuan/panda-zhuyin>
