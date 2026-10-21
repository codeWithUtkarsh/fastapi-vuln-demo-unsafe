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
