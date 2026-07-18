# Evaluation Results: Baseline RAG vs Self-Correcting RAG

> Generated: 2026-07-18 14:29:05 UTC  
> Test items: **5**

---

## Per-Item Comparison

| # | Question | Baseline answer (excerpt) | Corrected answer (excerpt) | Baseline (s) | Corrected (s) | Corr. Rounds |
|--:|---|---|---|--:|--:|--:|
| 1 | What are the main causes of the French Revolution? | [Baseline error: [WinError 10061] No connection could be made because the target machine active… | [Corrected error: [WinError 10061] No connection could be made because the target machine activ… | 4.4 | 12.5 | 0 |
| 2 | How does the CRISPR-Cas9 system edit DNA? | [Baseline error: [WinError 10061] No connection could be made because the target machine active… | [Corrected error: [WinError 10061] No connection could be made because the target machine activ… | 4.1 | 4.0 | 0 |
| 3 | What is the difference between supervised and unsupervised learni… | [Baseline error: [WinError 10061] No connection could be made because the target machine active… | [Corrected error: [WinError 10061] No connection could be made because the target machine activ… | 4.1 | 4.1 | 0 |
| 4 | What causes the northern lights (aurora borealis)? | [Baseline error: [WinError 10061] No connection could be made because the target machine active… | [Corrected error: [WinError 10061] No connection could be made because the target machine activ… | 4.1 | 4.0 | 0 |
| 5 | How does the TCP/IP protocol suite work? | [Baseline error: [WinError 10061] No connection could be made because the target machine active… | [Corrected error: [WinError 10061] No connection could be made because the target machine activ… | 4.1 | 4.0 | 0 |

---

## Generation Quality (RAGAS)

| Metric | Baseline | Self-Correcting | Δ (Corrected − Baseline) |
|---|--:|--:|--:|
| faithfulness | N/A | N/A | N/A |
| answer_relevancy | N/A | N/A | N/A |
| answer_correctness | N/A | N/A | N/A |
| context_entity_recall | N/A | N/A | N/A |

---

## Retrieval Quality (RAGAS)

| Metric | Baseline | Self-Correcting | Δ (Corrected − Baseline) |
|---|--:|--:|--:|
| context_precision | N/A | N/A | N/A |
| context_recall | N/A | N/A | N/A |

---

## Self-Correction Metrics

| Metric | Value |
|---|--:|
| Hallucination Fix Rate (%) | N/A |
| Hallucination Injection Rate (%) | N/A |
| Avg Correction Rounds | 0.00 |
| Max Rounds Hit (%) | 0.0 |
| Avg Latency Overhead (s) | 1.6 |

---

## Secondary Metrics

| Metric | Baseline | Self-Correcting |
|---|--:|--:|
| bertscore_f1 | N/A | N/A |
| rouge_l | N/A | N/A |

---

## Notes

- **Faithfulness**: fraction of answer claims supported by the retrieved context (higher = fewer hallucinations).
- **Answer relevancy**: how directly the answer addresses the question (higher = more on-topic).
- **Answer correctness**: factual overlap + semantic similarity vs. ground-truth answer.
- **Context entity recall**: key entities from ground truth present in retrieved context.
- **Hallucination Injection Rate**: the critical self-correction failure metric — should be near zero before reporting corrected faithfulness.
- A positive Δ means the Self-Correcting pipeline outperformed the baseline.
- `N/A` means RAGAS raised an exception for that pipeline (see console output for details).
- **Context pairing fix**: corrected-answer RAGAS contexts now use the full chunks returned by `run_corrected_query['correction_context']`, not the 120-char trace previews from the previous version.
