📊 Performance Testing & AI Anomaly Detection

A full-stack performance-testing framework that:

Runs load, stress, soak, and regression tests with JMeter, Locust, and k6.

Profiles application performance using Pyroscope.

Applies rule-based SLO checks and AI anomaly detection to uncover hidden issues.

Generates detailed build-to-build comparisons and human-readable reports.

🚀 Features

Unified Orchestration: Single command to start Pyroscope, run all tests, collect metrics, and stop the profiler.

Multi-tool Support: JMeter, Locust, and k6 for flexible load scenarios.

Rule-based Gates: Predefined latency, throughput, and error-rate checks.

AI Analysis: ML models to detect anomalies and highlight regressions automatically.

Infrastructure as Code: Terraform + Kubernetes manifests for repeatable environments.

CI/CD Integration: GitHub Actions & Jenkins pipelines ready out-of-the-box.

perf-testing/
├── docs/                # Design & runbooks
├── configs/             # Env configs & thresholds
├── tests/               # Load/stress/soak/regression scripts
├── runners/             # Orchestration & Pyroscope control
├── ai-analyzer/         # AI/ML anomaly detection
├── reports/             # Raw & processed metrics, HTML reports
├── dashboards/          # Grafana/Pyroscope JSON dashboards
├── ci/                  # GitHub Actions / Jenkins files
├── infra/               # Docker, Terraform, Kubernetes manifests
├── utils/               # Log & metrics helpers
├── requirements.txt     # Python dependencies
├── Makefile             # Common commands
└── README.md


| Tool                        | Purpose                  | Install                                                |
| --------------------------- | ------------------------ | ------------------------------------------------------ |
| **Python ≥3.10**            | AI analysis, utilities   | `pyenv` or system package                              |
| **Docker / Docker Compose** | Pyroscope & test runners | [Docker Docs](https://docs.docker.com/)                |
| **JMeter / Locust / k6**    | Performance testing      | As needed                                              |
| **Terraform & kubectl**     | Infra deployment         | [Terraform](https://developer.hashicorp.com/terraform) |
| **GNU Make**                | Shortcuts                | `brew install make` or package manager                 |
| **AWS CLI (optional)**      | S3/Cloud results         | [AWS CLI](https://docs.aws.amazon.com/cli/)            |


git clone https://your-repo-url.git
cd perf-testing
python3 -m venv venv && source venv/bin/activate
pip install -r requirements.txt

make run

make compare

🧠 AI Analysis

Trained models live in ai-analyzer/models/latest/.

ai-analyzer/src/analyze_results.py consumes raw metrics from reports/raw/ and flags anomalies.

Extend or retrain models in ai-analyzer/notebooks/.

🏗️ Infrastructure

Docker: Prebuilt images for Pyroscope and test runners in infra/docker/.

Terraform: Cloud infrastructure to spin up a test cluster (infra/terraform).

Kubernetes: infra/k8s manifests to deploy Pyroscope + Grafana to your cluster.

Deploy example:

cd infra/terraform
terraform init
terraform apply

🔗 CI/CD

GitHub Actions: ci/github-actions/perf-test.yml runs automated tests on pull requests.

Jenkins: ci/jenkins/Jenkinsfile for pipeline integration.

Environment variables (for both CI systems):

Variable	Description
ENV	Target environment (dev/staging/prod)
AWS_PROFILE	Optional AWS profile for artifact uploads
🧰 Common Make Commands
Command	Description
make run	Full profiling + tests + reports
make compare	Compare latest vs previous build
make clean	Remove generated data
make docker-build	Build all docker images
📈 Reports & Dashboards

Raw metrics → reports/raw/

Processed data → reports/processed/

HTML summaries → reports/html/

Grafana dashboards provided in dashboards/perf_overview.json.

🛠️ Troubleshooting

See docs/troubleshooting.md for:

Pyroscope agent connection issues

Load-test script failures

AI analyzer errors

📝 License

MIT or your company’s internal license.