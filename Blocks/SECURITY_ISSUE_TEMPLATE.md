## Security: Moderate severity vulnerability in webpack-dev-server

### Description
There are currently two moderate severity vulnerabilities in `webpack-dev-server` (through `@wordpress/scripts` dependency):

1. Source code exposure risk when accessing with non-Chromium based browsers (GHSA-9jgg-88mc-972h)
2. Source code exposure risk when accessing malicious websites (GHSA-4v9v-hfq4-rm2v)

### Current State
- Affects development environment only (webpack-dev-server)
- Present in `@wordpress/scripts` >=20.0.0
- Current version in use: ^30.3.0

### Impact
- Moderate severity
- Only affects development environment
- No production impact
- Risk is limited to local development scenarios

### Proposed Solution
Option 1 (Breaking Change):
- Downgrade `@wordpress/scripts` to version 19.2.4
- This would resolve the vulnerability but requires careful testing due to major version change

Option 2 (Alternative):
- Monitor for updates to `webpack-dev-server` in newer versions of `@wordpress/scripts`
- Implement additional development environment security controls

### Mitigation Steps (Until Fixed)
1. Use Chromium-based browsers for local development
2. Avoid browsing untrusted websites while running the development server
3. Consider running development server only when actively developing

### Technical Details
```
npm audit output:
webpack-dev-server  <=5.2.0
Severity: moderate
webpack-dev-server users' source code may be stolen when they access a malicious web site with non-Chromium based browser - https://github.com/advisories/GHSA-9jgg-88mc-972h
webpack-dev-server users' source code may be stolen when they access a malicious web site - https://github.com/advisories/GHSA-4v9v-hfq4-rm2v
```

### Related Links
- [GHSA-9jgg-88mc-972h](https://github.com/advisories/GHSA-9jgg-88mc-972h)
- [GHSA-4v9v-hfq4-rm2v](https://github.com/advisories/GHSA-4v9v-hfq4-rm2v)

### Labels
- security
- moderate
- development
- dependencies