policy_renewal_premium_calculator
Policy Renewal Premium Calculator
Purpose: Insurance policies are renewed annually. At renewal time, the premium for the next term isn't simply the same as last year's — it's adjusted up or down based on the policyholder's claims history, risk profile, and payment behavior over the previous term. This application takes a policy's data from the last term and computes the correct premium to charge for the upcoming renewal term.
What the application should do: Accept a policy's details as input, apply the adjustment rules below in order, and output the final renewed premium along with a breakdown of which adjustments were applied and why.
Inputs: policy_id, base_premium, claims_count_last_term, claim_free_years, risk_tier (Low / Medium / High)(Case insensitive), late_payment_count_last_term()
Output: policy_id, renewed_premium, applied_adjustments (a list showing which rules applied and what they changed)
Step 0 — Validate first
Check all inputs are present and sensible (no negative counts, risk_tier must be Low/Medium/High, base_premium must be a positive number) (late_payment_count_last_term(),claims_count_last_term, claim_free_years all must ne positive and Integer only,no decimal). If anything is invalid, stop and output an error explaining what's wrong. Do not calculate a premium.
Step 1 — Start with the base premium
renewed_premium = base_premium
Step 2 — Claims made this term? Add a loading.
If claims_count_last_term is 0 or 1 → no change, skip to Step 3.
If claims_count_last_term is 2 or more → for every claim beyond the first one, add 8% of the current renewed_premium.
Example: 3 claims → 2 claims beyond the first → apply the 8% increase twice, one after another.
Step 3 — No claims? Apply a claim-free discount instead.
(Only if claims_count_last_term is exactly 0 — skip this step entirely if any claims were made.)
Discount = claim_free_years × 3%, capped at a maximum of 20%.
Example: 5 claim-free years → 15% discount. 8 claim-free years → capped at 20%, not 24%.
Subtract this discount from the current renewed_premium.
Step 4 — Adjust for risk tier
Low → no change.
Medium → add 5% to the current renewed_premium.
High → add 15% to the current renewed_premium.
Step 5 — Late payment penalty
If late_payment_count_last_term is 2 or more → add a flat 10% of the original base_premium (not the running total) to renewed_premium.
If fewer than 2 → no change.
Step 6 — Round and finish
Round renewed_premium to the nearest whole number. This is your final answer.
Important: Steps 2 and 3 never both apply to the same policy — a policy either had claims (Step 2) or was claim-free (Step 3), never both.