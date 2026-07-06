# 胖打注音 — 台語衍生詞表（方音符號）

本儲存庫是 **胖打注音（Panda Zhuyin）** iOS 注音輸入法的**台語詞庫衍生資料**，以方音符號格式提供，供公開取用、研究與再利用。

## 為何有這個儲存庫

胖打注音的台語詞庫合併了以 **CC BY-SA 4.0** 授權的來源（台華線頂對照典）。CC BY-SA 的 **ShareAlike** 條款要求：衍生資料須以相同授權、且未受技術措施限制的可取得形式釋出。胖打注音主程式閉源，App Store 二進位受 DRM 保護，故在此以未加密、可改的形式公開衍生詞表，以履行 ShareAlike 的 availability 義務。

## 授權

本衍生詞表整體以 **[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)** 釋出（全文見 [`LICENSE`](LICENSE)）。再利用時請**標示來源**並以**相同授權**釋出你的衍生作品。

## 資料來源與各自授權

| 來源 | 詞條 | 授權 |
|---|---|---|
| iTaigi 華台對照典（ChhoeTaigi） | ~19.8K | CC0 |
| 教育部臺灣台語常用詞辭典（moedict-data-twblg） | ~25K | CC BY-ND 3.0 TW |
| 公視台語台《台語新詞辭庫》 | ~2.1K | CC BY 4.0 |
| **台華線頂對照典（ChhoeTaigi）** | ~91K | **CC BY-SA 4.0** |

- **台華線頂對照典** © [ChhoeTaigi 找台語](https://github.com/ChhoeTaigi/ChhoeTaigiDatabase)，CC BY-SA 4.0。本詞表含其衍生內容，故整體以 CC BY-SA 4.0 釋出。
- **教育部辭典**部分依 CC BY-ND 3.0 TW，以「格式轉換（臺羅→方音符號）非改作」立場重製並標示出處。
- **iTaigi**（CC0）、**公視新詞**（CC BY 4.0）向上相容併入 CC BY-SA。
- 臺羅→方音符號轉換規則移植自 g0v `trs2bpmf`（CC0）。

## 修改說明

（依 CC BY-SA 4.0 §3(a)(1)(B) 標示已對原始素材所做之修改）

- **格式轉換**：臺羅拼音 → 方音符號（g0v trs2bpmf 規則的忠實移植）
- **四源合併去重**：以（詞, 讀音）為鍵
- **來源票數加權**：原始三源各 2 票、台華線頂 1 票（使台華獨有詞落尾段當 fallback）
- **品質過濾**：剔除整句/諺語（≥7 漢字）、漢羅混寫、非法音節

## 檔案格式

| 檔案 | 內容 | 格式 |
|---|---|---|
| `phrases-taigi.txt` | 詞庫 | 每行 `詞 票數 方音音節…`（空白分隔） |
| `char-taigi.txt` | 單字讀音頻次 | 每行 `字 ⇥ 0 ⇥ 頻 ⇥ 讀音`（tab 分隔） |

各檔檔頭註解列出四源授權。

## 產出方式

由胖打注音的 `Scripts/taigi-lexicon/` build pipeline 自動產出。本儲存庫為該產出的**公開鏡像**，隨版本更新同步。

## 相關連結

- 胖打注音官網／說明書：<https://github.com/yintzuyuan/panda-zhuyin>
