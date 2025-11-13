# Compliance Notes — DELF B2 Landing Pages

## 1. Korea-Only Service Scope
- **Audience restriction:** All visible copy (hero notice, FAQ, CTA, structured data) now states that lessons are available exclusively to adult learners residing in the Republic of Korea. There are no non-Korean UI languages, currencies, or location-specific offers.
- **Operational steps to maintain restriction:**
  - Reject inquiries that list non-Korean phone numbers, addresses, or payment methods.
  - Keep DNS/hosting geofencing (if available) limited to Korea or display an auto-redirect notice for foreign IP ranges.
  - Remove any marketing campaigns targeting EU/UK, US, or Brazil regions (ads, newsletters, LMS funnels).

## 2. Aggregate-Only Analytics Configuration
- **Consent Mode enforced:** `gtag('consent','default', {ad_storage:'denied', ad_user_data:'denied', ad_personalization:'denied', analytics_storage:'denied'})` runs before any GA configuration on every page. This blocks storage/reading of GA cookies while still allowing anonymized, modeled reporting.
- **Additional safeguards:** `allow_google_signals:false`, `allow_ad_personalization_signals:false`, and `anonymize_ip:true` are set on the GA config call to prevent personal identifiers from being processed.
- **Operational proof to retain:**
  - Export the current HTML snippets (with timestamps) showing the consent defaults.
  - Capture GA4 Admin screenshots for Data Settings → Data Collection and Data Retention showing signals disabled and retention limited.
  - Store a short Loom/video recording of DevTools › Application › Cookies confirming `_ga`/`_ga_*` are absent when the page loads.

## 3. Evidence for “No Opt-In Required”
- **Traffic scope evidence:** Keep monthly hosting logs that demonstrate traffic originates from Korean IP ranges (can be summarized via GeoIP lookup). Retain at least 12 months of reports.
- **Service policy evidence:** Archive dated copies of hero/FAQ/CTA sections (or PDFs) showing the Korea-only notice in place.
- **Analytics evidence:** Save GA4 “Data Collection” configuration exports plus DevTools network traces showing `gcs=G100` hits (Consent Mode cookieless pings). Re-run and store traces whenever you update the site.
- **Operational log:** When rejecting non-Korean inquiries, keep a redacted record (timestamp + reason) to show enforcement.

Collecting and periodically updating this bundle ensures you can demonstrate why a cookie opt-in banner is not required under GDPR/LGPD/CPRA (no targeted marketing + no personal identifiers stored + non-covered geography).
