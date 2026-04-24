# SEP Negotiation Scenario Advisor — Prototype

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg) ![Status: Prototype](https://img.shields.io/badge/Status-Prototype-orange.svg) ![Last updated: 2026-04](https://img.shields.io/badge/Last%20updated-2026--04-blue.svg)

**Language / 語言**：[English](#english) · [繁體中文](#繁體中文)

---

<a id="english"></a>

## English

A research prototype that takes a Standard-Essential-Patent (SEP) licensing negotiation scenario in natural language and produces a structured analysis grounded in UK FRAND case-law (UPSC *Unwired Planet v Huawei* + the Lenovo quintet, 2020–2024).

The advisor routes a free-text scenario through a four-step pipeline — event extraction → doctrinal mapping → consequence chain → exposure synthesis — and returns which FRAND elements are engaged, what penalties (injunction, R11 lifelong payment, N33 compound interest, forum risk) follow, and what counter-moves are still available.

---

### ⚠️ Three things to know before reading further

#### 1. This is a research prototype

The advisor was designed, tested, and refined natively on **Claude (Opus 4.7)**. Two public-platform ports are now documented: a **Gemini Gem** build (`GEM_System_Prompt.md`, ~full-length) and a **ChatGPT 5.5** build (`ChatGPT_System_Prompt.md`, ≤8k-token orchestrator variant authored on the day ChatGPT 5.5 launched). Both are **portability demos** — they prove the methodology travels across platforms, but operate at materially reduced fidelity compared with the Claude-native original (weaker RAG grounding, occasional thinking-time instability, looser adherence to the hard constraints in the system prompt). The three examples in `examples/` deliberately include Gemini's mistakes with annotations, so readers can calibrate what "prototype" actually means.

#### 2. The factor codes are a personal research apparatus

The **L / R / N-D / N-P / N-M / N-F** factor codes, **P-xxx-##** proposition IDs, **T01–T09** thread IDs, the decomposition conventions, and the watch-item taxonomy are **the author's private analytical shorthand**, developed while tagging 18 UK FRAND judgments under a v1.1 taxonomy. They are not industry-standard, not academically published, and not intended for third-party adoption. External readers should **look through** the notation to the cited primary authorities (UPSC, GB052, GB054, GB058, GB059, GB068) for the actual legal content — the codes are structural plumbing, not doctrine.

#### 3. Not legal advice

Nothing in this repo constitutes legal advice. The doctrinal content is derived from public UK judgments but organised through a personal research taxonomy with known limitations (see §Known failure modes). Counsel is required for any actual licensing matter.

---

### What the advisor does

**Input** (Chinese or English, free text):
> 老闆說今天收到 notice 就算有 chart 也先假裝沒看到，等明年再來處理。

**Output structure**:
- **§1** Scenario recap
- **§2** Event extraction (actor / action / posture / timing)
- **§3** Doctrinal mapping (tags / proposition IDs / willingness-limb / thread)
- **§4** Consequence chain (3A willingness loss / 3B licensor info-duty breach / 3C R11 activation / 3D N33 accrual / 3E forum-choice / 3F counter-moves / 3G jurisdictional routing)
- **§5** Exposure report (qualitative injunction-risk, R11, N33, forum-risk; directional quantum with caveat; reversibility; relevant watch-items)
- **§6** Recommended next move
- **§7** Disclaimer (three-paragraph: prototype / personal-research / not legal advice)

See `examples/` for three fully-worked scenarios with actual Gemini output and annotations.

---

### Architecture

```
sep-negotiation-advisor/
├── README.md                ← this file
├── GEM_System_Prompt.md     ← Gemini Gem port (paste into Gem instructions)
├── ChatGPT_System_Prompt.md ← ChatGPT 5.5 port (≤8k orchestrator variant; paste into a custom GPT's instructions)
├── examples/
│   ├── 01_licensee_passive_ignore.md       ← implementer ignores notice + chart
│   ├── 02_licensee_tactical_delay.md       ← implementer demands full chart to stall
│   └── 03_licensor_info_withholding.md     ← licensor refuses comparables
└── LICENSE                  ← (see bottom of this README)
```

The repository deliberately **does not include the knowledge-base corpus**. See §Building your own RAG below for why and how to assemble one.

---

### Building your own RAG

The advisor depends on a retrieval-augmented knowledge base covering UK FRAND doctrine. **The author does not ship a pre-built corpus** for three reasons:

1. **Prototype integrity.** A user who downloads a turnkey corpus will treat this as a finished product. A user who has to build their own corpus necessarily reads the underlying authorities — which is the entire point.
2. **Research-work separation.** The author's Lenovo-campaign doctrinal synthesis is a multi-week manual work product. Publishing it as ready-to-use RAG converts personal research into freely-scrapable content.
3. **Doctrinal drift.** UK FRAND doctrine continues to evolve (CA and UKSC cases are in the pipeline). A shipped corpus ages immediately; a methodology to assemble one does not.

#### What the knowledge base needs to contain

A functional RAG for this advisor needs roughly the following doctrinal material, organised so each doctrinal vector is addressable:

**Core taxonomy layer** (1-2 documents):
- A tag dictionary enumerating the L / R / N-D / N-P / N-M / N-F factors, each with a clear operational definition and at least one paragraph anchor into a pilot case.
- A consolidation / aggregation memo recording how the taxonomy evolved — especially promotions and broadenings. Without this, the retriever will miss v1.1 updates to v1.0 entries.

**Doctrinal thread layer** (one per doctrine, ~9 documents for UK coverage):
- **T01 Willing-licensee cumulative test** — the five limbs (scope-determination / unconditionality / no-temporal-carve-out / no-forum-conditionality / active-initiating duty), with UPSC.158, GB058.538, GB058.540, GB054.13(viii), GB068.187 as anchors; plus the licensor-side information-provision duty (GB058.202).
- **T02 Non-discrimination (three registers)** — rate-equivalence / volume-discount / scope-differentiation (and the open assignment-continuity register); hard-edged MFN rejected at UPSC.114 and GB068.231/276.
- **T03 Limitation override (R11)** — the hybrid-action theory (GB058.533), perverse-incentive rationale (GB058.529), the eight CA-ratified strands at GB068 ¶186 onward; Nugee LJ reluctant concurrence (GB068.289-290).
- **T04 Comparables methodology (L16)** — primacy at GB058.16/945, Cimetidine clean-comparable restoration at GB055.90-115, two-stage valuation primacy at GB068.251-281.
- **T05 Forum-choice presumption (R12) & stay** — Nokia v Oppo [269]; GB054.87 foundation; GB057 [269]-[292] pretextuality; GB100 ¶72 cabin; stay slender-benefit (Conversant line).
- **T06 Confidentiality / open justice** — L2 and L11 registers; hearing-observer access (GB052 ¶3); rates-publication considerations (GB059).
- **T07 Kigen implementer trigger-right (L10)** — pre-commitment requirement; clock-stop vs clock-unwind distinction; applicability to portfolio licences.
- **T08 Two-stage valuation + appellate deference** — L6 range-of-rates; Lifestyle-Equities deference threshold; internal-consistency appellate pathway; bidirectional risk (Lenovo $0.175 → $0.225 uplift).
- **T09 FRAND compound interest (N33)** — 4% compound quarterly from quarter-of-use; Lenovo ~1.89× multiplier on 16-year principal; concavity in delay.

**Aggregation layer** (2-4 documents):
- **Practitioner matrix** — licensee and licensor checklists by lifecycle stage. This is the shape the advisor's §5 and §6 output most closely resembles.
- **Jurisdictional divergence** — UK-anchored inferences for DE / CN / US / NL / JP / EU transplant.
- **Watch-items** — open doctrinal questions that future cases may resolve. The advisor cites these by name in §5, so verbatim `W-xxx` titles matter.

**Anti-corpus** (what NOT to include):
- **Per-case retrospective tagging files.** These are the primary source material from which the threads were distilled. Including them alongside threads double-counts the content and causes the retriever to over-weight individual cases. Keep them out of the advisor's knowledge base even if you have them.
- **Taxonomy-maintenance methodology skills.** The advisor is a taxonomy *consumer*. A methodology-for-curating-the-taxonomy document will bleed curator-voice into scenario outputs.
- **Raw judgment text.** Too low-density. If you need paragraph-level accuracy, add specific judgment excerpts only where a thread cites them.

#### Deployment A — Gemini Gem

1. Author the knowledge base documents described above (in `.txt` or Google Doc format — Gemini does not accept `.md` uploads as of this writing).
2. Consolidate to **≤10 files** — the Gem platform enforces a file-count limit. Logical groupings: tag-dictionary + aggregation-memo standalone; aggregation layer (overview + practitioner matrix + jurisdictional divergence + watch-items) merged; threads merged pairwise by thematic coupling (e.g. T04+T08 rate-setting methodology, T05+T07 forum-and-trigger procedure).
3. Create a new Gem in Gemini. Paste the block between `=== BEGIN GEM PROMPT ===` and `=== END GEM PROMPT ===` from `GEM_System_Prompt.md` into the instructions field.
4. Upload the knowledge base files as the Gem's knowledge.
5. Test with the `examples/01_licensee_passive_ignore.md` scenario and verify the output identifies: Limb-5 breach, chart-delivery fulfilling P-N1-07 (licensor side performed), R11 activation, N33 accrual, R12 forum-choice risk. If any of these is missed or substantially garbled, retrieval is not grounding correctly.

#### Deployment B — ChatGPT 5.5 (custom GPT)

Authored on the day ChatGPT 5.5 launched. The prompt (`ChatGPT_System_Prompt.md`) is a condensed **≤8k-token orchestrator** that preserves the Step 0–5 pipeline (gate → events → doctrine map → trigger/threshold/consequence → consequence modules A–H → exposure report) and the hard rules, trimmed to fit ChatGPT's custom-GPT instruction budget.

1. Author / consolidate the knowledge base as above. The ChatGPT port references ten specific corpus filenames (`01_tag_dictionary.txt`, `02_v1.1_aggregation_memo.txt`, `03_aggregation_layer.txt`, `04_T01_willing_licensee.txt`, `05_T02_non_discrimination.txt`, `06_T03_R11_limitation.txt`, `07_T04_T08_rate_setting.txt`, `08_T05_T07_forum_and_trigger.txt`, `09_T06_confidentiality.txt`, `10_T09_N33_compound_interest.txt`) — either match these names or edit the `## RAG source of truth` block to your filenames.
2. Create a new custom GPT at chatgpt.com. Paste the entire `ChatGPT_System_Prompt.md` contents into the Instructions field.
3. Upload the ten knowledge-base files into the GPT's Knowledge section.
4. Enable the `File search` tool; disable image generation and code interpreter unless you have a reason to keep them.
5. Smoke-test with `examples/01_licensee_passive_ignore.md` (same success criteria as above).

Platform differences worth knowing: ChatGPT 5.5 retrieves corpus filenames aggressively (hence the explicit per-file mapping) and is stricter than Gemini about separating `doctrine engaged` from `outcome established` — the ≤8k port leans into that by naming Step 3 `trigger / threshold / consequence` explicitly. Failure modes A–E from §Known failure modes still apply in principle; the ChatGPT port has not yet been regression-tested against the three example scenarios in this repo.

#### Deployment C — Native Claude

Operator-specific and not documented here.

---

### Known failure modes

These are real failure modes observed across three Gemini test scenarios (all documented in `examples/`). Even with the hard constraints enumerated in the system prompt (rules 1–13), Gemini's baseline generative tendency produces these mistakes at non-trivial frequency. Claude-native deployment reduces but may not eliminate them.

#### A. Hallucinated watch-items

Gemini will invent plausibly-named `W-xxx` watch-items when the scenario touches a live doctrinal area but no exactly-matching corpus entry is retrievable. Example from test 2: `W-N33-rate-review` (not in the corpus). Example from test 3: `W-N1-licensor-information-CA` (paraphrase of `W-N1-licensor-information-asymmetry`). **Mitigation**: Discipline Rule 9 — any `W-xxx` cited must be a verbatim title from the watch-items document. Gemini complies inconsistently; readers should spot-check watch-item names against the corpus.

#### B. §4 consequence-chain silent omission

Forum-choice (3E) is the most frequently omitted chain, especially when the scenario involves implementer-side violations and the retriever's attention is saturated by 3A/3C/3D. **Mitigation**: Discipline Rule 10 — explicit `✓ triggered` / `— not triggered` marking for all seven chains in §4. Tests 1 and 2 under Gemini both failed this check (3E appeared only in §5); test 3 corrected after the rule was emphasised.

#### C. N33 base conflation

Gemini occasionally computes N33 compound interest against the licensor's demand price, the implementer's counter-offer, or any other negotiation figure present in the scenario. Correct base is **court-determined FRAND rate × past use**. Example from test 2: "若 10M 是全球總包價,兩年的複利... 將使該金額在判決時顯著膨脹" — the 10M is the licensor's demand, not the N33 base. **Mitigation**: Discipline Rule 11.

#### D. Party-attribution inversion

The taxonomy is structurally asymmetric — Limbs 1–5 are implementer-side willingness requirements. Gemini, when processing a licensor-violator scenario, tends to apply Limb labels to licensor conduct (e.g. labelling a licensor's form-of-licence inflexibility as "Limb 2 / Limb 4" breach — this is inversion). Example: test 3 §3 mapped three separate licensor/implementer events with inverted or mislabelled Limbs. **Mitigation**: Discipline Rule 12.

#### E. R11/N33 over-calling under maintained-posture implementer

When the implementer is the violator, R11 and N33 correctly escalate. When the licensor is the violator and the implementer is maintaining willingness posture (demanding info, proposing standstill, considering Kigen), R11/N33 should be `Preserved / Conditional`, not `High`. Gemini defaults to `High` because the UK architecture is implementer-risk-weighted in the corpus. Example: test 3 §5 labelled both R11 and N33 as `High` despite implementer actively demanding comparables (Limb 5 maintained). **Mitigation**: Discipline Rule 13.

#### Pervasive: implementer-asymmetric default

Failure modes D and E share a root cause. The underlying taxonomy was authored from the implementer-protection analytical angle (the Lenovo campaign was an implementer-side doctrinal reconstruction). Scenarios that invert the violator identity cause the advisor's default pattern to misfire. The v1.1 additions (L16, R12) partially address this but do not complete the symmetric version. Users should mentally prepare to cross-check any licensor-violator output against the L/R asymmetry note in the tag dictionary.

---

### Design rationale (short)

Fuller rationale is elided; key decisions:

- **Why a four-step pipeline?** Structural coverage is the primary defence against single-limb tunnel vision. A scenario that mentions "chart" may engage Limb 5 (licensee side), P-N1-07 (licensor side), R11, N33, R12, and L10 simultaneously; a free-form reasoning path will usually surface only two or three. The pipeline forces all seven consequence chains to be considered.

- **Why forbid paragraph-number fabrication?** The underlying judgments are real and paragraph numbers are public. A fabricated citation is both verifiable-as-false and more harmful than no citation at all. The advisor cites proposition IDs (`P-N1-05`) as grounded fallback when a specific paragraph number cannot be retrieved.

- **Why the implementer-asymmetric taxonomy?** The corpus was written for the implementer-protection angle of UK FRAND. A symmetric version is a future project. The current version is honest about its asymmetry (see §Known failure modes D/E) rather than pretending to neutrality it does not have.

- **Why not ship the corpus?** See §Building your own RAG above.

- **Why accept the Gemini / ChatGPT deployments' reduced fidelity?** Gemini Gem and ChatGPT custom GPTs are the most frictionless public-facing deployments for a prototype. Claude has better grounding but no comparable consumer-facing share primitive. The tradeoff is deliberate: portability and demo accessibility over output quality. The examples/ annotations document what was lost on Gemini; the ChatGPT 5.5 port is newer and has not yet been annotated against the same regression scenarios.

---

### Examples

| File | Scenario | What it illustrates |
|---|---|---|
| [`examples/01_licensee_passive_ignore.md`](examples/01_licensee_passive_ignore.md) | Implementer's employer instructs staff to ignore a received chart and delay response to next year | The canonical implementer-side violation — Limb 5 breach + R11 activation + N33 accrual + forum-choice risk. Also demonstrates the **dual insight** that chart delivery fulfils P-N1-07 (licensor-side performed) while ignoring it breaches Limb 5 (implementer side). |
| [`examples/02_licensee_tactical_delay.md`](examples/02_licensee_tactical_delay.md) | Implementer's employer treats licensor's offer as too high, plans to request full claim charts to stall two years, then offer a lowball settlement | Tactical delay + sham counter-offer. Triggers Limb 2 (unconditionality) and Limb 5 concurrently. Demonstrates Failure mode A (hallucinated watch-item) and Failure mode C (N33 base conflation). |
| [`examples/03_licensor_info_withholding.md`](examples/03_licensor_info_withholding.md) | Licensor demands a unit rate, refuses alternative forms, refuses to disclose comparables, threatens imminent action. Implementer angry | The canonical licensor-side violation — P-N1-07 breach + R12 pretextuality risk. Demonstrates Failure mode D (party-attribution inversion) and Failure mode E (R11/N33 over-calling under maintained-posture implementer). Also shows Gemini's best moment — capturing the "憤怒 ≠ posture" nuance. |

Each example contains: the input scenario as actually tested, the Gemini output verbatim, and inline annotations pointing to each failure mode (or success) observed.

---

### License

The system prompt and the methodology described in this repository are released under the **MIT License** (see `LICENSE`). The author retains copyright to the personal research apparatus described in §2 of the three-things-to-know section; independent re-use of the L/R/N codes or the proposition-ID convention is discouraged but not prohibited (they are not legally protected, only personally curated).

Actual case-law text and paragraph numbers referenced throughout are public judicial records and not subject to this repository's license.

---

<a id="繁體中文"></a>

## 繁體中文

一個研究原型（research prototype）：輸入一段自然語言描述的標準必要專利（SEP）授權談判場景，輸出一份基於英國 FRAND 判例法（UPSC *Unwired Planet v Huawei* 與 Lenovo 五件案——GB052 / GB054 / GB058 / GB059 / GB068，2020–2024）的結構化分析。

顧問將自由文字場景導入一條四步驟管線：事件萃取 → 法理映射 → 後果鏈 → 風險曝露綜合，並輸出：哪些 FRAND 元素被觸發、可能產生哪些後果（禁制令、R11 終身回溯付款、N33 複利、法院選擇風險），以及目前還可採取哪些反制動作。

---

### ⚠️ 閱讀前請先理解三件事

#### 1. 這是一個研究原型

顧問最初是在 **Claude（Opus 4.7）** 上原生設計、測試與打磨的。目前已記錄兩個公開平台的移植版本：**Gemini Gem** 版本（`GEM_System_Prompt.md`，接近完整長度），以及 **ChatGPT 5.5** 版本（`ChatGPT_System_Prompt.md`，≤8k token 的 orchestrator 精簡變體，於 ChatGPT 5.5 上線當日撰寫）。兩者都是 **可攜性展示**：證明這套方法能跨平台運作，但相較於 Claude 原生版，保真度明顯下降（RAG 接地較弱、思考時間偶有不穩、對系統提示裡的硬約束遵從較鬆散）。`examples/` 裡的三個範例刻意保留 Gemini 的錯誤並加上註解，讓讀者實際校準「原型」兩字的意義。

#### 2. 因子代碼是作者個人的研究工具

**L / R / N-D / N-P / N-M / N-F** 因子代碼、**P-xxx-##** 命題 ID、**T01–T09** 主題 ID、拆解慣例與 watch-item 分類，都是 **作者個人的分析速記**，是在以 v1.1 分類法逐件標注 18 份英國 FRAND 判決時產生的。這些代碼並非業界標準、尚未學術發表，也不預期第三方採用。外部讀者請 **穿透這套記號**，回到被引用的原始權威（UPSC、GB052、GB054、GB058、GB059、GB068）上去讀真正的法律內容。代碼只是結構性的管線，不是法理本身。

#### 3. 並非法律意見

此儲存庫的任何內容都不構成法律意見。法理內容雖來自公開英國判決，但透過一套有已知侷限的個人研究分類法進行組織（詳見 §已知失效模式）。實際授權事件必須由合格法律顧問處理。

---

### 顧問能做什麼

**輸入**（中文或英文，自由文字）：
> 老闆說今天收到 notice 就算有 chart 也先假裝沒看到，等明年再來處理。

**輸出結構**：
- **§1** 場景摘要
- **§2** 事件萃取（角色／行為／姿態／時點）
- **§3** 法理映射（tag／命題 ID／willingness limb／主題）
- **§4** 後果鏈（3A 善意授權資格喪失／3B 授權人資訊義務違反／3C R11 啟動／3D N33 累積／3E 法院選擇／3F 反制動作／3G 管轄路由）
- **§5** 風險曝露報告（禁制令、R11、N33、法院風險的定性評估；帶保留意見的方向性量化；可逆性；相關 watch-item）
- **§6** 建議下一步
- **§7** 免責聲明（三段式：原型／個人研究／非法律意見）

三個完整範例（含實際 Gemini 輸出與註解）在 `examples/` 目錄。

---

### 檔案架構

```
sep-negotiation-advisor/
├── README.md                ← 本檔
├── GEM_System_Prompt.md     ← Gemini Gem 移植版（貼入 Gem 指令欄）
├── ChatGPT_System_Prompt.md ← ChatGPT 5.5 移植版（≤8k orchestrator 變體；貼入自訂 GPT 的 Instructions）
├── examples/
│   ├── 01_licensee_passive_ignore.md       ← 實施者無視 notice + chart
│   ├── 02_licensee_tactical_delay.md       ← 實施者要求完整 chart 以拖延
│   └── 03_licensor_info_withholding.md     ← 授權人拒絕揭露比較授權
└── LICENSE                  ← 見本 README 末段
```

儲存庫刻意 **不附知識庫語料**。原因與自建指引見下方 §自建 RAG。

---

### 自建 RAG

顧問需要一個涵蓋英國 FRAND 法理的 RAG 知識庫。**作者不提供預建語料**，理由有三：

1. **原型完整性。** 下載現成語料的使用者會把它當成完成品；自己動手建語料的使用者必然會回去讀原始權威——這才是重點。
2. **研究工作切分。** 作者對 Lenovo 系列的法理彙整是數週的手工產出，直接以可用 RAG 形式發佈，等於把個人研究轉成可被任意抓取的內容。
3. **法理漂移。** 英國 FRAND 法理仍在演進（CA 與 UKSC 仍有案件在排程中）。語料一出版就會過時；但組裝語料的方法不會。

#### 知識庫應該包含什麼

一份可用的顧問 RAG 大致需要以下法理素材，並確保每個法理向量都可被檢索到：

**核心分類層**（1–2 份文件）：
- 一份 tag 字典，列出 L / R / N-D / N-P / N-M / N-F 各因子、操作性定義，以及至少一個 pilot case 的段落錨點。
- 一份彙整／aggregation memo，記錄分類法演進（特別是升格與擴展）。缺了這份，檢索器會錯過 v1.1 對 v1.0 條目的更新。

**法理主題層**（每個法理一份，英國範圍約 9 份）：
- **T01 善意被授權人累積檢驗** — 五 limb（範圍決定／無條件性／無時間切割／無法院條件／主動啟動義務），錨於 UPSC.158、GB058.538、GB058.540、GB054.13(viii)、GB068.187；再加授權人資訊義務（GB058.202）。
- **T02 非歧視三層暫存器** — 費率對等／量差／範圍差異（加上開放的 assignment-continuity 暫存器）；硬性 MFN 已於 UPSC.114 與 GB068.231/276 被拒。
- **T03 時效覆寫（R11）** — 混合訴因理論（GB058.533）、反激勵理由（GB058.529）、GB068 ¶186 以降經 CA 確認的八股線；Nugee LJ 勉強的協同意見（GB068.289-290）。
- **T04 比較授權方法（L16）** — 主導地位 GB058.16/945、Cimetidine 純淨比較授權重建 GB055.90-115、兩階段估價主導 GB068.251-281。
- **T05 法院選擇推定（R12）與停訴** — Nokia v Oppo [269]；GB054.87 基礎；GB057 [269]-[292] 藉口性；GB100 ¶72 的邊界；停訴 slender-benefit 脈絡（Conversant 線）。
- **T06 保密性／公開司法** — L2 與 L11 暫存器；庭審旁聽（GB052 ¶3）；費率公開考量（GB059）。
- **T07 Kigen 實施者觸發權（L10）** — 預先承諾要件；停錶 vs. 回溯撤銷區分；對組合授權的適用。
- **T08 兩階段估價 + 上訴審級尊重** — L6 費率區間；Lifestyle-Equities 尊重門檻；內部一致性上訴路徑；雙向風險（Lenovo $0.175 → $0.225 上調）。
- **T09 FRAND 複利（N33）** — 4% 季複利，自使用當季起算；Lenovo 對 16 年本金約 1.89× 乘數；延遲下的凹性。

**彙整層**（2–4 份文件）：
- **Practitioner matrix** — 依生命週期階段分類的被授權人／授權人檢查清單，這是顧問 §5、§6 輸出最接近的形狀。
- **Jurisdictional divergence** — DE / CN / US / NL / JP / EU 的英國錨定推論。
- **Watch-items** — 未來案件可能解答的開放法理問題。顧問會在 §5 直接引用 `W-xxx` 標題，所以必須與語料逐字一致。

**反語料**（不要放進去的東西）：
- **逐案回溯標注檔。** 這些是蒸餾出主題線的原始素材；與主題線並陳會重複計算並讓檢索器過度偏重單案。即使你手上有，也別放進顧問的知識庫。
- **分類維護方法論 skill。** 顧問是分類法的 *消費端*；放入維護方法論會讓策展者語氣滲入場景輸出。
- **原始判決全文。** 密度太低。若需段落級精度，只補入主題線實際引用的判決節錄。

#### 部署 A — Gemini Gem

1. 依上述結構撰寫知識庫文件（`.txt` 或 Google 文件格式；Gemini 目前不接受 `.md` 上傳）。
2. 合併至 **≤10 份** — Gem 平台有檔案數上限。建議分組：tag 字典與 aggregation memo 各自獨立；aggregation layer（overview + practitioner matrix + jurisdictional divergence + watch-items）合併；主題線依主題耦合成對合併（例如 T04+T08 費率方法、T05+T07 法院與觸發程序）。
3. 在 Gemini 建立新 Gem，把 `GEM_System_Prompt.md` 裡 `=== BEGIN GEM PROMPT ===` 到 `=== END GEM PROMPT ===` 的區塊貼入指令欄。
4. 把知識庫檔案上傳為 Gem 的 knowledge。
5. 以 `examples/01_licensee_passive_ignore.md` 進行煙霧測試，驗證輸出能正確識別：Limb 5 違反、chart 交付滿足 P-N1-07（授權人側已履行）、R11 啟動、N33 累積、R12 法院選擇風險。若其中任一缺漏或嚴重失真，代表檢索沒有正確接地。

#### 部署 B — ChatGPT 5.5（自訂 GPT）

於 ChatGPT 5.5 上線當日撰寫。提示檔 `ChatGPT_System_Prompt.md` 是壓縮過的 **≤8k token orchestrator**，保留 Step 0–5 管線（gate → 事件 → 法理映射 → trigger / threshold / consequence → 後果模組 A–H → 風險曝露報告）與硬規則，長度對齊 ChatGPT 自訂 GPT 的指令預算。

1. 依上述流程撰寫／合併知識庫。ChatGPT 移植版明確引用十個檔名（`01_tag_dictionary.txt`、`02_v1.1_aggregation_memo.txt`、`03_aggregation_layer.txt`、`04_T01_willing_licensee.txt`、`05_T02_non_discrimination.txt`、`06_T03_R11_limitation.txt`、`07_T04_T08_rate_setting.txt`、`08_T05_T07_forum_and_trigger.txt`、`09_T06_confidentiality.txt`、`10_T09_N33_compound_interest.txt`），要嘛比照命名，要嘛修改提示裡 `## RAG source of truth` 區塊的檔名對應。
2. 在 chatgpt.com 建立新的自訂 GPT，把整份 `ChatGPT_System_Prompt.md` 貼入 Instructions 欄。
3. 把十個知識庫檔案上傳至該 GPT 的 Knowledge。
4. 啟用 `File search` 工具；除非另有需求，建議關閉影像生成與 code interpreter。
5. 以 `examples/01_licensee_passive_ignore.md` 煙霧測試（驗證指標同上）。

平台差異值得留意：ChatGPT 5.5 對語料檔名的檢索較為強勢（因此顯式逐檔對應），而且對於「法理觸發」與「結論成立」兩者的區分比 Gemini 嚴格；≤8k 版本因此把 Step 3 明確命名為 `trigger / threshold / consequence`。§已知失效模式 A–E 原則上仍然適用；ChatGPT 版本尚未對本儲存庫的三個範例場景做迴歸測試。

#### 部署 C — Claude 原生版

屬操作者專屬，此處不公開文件。

---

### 已知失效模式

以下是在三個 Gemini 測試場景中實際觀察到的失效模式（均已存於 `examples/`）。即便系統提示列出了硬約束（規則 1–13），Gemini 的基線生成傾向仍會以不低的頻率產生這些錯誤。Claude 原生部署能降低但未必能完全消除。

#### A. 幻覺式 watch-item

場景觸及活躍法理領域，但語料中沒有完全對應條目時，Gemini 會編造聽起來合理的 `W-xxx`。測試 2 例：`W-N33-rate-review`（不在語料中）；測試 3 例：`W-N1-licensor-information-CA`（對 `W-N1-licensor-information-asymmetry` 的改寫）。**緩解**：紀律規則 9——任何被引用的 `W-xxx` 必須是 watch-items 文件中的逐字標題。Gemini 遵循不一致，讀者應對照語料查核。

#### B. §4 後果鏈靜默省略

最常被省略的是法院選擇（3E），尤其當場景以實施者違反為主、檢索器注意力被 3A / 3C / 3D 吃滿時。**緩解**：紀律規則 10——§4 必須對七條後果鏈每條都明示 `✓ triggered` 或 `— not triggered`。測試 1、2 於 Gemini 皆未通過此檢查（3E 只出現在 §5）；測試 3 在強調規則後修正。

#### C. N33 基底混用

Gemini 偶爾會把 N33 複利計在授權人要價、實施者反報價或其他場景中出現的談判數字上。正確基底是 **法院核定的 FRAND 費率 × 過去使用量**。測試 2 例：「若 10M 是全球總包價,兩年的複利... 將使該金額在判決時顯著膨脹」——10M 是授權人要價，不是 N33 基底。**緩解**：紀律規則 11。

#### D. 當事方歸屬反轉

分類法結構上不對稱——Limbs 1–5 是實施者側的善意要件。當場景是授權人違反時，Gemini 傾向把 Limb 標籤套到授權人行為上（例如把授權人在授權形式上的僵固稱為「Limb 2 / Limb 4」違反——這就是反轉）。測試 3 §3 把三個授權人／實施者事件做了反轉或錯標的 Limb 映射。**緩解**：紀律規則 12。

#### E. 實施者維持姿態時 R11 / N33 過度放大

當違反者是實施者時，R11 與 N33 正確地升級。當違反者是授權人、實施者在維持善意姿態（索取資訊、提出停訴、考慮 Kigen）時，R11 / N33 應為 `Preserved / Conditional`，不應為 `High`。Gemini 因語料中的英國架構偏重實施者風險，預設為 `High`。測試 3 §5 即便實施者積極索取比較授權（Limb 5 維持中），仍把 R11 與 N33 標為 `High`。**緩解**：紀律規則 13。

#### 普遍性偏誤：實施者側不對稱預設

失效模式 D 與 E 根源相同：底層分類法是從實施者保護角度撰寫的（Lenovo 系列本身就是實施者側的法理重建）。當場景把違反者身份倒過來，顧問的預設模式就會失靈。v1.1 的新增項（L16、R12）部分補強，但尚未完成對稱版本。讀者在面對授權人違反輸出時，應對照 tag 字典中 L / R 不對稱說明進行交叉檢查。

---

### 設計取捨（摘要）

以下只列關鍵決策，完整理由略：

- **為什麼用四步驟管線？** 結構化覆蓋是對抗單點隧道視野的首要防線。一段提到 chart 的場景可能同時觸發 Limb 5（被授權人側）、P-N1-07（授權人側）、R11、N33、R12 與 L10；自由推理路徑通常只會浮出其中兩三個。管線強制七條後果鏈都被逐一檢視。
- **為什麼禁止段落編號編造？** 底層判決是真實的、段號是公開的；被編造的引用既可被驗證為假、又比不給引用更有害。段號無法檢索到時，顧問退而引用命題 ID（例如 `P-N1-05`）作為有接地的備援。
- **為什麼保留實施者側不對稱？** 語料是以英國 FRAND 的實施者保護視角寫成的。對稱版本是未來工程。現版本誠實承認自己的不對稱（見 §已知失效模式 D / E），不假裝中立。
- **為什麼不附語料？** 見上方 §自建 RAG。
- **為什麼接受 Gemini / ChatGPT 部署的保真度下降？** Gemini Gem 與 ChatGPT 自訂 GPT 是目前原型對外最低摩擦的公開部署通道。Claude 接地較好但缺乏同級的公開分享原語。這是刻意的取捨：可攜性與展示可及性 > 輸出品質。`examples/` 的註解記錄 Gemini 上損失了什麼；ChatGPT 5.5 版本較新，尚未對同一組迴歸場景做註解。

---

### 範例

| 檔案 | 場景 | 要點 |
|---|---|---|
| [`examples/01_licensee_passive_ignore.md`](examples/01_licensee_passive_ignore.md) | 實施者老闆指示員工對收到的 chart 裝作沒看到，延到明年再處理 | 實施者側違反的典型型——Limb 5 違反 + R11 啟動 + N33 累積 + 法院選擇風險。同時示範 **雙面洞察**：chart 交付履行了 P-N1-07（授權人側已履行），被忽略則違反 Limb 5（實施者側）。 |
| [`examples/02_licensee_tactical_delay.md`](examples/02_licensee_tactical_delay.md) | 實施者老闆認為授權人要價太高，打算要求完整 claim charts 拖兩年，再出低價和解 | 戰術性拖延 + 偽反報價。同時觸發 Limb 2（無條件性）與 Limb 5。示範失效模式 A（幻覺 watch-item）與 C（N33 基底混用）。 |
| [`examples/03_licensor_info_withholding.md`](examples/03_licensor_info_withholding.md) | 授權人要求單位費率、拒絕其他形式、拒絕揭露比較授權、威脅即將行動。實施者憤怒 | 授權人側違反的典型型——P-N1-07 違反 + R12 藉口性風險。示範失效模式 D（當事方反轉）與 E（維持姿態下 R11 / N33 過度放大）。同時展現 Gemini 的亮點：抓到「憤怒 ≠ 姿態」的細節。 |

每個範例都包含：實際測試輸入、Gemini 逐字輸出、以及指向每個失效模式（或正確點）的行內註解。

---

### 授權條款

本儲存庫的系統提示與方法論以 **MIT License** 釋出（見 `LICENSE`）。作者保留「閱讀前三件事」§2 所述個人研究工具的版權；獨立重用 L / R / N 代碼或命題 ID 慣例 **不鼓勵但不禁止**（它們沒有受法律保護，只是個人策展）。

文中引用的判例原文與段落編號屬公開司法紀錄，不受本儲存庫授權條款限制。
