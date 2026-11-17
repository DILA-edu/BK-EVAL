# 2025-11-28 評測結果更正說明 Correction Note for the 2025-11-28 Results

日期 Date: 2026-11-16

本說明不更動任何資料檔。它只更正對這些檔案的解讀。
This note changes no data file. It corrects only how to read the files.

適用檔案 Files that this note applies to:

- `model_gemini-2.5-flash.csv`
- `model_gemini-2.5-pro.csv`
- `model_gemini-3-pro.csv`
- `model_gpt-5-mini.csv`（僅第 3 節 section 3 only）

---

## 1. 分數檔中的代碼 Codes in the score files

`model_*.csv` 中非數值的格子是一個字母的代碼。這份代碼表先前沒有發布。
A cell of `model_*.csv` that is not a number holds a one-letter code. This legend was not published before.

| 代碼 Code | 評測程式中的標籤 Label in the pipeline | gemini-2.5-flash | gemini-2.5-pro | gemini-3-pro |
|---|---|---|---|---|
| `S` | "Safety Block (finish_reason=2)"：見第 2 節 see section 2 | 257 | 509 | 69 |
| `Q` | API 配額用盡 API quota exceeded (HTTP 429) | 0 | 0 | 421 |
| `T` | 逾時 Timeout (HTTP 504) | 0 | 0 | 2 |
| `C` | 已取消 Cancelled (HTTP 499) | 0 | 0 | 1 |
| `I` | 無效回應 Invalid response | 0 | 0 | 1 |
| `U` | 未知或缺漏 Unknown or missing | 263 | 11 | 26 |
| 合計 Total | | 520 | 520 | 520 |

這三個 Gemini 模型在本資料夾中沒有任何已計分的格子。
The three Gemini models have no scored cell in this folder.

## 2. 更正：代碼 `S` 不表示安全封鎖 Correction: code `S` does not show a safety block

**中文**

1. 當 Gemini API 回傳 `finish_reason = 2` 時，評測程式給出代碼 `S`，並把它標為「Safety Block」。
2. 這個標籤是錯的。在 Gemini API 中，`finish_reason` 的數值 2 是 `MAX_TOKENS`，數值 3 才是 `SAFETY`。
3. 所以 `S` 格子表示回應停在輸出 token 上限。它不是安全過濾器的證據。
4. 可能的原因：評測程式對這些模型設定 512 個輸出 token 的上限，而模型內部的思考用完了這個上限。同一時期對 `gemini-2.5-flash` 的一項測試支持這一點：上限為 512 時，它回傳 `MAX_TOKENS` 且沒有內容；上限為 1024 時，它正常作答。這項測試只用了一題與一個模型。該次執行沒有記錄失敗呼叫的 token 數。
5. 評測程式沒有檢查數值 3。所以這些檔案無法顯示是否發生過安全封鎖。

**請勿**用這些檔案主張 Gemini 封鎖佛典文字或封鎖特定經典。**請勿**用本資料夾比較這三個 Gemini 模型與其他模型。`response_gemini-2.5-flash.csv` 有 265 個格子的答案，但它的分數檔沒有分數。

**English**

1. The pipeline gave the code `S` when the Gemini API returned `finish_reason = 2`. It labelled this result "Safety Block".
2. The label is wrong. In the Gemini API, the `finish_reason` value 2 is `MAX_TOKENS`. The value 3 is `SAFETY`.
3. So an `S` cell shows that the response stopped at the limit of output tokens. It is not evidence of a safety filter.
4. Probable cause: the evaluation code set a limit of 512 output tokens for these models, and the internal reasoning of the models used all of the limit. A test of `gemini-2.5-flash` from the same period supports this: with a limit of 512 it returned `MAX_TOKENS` and no content, and with a limit of 1024 it answered. That test used one question and one model. The run did not record token counts for failed calls.
5. The pipeline did not test for the value 3. So these files cannot show whether a safety block occurred.

**Do not** use these files to state that Gemini blocks Buddhist canon text or blocks specific works. **Do not** use this folder to compare the three Gemini models with other models. `response_gemini-2.5-flash.csv` has answers for 265 cells, but its score file has no scores.

## 3. 已知問題：`gpt-5-mini` 的 T0945 Known issue: T0945 for `gpt-5-mini`

**中文**

資料集中有兩部作品共用經號 T0945（第 15 列與第 21 列）。在 `model_gpt-5-mini.csv` 中：

- 第 21 列（楞嚴咒）有 8 個 `U` 格子。回應檔中這些格子沒有答案。
- 第 15 列的「全文內容_0」分數是 1，但回應（淫念）與答案（三昧）不同。

很可能是這兩列的配對出了錯。原因尚在調查中。在問題解決之前，使用 `gpt-5-mini` 的結果時請排除這兩列。

**English**

Two works in the dataset share the work ID T0945 (rows No. 15 and No. 21). In `model_gpt-5-mini.csv`:

- Row No. 21 (楞嚴咒) has 8 `U` cells. The response file has no answer for these cells.
- Row No. 15, column 全文內容_0, has the score 1, but the response (淫念) is not the answer (三昧).

A fault in the matching of these two rows is probable. The cause is under investigation. Until it is resolved, leave these two rows out when you use the `gpt-5-mini` results.

## 4. 公開演講中的相關陳述 Related statements in public talks

**中文**

這些結果曾在兩場公開演講中展示：

- 洪振洲、吳怡輝，〈大語言模型對佛教大藏經知識記憶能力的系統化評估研究〉，第十六屆數位典藏與數位人文國際研討會（DADH 2025），國立臺灣大學，2025-11-29。（論文集頁 318–324 只收錄摘要，沒有結果。）
- 洪振洲、吳怡輝，〈從鸚鵡到鏡子：一場讓 AI 照見本來記憶的佛典大考〉，2026 法鼓數位典藏專案春季發表會，2026-05-20。影片：https://youtu.be/-C17A6u1ius

本說明更正這兩場演講中的兩項陳述：

1. 兩場演講都把這三個 Gemini 模型標為「Safety Block」。第 2 節更正這一點：這些格子停在輸出 token 上限，不是安全封鎖的證據。
2. 2026 年的演講用 ▲/▼ 比較兩次評測的「綜合評分」。兩次的公式不同。2025 年的公式依題數加權平均三個層級，全文內容用平均相似度。2026 年的公式只在相似度 0.7 以上時才把全文內容題目算為答對。所以 2026 年的數值較低，每個 ▲/▼ 都低了 2.2 至 3.6 分。用同一公式時，GPT-5 → GPT-5.4、Claude Sonnet 4.5 → 4.6 與 Claude Opus 4.5 → 4.7 都是上升，不是下降。同一模型 Claude Haiku 4.5 的 ▼4.3 變為 −1.0。請分別比較各層級的分數，不要比較綜合評分。

**English**

These results were shown in two public talks:

- 洪振洲 and 吳怡輝, "A Systematic Study on Large Language Models' Memory of the Buddhist Canon", 16th International Conference on Digital Archives and Digital Humanities (DADH 2025), National Taiwan University, 2025-11-29. (Proceedings pp. 318–324 hold the abstract only, with no results.)
- 洪振洲 and 吳怡輝, 從鸚鵡到鏡子 ("From Parrot to Mirror"), 2026 法鼓數位典藏專案春季發表會 (Dharma Drum digital archives projects spring event), 2026-05-20. Video: https://youtu.be/-C17A6u1ius

This note corrects two statements in these talks:

1. Both talks labelled the three Gemini models "Safety Block". Section 2 corrects this: these cells stopped at the limit of output tokens. They are not evidence of a safety block.
2. The 2026 talk compared the pooled score (綜合評分) of the two campaigns with ▲/▼. The two campaigns used different formulas. The 2025 formula is the item-weighted mean of the three tiers, with the mean similarity for Full-text Content. The 2026 formula counts a Full-text Content item as correct only at a similarity of 0.7 or more. So the 2026 values are lower, and each ▲/▼ is 2.2 to 3.6 points too low. With one formula, GPT-5 → GPT-5.4, Claude Sonnet 4.5 → 4.6 and Claude Opus 4.5 → 4.7 all rise; they do not fall. For the same model, Claude Haiku 4.5, ▼4.3 becomes −1.0. Compare the scores of each tier separately. Do not compare pooled scores.
