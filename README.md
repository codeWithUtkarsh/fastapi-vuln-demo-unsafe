# fastapi-vuln-demo

Hello World FastAPI app with intentionally outdated, vulnerable dependencies.
For testing vulnerability scanners only. Do not deploy.

## Run
    docker build -t fastapi-vuln-demo .
    docker run -p 8000:8000 fastapi-vuln-demo
    curl localhost:8000

## Scan
    trivy fs .
    pip-audit -r requirements.txt
    trivy image fastapi-vuln-demo
    grype fastapi-vuln-demo

## Expected findings
- python-multipart 0.0.6: CVE-2024-24762 (fixed in 0.0.7)
- GitPython 3.1.31: CVE-2023-40267 (RCE via insecure clone/clone_from options, CVSS 9.8 critical; fixed in 3.1.32), CVE-2023-41040 (path traversal; fixed in 3.1.35)
- starlette 0.35.1: CVE-2024-47874 (fixed in 0.40.0), CVE-2025-54121 (fixed in 0.47.2)
