# 胖打注音 — 台語衍生詞表（方音符號）

*[English summary below](./README.en.md)*

本儲存庫是 **胖打注音（Panda Zhuyin）** iOS 注音輸入法的**台語詞庫衍生資料**：約 10.9 萬條（詞, 讀音）帶頻次、1.1 萬條單字讀音頻次、10.4 萬條臺羅／白話字對照，以**方音符號**格式提供，供公開取用、研究與再利用。格式與 [McBopomofo](https://github.com/openvanilla/McBopomofo) 詞庫相容——可直接餵給 McBopomofo／Megrez／[Homa](https://github.com/vChewing/vChewing-LibVanguard) 系組字引擎當語言模型，適合想做台語輸入法（iOS、Android、Rime、PC）的開發者直接取用。

> **授權以「逐檔授權」一節為準**。GitHub 在 repo 層顯示的 CC BY-SA 4.0 標籤是平台單一授權欄位的慣例限制，實際上 `emoji-annotations-taigi.txt` 為 CC0＋LGPL-3.0 混合血緣、無 BY-SA 約束，詳見下表。

## 這份資料能做什麼

- **輸入法詞庫**：`phrases-taigi.txt`＋`char-taigi.txt` 就是一組可直接載入的（詞, 頻次, 逐字讀音）語言模型資料，McBopomofo 格式
- **注音／臺羅／白話字三向對照**：`lexicon-taigi-romanization.txt` 每條詞帶方音、臺羅、白話字三種拼寫
- **台語 NLP**：帶真實語料頻次校正的詞表（頻次構成見「修改說明」）

最小取用範例（Python）：

```python
for line in open("phrases-taigi.txt", encoding="utf-8"):
    if line.startswith("#"):
        continue
    word, freq, *syllables = line.split()
    # word=漢字詞、freq=偽頻次（float）、syllables=逐字方音讀音
```

唯一的硬約束：`phrases-taigi.txt`／`char-taigi.txt`／`lexicon-taigi-romanization.txt` 是 **CC BY-SA 4.0**——你的衍生詞庫也必須以相同授權、可取得的形式釋出（照這個 repo 的做法做一份你的版本即可）。標示範本見「再利用標示範本」。

## 為何有這個儲存庫

胖打注音的台語詞庫合併了以 **CC BY-SA 4.0** 授權的來源（台華線頂對照典）。CC BY-SA 的 **ShareAlike** 條款要求：衍生資料須以相同授權、且未受技術措施限制的可取得形式釋出。胖打注音主程式閉源，App Store 二進位受 DRM 保護，故在此以未加密、可改的形式公開衍生詞表，以履行 ShareAlike 的 availability 義務。

## 版本對應與回饋

本儲存庫的 git tag 與 app 版本一一對應（例如 tag `v2.5.0` = App Store 上的 2.5.0 版詞庫）。每次 app 發版打 tag 時，由 CI 自動比對出貨詞庫並同步推送至此，公開內容永遠反映**已上架版本**。

- **回報錯字／誤讀音**：歡迎在本 repo 開 [issue](../../issues)
- **請勿直接發 PR**：檔案由 CI 從上游 pipeline 全量覆寫，直接改檔會在下次發版時被沖掉；修正會落在上游資料管線再同步出來

## 逐檔授權

| 檔案 | 內容 | 授權 |
|---|---|---|
| `phrases-taigi.txt` | 台語詞庫（詞＋頻次＋方音音節） | **CC BY-SA 4.0**（整體，含台華線頂衍生內容） |
| `char-taigi.txt` | 單字讀音頻次 | **CC BY-SA 4.0**（同上） |
| `lexicon-taigi-romanization.txt` | 詞條羅馬字（詞＋方音音節＋臺羅＋白話字）；臺羅為來源辭典**原文逐字保留**，白話字自臺羅轉出 | **CC BY-SA 4.0**（同上） |
| `emoji-annotations-taigi.txt` | 台語詞 → emoji 對應 | 混合血緣：台語詞取自 iTaigi（**CC0**）、emoji 對應衍生自 [rime-emoji](https://github.com/rime/rime-emoji)（**LGPL-3.0**，全文見 `LICENSES/`）；**不含**台華線頂內容，無 BY-SA 約束 |

`LICENSE` 為 CC BY-SA 4.0 全文，適用於 `phrases-taigi.txt`、`char-taigi.txt` 與 `lexicon-taigi-romanization.txt`。再利用這三檔時請**標示來源**並以**相同授權**釋出你的衍生作品；再利用 emoji 表時請依其血緣分別標示並隨附 `LICENSES/LGPL-3.0.txt`。

`lexicon-taigi-romanization.txt` 首行為 App 端 mmap 用的 pragma（`# panda-lexicon-v1 romanization`），其後為授權註解，再其後為 tab 分隔資料（按 UTF-8 byte order 排序）。以 `#` 開頭的行皆為註解。

## 檔案格式

| 檔案 | 格式 |
|---|---|
| `phrases-taigi.txt` | 每行 `詞 頻次 方音音節…`（空白分隔；頻次＝Dirichlet 混合偽頻次） |
| `char-taigi.txt` | 每行 `字 ⇥ 0 ⇥ 頻 ⇥ 讀音`（tab 分隔；第二欄恆為 `0`，是 McBopomofo 格式的佔位欄，無語意） |
| `lexicon-taigi-romanization.txt` | 每行 `詞 ⇥ 方音音節 ⇥ 臺羅 ⇥ 白話字`（tab 分隔） |
| `emoji-annotations-taigi.txt` | 每行 `台語詞 ⇥ emoji1,emoji2…`（tab 分隔） |

詞庫檔檔頭註解列出各源授權；以 `#` 開頭的行皆為註解。

### 方音符號編碼規格

讀音欄使用臺灣方音符號（Unicode 注音符號＋擴充區塊），調號與變音記號如下——寫 parser 時請以 Unicode code point 比對，不要目測字形：

| 聲調 | 記法 | Unicode |
|---|---|---|
| 陰平（1） | 無調符 | — |
| 陰上（2） | `ˋ` | U+02CB |
| 陰去（3） | `˪` | U+02EA |
| 陰入（4） | 裸入聲尾（ㆴㆵㆻㆷ 小字） | 尾字無附加符 |
| 陽平（5） | `ˊ` | U+02CA |
| 陽去（7） | `˫` | U+02EB |
| 陽入（8） | 入聲尾＋combining dot above | 尾字＋U+0307 |
| 輕聲 | 去調 base＋`˙`（尾為入聲尾則附 U+0307） | U+02D9 |

- 塞音韻尾 `-k` 一律用正字 **ㆻ**（U+31BB），不用 ㄍ 代用
- 鼻化、濁音等符號使用「注音符號擴充」區塊（ㆠ–ㆿ，U+31A0–U+31BF）
- 音節合法性以教育部方音符號系統為準；本資料所有讀音欄皆已通過合法音節白名單過濾，資料本身即可當白名單樣本使用

## 資料來源與各自授權

| 來源 | 收錄條數* | 授權 |
|---|---|---|
| [iTaigi 華台對照典](https://itaigi.tw/)（[ChhoeTaigi](https://github.com/ChhoeTaigi/ChhoeTaigiDatabase)） | ~16.7K | [CC0](https://creativecommons.org/publicdomain/zero/1.0/) |
| [教育部臺灣台語常用詞辭典](https://sutian.moe.edu.tw/)（[kemdict-data-ministry-of-education](https://github.com/kemdict/kemdict-data-ministry-of-education) 鏡像） | ~29.5K | [CC BY-ND 3.0 TW](https://creativecommons.org/licenses/by-nd/3.0/tw/) |
| [公視台語台《台語新詞辭庫》](https://github.com/kemdict/kemdict-pts-taigitv) | ~2.3K | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) |
| **[台華線頂對照典](https://github.com/ChhoeTaigi/ChhoeTaigiDatabase)（ChhoeTaigi）** | ~65.3K | **[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)** |
| **台灣植物名彙 1928（佐佐木舜一，[ChhoeTaigi](https://github.com/ChhoeTaigi/ChhoeTaigiDatabase)）** | ~0.7K（植物名） | **CC BY-SA 4.0** |
| [教育部學科術語臺灣台語／臺灣客語對譯查詢](https://sthj.moe.edu.tw/) | ~2.7K（學科術語，淨新增） | [政府網站資料開放宣告](https://data.gov.tw/license)（CC BY 等價） |
| **[iCorpus 臺華平行新聞語料庫漢字臺羅版](https://github.com/Taiwanese-Corpus/icorpus_ke5_han3-ji7)** | 詞頻（真實語料次數，非詞條） | CC BY 4.0 |

\* 通過品質過濾後併入本詞表的條數，隨版本演進。iCorpus 提供的是**詞頻**（非詞條），故無「收錄條數」。

- **台華線頂對照典** © [ChhoeTaigi 找台語](https://github.com/ChhoeTaigi/ChhoeTaigiDatabase)，CC BY-SA 4.0。本詞表含其衍生內容，故整體以 CC BY-SA 4.0 釋出。
- **台灣植物名彙 1928**（佐佐木舜一）© ChhoeTaigi，CC BY-SA 4.0。本詞表含其植物名衍生內容，同以 CC BY-SA 4.0 釋出。
- **教育部辭典**部分依 CC BY-ND 3.0 TW 重製並標示出處。臺羅→方音符號為規則驅動的機械式標音系統轉換，無創作性投入，屬**重製**而非改作；CC BY-ND 3.0 TW 第 3 條明文授權重製、散布與公開傳輸，且不限商業用途。
- **iTaigi**（CC0）、**公視新詞**（CC BY 4.0）向上相容併入 CC BY-SA。
- **教育部學科術語對譯**依政府網站資料開放宣告釋出（無償、得再授權、可改作、可商用，須註明出處＝CC BY 等價），向上相容併入 CC BY-SA。
- **iCorpus 臺華平行新聞語料庫漢字臺羅版** © 薛丞宏，CC BY 4.0（向上相容併入 CC BY-SA）。提供真實語料**詞頻**（非詞條），為頻次項的 count 來源（見「修改說明」）。
- 臺羅→方音符號轉換規則移植自 g0v [`trs2bpmf`](https://github.com/g0v/moedict-process)（CC0）。

## 再利用標示範本

再利用 BY-SA 三檔時，把下面這段放進你專案的 README／致謝即可滿足標示義務（CC BY-SA 4.0 §3(a)）：

> 台語詞庫衍生自「胖打注音台語衍生詞表」（<https://github.com/yintzuyuan/panda-zhuyin-taigi-lexicon>，CC BY-SA 4.0），
> 其上游來源含：台華線頂對照典・台灣植物名彙 1928 © ChhoeTaigi（CC BY-SA 4.0）、
> iTaigi 華台對照典（CC0）、教育部臺灣台語常用詞辭典（CC BY-ND 3.0 TW，重製）、
> 公視台語台《台語新詞辭庫》（CC BY 4.0）、教育部學科術語對譯（政府資料開放宣告）、
> iCorpus 臺華平行新聞語料庫 © 薛丞宏（CC BY 4.0，詞頻）。
> 本專案對上述資料所做修改：〔寫下你的修改，例如「重排頻次／轉換格式」〕。
> 本專案的詞庫依 CC BY-SA 4.0 釋出：〔你的釋出位置〕。

## 修改說明

（依 CC BY-SA 4.0 §3(a)(1)(B) 標示已對原始素材所做之修改）

- **格式轉換**：臺羅拼音 → 方音符號（g0v trs2bpmf 規則的忠實移植）
- **多源合併去重**（上表七源）：以（詞, 讀音）為鍵
- **詞頻（Dirichlet 混合偽頻次）**：`頻次 = 票數(prior) + iCorpus 真實語料次數 / μ`（μ=50）。
  - 票數 prior：原始三源各 2 票、台華線頂與台灣植物名彙各 1 票（fallback 源，獨有詞落尾段、不搶常用詞首位）；帶小數 ε 作來源優先度 tie-break（如 `凹 1.01 ㄠ`）。
  - iCorpus count：真實新聞語料的（詞, 讀音）出現次數，經臺羅→方音轉換後 join。**未命中語料的詞維持票數 prior 原值**（零證據詞排序不變）；c=1 單次觀測不翻越票數層（μ 護欄）。
- **單字頻次（char 層 standalone 注入）**：`頻次 = 來源覆蓋數(prior) + round(iCorpus 獨立單字詞次數 / 5)`。只計語料中**單獨成詞**的出現（複合詞構成字不灌入）；整數量化下微量觀測（c≤2）歸零；含少量新聞語體排除項（translationese，如被動句「被」）。
- **品質過濾**：剔除整句/諺語（≥7 漢字）、漢羅混寫、非法音節；另有以教育部辭典為 oracle 的字音與異寫品質閘門

## 產出方式

由胖打注音的 `Scripts/taigi-lexicon/` 與 `Scripts/taigi-emoji-overlay/` build pipeline 自動產出。本儲存庫為該產出的**公開鏡像**，app 發版時由 CI 自動同步。

## 相關連結

- 胖打注音官網／說明書：<https://github.com/yintzuyuan/panda-zhuyin>
