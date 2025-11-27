# BK-EVAL (Buddhist Canon Knowledge Evaluation Dataset) 

**佛典知識評測資料集**

本資料集為系統評估大語言模型（LLM）對佛教大藏經知識的記憶準確性為設立。
大藏經為佛教思想與實踐的核心文獻，其引用精確性對學術研究至關重要。然而，LLM 常出現「幻覺」現象，誤引或虛構經文內容，影響其在佛學應用的可靠性。為此，本研究建立三層級評估框架──「經典基本資料」、「經文摘要」、「全文內容」，並依 CBETA 閱讀與引用頻率，選取「常用核心」、「日常修行」、「常用儀軌」、「少用」四類經典為測試對象。建立此資料集。

**錯誤代碼說明:**
- `S` - Safety Block (Gemini finish_reason=2)
- `Q` - API Quota Exceeded (429)
- `T` - Timeout (504)
- `C` - Cancelled (499)
- `I` - Invalid response
- `U` - Unknown/missing
