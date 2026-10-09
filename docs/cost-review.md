# Historical estimate review

This is a review of my November 2023 academic quote, not a current Azure price estimate. The original workbook was inspected without editing it. Its service amounts are unvalidated historical inputs and should not be reused as a purchasing quote.

The proposal describes Canadian-dollar pricing. The workbook itself does not provide a consistent currency and billing-period field for each row, so the amounts below retain the original dollar notation without asserting that every line has a verified currency basis.

## Formula findings

Source worksheet: `Invoice Template`.

| Finding | Source cells | Verified behavior |
|---|---|---|
| VM line excluded from subtotal | B23:D23; D33 | 15 × 104.21 gives 1,563.15. D23 stores its displayed amount as text, so `SUM(D15:D32)` omits it. |
| Original subtotal | D33 | Cached value is 957,770.59 and matches the sum of numeric line items. |
| Original quote total | D34:D39 | After the 5,500 discount, 5% tax, and 2,500 shipping/handling, the cached result rounds to 1,002,384.12. |
| Labor mismatch | D27:D32 | The six labor entries total 240,000. The proposal's stated labor subtotal is 260,000. |
| Mixed cost periods | A15:D32 and proposal pricing section | Monthly service figures, reservation/backup descriptions, and implementation charges are combined without a consistent time horizon. |

The text VM amount also includes an invisible directional-formatting character. Converting that entry to a numeric value would repair its participation in the subtotal, but would not resolve the cost model's assumptions.

## Arithmetic illustration

Keeping every other historical input unchanged and including the VM amount would yield:

- Subtotal: 957,770.59 + 1,563.15 = **959,333.74**.
- After discount: 959,333.74 − 5,500 = **953,833.74**.
- Tax at the original 5% assumption: **47,691.687** before rounding.
- Total with the original 2,500 shipping/handling: **1,004,025.43**, rounded at the end.

This is only a formula illustration. It is not a corrected, valid project quote: billing periods, capacity, service selection, commitments, tax applicability, and handling charges still need review. No replacement workbook or commercial quote has been issued.

## What a revised model needs

Use separate sections for one-time implementation, recurring monthly operations, and reservation commitments. Each service row needs a service/SKU, region, quantity and unit, capacity, usage, currency, pricing date, billing period, and traceable calculator source. Distinguish reserved capacity from upfront or monthly payment treatment.

The 1,000 TiB storage assumption and large backup line need workload and retention justification. The 15 VMs also need roles that do not duplicate managed App Service and SQL capacity. The original reference sheet contains several hardware links that do not substantiate the listed cloud service amounts.

The reviewed workbook supports experience preparing and auditing estimates; it does not establish a reliable production budget or savings result.
