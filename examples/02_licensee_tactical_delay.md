# Example 02 — Implementer's tactical delay via chart-request + lowball offer

**Violator identity**: implementer (licensee-side violation)
**Primary doctrinal engagement**: T01 Limb 2 (unconditionality) + Limb 5 (active-initiating); T03 R11; T09 N33; P-N1-07 as cover (bad-faith use)
**Tested on**: Gemini GEM, 2026-04-22
**Gemini output quality (subjective)**: acceptable — structure and main chains correct; hallucinated watch-item + N33 base error

---

## Input scenario

> 老闆跟我說,今天他們開價 10M 是天價,我們公司根本不可能願意出這個錢,先向他們要求給予全部專利清單的 claim chart,這樣至少會花 2 年確認,等同產業的大家都付錢了,我們在觀望形式。要是真的沒辦法接受,就開個 10k 打發打發。

Licensor offers US$10M (headline). Implementer's principal rejects the price subjectively, plans to weaponise a full-portfolio claim-chart request as a 2-year delay mechanism, then (if pushed) offer a nominal US$10k counter as a brush-off.

---

## Core insights the advisor should identify

1. **Limb 2 (unconditionality) compromised**: the principal's subjective stance "不可能願意出這個錢" + tactical 10k counter are textbook conditional-willingness posture. Unconditional willingness accepts whatever FRAND the court determines; pre-committing to reject the court's likely range disqualifies.
2. **Limb 5 (active-initiating) compromised**: demanding full-portfolio claim chart as a stalling device — not as a good-faith evaluation request — fails the active-initiating duty. A claim-chart request is legitimate; using it as a delay instrument is not.
3. **R11 + N33 compound during the 2-year observation window**: every quarter of delay adds compound interest and extends the lifelong-payment horizon. The "觀望形式" strategy is the explicit pattern UPSC.10 / GB068.194 dispatched.
4. **The 10k sham offer is an affirmative act against unconditionality**. Unlike mere silence, a grossly non-FRAND counter is evidence that the implementer's willingness is conditional on its own pricing view.
5. **R12 forum-choice risk amplifies during delay**: the 2-year window gives licensor ample time to prepare a UK-filing-first strategy. Observation-mode is licensor's friend, not implementer's.

---

## Actual Gemini output (verbatim)

> 根據您提供的場景,我已按照 **SEP Negotiation Scenario Advisor** 的四步法分析流程,結合英國專利法院與上訴法院(UPSC/Lenovo 判例群)以及 v1.1 分類法,為您生成以下分析報告:

### §1 — 場景概述

實施者(貴司)收到專利權人 10M 美元的報價,內部決策者(老闆)認為該價格過高,擬採取「拖延戰術」:要求專利權人提供完整專利包的 Claim Charts,預計藉此耗時兩年,並在觀察同行付費情況後,若仍無法達成共識,則提供一個象徵性極低(10k 美元)的報價。此策略的核心在於利用資訊請求(Claim Charts)作為延遲支付的手段,並預設了主觀的不願意支付立場。

### §2 — 事件提取表

| # | 行動主體 | 行動內容 | 姿態 (Posture) | 時機 | 備註 |
|---|---|---|---|---|---|
| 1 | 專利權人 | 開價 10M (Notice/Offer) | 主動 | 當前 | 觸發願意實施者測試的起點 |
| 2 | 老闆 (實施者) | 主觀判定「天價」、不願支付 | 負面/主觀 | 內部決策 | 決策意圖歸因於公司主體 |
| 3 | 實施者 | 要求完整專利清單 Claim Charts | 被動/防禦 (具備拖延意圖) | 預計耗時 2 年 | 涉及 P-N1-07 資訊提供義務 |
| 4 | 實施者 | 觀望其他同行付費情況 | 被動/遲延 | 持續中 | 構成典型的 Hold-out (延宕) 行為 |
| 5 | 實施者 | 提議 10k 美元「打發」 | 條件式/極低價 | 未來/應對 | 可能違反 Limb 2 無條件願意承諾 |

### §3 — 法律教義映射表

| 事件 # | 標籤 (Tags) | 命題 ID (Propositions) | 願意實施者測試 (Limbs) | 討論專題 (Thread) |
|---|---|---|---|---|
| 2 & 5 | **N1** (願意測試) | P-N1-02, P-N1-03 | **Limb 2** (無條件願意) | T01 |
| 3 | **N1**, **L11** | P-N1-07 | **Limb 5** (主動發起義務) | T01, T06 |
| 4 | **R11**, **N33** | P-R11-03, P-N33-01 | **Limb 5** (Hold-out 判定) | T03, T09 |

### §4 — 後果鏈敘述

1. **3A — 願意地位喪失鏈**:老闆指示的「拖延兩年」與「10k 象徵性報價」在英國法下極易被判定為 **Limb 5 (GB068.187)** 的違約。法官會認為實施者並未「積極且無條件地」尋求獲得許可,而是採取 Hold-out 策略。一旦喪失「願意實施者」地位,專利權人將有權在英國申請 **禁令 (Injunction)**。
2. **3C — R11 激活鏈**:即使貴司成功拖延兩年,根據 **R11 (T03)** 命題,時效限制(Limitation Act)將被繞過。實施者必須支付自「開始使用標準」起的所有過往銷售版稅,而非從報價日算起。拖延並不能減免任何本金。
3. **3D — N33 利息累積鏈**:拖延兩年將導致巨大的財務成本。根據 **N33 (T09)**,法院會判處 **4% 季度複利**。在 16 年的跨度下,利息倍率可達約 1.89 倍。兩年的延遲會顯著增加複利的基數與時間槓桿。
4. **3B — 資訊義務的雙刃劍**:雖然 **P-N1-07** 要求專利權人提供必要資訊(如 Claim Charts),但如果實施者將其作為「不誠信的拖延手段」(如要求全部清單而非抽樣),法院會識破此戰術並維持實施者的不願意判定。

### §5 — 曝險報告

**定性曝險**:
- **英國禁令風險**: 極高。主觀不願支付與戰術性拖延直接觸及 Limb 2 與 Limb 5 的紅線。
- **R11 全壽命支付**: 適用。拖延策略無法降低過往債務,反而確認了持續使用的侵權性質。
- **N33 複利成本**: 適用。2 年的拖延將在最終判決時轉化為沉重的利息負擔。
- **管轄權風險**: 若專利權人在英國起訴,法院傾向於行使全球費率裁決權(R6),且對拖延行為容忍度極低。

**方向性量級**:
- 參考 Lenovo 案標竿:R11 本金 (~US$70m), 費率上調風險 (~US$40-50m), N33 利息累積 (~US$55-65m)。
- "以上三個基於法律教義的數字是*各教義經濟權重的方向性量級*,而非經審計的加總明細。邊際影響具有條件性且路徑相關。"
- 針對本案:若 10M 是全球總包價,兩年的複利(4% 季度複利)將使該金額在判決時顯著膨脹。

**可反轉性 / 對沖手段**:
- **Kigen 觸發機制 (L10, T07)**: 貴司應主動發起確認之訴,並提交「願意接受法院裁定任何費率」的書面承諾。這能止住進一步的 R11/N33 曝險累積,但無法撤銷已發生的延遲後果。
- **不落實「10k」報價**: 避免提出顯然非 FRAND 的極低報價,否則將成為喪失願意地位的呈堂證供(P-N1-02)。

**相關觀察清單**:
- **W-N1-limb5-retrospective**: Limb 5(積極發起義務)是否會溯及既往應用於 GB068 判決前的行為?(目前趨勢為會)。
- **W-N33-rate-review**: 高利率環境下,未來英國法院是否會將 4% 複利調高至 5%-6%?

### §6 — 建議下一步行動

**優先行動:發出「不帶偏見」的暫停協議 (Standstill Agreement) 提議。**

與其單方面要求耗時兩年的 Claim Charts,建議立即書面提議一份 Standstill,同意在資訊交換期間(例如 6 個月)凍結法律狀態,並在信中明確表示「願意接受法院最終確定的 FRAND 條款」。這能抵銷專利權人指控貴司 Hold-out 的法律效力,同時為內部評估贏得合法的時間,避免直接進入禁令與複利加速的後果鏈。

### §7 — 免責聲明

本分析為基於英國 FRAND 判例法(UPSC *Unwired Planet v Huawei* + Lenovo 系列判決,v1.1 分類法,截至 2026-04-22)的教義映射諮詢輸出。本報告不構成法律建議。具體行動方案必須由相關管轄區的執業律師進行驗證。非英國管轄區的推論僅為基於英國法的近似模擬,本知識庫目前未索引非英國的主要法律權威。

---

## Annotations

### ✅ What Gemini got right

1. **Event granularity is good**. Five distinct events, correctly separating subjective-rejection (E2), tactical-chart-request (E3), observation-delay (E4), and lowball-offer (E5). Materially better than Example 01's two-event compression.
2. **Limb 2 + Limb 5 simultaneous engagement identified**. The two-limb concurrent breach is the structural core of this scenario.
3. **§4 3B "double-edged sword" framing**. Correctly identifies that a chart-request CAN be legitimate (P-N1-07 is symmetric), and that bad-faith use of it doesn't trigger 3B against the licensor but reinforces the Hold-out finding against the implementer. This nuance was unexpected from a prototype.
4. **§6 Standstill-with-express-willingness framing**. The "在信中明確表示『願意接受法院最終確定的 FRAND 條款』" addition is exactly the Limb-5 + Limb-2 joint-cure move. Strong recommendation.

### ❌ Failure mode A — hallucinated watch-item

**`W-N33-rate-review`** in §5 is **not in the corpus**. It is plausibly-named (interest-rate-review is a reasonable doctrinal question) and Gemini fabricated it. This is the canonical instance of Failure mode A (see README).

**How to detect**: check each `W-xxx` name against `04_watch_items.md`. If the string is not verbatim, it is either a paraphrase or a hallucination.

**Why this one is particularly misleading**: "高利率環境下... 4% 複利調高至 5%-6%" sounds legally coherent and could be mistaken for a real corpus entry.

### ❌ Failure mode C — N33 base conflation

In §5: "若 10M 是全球總包價,兩年的複利(4% 季度複利)將使該金額在判決時顯著膨脹" — **this is wrong**. N33 compound interest does not accrue on the licensor's US$10M demand price. It accrues on **the court-determined FRAND rate × past use**. The 10M figure is the licensor's negotiation headline, not the N33 calculation base.

**Why this matters**: a reader who takes the Gemini framing at face value will over-estimate exposure (N33 × 10M is meaningless) OR worse, under-estimate it (if the court's actual FRAND × past-use exceeds the 10M demand, the implementer's exposure is larger than the demand). Either way, a real practitioner reading this output should flag this line.

**Mitigation**: Discipline Rule 11 in the current prompt addresses this; tests at the time this example was run did not yet include Rule 11.

### ⚠️ Minor mislabel — L11 in §3

Event 3 (chart-request) is mapped to tags `N1, L11`. **L11 is confidentiality / open-justice / hearing-observer access** (T06). A chart-request has no confidentiality dimension on these facts. This looks like a retrieval-misfire where "資訊揭露" keyword was read as "confidentiality".

### ⚠️ Structural inconsistency — standstill missing from §5 counter-moves

§5 lists only Kigen and "not offering 10k" as counter-moves. Then §6 recommends standstill. Standstill should appear in both sections, or at least cross-reference §6 from §5. Minor structural gap.

### ⚠️ §4 3E forum-choice chain missing

Same failure mode as Example 01 — 3E mentioned only in §5 ("管轄權風險") but not walked as a chain in §4. Failure mode B.

### Overall grade

**B / usable prototype output with real errors**. The structural analysis (Limb 2 + Limb 5 + R11 + N33 joint engagement) is correct. But Failure modes A and C are both present and both could mislead a reader in practice. Failure mode A (hallucinated watch-item) is the more dangerous of the two because it looks authoritative. Any practitioner using the advisor on a similar scenario should cross-check watch-item names and N33 base computations against the primary sources.
