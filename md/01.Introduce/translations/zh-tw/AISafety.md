﻿## Phi-3 模型的 AI 安全性

Phi 系列模型的開發符合[Microsoft 的負責任 AI 原則](https://www.microsoft.com/ai/responsible-ai)。

## 最佳實踐

像其他模型一樣，Phi 系列模型可能會以不公平、不可靠或冒犯的方式表現。

一些 SLM 和 LLM 的限制行為包括：

- **服務品質:** Phi 模型主要基於英文文本進行訓練。非英文語言的表現會較差，訓練數據中代表性較少的英語變體的表現可能會比標準美式英語差。
- **傷害的表現與刻板印象的延續:** 這些模型可能會過度或不足地代表某些人群，抹去某些群體的代表性，或強化貶低或負面的刻板印象。儘管進行了安全後訓練，由於不同群體的代表性水平不同或訓練數據中反映現實世界模式和社會偏見的負面刻板印象範例的普遍性，這些限制可能仍然存在。
- **不適當或冒犯性內容:** 這些模型可能會生成其他類型的不適當或冒犯性內容，這可能使其在沒有針對具體使用情況進行額外緩解的敏感情境中不適合部署。
資訊可靠性: 語言模型可以生成無意義的內容或捏造聽起來合理但實際上不準確或過時的內容。
- **程式碼的有限範圍:** Phi-3 訓練數據的大部分基於 Python 並使用常見套件，如 "typing, math, random, collections, datetime, itertools"。如果模型生成的 Python 腳本使用其他套件或其他語言的腳本，我們強烈建議用戶手動驗證所有 API 的使用。

開發者應該應用負責任的 AI 最佳實踐，並負責確保特定的使用案例符合相關法律和法規（例如隱私、貿易等）。

使用 LLM 和 SLM 時需要考慮的重要領域包括:

- **分配:** 模型可能不適合在未經進一步評估和額外去偏技術的情況下，用於可能對法律地位或資源或生活機會（例如：住房、就業、信貸等）產生重大影響的情景。
- **高風險情景:** 開發者應評估在高風險情景中使用模型的適用性，因為不公平、不可靠或冒犯性的輸出可能會帶來極高的成本或導致傷害。這包括在準確性和可靠性至關重要的敏感或專業領域提供建議（例如：法律或健康建議）。應根據部署情境在應用層面實施額外的保障措施。
- **錯誤資訊:** 模型可能會產生不準確的資訊。開發者應遵循透明度最佳實踐，並告知終端用戶他們正在與 AI 系統互動。在應用層面，開發者可以建構反饋機制和管道，將回應基於特定用例的上下文資訊，這種技術稱為檢索增強生成（RAG）。
- **有害內容的生成:** 開發者應評估輸出的上下文，並使用適合其用例的可用安全分類器或自定義解決方案。
- **濫用:** 其他形式的濫用，如欺詐、垃圾郵件或惡意軟體生成是可能的，開發者應確保其應用不違反適用的法律和法規。
- **個人識別:** 具有視覺能力的模型可能有潛力在圖像中唯一識別個人。安全後訓練引導模型拒絕此類請求，但開發者應考慮並實施適當的額外緩解措施或用戶同意流程，以符合其所在司法管轄區的要求（例如，在處理前建構模糊圖像輸入中人臉的措施）。

### 微調和 AI 內容安全

經過微調模型後，我們強烈建議利用 [Azure AI Content Safety](https://learn.microsoft.com/azure/ai-services/content-safety/overview) 措施來監控模型生成的內容，識別並阻止潛在的風險、威脅和品質問題。

![Phi3AISafety](../../../../imgs/01/phi3aisafety.png)

[Azure AI Content Safety](https://learn.microsoft.com/azure/ai-services/content-safety/overview) 支援文字和影像內容。它可以部署在雲端、離線容器和邊緣/嵌入式裝置上。

## Azure AI 內容安全概述

Azure AI Content Safety 不是一個一體適用的解決方案；它可以根據企業的特定政策進行自訂。此外，其多語言模型使其能夠同時理解多種語言。

![AIContentSafety](../../../../imgs/01/AIcontentsafety.png)

- **Azure AI 內容安全**
- **Microsoft 開發者**
- **5 部影片**

Azure AI Content Safety 服務檢測應用程式和服務中有害的用戶生成和 AI 生成的內容。它包括文字和圖像 API，可讓您檢測有害或不適當的材料。

[AI Content Safety Playlist](https://www.youtube.com/playlist?list=PLlrxD0HtieHjaQ9bJjyp1T7FeCbmVcPkQ)
