# SSDLC for github-ssdlc (Vue)

## Planning
- Security requirements
- Threat modeling (STRIDE)

## Development
- PR-based workflow
- Branch protection + reviews

## Testing
- SAST: CodeQL (every push/PR)
- Secret Scan: Gitleaks (every push/PR)
- Dependency Scan: Trivy/Dependabot (every push/PR)
- DAST: OWASP ZAP (after deploy)

## Release/Deploy
- GitHub Actions deploy to GitHub Pages

## Monitoring
- GitHub Security alerts (Code scanning, Dependabot)
