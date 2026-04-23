# SEP Negotiation Scenario Advisor — Prototype

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg) ![Status: Prototype](https://img.shields.io/badge/Status-Prototype-orange.svg) ![Last updated: 2026-04](https://img.shields.io/badge/Last%20updated-2026--04-blue.svg)

A research prototype that takes a Standard-Essential-Patent (SEP) licensing negotiation scenario in natural language and produces a structured analysis grounded in UK FRAND case-law (UPSC *Unwired Planet v Huawei* + the Lenovo quintet, 2020–2024).

The advisor routes a free-text scenario through a four-step pipeline — event extraction → doctrinal mapping → consequence chain → exposure synthesis — and returns which FRAND elements are engaged, what penalties (injunction, R11 lifelong payment, N33 compound interest, forum risk) follow, and what counter-moves are still available.

---

## ⚠️ Three things to know before reading further

### 1. This is a research prototype

The advisor was designed, tested, and refined natively on **Claude (Opus 4.7)**. The Gemini GEM version documented here is a **portability demo** — it proves the methodology travels across platforms, but operates at materially reduced fidelity (weaker RAG grounding, occasional thinking-time instability, looser adherence to the hard constraints in the system prompt). The three examples in `examples/` deliberately include Gemini's mistakes with annotations, so readers can calibrate what "prototype" actually means.

### 2. The factor codes are a personal research apparatus

The **L / R / N-D / N-P / N-M / N-F** factor codes, **P-xxx-##** proposition IDs, **T01–T09** thread IDs, the decomposition conventions, and the watch-item taxonomy are **the author's private analytical shorthand**, developed while tagging 18 UK FRAND judgments under a v1.1 taxonomy. They are not industry-standard, not academically published, and not intended for third-party adoption. External readers should **look through** the notation to the cited primary authorities (UPSC, GB052, GB054, GB058, GB059, GB068) for the actual legal content — the codes are structural plumbing, not doctrine.

### 3. Not legal advice

Nothing in this repo constitutes legal advice. The doctrinal content is derived from public UK judgments but organised through a personal research taxonomy with known limitations (see §Known failure modes). Counsel is required for any actual licensing matter.

---

## What the advisor does

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

## Architecture

```
sep-negotiation-advisor/
├── README.md                ← this file
├── GEM_System_Prompt.md     ← the system prompt (paste into GEM instructions)
├── examples/
│   ├── 01_licensee_passive_ignore.md       ← implementer ignores notice + chart
│   ├── 02_licensee_tactical_delay.md       ← implementer demands full chart to stall
│   └── 03_licensor_info_withholding.md     ← licensor refuses comparables
└── LICENSE                  ← (see bottom of this README)
```

The repository deliberately **does not include the knowledge-base corpus**. See §Building your own RAG below for why and how to assemble one.

---

## Building your own RAG

The advisor depends on a retrieval-augmented knowledge base covering UK FRAND doctrine. **The author does not ship a pre-built corpus** for three reasons:

1. **Prototype integrity.** A user who downloads a turnkey corpus will treat this as a finished product. A user who has to build their own corpus necessarily reads the underlying authorities — which is the entire point.
2. **Research-work separation.** The author's Lenovo-campaign doctrinal synthesis is a multi-week manual work product. Publishing it as ready-to-use RAG converts personal research into freely-scrapable content.
3. **Doctrinal drift.** UK FRAND doctrine continues to evolve (CA and UKSC cases are in the pipeline). A shipped corpus ages immediately; a methodology to assemble one does not.

### What the knowledge base needs to contain

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

### Deployment (Gemini Gem, the demo platform)

1. Author the knowledge base documents described above (in `.txt` or Google Doc format — Gemini does not accept `.md` uploads as of this writing).
2. Consolidate to **≤10 files** if using Gemini Gems — the platform enforces a file-count limit. Logical groupings: tag-dictionary + aggregation-memo standalone; aggregation layer (overview + practitioner matrix + jurisdictional divergence + watch-items) merged; threads merged pairwise by thematic coupling (e.g. T04+T08 rate-setting methodology, T05+T07 forum-and-trigger procedure).
3. Create a new Gem in Gemini. Paste the block between `=== BEGIN GEM PROMPT ===` and `=== END GEM PROMPT ===` from `GEM_System_Prompt.md` into the instructions field.
4. Upload the knowledge base files as the Gem's knowledge.
5. Test with the `examples/01_licensee_passive_ignore.md` scenario and verify the output identifies: Limb-5 breach, chart-delivery fulfilling P-N1-07 (licensor side performed), R11 activation, N33 accrual, R12 forum-choice risk. If any of these is missed or substantially garbled, retrieval is not grounding correctly.

Native Claude deployment is operator-specific and not documented here.

---

## Known failure modes

These are real failure modes observed across three Gemini test scenarios (all documented in `examples/`). Even with the hard constraints enumerated in the system prompt (rules 1–13), Gemini's baseline generative tendency produces these mistakes at non-trivial frequency. Claude-native deployment reduces but may not eliminate them.

### A. Hallucinated watch-items

Gemini will invent plausibly-named `W-xxx` watch-items when the scenario touches a live doctrinal area but no exactly-matching corpus entry is retrievable. Example from test 2: `W-N33-rate-review` (not in the corpus). Example from test 3: `W-N1-licensor-information-CA` (paraphrase of `W-N1-licensor-information-asymmetry`). **Mitigation**: Discipline Rule 9 — any `W-xxx` cited must be a verbatim title from the watch-items document. Gemini complies inconsistently; readers should spot-check watch-item names against the corpus.

### B. §4 consequence-chain silent omission

Forum-choice (3E) is the most frequently omitted chain, especially when the scenario involves implementer-side violations and the retriever's attention is saturated by 3A/3C/3D. **Mitigation**: Discipline Rule 10 — explicit `✓ triggered` / `— not triggered` marking for all seven chains in §4. Tests 1 and 2 under Gemini both failed this check (3E appeared only in §5); test 3 corrected after the rule was emphasised.

### C. N33 base conflation

Gemini occasionally computes N33 compound interest against the licensor's demand price, the implementer's counter-offer, or any other negotiation figure present in the scenario. Correct base is **court-determined FRAND rate × past use**. Example from test 2: "若 10M 是全球總包價,兩年的複利... 將使該金額在判決時顯著膨脹" — the 10M is the licensor's demand, not the N33 base. **Mitigation**: Discipline Rule 11.

### D. Party-attribution inversion

The taxonomy is structurally asymmetric — Limbs 1–5 are implementer-side willingness requirements. Gemini, when processing a licensor-violator scenario, tends to apply Limb labels to licensor conduct (e.g. labelling a licensor's form-of-licence inflexibility as "Limb 2 / Limb 4" breach — this is inversion). Example: test 3 §3 mapped three separate licensor/implementer events with inverted or mislabelled Limbs. **Mitigation**: Discipline Rule 12.

### E. R11/N33 over-calling under maintained-posture implementer

When the implementer is the violator, R11 and N33 correctly escalate. When the licensor is the violator and the implementer is maintaining willingness posture (demanding info, proposing standstill, considering Kigen), R11/N33 should be `Preserved / Conditional`, not `High`. Gemini defaults to `High` because the UK architecture is implementer-risk-weighted in the corpus. Example: test 3 §5 labelled both R11 and N33 as `High` despite implementer actively demanding comparables (Limb 5 maintained). **Mitigation**: Discipline Rule 13.

### Pervasive: implementer-asymmetric default

Failure modes D and E share a root cause. The underlying taxonomy was authored from the implementer-protection analytical angle (the Lenovo campaign was an implementer-side doctrinal reconstruction). Scenarios that invert the violator identity cause the advisor's default pattern to misfire. The v1.1 additions (L16, R12) partially address this but do not complete the symmetric version. Users should mentally prepare to cross-check any licensor-violator output against the L/R asymmetry note in the tag dictionary.

---

## Design rationale (short)

Fuller rationale is elided; key decisions:

- **Why a four-step pipeline?** Structural coverage is the primary defence against single-limb tunnel vision. A scenario that mentions "chart" may engage Limb 5 (licensee side), P-N1-07 (licensor side), R11, N33, R12, and L10 simultaneously; a free-form reasoning path will usually surface only two or three. The pipeline forces all seven consequence chains to be considered.

- **Why forbid paragraph-number fabrication?** The underlying judgments are real and paragraph numbers are public. A fabricated citation is both verifiable-as-false and more harmful than no citation at all. The advisor cites proposition IDs (`P-N1-05`) as grounded fallback when a specific paragraph number cannot be retrieved.

- **Why the implementer-asymmetric taxonomy?** The corpus was written for the implementer-protection angle of UK FRAND. A symmetric version is a future project. The current version is honest about its asymmetry (see §Known failure modes D/E) rather than pretending to neutrality it does not have.

- **Why not ship the corpus?** See §Building your own RAG above.

- **Why accept the Gemini deployment's reduced fidelity?** Gemini GEM is the most frictionless public-facing deployment for a prototype. Claude has better grounding but no comparable consumer-facing share-a-Gem primitive. The tradeoff is deliberate: portability and demo accessibility over output quality. The examples/ annotations document what was lost.

---

## Examples

| File | Scenario | What it illustrates |
|---|---|---|
| [`examples/01_licensee_passive_ignore.md`](examples/01_licensee_passive_ignore.md) | Implementer's employer instructs staff to ignore a received chart and delay response to next year | The canonical implementer-side violation — Limb 5 breach + R11 activation + N33 accrual + forum-choice risk. Also demonstrates the **dual insight** that chart delivery fulfils P-N1-07 (licensor-side performed) while ignoring it breaches Limb 5 (implementer side). |
| [`examples/02_licensee_tactical_delay.md`](examples/02_licensee_tactical_delay.md) | Implementer's employer treats licensor's offer as too high, plans to request full claim charts to stall two years, then offer a lowball settlement | Tactical delay + sham counter-offer. Triggers Limb 2 (unconditionality) and Limb 5 concurrently. Demonstrates Failure mode A (hallucinated watch-item) and Failure mode C (N33 base conflation). |
| [`examples/03_licensor_info_withholding.md`](examples/03_licensor_info_withholding.md) | Licensor demands a unit rate, refuses alternative forms, refuses to disclose comparables, threatens imminent action. Implementer angry | The canonical licensor-side violation — P-N1-07 breach + R12 pretextuality risk. Demonstrates Failure mode D (party-attribution inversion) and Failure mode E (R11/N33 over-calling under maintained-posture implementer). Also shows Gemini's best moment — capturing the "憤怒 ≠ posture" nuance. |

Each example contains: the input scenario as actually tested, the Gemini output verbatim, and inline annotations pointing to each failure mode (or success) observed.

---

## License

The system prompt and the methodology described in this repository are released under the **MIT License** (see `LICENSE`). The author retains copyright to the personal research apparatus described in §2 of the three-things-to-know section; independent re-use of the L/R/N codes or the proposition-ID convention is discouraged but not prohibited (they are not legally protected, only personally curated).

Actual case-law text and paragraph numbers referenced throughout are public judicial records and not subject to this repository's license.
