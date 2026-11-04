# Compliance Rules Reference

Use this file for all 6 compliance checks.

## A — Discount & DOA Thresholds

DOA (Delegation of Authority) defines who approves a deal based on discount level and ACV.

| Level | Approver | Typical Trigger |
|-------|----------|-----------------| 
| Level 1 | AE | Standard deal within guidelines |
| Level 2 | CBP / First Approver | Discount above threshold or ACV above limit |
| Level 3 | Sales Director / VP | Significant discount or strategic deal |
| Level 4 | SVP or above | Deep discount or major exception |

Key checks: Is DISCOUNT_PCT within guidelines? Is ACV correctly calculated?
Is there documented pre-approval for exceptions?

## B — DHI Flags in Harmony

| Flag | Trigger | Resolution |
|------|---------|------------|
| Price below floor | Net price below minimum floor | Increase price or get floor exception |
| Missing mandatory product | Required companion product absent | Add mandatory product line |
| Duplicate line item | Same SKU appears more than once | Remove duplicate, consolidate |
| Contract term mismatch | Dates don't align with billing plan | Correct dates or billing plan |
| Missing authorization code | Required code not entered | Enter correct authorization code |
| Invalid order type | Order type doesn't match deal | Correct the order type |
| Missing predecessor quote | Restructure has no source quote linked | Link source quote in Harmony |
| OBV mismatch | Original Booked Value doesn't match source | Recalculate OBV from source contract |
| Missing billing plan | No billing plan on a line item | Add billing plan to every line item |

## C — SWAP / Restructure Compliance

C2CEP (Cloud-to-Cloud Extension Program) rules:
1. Replacement start date must fall within permitted window before source contract end.
2. Source contract must still be active.
3. No downsell without approved exception.
4. Correct Harmony quote type must be selected.

| Quote Type | When to Use |
|-----------|-------------|
| OQR | Replacing contract outside current fiscal quarter |
| IQR | Replacing contract within current fiscal quarter |
| ADMIN | Administrative change only, no commercial change |
| SWAP | Replacing one product with a different product |
| Change Quote | Minor amendment to an active quote not yet booked |

Key checks: C2CEP window met? Source contract active? Correct quote type?
SOURCE_QUOTE_ID present? OBV correctly calculated?

## D — Deal Model Validation

| Deal Type | Required Harmony Order Type |
|-----------|-----------------------------|
| New Business | New |
| Renewal | Renewal |
| Upsell | Upsell |
| Cross-sell | Cross-sell or New |
| SWAP | Restructure |
| OQR / IQR | Restructure |
| ADMIN | Admin / Restructure |

FBS out-of-scope scenarios (if ASSIGNED_SSE = yes):
- Simple Upsell small volume
- Cross-sell with Assigned SSE
- Simple Administrative changes
- LoB quotes with Assigned SSE

## E — Approval Routing

| Scenario | Required Approver |
|----------|-------------------|
| Standard deal within guidelines | AE self-approval |
| Discount above standard threshold | CBP / First Approver |
| ACV above self-approval limit | CBP / Sales Manager |
| Any OQR, IQR, or SWAP | CBP / First Approver always required |
| Floor price exception | Deal Desk + CBP |
| Downsell | CBP + higher DOA level |
| Manually overridden DHI flag | CBP / First Approver sign-off |

## F — BOM Completeness

| Issue | Fix |
|-------|-----|
| Missing mandatory product | Add the companion product line |
| Wrong quantity | Correct quantity on affected line |
| Missing billing plan | Add billing plan to every line item |
| Incorrect contract dates | Align all line item dates with header |
| Missing configuration | Complete all required configuration fields |
| Outdated price | Refresh price from current price book |
| Wrong SKU | Replace with correct SKU for region/deployment |
