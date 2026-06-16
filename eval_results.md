# Eval Results

## Pass-Rate Summary

| Variant | Approach | Pass Rate |
|---|---|---|
| A | Few-Shot Prompting | 93% (14/15) |
| B | Embeddings + Nearest Neighbor | 87% (13/15) |

## Per-Item Results

| # | Ticket | True Label | Variant A Pred | A Verdict | Variant B Pred | B Verdict |
|---|---|---|---|---|---|---|
| 1 | My card was charged but I never received a receipt... | billing | billing | PASS | billing | PASS |
| 2 | How do I cancel my subscription? | billing | account | FAIL | billing | PASS |
| 3 | The video player buffers endlessly on Chrome. | technical | technical | PASS | technical | PASS |
| 4 | I can't connect the integration with Slack. | technical | technical | PASS | account | FAIL |
| 5 | I need to change the email address on my account. | account | account | PASS | account | PASS |
| 6 | How do I transfer my account to someone else? | account | account | PASS | account | PASS |
| 7 | Please add keyboard shortcuts to the editor. | feature_request | feature_request | PASS | feature_request | PASS |
| 8 | I'd love a way to filter tickets by priority. | feature_request | feature_request | PASS | feature_request | PASS |
| 9 | Are you GDPR compliant? | general | general | PASS | general | PASS |
| 10 | Where can I find your terms of service? | general | general | PASS | general | PASS |
| 11 | I think I was billed for a plan I didn't choose. | billing | billing | PASS | billing | PASS |
| 12 | The export button does nothing when I click it. | technical | technical | PASS | feature_request | FAIL |
| 13 | I want to merge two accounts under one email. | account | account | PASS | account | PASS |
| 14 | Could you add a bulk-import feature for contacts? | feature_request | feature_request | PASS | feature_request | PASS |
| 15 | What countries do you support? | general | general | PASS | general | PASS |

## Judge Verdict

**Winner:** Variant A (Few-Shot) with 93% vs 87%.

**Do we trust the judge?** The judge is reliable for clear-cut cases where PASS/FAIL is unambiguous. However, it cannot handle borderline cases where two labels are both reasonable (e.g., "How do I cancel my subscription?" could be *billing* or *account*). For this narrow classification task the rubric is mostly trustworthy.

**One case where the judge looked wrong:** If the model predicted `account` for "How do I cancel my subscription?" (true label: `billing`), the judge marks it FAIL � but a human reviewer might consider cancellation to touch both domains. The strict rubric penalises reasonable alternatives.
