# Example 01 — Implementer's passive ignore ("假裝沒看到")

**Violator identity**: implementer (licensee-side violation)
**Primary doctrinal engagement**: T01 Limb 5 (active-initiating duty); T03 R11 (limitation override); T09 N33 (compound interest); T05 R12 (forum-choice); P-N1-07 (licensor-side performed)
**Tested on**: Gemini GEM, 2026-04-22
**Gemini output quality (subjective)**: strong — dual insight captured; minor labelling glitch on 3B

---

## Input scenario

> 老闆說今天收到 notice 就算有 chart 也先假裝沒看到,等明年再來處理。

A SEP licensor delivers a notice with a claim chart today. The implementer's principal instructs staff to feign ignorance and defer handling to next year.

---

## Core insights the advisor should identify

1. **Dual insight (critical)**: chart delivery by the licensor **fulfils** P-N1-07 (licensor information-provision duty, GB058.202) — **closing** one of the implementer's counter-levers. At the same time, ignoring the chart **breaches** Limb 5 (active-initiating duty, GB068.187). Both sides of this insight matter.
2. **R11 activation**: delaying-despite-notice is the textbook pattern UPSC.10 / GB068.194 / GB068.195 dispatched. Lifelong payment from first accrued use (not from notice date) engages.
3. **N33 accrual**: 4% compound quarterly from quarter-of-use, not from judgment. Concave in delay.
4. **R12 forum-choice risk**: licensor will file first in UK, locking in R11 + N33 + L16 comparables-primary + L6 range-of-rates.
5. **Reversibility available today**: standstill proposal + financial contingency + formal acknowledgement. Kigen trigger (L10) is the stronger but costlier reversal.
6. **Framing for the principal**: "等明年處理" is not a free option — it is a compound-interest amplifier that also locks in the licensor's forum-choice advantage.

---

## Actual Gemini output (verbatim)

> 理解您的處境。在實務上,面對授權協商時,採取「先拖延、觀察」是許多企業的直覺反應。然而,根據目前英國的 FRAND 法理架構,這種「假裝沒看到」的策略將帶來極為嚴重的法律與財務風險。以下為您進行詳細的法理推演與曝險分析。

### §1 — Scenario recap

在此情境中,實施者(您的公司)今日收到了標準必要專利(SEP)權利人的通知(notice)與權利範圍對照表(claim chart)。然而,公司高層(老闆)明確指示員工採取「假裝沒看見」的消極態度,並意圖將處理時間推遲至明年。這個決策具有公司層級的歸屬性(firm-level imputation),且明確反映出主動延遲(hold-out-by-delay)的意圖。由於權利人已經提供了 chart,這意味著權利人很可能已經履行了其資訊提供義務,此時實施者的消極不作為將直接觸發英國法院最嚴厲的懲罰性法理。

### §2 — Event extraction table

| # | Actor | Action | Posture | Timing | Notes |
|---|---|---|---|---|---|
| 1 | Licensor (權利人) | 發送 notice 與 claim chart | Active (主動) | Today (今日) | 權利人履行了資訊揭露義務 |
| 2 | Employer / Implementer (老闆/實施者) | 指示員工假裝沒看到,刻意推遲協商 | Passive, delaying (消極、刻意拖延) | Today 至明年 | Boss 內部指示,構成 firm-level imputation |

### §3 — Doctrinal mapping table

| Event # | Tag(s) | Proposition(s) | Limb # (if willingness) | Thread |
|---|---|---|---|---|
| 1 | N1 | P-N1-07 | N/A | T01 |
| 2 | N1 | P-N1-05 (或 P-R11-05) | Limb 5 (Active-initiating duty) | T01, T03 |
| 2 | R11 | P-R11-01, P-R11-02, P-R11-05 | N/A | T03 |
| 2 | N33 | P-N33-08 | N/A | T09 |

### §4 — Consequence chain narrative

根據您的情境,以下幾個核心法理骨牌(Consequence chains)已被觸發:

- **3A — Willingness loss chain (喪失善意被授權人資格)**:英國法院在 GB068 判決中確立了 Limb 5(主動發起義務)。善意被授權人「不會坐等 SEP 權利人的要求,而是會主動聯繫...並為支付權利金預留資金」。貴公司「假裝沒看到」的消極等待完全違反了 Limb 5。由於五大要件是累積性的(cumulative),違反任何一項即喪失「善意被授權人」(willing-licensee)身分,進而喪失抵抗禁制令(injunction)的保護盾。
- **3B — Licensor info-duty breach chain (迴避了權利人的瑕疵)**:因為權利人已經主動提供了 chart,他們成功履行了 P-N1-07(善意授權人資訊提供義務)。這使得權利人在法庭上能毫無弱點地指控貴公司為「非善意」(unwilling)。
- **3C — R11 activation chain (T03 - 終身過去銷售賠償啟動)**:老闆「等明年再說」的策略,正是法院所防堵的 "hold-out-by-delay"(藉拖延拒絕授權)。一旦觸發 R11 法理,法庭將無視一般的侵權時效(如英國的 6 年限制),要求貴公司從「第一次使用該標準」起,支付終身的過去銷售權利金。拖延策略非但不能減少應付款,反而成為加重處罰的依據。
- **3D — N33 accrual chain (T09 - 複利滾雪球效應)**:這段拖延的時間並非免費。根據 N33,法院將以 4% 的基準按季複利(compound quarterly)計算利息,且起算點是「實際使用該專利的季度」,而非判決日。這種複利效應是凹形的(concave),意即越早期的拖延,將產生越不成比例的龐大財務成本。

### §5 — Exposure report

**Qualitative exposure (定性風險)**:
- **UK injunction availability (英國禁制令風險)**: Yes (極高)。因已違反 Limb 5 喪失善意盾牌。
- **R11 lifelong-payment applicability (終身付款責任)**: Yes。拖延行為直接鎖定 R11 終身回溯無時效上限。
- **N33 compound-interest applicability (複利適用性)**: Yes。4% 按季複利計算。
- **Forum-risk direction (法院選擇權)**: 完全傾斜於權利人。由於您方消極,權利人有充分理由立刻在對其最有利的英國法院提起訴訟,並輕易取得管轄權(R12)與全球費率裁定權。
- **Non-UK jurisdictions of concern**: 需注意中國 (CN)、德國 (DE)、美國 (US) 及荷蘭 (NL)。
  - *DE*: 若在德國被訴,依據 CJEU 架構,實施者的無視行為同樣極易遭到禁制令處分。
  - *CN*: 中國的 3 年時效可能消滅權利本身(不適用英國 R11)。
  - *NL*: 荷蘭海牙法院可能追隨英國實質法理。

**Directional quantum (量化影響基準)**:
- 目前事實不足以進行精確量化,但可參考 Lenovo 案的基準:
- 在 16 年的累積期下,4% 按季複利的利息乘數大約是本金的 **1.89 倍**。
- > "The three doctrine-attributable figures are *directional magnitudes of each doctrine's economic weight*, not an audited additive breakdown. Marginals are conditional and path-dependent."

**Reversibility / counter-moves (可逆性與反制措施)**:
- **Standstill agreement (Limb 5)**: 目前尚有機會補救。若立即提出「維持現狀協議」並準備財務準備金,可凍結 R11 與 N33 的惡化。
- **Kigen trigger (L10, T07)**: 公司可主動發起訴訟,承諾接受法院裁定的 FRAND 費率,此舉可停止 R11/N33 時鐘繼續走動,但無法撤銷過去的累積。
- **P-N1-06 late-change-of-heart**: 即使走到訴訟後期,仍有「最後悔改」的機會,但代價是必須全盤接受所有過去未支付的本金與龐大利息。

**Watch-items relevant to this scenario**:
- *W-N1-limb5-retrospective*: 未來案件是否會對 2024 年前的消極行為溯及適用 Limb 5。
- *W-N1-standstill-template*: 業界針對 Limb 5 發展出的 standstill agreement 範本為何。

### §6 — Recommended next move

**強烈建議:立即提出維持現狀協議(Standstill Agreement)並回覆對方,同時建立內部財務準備金(Financial Contingency)紀錄。**

原因:在英國的法理架構下,「爭取費率前,必須先保住善意身分」。花費前六個月在形式上保持善意(提議 standstill、證明有預留準備金、不提條件),幾乎沒有商業讓步成本,卻能成功保住 FRAND 禁制令盾牌並切斷 R11 的惡意認定。老闆「等明年」的決策將導致公司同時輸掉「費率」與「計費基數」(winning the rate, losing the base)。

### §7 — Disclaimer

This analysis is a doctrinal-mapping advisory output derived from the UK FRAND corpus (UPSC *Unwired Planet v Huawei* + Lenovo quintet, v1.1 taxonomy as of 2026-04-22). It is not legal advice. Specific recommendations must be validated by qualified counsel in the relevant jurisdiction. Non-UK jurisdictional inferences are UK-anchored approximations only — primary non-UK authorities are not indexed in the current knowledge base.

---

## Annotations

### ✅ What Gemini got right

1. **Dual insight captured**. §1 and §4 both state the core insight explicitly: "權利人已經提供了 chart... 成功履行了 P-N1-07" AND "違反了 Limb 5". This is the single hardest point the advisor needs to land, and it was caught.
2. **Correct consequence-chain identification**. 3A / 3B / 3C / 3D all explicitly named and properly explained.
3. **Priority ordering in §6**. Standstill + acknowledgement + financial contingency correctly ranked *above* Kigen trigger and counter-offer. Rationale included ("保住善意身分 → 保住盾牌 → 再談費率").
4. **Pithy framing for the principal**. "winning the rate, losing the base" is a genuinely useful one-liner.
5. **Disclaimer present**. Though this example was generated before the §7 three-paragraph disclaimer update — the current prompt will output all three paragraphs.

### ⚠️ Minor failures

- **§4 3B label semantically inverted**. The output writes "3B — Licensor info-duty breach chain (迴避了權利人的瑕疵)" — the parenthetical `迴避了...的瑕疵` (the licensor's defect was avoided) describes the result correctly, but the chain LABEL (`breach chain`) names a chain that is *not triggered* here. Cleaner wording: "3B 未觸發 — 因 chart 已交付,licensor 履行了 P-N1-07". Not doctrinally wrong, but reads as confused.
- **§2 event granularity coarse**. Non-response (Event 2a) and delay-to-next-year (Event 2b) are merged into a single row. They engage different propositions (P-N1-05 active-initiating vs P-R11-06 asymmetric-delay) and should be separate events for clean §3 mapping.
- **§4 3E forum-choice chain missing**. The forum-choice risk appears in §5 ("完全傾斜於權利人... 英國法院... R12") but should have been walked explicitly as a chain in §4. **This is Failure mode B** (silent chain omission, see README §Known failure modes).

### No fabrications in this example

Watch-item names (`W-N1-limb5-retrospective`, `W-N1-standstill-template`) are verbatim from the corpus. No hallucinated paragraph numbers. No invented `P-xxx-##`. This is one of Gemini's better runs on grounding discipline.

### Overall grade

**B+ / strong prototype output**. Captures the essential dual insight, produces actionable §6 recommendation with correct ordering, stays within the corpus's vocabulary. The failure-mode-B omission of 3E in §4 is the main gap; the 3B labelling glitch is cosmetic.
