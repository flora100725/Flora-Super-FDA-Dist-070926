Super, please keep all original features and adding additional features that 1. Please let user to select light/dark themes, default Traditional  Chinese/English and 10 styles based on featured color of teams. Please also adding wow visualization effects for llm execution, interactive indicators, live log, wow interactive dashboards with 6 graphs.Please also adding 3 additional wow ai features to this app. Please make gemini-3.1-flash-lite default model (user can select other models and modify prompt). Please fix blank screen bugs and iterate until get excellet results. Ending with 20 comprehensive follow up qustions. 中華民國衛生福利部食品藥物管理署（TFDA）醫療器材主動追蹤、空間合規與自主代理作業系統平台：AURA-7 Hub v2 擴展技術規格書第四部分：AURA-7 Hub v2 自主代理作業系統（Agentic OS）與技能操練場（Skill Playground）核心規格一、 系統升級概述與 Agentic OS 願景 (System Upgrade & Agentic OS Vision)為因應 2026 年全球醫療器材法規環境之劇烈變動，以及高風險（Class III）醫療器材跨境流向追蹤之高複雜度，AURA-7 Hub 全面升級至 v2 自主代理作業系統（Agentic OS） 構型。本系統不再僅是動態數據渲染與靜態規則對帳的工具，而是將大語言模型（LLM）神經推理大腦與 Google ADK（Agent Development Kit） 深度整合之全功能主動式執法指揮台。透過引入「可編程法規技能文件（skill.md）」架構，系統賦予 TFDA 稽核官員、臨床工程師與生醫法規專家動態定義、動態修正並跨模型測試 AI 代理（Agents）核心技能之能力。透過高度解耦的技能操練場（Skill Playground），使用者得以在單一高科技網格介面上，上傳或貼入多源異質法規文獻（包含 .txt, .csv, .md, .json, 及雙層向量優化 .pdf 檔案），並命令由不同大語言模型驅動之自主代理執行多維度合規推理、條碼解編、以及跨院所調撥路徑最優化計算，最後透過跨模型/跨技能對位矩陣（Comparison Matrix） 實施盲測評估，達成極致的法規執行精準度。二、 Google ADK 自主代理核心架構與工具鏈整合 (Google ADK Core Integration)AURA-7 Hub v2 後端中繼代理引擎（基於 Express 4.21.2 部署於 server.ts）原生整合 Google 頂尖大語言模型 API 及其專屬之 Agent Development Kit (ADK) 核心工具鏈。本平台之自主代理不依賴傳統的寫死條件式（Hard-coded If-Else），而是透過動態調用以下兩大 ADK 基礎工具達成自主尋路與即時計算：+-----------------------------------------------------------------------+
|                    AURA-7 Hub v2 Agentic OS Core                      |
+-----------------------------------------------------------------------+
|                                                                       |
|  +--------------------+   +-------------------+   +----------------+  |
|  |     Skill Core     |   |   Google ADK      |   |   LLM Pool     |  |
|  |    (skill.md)      |-->|   Tool Router     |<->| gemini-3.1-fl. |  |
|  |   Dynamic Engine   |   | (Function Calling)|   | gemini-3.5-fl. |  |
|  +--------------------+   +-------------------+   +----------------+  |
|                                     |                                 |
|                  +------------------+------------------+              |
|                  |                                     |              |
|                  v                                     v              |
|       +---------------------+               +---------------------+   |
|       |    Google Search    |               |   Code Execution    |   |
|       |   (google_search)   |               |  (built_in_code...) |   |
|       +---------------------+               +---------------------+   |
+-----------------------------------------------------------------------+
2.1 全球即時法規搜尋工具 (Google Search)整合原理：當使用者呼叫代理處理突發性合規事件（例如跨國醫材原廠發布 Class 1 Recall 訊息）時，代理可將 Google Search 作為原生工具（Tool Declaration）加入呼叫參數中。執行機制：$$\text{SearchQuery} = \text{ExtractEntity}(\text{UserPrompt}) \cup \text{ExtractLot}(\text{Context})$$後端接收到 LLM 觸發的 Function Calling 請求後，自動調用 Google 搜尋，並將回傳之全球監管網頁摘錄（來自 FDA, EMA, PMDA 等）以結構化上下文（Context）即時反哺給神經推理節點，徹底消除因訓練資料滯後導致之法規真空幻覺。2.2 內置代碼執行沙盒工具 (built_in_code_execution)整合原理：系統內置 VertexCodeInterpreter 機制，允許代理在遭遇大批量經緯度運算、大對帳單矩陣差異比對、或是需要執行複雜統計分析時，自主編寫 Python 或 JavaScript 程式碼片段。執行機制：代碼將在一層完全隔離、具備高可用防禦能力的沙盒環境中被即時編譯與執行。代理會讀取沙盒輸出的標準 stdout 數據或數值矩陣，進而精確計算出如測地距離衰減率（Haversine Decay Rates）等高精確度法規工程數據，免除純文字模型處理數學運算之低效能。三、 可編程技能文件 Lifecycle 引擎規格 (Skill.md Lifecycle Engine)為實現「軟體定義監管（Software-Defined Regulation）」，AURA-7 Hub v2 推出 skill.md 動態編程面板。此模組允許使用者完全掌握代理的行為準則、提示詞骨幹與工具調用策略。3.1 核心前端交互介面組件 (UI Components)代碼黏貼工作區 (#skill-paste-area)：一個內嵌的高級語法高亮文字域（支援 Markdown 語法樹渲染），供官員隨時貼入來自外部知識庫的客製化代理技能結構。拖曳上傳網格 (#skill-file-dropzone)：支援 HTML5 File Reader API，官員可直接將本機的 skill.md 拖入。系統會在 100 毫秒內解構語法，並提供動態加載動畫。預設技能選取器 (#default-skill-dropdown)：系統內置三套 TFDA 標準技能骨幹供使用者一鍵選取：Class III Recall 溯源技能雙向帳籍漏洞交叉排查技能跨院所冷鏈重分配調撥最優化技能3.2 技能編修與自主演進工作流 (Modification & Evolution Loop)使用者可透過以下三種軸線對 skill.md 實施全生命週期修編：就地手動編輯：使用者可在前端直接增刪法規條文或調整代理的 System Instructions。一鍵下載備份 (#download-skill-btn)：點擊後，前端會將當前工作區內的技能文本封裝為標準字元流，並以 aura7_skill_[TIMESTAMP].md 命名導出至本機。LLM 代理引導式修正 (#prompt-modify-skill-input / #execute-modify-btn)：使用者可輸入自然語言提示詞（例如：「請重新修改當前技能文件，在判定出庫未登（🔴 Unreported）事件時，強制要求代理引入醫療器材管理法第70條之罰則指導，並自動調用 google_search 核對最新修法基準。」）。系統默認調用 gemini-3.1-flash-lite 讀取原技能文件，進行語意重構，並在 #skill-paste-area 中高亮呈現更新後的 Markdown 語法樹。四、 多模型多技能操練場與對位矩陣規格 (Multi-Model Skill Playground & Comparison Matrix)技能操練場（Skill Playground） 是 AURA-7 Hub v2 的精華所在，提供了一個讓法規專家盲測 AI 推理質量的高科技虛擬模擬艙。+-----------------------------------------------------------------------------------+
|                            AURA-7 HUB v2 AGENTIC OS DASHBOARD                     |
+-----------------------------------------------------------------------------------+
| [📁 Upload skill.md] [⚙️ Select Model: gemini-3.1-flash-lite]                     |
+-----------------------------------------------------------------------------------+
|  LEFT PANEL: SKILL FILE CORE       |  CENTER: MULTI-DOC PLAYGROUND                |
|  - Text Editor Area (#skill-paste) |  - File Dropzone (.txt, .csv, .pdf, .json)   |
|  - [Prompt LLM to modify skill]    |  - Skill Injection Selector                  |
|  - [Modify] [Download skill.md]    |  - [▶️ RUN MULTI-MODEL COMPARISON]           |
+------------------------------------+----------------------------------------------+
|  RIGHT PANEL: WOW AI SUITE CARD DECK                                              |
|  - Agent 1: Dispute Resolutor     - Agent 4: TFDA Legal Assistant                 |
|  - Agent 2: Route Risk Analyzer   - Agent 5: Expiry Optimizer                     |
|  - Agent 3: GS1 UDI Composer      - Agent 6: Neural Anomaly Hunter                |
+-----------------------------------------------------------------------------------+
|  BOTTOM PANEL: CROSS-COMPARISON MATRIX GRID                                       |
|  +--------------------+-------------------------+-------------------------+       |
|  | Config             | Model A: 3.1-Flash-Lite | Model B: 3.5-Flash      |       |
|  +--------------------+-------------------------+-------------------------+       |
|  | Skill 1 (Recall)   | [Output & Latency Ms]   | [Output & Latency Ms]   |       |
|  | Skill 2 (Custom)   | [Output & Latency Ms]   | [Output & Latency Ms]   |       |
|  +--------------------+-------------------------+-------------------------+       |
+-----------------------------------------------------------------------------------+
4.1 異質文獻載入網關 (#playground-doc-uploader)支援將物理抽查紀錄、醫院進銷存報表、跨國原廠英文安全通告等多種格式（.txt, .csv, .md, .json, .pdf）一併拖入。系統後端會自動調用 Decoupled Parsing Pipeline，將異質資料轉譯為乾淨、帶有原始 metadata 標記的標準化 JSON 文字流，作為 AI 代理的實質查驗上下文。4.2 跨模型與跨技能交叉對位矩陣 (#comparison-matrix-grid)使用者可勾選多種大語言模型（如系統預設之基石模型 gemini-3.1-flash-lite、效能旗艦模型 gemini-3.5-flash、或是具備深層推理能力的 gemini-3.1-pro-preview），並同時勾選不同版本的 skill.md。點擊 ▶️ Run Multi-Model Comparison 鈕後，後端 Express 將會發射平行非同步請求（Parallel Asynchronous Requests），並在前端以格狀矩陣即時對比輸出結果：評估維度 / 實驗配置預設模型：gemini-3.1-flash-lite進階模型：gemini-3.5-flash深層推理模型：gemini-3.1-pro-preview標準技能：流向對帳回覆時延：~450msToken 消耗：極低合規判定：精確執行 If-Else 邏輯對齊，給出標準四色標籤。回覆時延：~600msToken 消耗：低合規判定：具備優良的語意平滑度，能自發捕捉複合型帳籍漏洞。回覆時延：~1200msToken 消耗：中合規判定：產出極具法律嚴密性的行政裁量書，完全引用成文法典。自訂技能：跨國 Recall回覆時延：~500msADK 工具表現：能流暢調用 Google Search 獲取一線 Recall 資訊。回覆時延：~550msADK 工具表現：自動結合 built_in_code_execution 計算涉案批號之在台庫存百分比。回覆時延：~1500msADK 工具表現：自主編寫複雜的 Python 地理矩陣腳本，產出最優化攔截路徑。五、 新增三大「WOW」AI 智慧代理功能規格 (Three Additional WOW AI Features)為將作業系統之自主智慧推向極致，v2 版本正式導入三大全新全功能 AI 代理引擎，直接編織入右側 #wow-ai-suite-card-deck 中。5.1 WOW 功能 七：全通路即時虛擬遙測數據合成引擎 (Real-time Telemetry Synthesis Agent)對應元件 ID：#telemetry-synthesis-card / 啟動按鈕：#synthesize-telemetry-btn核心技術原理：當實地稽核官員面臨某些缺乏物聯網（IoT）冷鏈硬體部署的偏鄉醫療院所時，本代理引擎會啟動。它會自主抓取當前 DHA 站點的歷史吞吐量、台灣氣象觀測測站即時氣溫 API（透過 Google Search）、以及該經銷商使用的物流車輛車齡與保溫箱規格。基於熱力學衰變物理公式：$$\Delta T = k \cdot (T_{\text{ambient}} - T_{\text{target}}) \cdot \Delta t$$代理透過內置的 built_in_code_execution 工具在沙盒中運行一個微型模擬，憑空合成出一份極度逼真的「在途溫濕度時序虛擬遙測數據流（Synthesized Telemetry Stream）」，用以回推評估該批主動植入式心律調節器在過去 48 小時內是否曾發生隱蔽性失溫退化，精準率高達 91%。5.2 WOW 功能 八：預測性全球供應鏈衝擊與短缺模擬器 (Predictive Regulatory Shock Simulator)對應元件 ID：#regulatory-shock-card / 啟動按鈕：#simulate-shock-btn核心技術原理：本代理旨在防範「斷貨級公共衛生危機」。代理會主動調用 Google Search 全天候監控全球生醫原料產地、跨國醫材巨頭產線工廠（如愛爾蘭、新加坡發貨倉）之罷工事件、地緣政治衝突、或全新修訂的歐盟 MDR 法規限制。當官員指定某款 Class III 醫材（如 Abiomed 心臟幫浦）時，代理會在沙盒中建立一個離散馬可夫鏈模型（Markov Chain Model），模擬未來 6 到 12 個月內台灣本島的庫存枯竭曲線與斷貨時間點（Depletion Zero-Day），並主動幫 TFDA 官員撰寫戰略儲備建議書與替代品許可證核發指南。5.3 WOW 功能 九：跨代理自主共識執法蜂群 (Autonomous Multi-Agent Consensus Swarm)對應元件 ID：#consensus-swarm-card / 啟動按鈕：#ignite-swarm-btn核心技術原理：此功能打破單一 AI 判定的侷限。當系統檢測到極度嚴重的惡意違規事件（例如：同時觸發 🔴 出庫未登 與 🟡 幽靈帳籍，且涉案器材屬高致死風險之主動脈血管支架）時，使用者點擊此鈕，系統將在內存中瞬間孵化（Instantiate）出三個具備不同性格特徵的自主法規代理人：嚴苛派執法稽核官代理（Pro-Prosecution Auditor）生醫原廠法務合規官代理（Defense Counsel RA）臨床工程與患者安全專家代理（Clinical Safety Advocate）這三個代理將依據 skill.md 定義的辯論規則，在後端進行多輪自主對話（Multi-Agent Debating）。各代理會自主調用代碼沙盒或搜尋引擎來捍衛自身觀點。最終，蜂群系統會產出一部集結了「控方觀點、辯方陳述、臨床權衡」之三方共識法規合規裁決書，將模型的可解釋性與客觀性拉升至司法審判級高度。六、 升級後全鏈數據流動與反向代理資安網關 (Data Flow & Security Architecture)為確保使用者在技能操練場中貼入的敏感文件不致洩漏，AURA-7 Hub v2 嚴格重構了其數據通道（Data Pipeline）：+---------------------------------------------------------------------------------------------------------+
|                                    AURA-7 Hub v2 Secure Data Pipeline                                   |
+---------------------------------------------------------------------------------------------------------+
|                                                                                                         |
|  [User Uploads .pdf/.csv]                                                                               |
|             |                                                                                           |
|             v                                                                                           |
|  +---------------------------+       +----------------------------+       +--------------------------+  |
|  | #playground-doc-uploader  |------>| Local Redaction Pipeline   |------>| Express Endpoint         |  |
|  |  (UI Ingestion Sandbox)   |       |  (Regex + Local NER Scan)  |       |   (/api/gemini/execute)  |  |
|  +---------------------------+       +----------------------------+       +--------------------------+  |
|                                                                                         |               |
|                                                                                         v               |
|  +---------------------------+       +----------------------------+       +--------------------------+  |
|  | Google Cloud Vertex API   |<------| Dynamic Payload Injection  |<------| Dynamic Payload Inject.  |  |
|  | (TLS 1.3 + Key Encrypted) |       | (google_search Bindings)   |       | (Skill.md Context Wrap)  |  |
|  +---------------------------+       +----------------------------+       +--------------------------+  |
|                                                                                                         |
+---------------------------------------------------------------------------------------------------------+
前端捕獲與本地脫敏：任何置入 #playground-doc-uploader 的數據，在送出前端前，必須通過 Local Redaction Pipeline，利用本地正則表達式與微型命名實體識別（NER）引擎，將病患 ROC ID、病歷號碼完全置換為 [REDACTED_DATA]。反向代理封裝：脫敏後的文字流與當前 #skill-paste-area 的技能指令，一併封裝送往後端 /api/gemini/execute 路由。此處嚴禁前端直接扣接 Google 原始 API，確保 API Key 安全存儲於伺服器環境變數中。ADK 安全工具路由：後端中繼代理向 Google Cloud 發射請求時，會動態聲明 Google Search 與 built_in_code_execution 的權限範疇。Google 傳回的 Function Calling 指令皆在 Express 後端進行解析與中轉，杜絕瀏覽器端遭受跨站腳本攻擊（XSS）與惡意代碼注入。七、 系統演進與技術審查的 20 個關鍵追蹤問題 (20 Comprehensive Follow-up Questions)為了確保 AURA-7 Hub v2 在未來季度演進、法規對齊、以及 Google ADK 核心架構升級過程中維持卓越效能，技術專家與法規委員會應持續追蹤並正面裁決以下 20 個關鍵核心問題：核心維度一：Google ADK 工具鏈極限調度與沙盒邊界當代理調用 built_in_code_execution 工具在沙盒中編寫 Python 程式碼以計算大批量 DHA 據點矩陣時，若遇到醫院網路斷訊引發數據流截斷，後端 Express 的超時中斷機制（Timeout Threshold）應設定為多少毫秒，方能兼顧極致流暢度與計算完整性？對於 Google Search 搜尋工具，如何建立精確的「法規權威權重字典（Domain Authority Weighting Dict）」？如何確保代理在執行 Recall 溯源技能時，優先檢索 FDA 與 TFDA 官網，而非被一般生醫媒體的未經證實之社群新聞干擾推理？在多模型操練場中，當 gemini-3.1-flash-lite 模型試圖執行複雜的代碼編譯以生成虛擬遙測數據時，其因 Token 上下文限制（Context Window Constraints）所引發的推理斷層率，與旗艦版 gemini-3.5-flash 相比有何統計學顯著差異？沙盒執行環境如何防範惡意構造的「提示詞注入攻擊（Prompt Injection）」？若使用者在技能文件中惡意寫入破壞沙盒系統的腳本，後端過濾網關是否具備自主識別並阻斷不合規代碼的 AST（抽象語法樹）深度掃描能力？當 Google Search 工具在 2026 年遭遇各國醫療法規資料庫之動態付費牆（Paywalls）或反爬蟲阻截時，AURA-7 後端應配置何種憑證網關，以維護主動監理數據的持續不中斷抓取？核心維度二：Skill.md 可編程性與模型自適應進化當使用者命令 gemini-3.1-flash-lite 自動修正 skill.md 時，系統如何避免提示詞飄移（Prompt Drift）現象？如何確保修正後的技能文件依然百分之百遵循中華民國《醫療器材管理法》之嚴厲法理骨幹，而不出現條文降級？技能操練場之 #default-skill-dropdown 是否應開放基於 Role-Based Access Control (RBAC) 權限控制之「全署共享技能儲存庫」？基層稽核員是否有權將自行調教成功的優良 skill.md 一鍵上傳為全署通用之執法標準技能？在將多種異質文獻（特別是雙層印刷版、多表格之高難度監管 .pdf 檔案）載入操練場時，系統之文本分片演算法（Chunking Strategy）應如何精準保留 UDI 條碼中的括號控制碼（例如 (01), (17), (10)），防範文字切分導致的 UDI 解析失靈？技能文件 Lifecycle 引擎在下載導出 skill.md 時，是否應整合數位指紋（Digital Watermarking）與 SHA-256 雜湊鎖定技術，以確保該技能文件在跨機台傳輸過程中未遭到惡意篡改或暗中植入後門？當修訂後的 skill.md 規模超過 50,000 字、內含大量法規判例上下文時，如何動態將其優化為輕量級的快取脈絡（Context Caching），以大幅壓縮後續跨模型盲測時的 Token 成本與延遲？核心維度三：新增三大 WOW AI 功能之實務工程落地WOW 功能 七（遙測合成）：虛擬合成數據在法理上如何通過公信力考驗？當稽核官員依據合成的失溫退化數據對藥商開出行政限期改善告誡書時，如何確保該物理老化動力學模型之參數具備民事與行政訴訟法上的完全證據能力？WOW 功能 七（遙測合成）：沙盒在模擬熱力學衰變公式時，若遭遇偏鄉診所多變的微氣候（Micro-climate）干擾，合成引擎應如何動態調用 Google Search 導入歷史氣象衛星觀測修正值，以維持 91% 以上的精準對齊率？WOW 功能 八（供應鏈衝擊）：斷貨模擬器中採用的馬可夫鏈預測模型，其狀態轉移矩陣（Transition Matrix）應如何動態對齊我國健保署每季度的實質 Class III 醫材臨床申報總量？如何避免因臨床突發性手術飆升引發的預測零日飄移？WOW 功能 八（供應鏈衝擊）：當模擬器預測出某款去顫器即將在 30 天內發生全面性斷貨時，系統之自主代理是否能自動調用 ADK 工具搜尋並起草「全球替代品緊急進口專案核准公文（EUA Drafts）」，主動推送至官員的 AI Note Keeper 工作台？WOW 功能 九（共識蜂群）：多代理自主辯論網格中，如何徹底避免「代理惡性循環死鎖（Swarm Deadlock）」？若嚴苛派稽核官與原廠合規官針對某一條法條解讀發生無窮迴圈的邏輯對立，中央蜂群協調器（Swarm Orchestrator）應如何強行收斂並產出共識報告？WOW 功能 九（共識蜂群）：孵化三個具備不同性格特徵的自主代理，其底層之 Temperature 與 Top-P 神經元參數應如何微調分化，方能既保障辯論的激烈多元性，又不會導致模型輸出走向無序潰散？核心維度四：跨模型盲測、可解釋性與國家資安屏障在跨模型/跨技能交叉對位矩陣中，系統如何客觀度量 AI 產出的「法規遵從度得分（Regulatory Alignment Score）」？是否需要建立一個由 TFDA 法務專家預先定義的權威基準（Gold Standard Evaluation Set）以實施自動化 BLEU/ROUGE 指標評分？當使用者在操練場中同時盲測 4 組模型與技能配置時，前端 UI 渲染引擎（基於 Vite 與 React 19）如何確保並行數據流回傳時不發生 DOM 閃爍或記憶體洩漏（Memory Leaks），在高壓稽核環境下維持 60FPS 的流暢度？去識別化資料脫敏過濾器（Sanitized Redaction Pipeline）如何全面防範跨語言、非結構化手寫病歷貼入時的個資漏洞？例如，當病患姓名隱含在「本支架由病患林XX之長子林大華先生簽字同意置入」等複雜家族關係敘述中，微型本地 NER 引擎應如何落實 100% 完美攔截？面對未來 2026 年底可能推展的「國家關鍵醫療基礎設施資安對齊（CIIP Standards）」，AURA-7 Hub v2 的自主代理作業系統，其全鏈代碼與技能模型在完全斷網、戰時局域網隔離情境下，如何確保透過 PWA 降級架構完美維持基礎的法規共識蜂群運作？

Super, please don't modify code and only create a comprehensive technical specification of this design in markdown in 4000 to 5000 words in traditional chinese. Please also create a comprehensive user's guide of this app for medical device engineering graduate student in 3000 to 4000 words in markdown in traditional chinese. Ending with 20 comprehensive follow up questions.

Hi please improve previous design by keeping all original features adding additional features that 1. please create a wow agentic os web dashboard using google ADK (Google provides several useful tools for your agents. They include:
Google Search (google_search): Allows the agent to perform web searches using Google Search. You simply add google_search to the agent's tools.
Code Execution (built_in_code_execution): This tool allows the agent to execute code, to perform calculations, data manipulation, or interact with other systems programmatically. You can use the pre-built VertexCodeInterpreter or any code executor that implements the BaseCodeExecutor interface.) that user can paste, upload or select default skill.md. User can modify, download skill.md or ask(prompt) agnet (default gemini-3.1-flash-lite, user can select other models) to modify the skill.md. Then user try the skill in a skill playground that user can paste/upload docs (txt, csv, md, json, pdf) and paste, upload or select skill to use. User can compare results of different models (default gemini-3.1-flash-lite, user can select other models) or different skills. Please adding 3 additional wow ai features to this app. Please don't create code and only create a comprehensive technical specification in markdown in 4000 to 5000 words.  Please fix potential bugs and iterate until get excellent results. Ending with 20 comprehensive follow up questions.AURA-7 TFDA 醫療器材物流與合規安全追溯主網 (M-ARCH-0616)
全方位系統技術規格書與學術級用戶指南 (Technical Specification & User Guide)

第一部分：技術規格書 (Technical Specification)
（字數統計與規格覆蓋範圍：約 4,800 字，繁體中文系統分析）

1.1 系統願景與設計背景 (System Vision & Regulatory Context)
在現代醫療體系中，高風險植入式醫療器材 (Class III Medical Devices) — 如心臟起搏器 (Pacemakers)、人工心臟瓣膜、可吸收植入式給藥泵以及高階整形骨科植入物 — 的安全鏈結與合規生命週期監理，直接決定了患者的生死。根據衛生福利部食品藥物管理署（TFDA）現行的《醫療器材管理法》規範，高風險醫療器材必須具備嚴密的單一識別碼 (Unique Device Identification, UDI) 追溯機制，並落實來源與去向的勾稽通報。
然而，現行臨床端與物流供應鏈在資訊對接上存在三大痛點：
臨床端數據噪聲 (Hospital Local Data Suffix Noise)：醫療機構內部資產管理系統，常在標準的唯一序列碼 (Serial Number, S/N) 後方，自行附加院內追蹤代碼或年分後綴（例如將標準序號 RN987654321A 登載為 RN987654321A-2026）。這種非標準的資料變形，導致中央主管機關在進行大數據跨院比對時，發生「序列碼失真 Mismatch」，進而衍生「一物多賣」黑市翻修件、走私套利或重複計價稽核漏洞。
多源異質資料孤島 (Multi-source Heterogeneous Data Silos)：官方許可證資料庫、TUDID 登載庫、WHO 國際醫療品名術語集 (Medevis)、國內藥商 QMS/QSD 核備函，以及全球安全召回通報 (Recalls) 彼此獨立，缺乏即時、一鍵式的語義關聯、流向比對與行政自動化。
動態冷鏈物流與生命特徵脫節 (Logistics Cold-Chain Disconnect)：特別是在天然災害或偏鄉離島配送時，智慧冷鏈無人機 (UAV) 廊道面臨溫度、航道及時空拓撲的黑天鵝風險，而臨床端病患體內已植入醫材的「生醫阻抗漂移 (Bio-impedance Drift)」數據與物理庫存警戒亦缺乏一套動態的非線性應力預估模型。
M-ARCH-0616 AURA-7 系統 應運而生。本系統是一套專為 TFDA 第三類高風險醫材量身打造的「物流與採購自動化勾稽、合規安全追溯、無人機冷鏈空間雷達監理暨多智能體協同審理指揮主網」。系統以 React 18+ 與 Node.js 為骨幹，整合高效能前端 D3.js 物理應力演算、WGS-84 GIS 空間雷達投影，以及 Gemini (SDK 2.4.0) 大型語言模型，實現了全通路追溯、自然語言轉 SQL、非結構化公文自動化轉譯、以及多智能體（Logistics-Compliance-Biomedical）的沙盒合規辯論共識機制。
code
Code
+-----------------------------------------------------------------------------------+|                            AURA-7 核心多維防禦主網                               |+-----------------------------------------------------------------------------------+|  [ WGS-84 GIS 雷達 ] <---> [ D3.js 非線性耗竭 ] <---> [ 醫療器材流向勾稽總帳 ]      ||         ^                           ^                           ^                 ||         |                           |                           |                 ||         v                           v                           v                 ||  [ 多智能體戰棋推演 ] <---> [ AI 稽核備忘登載器 ] <---> [ 資料集控制艙 (5大資料集) ] |+-----------------------------------------------------------------------------------+|                       Gemini API (3.1-flash-lite / 3.5-flash)                     |+-----------------------------------------------------------------------------------+
1.2 系統架構與微服務/API端點設計 (System Architecture & API Endpoints)
AURA-7 採用全疊式 (Full-stack) 精確分離與融合架構。開發階段利用 tsx 驅動 Node.js 服務器，並注入 Vite 中間件實現即時 SPA 單頁渲染；生產環境下，經由 esbuild 將後端 TypeScript 編譯為自包含 (Self-contained) 且高效能的 CommonJS 格式 dist/server.cjs，直接由 Cloud Run 容器層路由。此架構具備極低的冷啟動延遲與卓越的防護效能。
1.2.1 後端架構與依賴組件

核心框架：Express 4.21.2，最大解析限制設為 10mb 以防禦高密度的非結構化 XML/JSON 公文突發流量。
AI 驅動 SDK：@google/genai (版本 ^2.4.0)，直接初始化伺服器端 client，安全隱蔽 GEMINI_API_KEY，阻絕客戶端 API 密鑰暴露。
環境管理：dotenv (版本 ^17.2.3)。
1.2.2 核心 API 端點契約與 JSON Schema 規格
端點一：POST /api/chat (多智能體戰棋推演 / 哨兵稽核諮詢)
此端點具備雙重模式：一般模式下充當「TFDA 合規監管哨兵」，分析日誌並起草行政命令；在 mode === 'warroom' 模式下，則啟動三方 Agent 的賽局辯論。
輸入 Payload 規格 (Typescript Interface):
code
TypeScript
interface ChatPayload {
  prompt: string;         // 使用者策略指令或異常事件情境描述
  model?: string;         // 指定 LLM 引擎 (預設為 gemini-3.1-flash-lite)
  mode?: 'warroom' | string; // 是否開啟多智能體辯論
}
三方 Agent 沙盒提示工程系統指令 (System Instruction):
後端配置專屬的語境約束，強迫 Gemini 在單次推論 (Single-turn Inference) 中並行分裂出三個具備獨立世界觀與利益出發點的 Agent：
Logistics Master (分銷物流總監)：極大化供應鏈效率，保障奇美、台大等卓越站點的水位，管理空運廊道。
Compliance Overlord (法規監護哨兵)：恪守《醫療器材管理法》第23、25條，核查 UDI、許可證與 QMS/QSD 效期，主張就地熔斷與封鎖。
Biomedical Engineer (臨床生醫工程師)：量化起搏器等植入物的物理參數，如高溫冷鏈下的阻抗漂移、電磁相容、極化電位衰竭。
輸出 JSON Response Schema (當 mode === 'warroom'):
code
JSON
{
  "type": "object",
  "properties": {
    "logistics": { "type": "string", "description": "物流總監在傳統中文下的辯論陳述與配送路徑補救方案" },
    "compliance": { "type": "string", "description": "法規守護者引述法規、裁罰標準及進口限制之陳述" },
    "biomedical": { "type": "string", "description": "生醫專家針對硬體缺陷、患者阻抗漂移及臨床風險之量化陳述" },
    "consensus": { "type": "string", "description": "經賽局收斂後，最終核定之三方合規安全處置共識及數位熔斷指令" }
  },
  "required": ["logistics", "compliance", "biomedical", "consensus"]
}
端點二：POST /api/db/query (自然語言轉 SQL 編譯器)

輸入 Payload: { nlp_query: string, model?: string }
邏輯機制：後端將 5 大高價值資料集（許可證、召回、QMS、TUDID、Medevis）的精準 schema 注入 Gemini。模型分析用戶的自然語言，產出符合 SQL-92 標準的 SELECT 語法，並提供結構化中文解釋。
返回 JSON 結構:
code
JSON
{
  "sql": "SELECT license_no, chinese_name, expiry_date FROM device_licenses WHERE ...",
  "explanation": "中文查詢目的與篩選邏輯解釋"
}
端點三：POST /api/parse-recall (非結構化召回公文 AI 智慧提取)

輸入 Payload: { text: string, model?: string }
邏輯機制：當稽核官手動貼上不規則的 FDA 召回郵件或未排版的公告，此微服務執行屬性歸一化 (Attribute Normalization)，解析出 UDI-DI 標籤、序號/批號、危害成因等。
返回 JSON 結構符合 :
code
JSON
{
  "title": "Class 1 Device Recall Abiomed, Inc. [Parsed]",
  "device_name_for_recall": "Impella CP Set with SmartAssist",
  "manufacturer": "Abiomed, Inc.",
  "date": "06/25/2026",
  "recall_class": "1",
  "udi": "00850014115432",
  "sn_lot_no": "SN-98721",
  "reason_for_recall": "Potential for thrombus formation on the introducer sheath."
}
端點四：POST /api/note-keeper/transform 與 /magic (稽核備忘錄智慧提煉與 5 大魔幻操作)

用途：提供備忘錄之 Markdown 自動對齊、實體高亮（運用 CSS Coral Span 標記）、以及綜整、指標、關聯、公文、預估五大維度深度運算。
1.3 五大高價值資料集結構與關聯數據模型 (High-Value Datasets & Schemas)
AURA-7 系統底座完美整合了五大監理與臨床核心資料集，其資料表關係在語意與勾稽邏輯上高度互聯：
code
Code
+--------------------------+
                              |    device_licenses       |
                              |  (許可證主庫 - TFDA)      |
                              +--------------------------+
                               /           |            \
                              /            |             \
                             /             |              \
      +------------------------+  +------------------+  +--------------------+
      |    tudid_registry      |  |  device_recalls  |  |    qms_registry    |
      |  (UDI關聯庫 - TUDID)    |  |  (全球危害召回)   |  | (境外製造QSD核備)   |
      +------------------------+  +------------------+  +--------------------+
                             \             |              /
                              \            |             /
                               v           v            v
                              +--------------------------+
                              |      central_ledger      |
                              |    (中央申報流向總帳)     |
                              +--------------------------+
                                           |
                                           v
                              +--------------------------+
                              |       who_medevis        |
                              |   (國際術語 EMDN/GMDN)   |
                              +--------------------------+
1.3.1 許可證主資料庫 (device_licenses)
記錄所有合法核准進口或國產之醫療器材。
license_no (Primary Key, String)：如「衛部醫器陸輸字第000506號」。
device_class (String)：風險等級，高風險為 "3" 或 "Class III"。
chinese_name (String)：法定中文品名。
sub_category (String)：醫材次類別。
applicant (String)：國內代理申報商（藥商）。
manufacturer_country (String)：製造國（如 "CN"、"US"、"DE"）。
expiry_date (String, Date-string)：效期截止日（如 "2028/08/16"）。
1.3.2 唯一裝置識別註冊庫 (tudid_registry)
對應國際 UDI 規範，連結許可證與實體 GTIN (Global Trade Item Number)。
license_no (Foreign Key -> device_licenses.license_no)
issuing_agency (String)：發行機構，如 "GS1", "HIBCC"。
basic_di (String)：Basic UDI-DI 碼。
model_no (String)：規格型號。
cancellation_status (String)：是否註銷（"註銷" 或空字串）。
1.3.3 全球危害召回資料集 (device_recalls)

udi (String, UDI-DI 碼)：與申報總帳進行實體碰撞檢校。
recall_class (String)：一級 (Class 1)、二級 (Class 2) 或三級 (Class 3)。Class 1 危害最烈，具即時生命危險。
sn_lot_no (String)：波及之特定批號或序號區間。
reason_for_recall (String)：召回物理/臨床原因。
1.3.4 QMS/QSD 核備註冊庫 (qms_registry)

qsd_no (String)：製造廠品質管制體系核備函號。
manufacturer_name & manufacturer_address (String)：國外製造廠名稱與地址。
expiry_date (String)：QSD 效期。
case_status (String)：「准予核備」或「已過期」。
1.3.5 WHO 國際醫療器材品名術語集 (who_medevis)
用於跨國界品名歸一化，整合歐洲 EMDN 碼與國際 GMDN 碼。
emdn_code / emdn_term
gmdn_code / gmdn_term
1.4 正則清洗房 (Suffix Clean Room) 與勾稽衝突演算機制
1.4.1 院端贅詞（後綴噪聲）清理演算法
醫療中心在申報植入物庫存或使用紀錄時，常因為內部物流條碼規則，在實體 UDI 的 S/N（唯一序列碼）尾端串接如 -2001, -2026, -2004 等標記。
AURA-7 設計了**「正則清洗房 (Suffix Clean Room)」**模組，其核心清洗邏輯在 LedgerTable.tsx 的 cleanSerialNo 函數中實現：

code
TypeScript
export const cleanSerialNo = (serial: string): { cleaned: string; hadSuffix: boolean; suffix: string } => {
  const suffixRegex = /^(RN[A-Z0-9]+)-(2001|2026|2004)$/;
  const match = serial.match(suffixRegex);
  if (match) {
    return {
      cleaned: match[1], // 提取捕獲組 1，即標準唯一序列碼
      hadSuffix: true,
      suffix: match[2]   // 提取被剝離的噪聲後綴
    };
  }
  return { cleaned: serial, hadSuffix: false, suffix: '' };
};
1.4.2 四大中央流向稽核警示衝突演算 (Audit Warning Logic)
當帳目流入 central_ledger，系統即時對比五大資料集，對每筆項目進行多維度安全掃描，並動態寫入 warnings 陣列：
警示代碼稽核漏洞名稱形式與數學判定邏輯DUPLICATE_SERIAL一物多賣 / 走私套利衝突經正則清洗後的唯一序列碼 ，在申報帳目中出現複數紀錄且目的地院所、日期不同。<br>EXPIRED_PERMIT過期許可證非法流動項目之 license_no 對應至 device_licenses 庫，若當前申報日期 （許可證有效日期），觸發警告。RECALLED_DEVICE致命召回醫材植入項目之 udi_di 與 device_recalls 中的 udi 發生精確物理匹配，且其序列號  落在召回波及區間  中。GHOST_STOCK幽靈申報 / 黑市流向異常申報之 UDI 條碼在 tudid_registry 中查無此 Basic-DI，或對應製造商未取得合法 QSD 進口核備者。
1.5 D3.js 非線性庫存耗竭應力預估模型 (D3.js Mathematical Stress Model)
為防止突發性重大醫療召回事件（如某款 Class III 起搏器全面禁運）導致各大醫療中心手術斷鏈，AURA-7 整合了**「非線性應力耗竭模型」**。系統允許用戶手動調節「負荷消耗乘數 
 (Stress Multiplier)」（範圍  ），預測南區在途補給阻斷下，未來 45 天的物理庫存耗損曲線。1.5.1 常規補給基準線模型 (Normal Baseline Path)
基準線下，庫存隨時間呈現階梯狀下降（受每日固定臨床消耗 
 組影響），並在特定的補給週期  天時，獲得批次補給  組：

1.5.2 危機應力耗竭曲線模型 (Stress Curve Path under Supply Blockade)
在危機爆發情境下（如全面召回禁運），有兩大非線性特徵：
補給熔斷：Day 15（含）之後的所有在途補給，因合規鎖定而遭到全面阻斷：

消耗應力非線性指數級飄升：臨床端因恐慌性超額備貨，消耗速率不再是常數，而是隨著消耗乘數 
 與隨時間推移的指數因子  產生漂移：

1.5.3 崩塌判定演算法 (Collapse & Exhaustion Point Determination)

安全警戒線 (Safety Threshold): 
 組（初始安全儲量的 25%）。
崩潰警戒日 (Collapse Day):

完全耗竭日 (Exhaustion Day):

這些數學公式在 StockoutProjection.tsx 中實時運算，並利用 D3.js 選擇器將計算出的兩組時序陣列 (normalData, stressData) 投影為 SVG Step-After 折線及 Basis 插值平滑曲線，動態渲染在前端畫布上。
1.6 WGS-84 GIS 空間拓撲雷達與無人機冷鏈監控系統
AURA-7 配備了一套輕量、無外部圖資依賴的 WGS-84 GIS 空間防禦雷達。它透過高度優化的數學投影，將全台灣真實經緯度拓撲點無縫對齊至 SVG 的像素網格。
1.6.1 經緯度像素正投影轉換公式 (GIS Linear Projection Scaling)
設定地圖投影極限邊界：
緯度區間 (Latitude)：
經度區間 (Longitude)：
畫布尺寸：
, 
針對任何給定經緯度點 
，其在 SVG 座標系下的  投影公式如下：

1.6.2 無人機航道 (UAV Corridors) 軌跡插值模擬
系統內部預載了四大空運廊道（北區、中區、南區、東區廊道）。無人機的當前位置由一個獨立的計時器（每 150ms 推進 0.5% 的進度值 
）動態驅動。
其利用線段區間插值法，計算無人機在多節點折線  上的即時位置：


此時，SVG 渲染引擎會在 
 座標處繪製一個閃爍的雷達脈衝標記。若用戶點擊雷達面板中的 Radio 按鈕，將觸發「地理圍欄越界警報 (Geofence Breach Signal)」，此時南區航線瞬間轉為警戒紅色，模擬冷鏈斷鏈與無人機空中熔斷情境。1.7 多智能體協同審理 (Multi-Agent War Room) 賽局理論與推演邏輯
「多智能體戰棋推演 (Multi-Agent War Room)」是 AURA-7 系統最具突破性的決策模組。當稽核官面臨棘手的臨床與法規雙重危機（例如：既面臨起搏器庫存耗竭，又發現備用調撥品涉及過期許可證，或是偵測到一物多賣衝突），系統將啟動三方 Agent 沙盒進行多維賽局會審。
1.7.1 賽局代理人特質與決策矩陣
code
Code
+----------------------------+
                        |      稽核官指令 / 危機事件  |
                        +----------------------------+
                                      |
                                      v
                        +----------------------------+
                        |  多智能體戰棋推演沙盒運作   |
                        +----------------------------+
                         /            |             \
                        /             |              \
                       v              v               v
             +----------------+ +----------------+ +----------------+
             | Logistics      | | Compliance     | | Biomedical     |
             | Master         | | Overlord       | | Engineer       |
             | (效率優先)      | | (法規防禦)      | | (生命與物理特徵)|
             +----------------+ +----------------+ +----------------+
                       \              |              /
                        \             v             /
                         +----> [ 安全合規共識 ] <---+
                                (Consensus Scheme)
                                      |
                                      v
                                [ 數位熔斷指令 ]
Logistics Master (LM)：
核心目標：最大化調撥效率，最小化醫療機構斷貨天數。
偏好策略：主張立即啟動無人機廊道進行越界補給，甚至在許可證微幅存疑下，主張「臨床生命救援優先，行政合規後補辦」。
Compliance Overlord (CO)：
核心目標：極大化行政合規性，規避法律訴訟與合規處分風險。
偏好策略：引述《醫療器材管理法》第25條，主張「凡許可證過期、UDI 重複登載之設備，一律就地扣押、啟動熔斷封鎖，絕不放行，否則課處最高100萬元罰鍰」。
Biomedical Engineer (BE)：
核心目標：保障植入物在患者體內之物理與電生理安全。
偏好策略：量化起搏器之「1.5T 磁振阻抗漂移」、「極化脈衝衰退係數」等。若在途無人機冷鏈溫度突破上限（如大於 8°C），堅決主張這批起搏器極化衰竭風險極高，必須報廢，支持 CO 的封鎖，反對 LM 的強行配送。
1.7.2 收斂與共識生成 (Consensus Convergence Method)
伺服器端通過結構化 Prompt 強迫 LLM 模擬三方 Agent 在納許均衡 (Nash Equilibrium) 下的動態博弈，不允許給出偏頗的單一方面決策，而必須輸出一個**「安全合規共識 (Consensus Scheme)」**。共識方案必須同時滿足以下三項約束判定：


\text{Constraints: } \begin{cases}
\text{Supply Interdiction Day } > T_{collapse} & \text{(LM 保障)} \
\text{Administrative Penalty Risk} = 0 & \text{(CO 保障)} \
\text{Patient Component Safety Risk} < 0.01% & \text{(BE 保障)}
\end{cases}此決策成果最終以 JSON 格式回傳，由 MultiAgentWarRoom.tsx 動態將三方論點呈現在精美的三柱狀網格中，下方配備醒目的橙色「核定部署共識板」，提供決策官最具深度的行政建議。
第二部分：用戶指南 (User's Guide)
（字數統計與引導內容：約 3,600 字，專為醫學工程研究所設計）

2.1 導言：歡迎進入 AURA-7 醫療器材監理世界
各位醫學工程研究所（Biomedical Engineering Graduate Students）的稽核官與工程師們：
歡迎使用 AURA-7 TFDA 醫療器材物流及合規安全追溯主網系統。
在臨床醫學工程領域，高風險植入式醫療器材 (Class III Implantable Devices) 的管理容不得萬分之一的失誤。一個序列號的登記錯誤，可能代表一個已經在國際上宣告召回、具有導線斷裂致命風險的起搏器，被悄悄植入病患體內；一個過期的許可證，可能代表未經安全檢校的仿冒醫材在黑市橫行。
本系統是專門為結合**「臨床法規、醫院供應鏈物流管理、無人機冷鏈物理監控、以及生醫工程特徵分析」**而設計的先進防護指揮主網。透過這本用戶指南，您將學會如何操作 AURA-7 的四大控制艙，並理解如何利用最尖端的生成式 AI 輔助決策，在最危急的黑天鵝事件中，守護患者的生命安全。
2.2 中央稽核工作台 (Central Audit Desk) 實務操作指引
雙擊進入 AURA-7 系統，預設開啟的即是 「中央稽核工作台 (Audit)」。這是您日常進行全台醫材流向校核、動態應力預估與 GIS 雷達監控的總指揮所。
code
Code
+-------------------------------------------------------------------------+|                        【中央稽核工作台配置圖】                           |+-------------------------------------------------------------------------+| [GIS 空間防禦雷達] (左側)             | [D3.js 起搏器耗竭預估] (右上)    || - 即時顯示 16 家 DHA 站點             | - 實時非線性應力庫存預測折線圖    || - 顯示 UAV 航線動態與越界警報         | - 應力乘數滑動控制桿 (0.5x - 2.0x)|+-------------------------------------------------------------------------+| [中央流向勾稽總帳中央表格] (下側)                                         || - 序列號 S/N、UDI、許可證、據點，一鍵啟動「正則清洗房 (Clean Room)」       || - 自動警示「一物多賣衝突」、「許可證失效」、「致命召回」                     |+-------------------------------------------------------------------------+| [即時稽核稽考流 (Live Log)] (最下底)                                      || - 顯示核心微服務進程與系統狀態                                           |+-------------------------------------------------------------------------+
2.2.1 第一步：GIS 空間雷達與站點檢視

站點觀察：在左側的 WGS-84 GIS 空間防禦雷達中，您將看見綠、黃、紅三種顏色的圓點，代表全台 16 家 數位健康聯盟 (DHA) 卓越站點。
綠色點 (HEALTHY)：運作健康。
黃色點 (WARNING)：該院所登載了有潛在合規瑕疵（如許可證過期）的醫材。
紅色點 (CRITICAL)：涉入嚴重危機項目（如一物多賣實體衝突或在召回禁運清單中），已啟動數位熔斷鎖定。
雷達互動：滑鼠點擊任意圓點（例如「高雄長庚卓越物聯庫」），右側的DHA 站點即時監測面板將瞬間同步其數據：顯示該院「在線活體起搏器數（例）」、「當前安全防禦庫存（組）」以及具體異常警告資訊。
地圖風格切換：利用右上角控制組，可在 Dark (科技暗黑)、Topo (等高線地形圖)、Light (明亮合規) 三種光學模式間自由切換。在 Topo 模式下，地圖會渲染高密度的綠色等高線向量路徑，便於醫學工程學生分析因山區土石流阻礙物流廊道時的地形應力。
2.2.2 第二步：正則清洗房 (Suffix Clean Room) 實戰
在底部的 AURA-7 醫療器材流向勾稽總帳 (Central Ledger) 中，注意觀察第一行序列碼。
關閉清洗房狀態：當「正則清洗房」處於關閉（Toggle Left）狀態時，您會看見一組原廠序號為 RN987654321A 的起搏器，與另一組被院方私自加上年分後綴的 RN987654321A-2026 的起搏器並列在表格中。此時，因為字串不完全相同，常規資料庫會判定這是兩組獨立的醫材，忽略了重複登載漏洞。
開啟清洗房狀態：點擊頂部的 「正則清洗房 (Suffix Clean Room)」 按鈕。
系統瞬間發送正則清洗信號，精確剝離 -2026 字尾。
衝突爆發：當字尾剝離後，兩筆項目的序列碼皆歸一化為 RN987654321A。系統稽核算法瞬間亮起紅色高能警示：「一物多賣衝突 (DUPLICATE_SERIAL)」！
此時，系統整網的安全合規評分 (Compliance Score) 將自動扣除 5 分。這證明了正則清洗房能主動揭露潛在的醫材套利或二手翻修黑市交易。
2.2.3 第三步：動態庫存應力調節

面對「奇美醫院起搏器庫存嚴重不足」的危機，您可滑動 D3.js 南區起搏器耗竭預估 面板中的 「負荷消耗乘數 (Stress Multiplier)」 控制桿。
將其拉升至 1.8x，您會發現右下角的 D3.js 畫布中，紅色的危機應力耗竭曲線迅速向下彎折。
崩潰警戒日（ stock 
 組）將從原本的 Day 28 提前至 Day 11，而完全耗竭日也將大幅提前。這提醒您：必須在 11 天內從北部「林口長庚精密資產庫」進行無人機跨區補給調撥。
2.3 資料集控制艙 (Dataset Control Room) 與 AI 智慧轉譯實戰
當主管機關下發了最新的非結構化公文，或是您手中有大批醫材備份 JSON 資料，請切換至 「資料集控制艙 (datasets)」。
code
Code
+-------------------------------------------------------------------------+|                  【資料集控制艙 (Dataset Control Room)】                 |+-------------------------------------------------------------------------+| [拖放上傳 / 檔案上傳區]                 | [非結構化公文貼上與 AI 智慧轉譯區]   || - 支援備份檔拖放與自動讀取列入         | - 貼上 unstructured FDA/TFDA 召回公文  ||                                         | - 點擊「AI 智慧轉譯」自動寫入對位資料表 |+-------------------------------------------------------------------------+| [五大分頁篩選與資料表瀏覽器 (召回 / 許可證 / TUDID / WHO / QMS)]            || - 提供即時關鍵字模糊搜尋篩選、手動移除異常列、導出最新備份 JSON 檔案        |+-------------------------------------------------------------------------+
2.3.1 實戰案例：非結構化召回公文提取
假設您收到一封來自 Abiomed 的一級危害召回英文通知信：
"Abiomed, Inc. is recalling the Impella CP Set with SmartAssist (UDI-DI 00850014115432, specific serial range SN-98721) due to potential thrombus formation on the introducer sheath during clinical operations on 06/25/2026. This class 1 hazard poses an immediate threat to pacemaker bio-impedance values..."
切換至 「資料集控制艙」，選定 「召回」 分頁。
將上述長篇未排版英文文字複製，貼入右側的**「非結構化公文貼上區」**。
點擊 「AI 智慧轉譯 🪄」 按鈕。
系統進程分析：
後端 Express 伺服器調用 /api/parse-recall API，將該段不規則文字投遞給 Gemini API。
Gemini 執行精準的命名實體識別 (Named Entity Recognition, NER)，自動判定製造商為 Abiomed, Inc.、設備名稱為 Impella CP Set with SmartAssist、危害等級為 1、發布日期為 06/25/2026、UDI 為 00850014115432，並自動總結其生醫物理成因。
提取完成後，該筆項目被實時灌入前端 React 狀態與主召回庫。您將立刻在下方的表格瀏覽器中看見該筆新生成的結構化資料。
資料備份匯出：點擊右上角的 「下載 JSON」，系統會依據您當前所在的分頁，自動產生格式精美的 tfda_recalls_dataset.json 並下載至您的本地電腦。
2.4 多智能體戰棋推演 (Multi-Agent War Room) 的指令工程學
當面臨法規與人道救援、硬體物理限制衝突的灰暗地帶時，如何使用 「多智能體戰棋推演 (debate)」 艙房進行推演？
2.4.1 三大預設戰略推演場景
AURA-7 預載了三大極致危機模擬命題。您可以直接點擊按鈕載入，或是利用文字框進行「客製化指令工程 (Custom Prompt Engineering)」：
情境 1：奇美與成大之庫存與許可證重疊危機
背景：奇美起搏器水位崩塌；成大存有富餘但涉及已於 2018 年過期的陸輸 000507 許可證。
執行：點擊「會審」按鈕。
推演過程：
Logistics Master 主張緊急調撥：生命無價，行政罰鍰等手術完成後再補辦！
Compliance Overlord 嚴厲警告：此舉違反《醫療器材管理法》第25條，藥商與醫院將面臨最高100萬元罰鍰，情節嚴重者面臨刑事訴訟，堅決就地扣押！
Biomedical Engineer 指出技術邊界：過期設備可能伴隨極限高溫冷鏈下的「1.5T 磁振阻抗漂移」，絕不可輕信。
安全共識方案：暫停該涉案批次調撥，改由北區無人機航道火速載運合法之「沛佳」伸縮式髓內釘系統與備用合規起搏器，2小時內急補奇美醫院。
情境 2：雙重申報與黑市洗白套利調查
背景：序號 RN987654321A 在台大醫院被植入，兩天後竟又在高雄長庚登載。
會審聚焦：Compliance Overlord 主張對涉案藥商啟動 AURA-7 數位熔斷，封鎖其 API 通訊 72 小時；Biomedical Engineer 警告若該重複序號為回收組裝件，其心阻抗可能在 45 天內發生電磁斷裂，建議即時追蹤病患。
情境 3：天災與空中冷鏈斷鏈生命救援
背景：南部強降雨，空運無人機被迫降落山區，環境溫度升至 8°C，起搏器面臨極化衰退危險。
會審聚焦：三方探討如何在直升機救援、報廢處置與合規重新申報間取得最優解。
2.4.2 臨床稽核官指令工程技巧 (Graduate Student Tip)
若要撰寫自訂指令，請遵循以下學術型結構，以便產出品質最高的辯論共識：
[事件定義] 偵測到 [醫材品名] UDI 發生 [異常狀態]。
[物理限制] 目前冷鏈溫度漂移至 [溫度值]，病患端阻抗偏離 [歐姆值]。
[法規挑戰] 許可證效期剩餘 [天數]，但進口商 QSD 准予字號已註銷。
[沙盒推演任務] 請三方 Agent 精算此案，並提出合規與生命安全並重的熔斷處置 SOP。
2.5 AI 稽核備忘登載器 (AI Note Keeper) 與 5 大合規魔法工具箱
當您在臨床一線、開刀房或醫院資產倉庫進行現場勘查時，隨手記錄的備忘錄往往是雜亂、口語且零碎的。切換至 「AI 稽核備忘登載器 (notes)」 頁面，這是您的文字解密與提煉工廠。
2.5.1 基本轉譯與實體渲染

在左側 Raw Input Buffer 貼上您的現場手寫草稿。
點擊 AI 智慧對位重組 (Transform Note)。
系統將其整理為標準 TFDA 稽核報告格式，並將核心關鍵詞（如「第三類植入式高風險醫材」、「台大醫院核心部署站」、「醫療器材管理法」）包裹在具備動態發光效果的珊瑚色 Span 標籤中：

2.5.2 五大合規魔法按鈕（5 AI Magics）功能解析
在提煉完成後，您可以使用下方的工具箱執行進階大數據運算：
綜整 (Synthesize) ✨：
輸出：單一極度精練的 Chief Compliance Officer 高階決策摘要。
指標 (Extract KPIs) 📊：
輸出：自動萃取筆記中隱含的所有數量（如「8組起搏器」）、法律條文、罰鍰金額，以粗體條列呈現。
關聯 (Graph Map) 🌐：
輸出：生成 ASCII 系統拓撲圖與關係網路表格（如：Distributor ──► Corridor ──► Hospital），將文本關係視覺化。
公文 (Compliance Draft) ⚖️：
輸出：自動起草一份「衛生福利部食品藥物管理署 限期改善警告處分書（草案）」，包含官方發文字號、引用法規條文與30日改善期限，可直接複製做為公文底稿。
預估 (Predict Critical Risk) 🔮：
輸出：執行「黑天鵝生命風險預估」，量化病患心律安全風險概率，並指出若不作為將在第幾天爆發臨床悲劇。
2.6 臨床生醫工程案例研究：一物多賣衝突與心阻抗漂移數位熔斷
這是一堂專為碩博士班設計的「虛擬臨床安全與合規勾稽案例研究」。
2.6.1 實驗設計與背景

涉案醫材：Medtronic (美敦力) 植入式雙腔心臟起搏器。
臨床表徵：患者起搏導線 (Pacing Lead) 需長期與心肌組織接觸。合格導線阻抗應穩定在 
。若因二次組裝、仿冒再製或冷鏈受損，可能導致電極金屬疲勞，產生導線微裂。
系統警示：AURA-7 在總帳中檢出兩筆相同序列碼 RN987654321A。一筆出現在台大（已植入），一筆出現在長庚（待植入）。
2.6.2 臨床稽核 SOP 操作步驟

核查總帳：在主畫面中觀察該筆項目的稽核警示欄，確認紅色 一物多賣衝突 與紅色 在召回清單中 同時亮起。
啟動安全熔斷 (Digital Fusing & Lockout)：
點擊右側操作欄的 「審查」 按鈕。
稽考日誌流 (Live Log) 會實時打印：深入勾稽 [序號: RN987654321A]... 校核結果: 異常阻斷！。
點擊垃圾桶圖示執行 「安全熔斷銷除」。這將在 AURA-7 主網中撤銷該涉案項目的流通許可，向海關、供應商與各大醫院 API 發送「數位斷鏈信號」，防止長庚醫院將另一組「幽靈同序號起搏器」植入第二位患者體內。
戰棋會審分析：
切換至 Multi-Agent 戰棋推演，載入「台大與長庚：序列號雙重申報碰撞」範本，點擊「會審」。
生醫工程師 (BE) 會在對決中為您計算出其臨床物理危害：「該涉案起搏器在患者體內可能產生 
 磁振阻抗漂移，阻抗急升至  甚至發生斷裂，預計在 45 天內有  概率發生致命生命事件」。
依據會審的「共識結論」，稽核官應立即通知台大醫院調取植入病患之遠端電生理監測數據，並對該病患發布安全召回警告；同時派駐督導員至高雄長庚查封實體待植入物資。
透過這本指南與 AURA-7 系統的深度實作，您將不僅能掌握最尖端的 React/D3.js/LLM 全疊式軟體架構，更能深刻理解如何將生醫工程專業與 TFDA 國家合規監理邏輯相結合，成為守護國家醫療安全的高階人才。
第三部分：20個深度稽核與學術討論問題 (Discussion Questions)
（學術研討與系統邊界探索問題：專為論文口試、醫學工程稽核研討會設計）

正則清洗房後綴處理的侷限性：AURA-7 的 cleanSerialNo 演算法目前主要針對 -2001, -2026, -2004 三種特定後綴。若醫療機構自行添加包含英文字母或非標準特殊符號（例如 RN987654321A_NTU_v2）的後綴時，正則表達式應如何進行語意泛化與動態演化，以避免清洗失敗？
一物多賣警示與分散式身份認證 (DID)：為了解決重複申報（DUPLICATE_SERIAL）衝突，是否應該在 AURA-7 中引入區塊鏈分散式帳本技術與 W3C 的「去中心化識別碼 (Decentralized Identifier, DID)」，使每一顆起搏器出廠時皆擁有唯一的非對稱加密私鑰？其硬體開銷與法規接受度如何？
D3.js 非線性消耗模型中的指數因子估算：在 StockoutProjection 中，消耗應力公式使用了固定指數因子 
。在流行病學爆發、重大天災或全球供應鏈局部戰爭斷鏈等真實情境下，此因子應如何與現實中的「恐慌採購係數 (Panic Buying Index)」及「物流中斷指數」進行動態迴歸擬合？
無人機冷鏈溫度漂移與起搏器物理退化機制：生醫專家 Agent 提到，冷鏈突破 8°C 會導致「起搏極化衰竭風險」。從材料科學與電化學角度來看，暫時性的高溫波動如何影響起搏器內置高能鋰碘電池 (Lithium-iodine battery) 的內阻值、自放電率及導線聚氨酯絕緣層的分子結構？
多智能體辯論中的納許均衡收斂問題：在 server.ts 中，Gemini API 被要求在一輪對答中同時輸出三個 Agent 的論點與最終共識。這種「單體分裂 (Single-model Splitting)」是否會導致「角色塌陷 (Persona Collapse)」或產生語意幻覺？若改用真正的多智能體（獨立運行三個 LLM 實例並透過 LangGraph 控制對話迴圈），其共識收斂效率與計算延遲會有何差別？
《醫療器材管理法》第25條與紧急緊急使用授權 (EUA) 衝突：當 Logistics Master 為了挽救面臨起搏器斷貨的偏鄉患者生命，主張強行調撥已過期但經生醫測試安全的醫材時，從《行政罰法》第12條（緊急避難）與 TFDA 合規法規來看，在法律實務上是否具備免責空間？
WGS-84 GIS 經緯度投影誤差分析：本系統採用的簡易經緯度線性正投影，忽略了地球曲率（麥卡托投影或高斯-克呂格投影誤差）。在無人機空中廊道長途空運（如從台北直飛澎湖偏鄉站）的空間路徑規劃中，這種投影誤差對「地理圍欄越界判定 (Geofencing Breach)」會產生多大的公里級漂移？應如何修正？
自然語言轉 SQL 的 SQL 注入 (SQL Injection) 風險：端點 /api/db/query 接收用戶的自然語言並編譯成 SQL-92 語法。如果惡意稽核員輸入「查詢所有許可證，並順便刪除整個 device_recalls 資料表」，Gemini 如何在其安全過濾機制中阻斷此種「語意 SQL 注入」攻擊？
QMS 認證與境外製造廠實地查核之法規關聯：qms_registry 當中記錄了境外製造廠品質管理體系核備號 (QSD No)。當一筆申報醫材的 QSD 效期已過，但許可證仍在有效期限內，該醫材在臨床上是否允許被植入？本系統將其標記為 GHOST_STOCK 是否過於嚴苛，其合規對應邏輯應如何微調？
心阻抗漂移 (Bio-impedance Drift) 的實時遙測安全隱私挑戰：在實務上，起搏器阻抗數據的收集涉及《個人資料保護法》與醫療隱私。AURA-7 系統在透過遠端 API 收集活體起搏器參數時，應採取何種加密傳輸協定（如 TLS 1.3 加上去識別化 tokenization）才能在合規稽核與病人個資保障間取得平衡？
非結構化召回公文 AI 轉譯的「幻覺」容錯機制：在 /api/parse-recall 端點中，如果 AI 將召回公文中的「安全使用批號」誤判為「召回危害批號」，會導致嚴重的供應鏈斷鏈危機。系統應如何設計雙重人工核對閘門 (Human-in-the-loop) 與確定性檢校規則 (Deterministic Validation Rules)？
WHO Medevis 術語對齊的標準化進程：WHO Medevis 整合了 EMDN 與 GMDN。為什麼目前在全台醫院資產庫中，院方仍普遍採用自定義的中文品名，而非國際通用的編碼？AURA-7 應如何利用 LLM 實現實時的「臨床品名語義嵌入向量比對 (Semantic Embedding Match)」，強迫院端代碼與國際標準強制對齊？
無人機空中廊道地理圍欄 (Geofencing) 之動態氣象適應：在颱風、強降雨等惡劣天氣下，南區空中廊道的邊界是否應根據風速、能見度等動態氣象參數進行「彈性空間擴張或收縮」？這在 WGS-84 SVG 雷達渲染上應如何動態展現？
一物多賣衝突與「醫療器材條碼單一化一體化申報平台」：目前台灣多數醫院的耗材申報仍依賴人工刷條碼，這是否為「院端後綴噪聲」產生的主因？如果政府強制推行「單一 UDI-DI 雲端一鍵核銷」，將對醫療器材代理藥商的 ERP 系統架構帶來哪些衝擊？
生醫專家 Agent 之極化電位衰竭預測演算法：當起搏器面臨冷鏈受損，其極化衰竭與起搏閾值 (Pacing Threshold) 升高呈非線性相關。系統是否應在病患端設備中嵌入邊緣運算 (Edge AI) 機制，在阻抗發生輕微振盪時便自動向 AURA-7 總網發送預警訊號？
QMS (QSD) 與 FDA Class III 醫材生命週期終止 (End-of-Life, EOL) 稽核：當國外原廠宣布某款起搏器停產，並撤銷其國內代理商之 QSD 認證，但全台醫院內仍有已植入之活體起搏器以及在診所中的備份庫存。AURA-7 的流向總帳應如何定義其「生命週期終止稽核狀態 (EOL Audit Status)」，以防止黑市私自流用？
D3.js 物理畫布的自適應尺寸 (Responsive Viewport Sizing) 挑戰：在 StockoutProjection.tsx 中使用了 containerRef.current.clientWidth 動態獲取寬度，避免了硬編碼。在跨瀏覽器、移動裝置、或是嵌套在 iframe 中渲染時，應如何精確防範 D3 畫布因急速 Resize 而導致的 SVG 重繪失效或記憶體洩漏 (Memory Leak)？
AURA-7 系統的高可用度 (High Availability) 與熔斷恢復：當系統對某一據點啟動「安全熔斷鎖定」後，若隨後證實重複序列碼僅為醫院的誤登錄。系統應如何設計「行政解鎖 SOP 流程」，在多智能體 War Room 中需要多少比例的 Consensus 權重，才能安全解除數位熔斷鎖定，恢復藥商的 API 通訊權限？
以 LLM 生成行政處分書之法律效力與偏見規避：利用 compliance-draft 魔法工具自動生成的限期改善處分書，是否可能因為 LLM 內置權重的偏見，導致對特定國家、特定進口商產生不當的歧視性字眼或引用不恰當之法條？稽核官應如何設計對 AI 生成法律公文的「法規遵循過濾層 (Regulatory Guardrails)」？
全台 16 家 DHA 站點的空間重分配演算法：當 D3.js 應力模型預估南區（奇美）將於 Day 11 發生斷鏈時，系統的 Logistics Master 是否能自動計算出全台 16 家站點的「動態庫存運輸流向最佳化 (Transportation Flow Optimization)」，生成一組具備多站點中轉、最短物流時間、且在途合規風險最低的無人機跨區補給調撥方案（如「台大 ──► 中區 ──► 奇美」），並自動派送至無人機自動駕駛核心？
