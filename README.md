# NU7 Evolution verification evidence

Captured October 16, 2026 UTC from production build of frontend commit `dca8c913cbc6f2a54de4bcb67999ba04c90fbd29`, integration branch `feat/nu7-evolution`.

Route: `http://localhost:3007/en/zcash-evolution#nu7` (default English canonicalizes to `/zcash-evolution#nu7`). Also verified `/it/zcash-evolution#nu7`.

| Capture | Viewport | State |
| --- | --- | --- |
| desktop-expanded.png / desktop-collapsed.png | 1440 × 1000 | NU7 element, expanded / collapsed |
| desktop-page.png | 1440 × 1000 | Full page, expanded |
| phone-expanded.png / phone-collapsed.png | 390 × 844 | NU7 element, expanded / collapsed |
| phone-page.png | 390 × 844 | Full page, expanded |
| phone-sequence-1.png through phone-sequence-3.png | 390 × 844 | Overlapping viewport captures down the expanded card |
| narrow-expanded.png | 320 × 844 | Full NU7 element |
| narrow-guide-focus.png | 320 × 844 | Keyboard focus ring on the community guide |

Element/full-page PNG dimensions exceed the viewport to include the full content. No application content was hidden or modified for these real Chromium captures. Existing sticky site navigation and floating chatbot may appear over parts of tall captures; overlapping viewport captures supply additional context. All captures visually inspected: separate rollout labels, pending Mainnet height, visible notice, wrapping links, comparison, issuance explanation, and keyboard focus are readable. At 320px the existing site navigation produces 323px document width; the card fits the viewport and adds no overflow.

## Validation

- `yarn tsc --noEmit`: passed.
- `NEXT_TELEMETRY_DISABLED=1 yarn build`: passed. Existing missing OWNER/REPO/BRANCH settings cause remote-content generation to skip; curated navigation/search fallback remains in use.
- `EGRESS_BASE_URL=http://localhost:3007 yarn test:e2e e2e/evolution-nu7.spec.ts --workers=2`: 10 passed against `yarn start --port 3007` (4.9 seconds).
- `git diff --check`: passed.
- Standards/accessibility review: zero actionable introduced findings. Spec review: zero actionable code findings.
- `yarn lint`: existing failure, ESLint 9 cannot find flat `eslint.config.*`; configuration and package files are unchanged from the base. No lint pass claimed.

Browser coverage: collapsed/expanded scope and notice; distinct network rows and Mainnet-qualified badge; Ironwood hero and one NU7 meter segment; comparison and issuance wording; independent notice/source link activation and focus; Enter/Space; hash opening/scroll; desktop/390px/320px; historical Genesis/Sapling/Ironwood; Italian route. External navigation is intercepted in interaction tests; source reachability/applicability was checked separately against live sources.

## Sources rechecked October 16, 2026

- [ZIP 259](https://zips.z.cash/zip-0259): Draft; deployment scope still matches the card, Testnet height set, Mainnet height pending.
- [Zcash Foundation rollout update](https://forum.zcashcommunity.com/t/zf-engineering-update-21-september-5-october-2026/58059): October 4 Testnet activation; November 5 tentative Mainnet date.
- [ZIP 218](https://zips.z.cash/zip-0218), [ZIP 235](https://zips.z.cash/zip-0235), [ZIP 237](https://zips.z.cash/zip-0237), and [ZIP 2008](https://zips.z.cash/zip-2008): spacing/issuance, fees, NSM and recipient update verified. All remaining linked ZIP URLs return the expected documents.
- [ZIP 2003](https://zips.z.cash/zip-2003) and the browser-rendered [community recovery guide](https://zechub.wiki/using-zcash/recovering-funds): Sprout-specific limitation and supported wallet/key guidance checked. The card preserves official tentative rollout wording and offers no universal or post-activation recovery promise. No wallet operations performed.

These artifacts live on a separate evidence branch so screenshots and local planning files do not enter the frontend PR diff.
