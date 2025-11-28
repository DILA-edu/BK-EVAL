# BK-EVAL (Buddhist Canon Knowledge Evaluation Dataset) 
佛典知識評測資料集 

本資料集為系統評估大語言模型（LLM）對佛教大藏經知識的記憶準確性為設立。
大藏經為佛教思想與實踐的核心文獻，其引用精確性對學術研究至關重要。然而，LLM 常出現「幻覺」現象，誤引或虛構經文內容，影響其在佛學應用的可靠性。為此，本研究建立三層級評估框架──「經典基本資料」、「經文摘要」、「全文內容」，並依 CBETA 閱讀與引用頻率，選取「常用核心」、「日常修行」、「常用儀軌」、「少用」四類經典為測試對象。建立此資料集。

This dataset is designed to systematically evaluate the accuracy of Large Language Models (LLMs) in recalling knowledge from the Buddhist Canon (大藏經). The Buddhist Canon serves as the foundational corpus for Buddhist thought and practice, making citation precision critical for academic research. However, LLMs frequently exhibit "hallucination" phenomena—misquoting or fabricating scriptural content—which undermines their reliability in Buddhist studies applications. To address this issue, this research establishes a three-tier evaluation framework: "Scripture Metadata," "Textual Summaries," and "Full-text Content." Based on CBETA reading and citation frequencies, we selected test materials across four categories: "Core Classics," "Daily Practice Texts," "Common Rituals," and "Rarely-Used Texts," to construct this evaluation dataset.

## 資料集資訊 Dataset Information

| 項目 | 內容 |
|------|------|
| 資料集名稱 | 大型語言模型對佛教大藏經知識記憶能力之評估資料集 |
| 版本 | 1.0.0 |
| 建立日期 | 2025-11-27 |
| 經典總數 | 40 部 |
| 題目總數 | 520 題 |
| 每部經典題數 | 13 題 (5 + 3 + 5) |

## 經典分類 Work Categories

資料集中的40部經典按使用頻率分為四類：

| 類別 | 數量 | 說明 |
|------|------|------|
| 常用核心經典 | 10 部 | 《大方廣佛華嚴經》(80卷本) (T0279)</br>《維摩詰所說經》 (T0475)</br>《大般若波羅蜜多經》 (T0220)</br>《妙法蓮華經》 (T0262)</br>《大般涅槃經》 (T0374)</br>《六祖大師法寶壇經》 (T2008)</br>《雜阿含經》 (T0099)</br>《增壹阿含經》 (T0125)</br>《大智度論》 (T1509)</br>《中論》 (T1564) |
| 常用日常修行經典 | 10 部 | 《佛說無量壽經》 (T0360)</br>《佛說阿彌陀經》 (T0366)</br>《地藏菩薩本願經》 (T0412)</br>《藥師琉璃光如來本願功德經》 (T0450)</br>《大佛頂如來密因修證了義諸菩薩萬行首楞嚴經》 (T0945)</br>《般若波羅蜜多心經》 (T0251)</br>《金剛般若波羅蜜經》 (T0235)</br>《梵網經菩薩戒本》(《佛說梵網經》下卷) (T1484)</br>《雜寶藏經》 (T0203)</br>《法句譬喻經》 (T0211) |
| 常用儀軌經典 | 10 部 | 《大佛頂如來密因修證了義諸菩薩萬行首楞嚴經．楞嚴咒》(楞嚴咒) (T0945)</br>《千手千眼觀世音菩薩大悲心陀羅尼》(大悲咒) (T1064)</br>《諸經日誦集要．蒙山施食》 (JB044)</br>《慈悲道場懺法》(梁皇寶懺) (T1909)</br>《慈悲三昧水懺》 (T1910)</br>《千手眼大悲心咒行法》(大悲懺) (X1480)</br>《法華三昧懺儀》 (T1941)</br>《百丈清規證義記．蘭盆儀軌摘要》 (X1244)</br>《法界聖凡水陸勝會修齋儀軌》(水陸法會) (X1497)</br>《瑜伽集要施食儀軌》(焰口) (X1080) |
| 少用經典 | 10 部 | 《佛說除蓋障菩薩所問經》 (T0489)</br>《佛說華手經》 (T0657)</br>《大乘中觀釋論》 (T1567)</br>《最上乘論》 (T2011)</br>《楞嚴摸象記》 (X0276)</br>《那先比丘經》 (T1670A)</br>《信力入印法門經》 (T0305)</br>《大乘離文字普光明藏經》 (T0829)</br>《大廣博嚴淨不退轉法輪經》 (T0268)</br>《佛說蓮華面經》 (T0386) |

## 題目層級 Question Tiers

### Tier 1: 經文基本資料 (Background Info)
- **題型**: 單選題
- **每部經典**: 5 題
- **總數**: 200 題
- **評分**: 二元評分 (0/1)

| 題目編號 | 問題焦點 |
|----------|----------|
| 0 | 經號 (CBETA ID) |
| 1 | 作譯者 |
| 2 | 翻譯朝代 |
| 3 | CBETA 部類 |
| 4 | 經文結構 |

### Tier 2: 經文摘要 (Summary)
- **題型**: 單選題 (選項為長文摘要)
- **每部經典**: 3 題
- **總數**: 120 題
- **評分**: 二元評分 (0/1)
- **答題格式**: 回覆英文代碼 (A/B/C/D)

#### 經典類 (Sutras)
| 題目編號 | 問題焦點 |
|----------|----------|
| 0 | 法會摘要 (法會背景與說法因緣) |
| 1 | 法義摘要 (核心法義與修行要點) |
| 2 | 本品重要性 (在全經中的地位) |

#### 律典類 (Vinaya)
| 題目編號 | 問題焦點 |
|----------|----------|
| 0 | 制律背景 (制戒因緣與對象) |
| 1 | 戒律內容 (戒條、持犯、懺悔) |
| 2 | 本戒重要性 (對僧團管理的意義) |

#### 論典類 (Abhidharma)
| 題目編號 | 問題焦點 |
|----------|----------|
| 0 | 論述背景 (論主、造論因緣、論證架構) |
| 1 | 論證內容 (破立對象、論證方法) |
| 2 | 本品重要性 (在該論中的地位與貢獻) |

#### 佛教故事類 (Buddhist Stories)
| 題目編號 | 問題焦點 |
|----------|----------|
| 0 | 故事背景 (出處、說法因緣、故事類型) |
| 1 | 故事梗概 (起承轉合、因果關係) |
| 2 | 法義啟示 (核心教義與修行啟發) |

#### 儀軌類 (Rituals)
| 題目編號 | 問題焦點 |
|----------|----------|
| 0 | 儀軌背景 (來源、傳承、編纂因緣) |
| 1 | 儀軌內容 (結構、流程、修持方法) |
| 2 | 儀軌重要性 (功德特色與實踐價值) |

### Tier 3: 全文內容 (Fulltext)
- **題型**: 填充題
- **每部經典**: 5 題
- **總數**: 200 題
- **評分**: 編輯距離相似度 (0.0~1.0)
- **答題格式**: 按⭘數填入相應長度的答案

| 難度分布 | 說明 |
|----------|------|
| 簡單 | 專有名詞 (如：毘盧遮那如來) |
| 中等 | 教義概念 (如：三昧、普順十方國土) |
| 困難 | 較長或罕見詞彙 (如：阿耨多羅三藐三菩提) |

## 系統提示詞 System Prompt

```
你是專業的佛學文獻分析專家，回答以下佛教相關問題時，請不要連接網際網路向外蒐集資訊，
根據內建記憶來回答就好。在回答佛教經文基本資料問題時，請由答案選項中選出一個最合適的答案；
回答佛教經文摘要問題時，回覆答案選項的代號就好；
回答佛教全文內容問題時，請按⭘⭘數給出同等長度文字。
以上都不用給解釋，直接回覆答案或答案代碼即可。
```

## 資料結構 Data Structure

```json
{
  "system_prompt": { "prompt_text": "..." },
  "dataset_metadata": {
    "dataset_name": "大型語言模型對佛教大藏經知識記憶能力之評估資料集",
    "dataset_version": "1.0.0",
    "total_works": 40
  },
  "works": [
    {
      "work_id": "T0279",
      "work_type": "常用核心經典",
      "cbeta_url": "https://cbetaonline.dila.edu.tw/zh/T0279",
      "authority_id": "CA0001373",
      "title": "《大方廣佛華嚴經》(80卷本)",
      "question_sets": {
        "background_info": [...],  // 5 questions
        "summary": [...],          // 3 questions
        "fulltext": [...]          // 5 questions
      }
    }
  ],
  "evaluation_guidelines": {...}
}
```

### 問題物件結構 Question Object

```json
{
  "question_focus": "經號",
  "question_type": "單選題",
  "question": "《大方廣佛華嚴經》(80卷本)的CBETA經號是多少？...",
  "answer_options": "T0279，T0412，T0278，T0305",
  "correct_answer": "T0279",
}
```

## 評分標準 Scoring Guidelines

### Tier 1 & Tier 2: 二元評分
| 結果 | 分數 |
|------|------|
| 正確 | 1 |
| 錯誤 | 0 |

### Tier 3: 編輯距離評分
使用 Levenshtein 編輯距離計算相似度：

$$similarity = 1 - \frac{distance}{max\_length}$$

| 相似度範圍 | 說明 |
|------------|------|
| 1.0~0 | 完全正確～部分正確～錯誤 |


## 使用方式 Usage

### 載入資料集
```python
import json

with open('LLM_Buddhist_Canon_Evaluation_Dataset_v1.0.0.json', 'r', encoding='utf-8') as f:
    dataset = json.load(f)

system_prompt = dataset['system_prompt']['prompt_text']
works = dataset['works']

# 遍歷所有問題
for work in works:
    work_id = work['work_id']
    for tier in ['background_info', 'summary', 'fulltext']:
        questions = work['question_sets'][tier]
        for i, q in enumerate(questions):
            question_id = f"{work_id}_{tier}_{i}"
            prompt = q['question']
            if q['answer_options']:
                prompt += f"\n\n答案選項：{q['answer_options']}"
            # 發送給 LLM 進行評估
```

## 資料來源 Data Sources

- **CBETA 中華電子佛典協會**: https://cbetaonline.dila.edu.tw/
- 經典元資料來自 CBETA Authority Database
- 經文內容來自 CBETA 電子佛典集成

## 授權說明 License

本資料集僅供學術研究使用。內容版權歸屬法鼓文理學院數位典藏組。

## 引用 Citation

如使用本資料集，請引用：

```
@dataset{llm_buddhist_canon_eval_2025,
  title={Buddhist Canon Knowledge Evaluation Dataset},
  author={DILA Digital Archive Team},
  year={2025},
  version={1.0.0}
}
```

## 更新紀錄 Changelog

### v1.0.0 (2025-11-27)
- 初始版本發布
- 包含 40 部經典、520 題評估問題
- 支援三層級評估：經文基本資料、經文摘要、全文內容
