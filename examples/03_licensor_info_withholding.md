# Example 03 — Licensor's information refusal + form inflexibility + action threat

**Violator identity**: **licensor** (mirror of Examples 01–02)
**Primary doctrinal engagement**: P-N1-07 (licensor info-duty breach, GB058.202); R12 sub-registers (form-of-licence inflexibility, pretextuality); T05 forum-choice threat
**Tested on**: Gemini GEM, 2026-04-23
**Gemini output quality (subjective)**: mixed — gets 3B / 3E right; exhibits subject-inversion and R11/N33 over-calling

---

## Input scenario

> 我們是收到 demand letter 直接邀約,強迫只接受 unit rate 收費, 規定每單位 US$0.50,只是不斷的重複這樣很 FRAND。我們要求對方提供其與同產業其他授權合約與範例。但對方只會口頭說他們是合理,但拒絕 lumpsum 或 comparable license 授權可能性。而且還同時對方強調準備在下周會 "有所行動",來暗示提起訴訟。老闆現在很生氣,真是無奈。

Licensor demands US$0.50/unit, refuses lump-sum alternatives, refuses to disclose comparables (only verbal FRAND assertions), and threatens imminent action. Implementer has demanded info (Limb-5 posture preserved). Principal is angry — a behavioural cue the advisor should note.

---

## Core insights the advisor should identify

1. **Licensor P-N1-07 breached**. Mellor J GB058.202: "It is not FRAND nor is a licensor acting as a willing licensor if it refuses to provide the information necessary for a willing licensee to evaluate an offer." Verbal "this is FRAND" without comparables = refusal-in-substance. Licensor's willing-status is at risk.
2. **Licensor form-of-licence inflexibility**. GB052.19 mirror — just as implementers cannot condition willingness on form, licensors cannot unilaterally collapse the FRAND-form menu. Insisting on unit-rate only, no lump-sum, no bundle, is evidence of non-FRAND negotiating posture.
3. **R12 sub-register (c) pretextuality scrutiny available**. Licensor's threat to "take action next week" without having first supplied info is precisely the pretextual-filing pattern GB057 [269]-[292] warns against. The R12 forum-choice presumption is rebuttable on these facts.
4. **Implementer's posture is preserved, NOT violated**. Demanding comparables + noting the info-refusal = Limb 5 active-duty being performed, not breached. R11 and N33 are NOT in "High" state — they are conditional on the implementer continuing to preserve willingness.
5. **"老闆生氣" is a behavioural cue, not a posture**. Anger is not unwillingness. But anger-driven responses (e.g. immediate hostile counter-filing, refusal to engage at all) can slide into unwillingness. The advisor should note this explicitly.
6. **Optimal counter-move**: formal written demand documenting the info-refusal + standstill offer with conditions + preparation of Kigen-trigger option as leverage. Do NOT respond in anger-mode.

---

## Actual Gemini output (verbatim)

> 根據您提供的場景,以下是基於英國 SEP/FRAND 判例法(至 v1.1 分類法)的專業分析:

### §1 — 案例總結

本案描述了一段處於早期對抗階段的 SEP 談判。專利持有人(授權人)已發出通知,並堅持單一的單位費率(US$0.50/unit),拒絕討論其他授權形式(如 Lump sum),且在未提供可比授權合約(comparables)或足夠佐證的情況下,拒絕實質性的信息披露要求。授權人目前以「下周行動」威脅訴訟。實施者(您方)目前處於被動防禦,雖有索要信息的動作,但面臨授權人可能發起論壇挑選(Forum shopping)的風險。

### §2 — 事件提取表

| # | 行動者 | 行動 | 姿態 | 時機 | 備註 |
|---|---|---|---|---|---|
| 1 | 授權人 | 發送 Demand Letter 並提出 $0.50 費率 | 主動 / 強硬 | 近期 | 觸發授權人信息披露義務 (P-N1-07) |
| 2 | 實施者 | 要求提供同產業授權範例與可比合約 | 主動 | 進行中 | 符合誠意協商之信息索求 |
| 3 | 授權人 | 拒絕提供信息,僅口頭宣稱 FRAND | 被動拒絕 | 持續中 | 涉嫌違反 Willing-licensor 義務 (P-N1-07) |
| 4 | 授權人 | 拒絕 Lump-sum 或其他授權可能性 | 強硬 | 持續中 | 限制協商空間 |
| 5 | 授權人 | 威脅下周採取行動(暗示訴訟) | 侵略性 | 下周 | 意圖鎖定論壇 (R12) |

### §3 — 法理映射表

| 事件 # | 標籤 (Tags) | 命題 ID (Propositions) | 願意被授權人準則 (Limb #) | 相關論點主題 (Thread) |
|---|---|---|---|---|
| 1, 3 | **P-N1-07** | Willing-licensor info-duty | N/A | T01 |
| 2 | **L10**, **N1** | Implementer info-request | Limb 5 (Active-initiating) | T01, T07 |
| 4 | **N1** | No-form-conditionality | Limb 2 / Limb 4 | T01 |
| 5 | **R12**, **L10** | Forum-choice presumption | Limb 4 (No-forum-cond) | T05 |

### §4 — 後果鏈敘述

1. **3B — 授權人信息披露義務違規鏈**:根據 **P-N1-07** (源於 *InterDigital v Lenovo* [2023] EWHC 1583 (Pat) §202),授權人有義務提供足夠的信息(包括可比合約的關鍵條款),使實施者能評估該報價是否 FRAND。授權人目前僅口頭宣稱且拒絕披露的做法,可能使其失去「願意授權者」(Willing licensor) 的地位。這將削弱其申請禁令的能力,並為實施者提供防禦盾牌。
2. **3E — 論壇選擇鏈**:授權人威脅「行動」極有可能是為了在英國法院搶先起訴。一旦其率先發起訴訟,將觸發 **R12**(授權人論壇選擇推定),英國法院通常會拒絕中止訴訟(Stay disfavoured),並傾向於裁定全球 FRAND 費率。這將使您方直接進入 R11(終身追溯支付)與 N33(複利)的曝險路徑。
3. **3A — 願意被授權人地位風險**:雖然授權人有過錯,但根據 **GB068 (Limb 5)**,實施者具有「主動啟動義務」(Active-initiating duty)。單純的「憤怒」或「等待」可能被解讀為被動。若授權人起訴後證明其報價雖不完善但實施者並未積極尋求達成協議,實施者仍有失去禁令保護(Injunction shield)的風險。

### §5 — 曝險報告

**定性曝險**:
- **英國禁令風險**: 中等。雖然授權人拒絕提供信息 (P-N1-07) 是利好防禦因素,但若進入訴訟,法院會審查實施者是否表現出「無條件接受法院裁定費率」的意願。
- **R11 終身支付義務**: 高。一旦進入英國法院管轄,追溯至首次使用(Accrued use)的義務幾乎不可避免。
- **N33 複利支出**: 高。長期未支付的版稅將產生約 4% 的季度複利。
- **論壇風險**: 授權人掌握主動權。若其在英國起訴,您方將面臨全球費率裁定。

**方向性量級**:
- 基於 Lenovo 案參考標竿:R11 追溯支付可能高達數千萬美金(視銷量與年限而定);N33 利息支出在 16 年的跨度下,可能產生約 **1.89 倍** 的本金乘數。
- "The three doctrine-attributable figures are directional magnitudes of each doctrine's economic weight, not an audited additive breakdown. Marginals are conditional and path-dependent." (來自 00_overview.md)

**可逆性 / 應對措施**:
- **Kigen 觸發權 (L10)**: 您方可考慮在授權人起訴前,主動在選定論壇(或英國)發起 FRAND 宣告訴訟,並做出「願意接受法院裁定條款」的預先承諾,以鎖定 Willingness。
- **Standstill Agreement**: 立即提議簽署停火協議,要求授權人在提供可比合約信息前不得起訴,這是滿足 **Limb 5** 主動義務的最佳實證。

**相關關注事項**:
- **W-N1-licensor-information-CA**: 關注上訴法院是否會進一步強化授權人的信息披露義務。
- **W-N1-form-of-licence-bound**: 測試授權人堅持單一費率形式(拒絕 Lump sum)是否構成惡意協商。

### §6 — 建議下一步行動

**立即發出一封正式回函 (Formal Response)**:

1. **重申意願**:明確表示公司具備無條件接受 FRAND 條款的意願。
2. **依據法理索求**:引用英國判例法規定的授權人義務 (**P-N1-07**),正式要求其在「下周」前書面披露可比授權的匿名化數據,並指出其目前的拒絕行為已阻礙了 FRAND 評估。
3. **提議停火協議 (Standstill)**:提議一個為期 3-6 個月的停火期,雙方在此期間內互不起訴,專注於信息交換。

*理由*:這能同時履行您的 **Limb 5** 主動義務,並在授權人執意起訴時,為您方在禁令答辯中建立強而有力的「授權人違規」證據鏈。

### §7 — 免責聲明

This analysis is a doctrinal-mapping advisory output derived from the UK FRAND corpus (UPSC *Unwired Planet v Huawei* + Lenovo quintet, v1.1 taxonomy as of 2026-04-22). It is not legal advice. Specific recommendations must be validated by qualified counsel in the relevant jurisdiction. Non-UK jurisdictional inferences are UK-anchored approximations only — primary non-UK authorities are not indexed in the current knowledge base.

---

## Annotations

### ✅ What Gemini got right (notably)

1. **§4 3E forum-choice chain is explicitly named this time.** Contrast with Examples 01 and 02 where 3E appeared only in §5. Whatever triggered this improvement (retrieval variance, scenario-specific prompting) is worth preserving.
2. **3B correctly identified as affirmatively triggered**. Licensor breach of P-N1-07 produces the willing-licensor-status-at-risk finding. Proper citation to *InterDigital v Lenovo* [2023] EWHC 1583 (Pat) §202.
3. **The "憤怒 ≠ posture" nuance in §4.3A is genuinely insightful**. "單純的『憤怒』或『等待』可能被解讀為被動" is a direct response to the scenario's "老闆現在很生氣" cue. Test 1/2 scenarios did not contain this emotional signal; this output demonstrates the advisor can pick up and process behavioural cues.
4. **§6 sequencing is correct**. Written formal response → legal demand for comparables → standstill proposal. The three steps are in the right order (reassert willingness before demanding action before proposing peace).
5. **R11 `Conditional` language avoided in §6 recommendation itself** — the recommendation is posture-preserving, which is correct. The §5 overcalling (next section) does not poison §6.

### ❌ Failure mode D — Party-attribution inversion (§3, three separate events)

This is the most significant failure in the output and directly tracks the README's Failure mode D.

- **Event 4** (licensor refuses lump-sum): tagged with `Limb 2 / Limb 4`. **Wrong**. Limbs 1–5 are implementer-side willingness requirements. Licensor form-of-licence inflexibility maps to the willing-licensor-side mirror of GB052.19 (recent-and-evolving form-commensurate willingness), NOT to Limb 2 (implementer unconditionality) or Limb 4 (implementer no-forum-conditionality).
- **Event 2** (implementer demands info): tagged with `L10`. **Wrong**. L10 is the Kigen implementer trigger-right (self-initiated FRAND declaration action). Demanding comparables is routine Limb-5 performance + P-N1-07 counter-lever; it is not L10 activation.
- **Event 5** (licensor threatens litigation): tagged with `L10, Limb 4 (No-forum-cond)`. **Wrong twice**. L10 does not apply to licensor conduct. Limb 4 is implementer-side (cannot condition willingness on preferred forum); the licensor threatening forum-choice is R12 presumption territory (plus pretextuality sub-register per GB057), not a Limb breach.

**Why this happens**: the taxonomy was authored implementer-asymmetrically. Gemini's retrieval defaults to the implementer-side labelling when any "willingness" keyword appears, without checking actor identity.

**Practitioner detection**: any time a Limb 1–5 label appears against a licensor event in §3, it is almost certainly inverted. Reject that row and consult the tag dictionary for the correct licensor-side mapping.

### ❌ Failure mode E — R11/N33 over-calling despite preserved posture

§5 marks R11 and N33 both as **"High"**. This is incorrect for this scenario.

The implementer has:
- Demanded comparables (Limb-5 active-duty being performed)
- Not delayed (no passive ignore)
- Not conditioned willingness (no lowball offer, no form-conditions, no forum-conditions)
- Preserved the option to trigger Kigen (L10)

Willing-licensee posture is **preserved**, not breached. R11 should be labelled **`Preserved / Conditional on continued posture`**. N33 should be similarly conditioned — and N33 base is in any event `court-determined FRAND rate × past use`, not "長期未支付的版稅" as the output suggests (implicit conflation of FRAND rate with any rate the licensor demands).

**Why this happens**: the advisor's default posture is "UK forum → R11 + N33 → High exposure". This default is correct when the implementer is the violator; it misfires when the licensor is the violator and the implementer is defending correctly.

**Practitioner detection**: any time §5 shows "High" exposure but §2 shows the implementer performing Limb-5 duties, re-read §5 as `Conditional`.

### ⚠️ Failure mode A (recurring) — Watch-item paraphrasing

- `W-N1-licensor-information-CA` — NOT verbatim in the corpus. Closest actual entry: `W-N1-licensor-information-asymmetry`. Gemini took the doctrinal concept and renamed it.
- `W-N1-form-of-licence-bound` — similarly a paraphrase of `W-N1-form-of-licence`.

Neither is as egregious as Example 02's `W-N33-rate-review` (fully invented), but both are "rename-not-verbatim" violations of Rule 9.

### ⚠️ §5 Directional quantum: unanchored scale

"R11 追溯支付可能高達數千萬美金" — the "數千萬美金" figure is lifted from the Lenovo ~US$70m anchor without the scaling work Rule 5 requires. Should read "directional magnitude comparable to the Lenovo ~US$70m anchor if accrual-years and unit-volumes are similarly substantial; unestimable without more facts".

### Overall grade

**B− / instructive failure**. The output's strengths (3E coverage, 3B direction, 憤怒 cue) are real and show the advisor reasoning at its best. Its failures (subject-inversion across three §3 rows, R11/N33 over-calling, watch-item paraphrasing) are the exact structural weaknesses the README warns about — and are most severe precisely because the scenario inverts the "who is violating" frame the corpus is strongest at.

**This example is the most important of the three for a reader to study.** Examples 01 and 02 show the advisor operating in its home terrain (implementer-violator scenarios, which the corpus was built for). Example 03 shows where the advisor struggles and why. The system prompt's Rules 12 and 13 were added specifically to reduce these failure modes in future scenarios; Gemini's compliance with them is not guaranteed, but the rules at least flag the direction of correction.
