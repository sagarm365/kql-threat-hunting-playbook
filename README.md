Production KQL detection rules for Microsoft Defender XDR — AiTM, password spray, brute force, phishing, and identity-based attacks. MITRE ATT&CK mapped.

## AiTM Detection Suite
A complete 4-query detection chain covering the full AiTM attack lifecycle:

| Query | Technique | MITRE |
|-------|-----------|-------|
| High-Confidence AiTM Detection | Phishing click → MFA → Different IP | T1557, T1566 |
| Session Replay / Token Theft | Same session across countries/browsers | T1539, T1550.004 |
| MFA Session Reuse | MFA token replayed from multiple locations | T1111, T1557 |
| Post-AiTM BEC Activity | Inbox rules, OAuth abuse, mail forwarding | T1114.003, T1137 |
