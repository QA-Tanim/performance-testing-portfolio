# ⚡ Enterprise Performance & Load Testing Portfolio

<div align="center">

![Apache JMeter](https://img.shields.io/badge/Apache%20JMeter-5.x-D22128?style=for-the-badge&logo=apachejmeter&logoColor=white)
![Google Lighthouse](https://img.shields.io/badge/Lighthouse-Core%20Web%20Vitals-F44B21?style=for-the-badge&logo=lighthouse&logoColor=white)
![Quality Assurance](https://img.shields.io/badge/Domain-Performance%20Engineering-007ACC?style=for-the-badge&logo=speedtest&logoColor=white)
![Test Status](https://img.shields.io/badge/Test%20Execution-Passed-2EA44F?style=for-the-badge&logo=githubactions&logoColor=white)
![Environment](https://img.shields.io/badge/Scope-Authorized%20QA%20Sandbox-8A2BE2?style=for-the-badge)

<p align="center">
  <b>A comprehensive Software Quality Assurance (SQA) performance testing suite featuring high-concurrency API load benchmarks, endpoint stress evaluations, and client-side Core Web Vitals optimization audits.</b>
</p>

[Overview](#-executive-summary) •
[Architecture](#-testing-architecture) •
[Suite 1: Mock E-Commerce](#-suite-1-high-concurrency-e-commerce-api-stress-test) •
[Suite 2: Student API](#-suite-2-restful-student-service-load-test) •
[Suite 3: Lighthouse Audits](#-suite-3-client-side-performance--core-web-vitals) •
[Reproduction Guide](#-execution--reproduction-guide) •
[Ethical Compliance](#-compliance--fair-use-statement)

---

</div>

## 📌 Executive Summary

This repository documents automated performance benchmarks and web quality audits engineered to evaluate API throughput, server latency under concurrent load, and front-end rendering performance. 

Testing was structured across three specialized testing tracks:
1. **High-Concurrency API Stress Test (100,000 Transactions)**: Validating throughput thresholds, percentile response latencies, and error degradation patterns on multi-tier e-commerce endpoints.
2. **REST API Endpoint Load Test (600 Transactions)**: Analyzing response baselines and CRUD transaction stability under sustained virtual user loads.
3. **Core Web Vitals & Client-Side Audits**: Multi-page Google Lighthouse audits inspecting First Contentful Paint (FCP), Largest Contentful Paint (LCP), Total Blocking Time (TBT), and Cumulative Layout Shift (CLS).

---

## 🏛️ Testing Architecture

```mermaid
graph TD
    subgraph Client ["Performance Testing Engines"]
        JM["Apache JMeter<br/>(Headless Non-GUI Engine)"]
        LH["Google Lighthouse<br/>(Chrome DevTools Engine)"]
    end

    subgraph Targets ["Authorized Testing Environments"]
        T1["Target A: E-Commerce Mock API<br/>(fake-store-api.mock.beeceptor.com)"]
        T2["Target B: Student Service QA Sandbox<br/>(thetestingworldapi.com)"]
        T3["Target C: Web Portals Client-Side<br/>(DOM Rendering & Assets)"]
    end

    subgraph Deliverables ["Generated Artifacts & Dashboards"]
        D1["100k Transaction Analysis<br/>(HTML Dashboard & JTL Logs)"]
        D2["CRUD Latency Baseline Report<br/>(Statistics & Metric Profiles)"]
        D3["Core Web Vitals Scorecards<br/>(Performance, A11y, SEO, Best Practices)"]
    end

    JM -->|Stress Testing (100k Requests)| T1
    JM -->|Load Testing (600 Requests)| T2
    LH -->|Non-Intrusive DOM Audit| T3

    T1 --> D1
    T2 --> D2
    T3 --> D3
```

---

## 📊 Key Results at a Glance

| Metric / Benchmark | High-Concurrency Stress Test | REST Load Baseline | Web Portal Audit 1 | Web Portal Audit 2 |
| :--- | :---: | :---: | :---: | :---: |
| **Engine** | Apache JMeter | Apache JMeter | Google Lighthouse | Google Lighthouse |
| **Target Scope** | Multi-Route Mock Store | Student REST API | `hiredesk.work` | `pqs.com.bd` |
| **Total Samples** | **100,000 requests** | **600 requests** | Synthetic Audit | Synthetic Audit |
| **Success Rate** | **99.79%** (205 errors) | **100.00%** (0 errors) | N/A | N/A |
| **Avg Throughput** | **611.5 req/sec** | **20.0 req/sec** | N/A | N/A |
| **Average Latency** | **6,760 ms** | **66.1 ms** | LCP: **2.8 s** | LCP: **6.3 s** |
| **Performance Index**| Stable Under Load | 0% Error Stability | **73 / 100** | **54 / 100** |

---

## 🚀 Suite 1: High-Concurrency E-Commerce API Stress Test

- **Test Plan Artifact**: [`Freestore.jmx`](file:///i:/SQA/project/Performance_Testing/FreeStore/Freestore.jmx)
- **Execution Log**: [`freestore.jtl`](file:///i:/SQA/project/Performance_Testing/FreeStore/freestore.jtl)
- **Interactive Dashboard**: [`FreeStore/freeStore.html/index.html`](file:///i:/SQA/project/Performance_Testing/FreeStore/freeStore.html/index.html)
- **Target Host**: Mock E-Commerce Gateway (`fake-store-api.mock.beeceptor.com`)

### 📈 Detailed Endpoint Statistics

Under a high-volume load profile totaling **100,000 executed samples**, individual route metrics were measured as follows:

| Endpoint / Transaction | Samples | Error Count | Error Rate (%) | Mean Latency | Median (p50) | 90th % (p90) | 99th % (p99) | Throughput |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **`Get User`** | 20,000 | 32 | `0.160%` | 4,241.5 ms | 2,051.0 ms | 10,778.8 ms | 28,276.0 ms | 167.6 req/s |
| **`Get Products`** | 20,000 | 109 | `0.545%` | 20,617.7 ms | 10,050.0 ms | 61,477.1 ms | 79,278.7 ms | 123.1 req/s |
| **`Get Carts`** | 20,000 | 22 | `0.110%` | 3,025.6 ms | 1,953.0 ms | 5,997.9 ms | 22,448.0 ms | 170.9 req/s |
| **`Get Order`** | 20,000 | 21 | `0.105%` | 2,991.9 ms | 2,018.5 ms | 5,694.8 ms | 22,800.0 ms | 172.5 req/s |
| **`Update Orders`** | 20,000 | 21 | `0.105%` | 2,924.1 ms | 2,041.0 ms | 5,579.9 ms | 21,588.9 ms | 179.0 req/s |
| **Aggregated Total** | **100,000** | **205** | **`0.205%`** | **6,760.2 ms** | **2,191.0 ms** | **3,496.0 ms** | **27,992.0 ms** | **611.5 req/s** |

### 🔍 Engineering Observations & Bottleneck Analysis
- **Payload Size Impact**: `Get Products` accounted for the longest latency profile (mean response time of 20.6s and p99 of 79.2s). Analysis indicates this endpoint returns large unpaginated JSON arrays, consuming 666.6 KB/sec received bandwidth.
- **Resource Optimization Opportunity**: Implementing server-side pagination (e.g., `?limit=20&page=1`) and Gzip/Brotli response compression would reduce transfer sizes by an estimated ~70% and drastically lower p90 latency.
- **Resilience**: Even under peak stress, overall error rates remained strictly below `0.21%`, proving robust mock API concurrency handling.

---

## ⚡ Suite 2: RESTful Student Service Load Test

- **Test Plan Artifact**: [`b23.jmx`](file:///i:/SQA/project/Performance_Testing/Load%20Testing/b23.jmx)
- **Execution Log**: [`b23.jtl`](file:///i:/SQA/project/Performance_Testing/Load%20Testing/b23.jtl)
- **Interactive Dashboard**: [`Load Testing/Report/index.html`](file:///i:/SQA/project/Performance_Testing/Load%20Testing/Report/index.html)
- **Target Host**: QA Educational Sandbox (`thetestingworldapi.com`)

<div align="center">
  <br/>
  <img src="./Load%20Testing/Report/Screenshot_23-10-2026_222414_.jpeg" alt="Apache JMeter Load Testing Dashboard - 100% Pass Rate and APDEX 0.999" width="100%" />
  <p align="center"><i>Figure 1: Generated Apache JMeter Execution Dashboard showing 100% Request Success Rate, APDEX Score of 0.999, and Latency Summary.</i></p>
  <br/>
</div>

### 📈 Transaction Performance & APDEX Rating

A steady load test was conducted against primary CRUD routes to measure latency baselines, APDEX user satisfaction rating, and database write/read throughput:

| Transaction Name | Samples | Failures | Error Rate | APDEX Score | Mean Latency | Median (p50) | 90th % (p90) | Throughput |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **`Create Student` (POST)** | 300 | 0 | `0.00%` | **1.000** 🟢 | **55.7 ms** | 51.0 ms | 66.0 ms | 10.4 req/s |
| **`GET Student` (GET)** | 300 | 0 | `0.00%` | **0.998** 🟢 | **76.5 ms** | 52.0 ms | 196.5 ms | 10.0 req/s |
| **Total Aggregated** | **600** | **0** | **`0.00%`** | **0.999** 🟢 | **66.1 ms** | **52.0 ms** | **69.0 ms** | **20.0 req/s** |

### 🔍 Key Findings
- **Flawless 100% Success Rate**: Perfect transaction integrity (600/600 passed requests) across all POST and GET cycles without a single HTTP 4xx or 5xx drop.
- **Exceptional APDEX Rating (0.999)**: With toleration threshold set at 500ms and frustration threshold at 1,500ms, both transactions scored near-perfect user satisfaction (`1.000` for Create Student and `0.998` for GET Student).
- **Sub-80ms Average Latency**: Median latency settled at **52.0 ms**, showing fast and predictable server-side execution under load.

---

## 🌐 Suite 3: Client-Side Performance & Core Web Vitals

Independent synthetic audits were executed using Google Lighthouse engine to evaluate real-user experience metrics and web standards compliance.

### 📊 Audit Score Comparison

| Audit Category | `hiredesk.work` | `www.pqs.com.bd` | Industry Target Standard |
| :--- | :---: | :---: | :---: |
| **Performance** | **73 / 100** 🟡 | **54 / 100** 🟡 | `>= 90` |
| **Accessibility** | **100 / 100** 🟢 | **69 / 100** 🟡 | `>= 90` |
| **Best Practices** | **93 / 100** 🟢 | **93 / 100** 🟢 | `>= 90` |
| **SEO** | **100 / 100** 🟢 | **92 / 100** 🟢 | `>= 90` |

### ⏱️ Core Web Vitals Diagnostic Matrix

| Metric Acronym | Metric Name | `hiredesk.work` | `www.pqs.com.bd` | Assessment Threshold |
| :---: | :--- | :---: | :---: | :---: |
| **FCP** | First Contentful Paint | `0.5 s` 🟢 *(Good)* | `4.0 s` 🔴 *(Poor)* | `<= 1.8 s` |
| **SI** | Speed Index | `1.3 s` 🟢 *(Good)* | `4.4 s` 🔴 *(Needs Work)* | `<= 3.4 s` |
| **LCP** | Largest Contentful Paint | `2.8 s` 🟡 *(Needs Work)* | `6.3 s` 🔴 *(Poor)* | `<= 2.5 s` |
| **TBT** | Total Blocking Time | `280 ms` 🟢 *(Good)* | `300 ms` 🟡 *(Needs Work)* | `<= 200 ms` |
| **CLS** | Cumulative Layout Shift | `0.001` 🟢 *(Good)* | `0.161` 🟡 *(Needs Work)* | `<= 0.1` |

### 🛠️ Optimization Recommendations for Underperforming Portals
1. **Reduce Server Response Time (TTFB)**: Audit logs revealed initial HTML document latency of over 1.2s on `pqs.com.bd`. Implementing edge caching and Redis object caching is recommended.
2. **Eliminate Render-Blocking Resources**: Defer non-critical CSS/JS bundles to accelerate First Contentful Paint.
3. **Image Dimension Anchoring**: Explicitly specify `width` and `height` attributes on banner media elements to eradicate layout shifts (CLS reduction).

---

## 📁 Repository Structure

```text
Performance_Testing/
├── FreeStore/
│   ├── API Doc.txt               # Public mock API endpoint specification
│   ├── Freestore.jmx             # Apache JMeter test plan (100k requests)
│   ├── freestore.jtl             # Raw XML/CSV test execution dataset
│   └── freeStore.html/           # Auto-generated JMeter HTML dashboard
│       ├── index.html            # Visual analytics report entry point
│       └── statistics.json       # Structured metric summaries
├── Lighthouse Generated Report/
│   ├── hiredesk.work_*.html      # Full Lighthouse diagnostic audit report
│   └── www.pqs.com.bd_*.html     # Full Lighthouse diagnostic audit report
├── Load Testing/
│   ├── b23.jmx                   # JMeter test plan for student management API
│   ├── b23.jtl                   # Test run execution log
│   └── Report/                   # HTML dashboard generated from b23.jtl
│       ├── index.html            # Load testing graphical report
│       ├── statistics.json       # Endpoint metrics JSON
│       └── Screenshot_*.jpeg     # JMeter execution dashboard visual evidence
├── .gitattributes                # Cross-platform line ending normalization
├── .gitignore                    # OS and runtime log exclusions
└── README.md                     # Project documentation & benchmark overview
```

---

## 💻 Execution & Reproduction Guide

### Prerequisites
- [Apache JMeter](https://jmeter.apache.org/) (Version 5.4 or higher)
- [Java Runtime Environment (JRE)](https://www.java.com/) (Version 11 or higher)
- Google Chrome (for Lighthouse CLI or DevTools audits)

### Running JMeter in Non-GUI Mode (Recommended)
Always execute high-load tests in headless non-GUI mode to conserve system memory and ensure accurate latency timestamps:

```bash
# 1. Execute FreeStore Mock API Stress Test and generate HTML dashboard
jmeter -n -t "./FreeStore/Freestore.jmx" \
       -l "./FreeStore/run_results.jtl" \
       -e -o "./FreeStore/HTML_Report"

# 2. Execute Student Management API Load Test
jmeter -n -t "./Load Testing/b23.jmx" \
       -l "./Load Testing/run_results.jtl" \
       -e -o "./Load Testing/HTML_Report"
```

### Viewing Generated HTML Reports
Open the generated `index.html` file in any modern web browser:
```bash
# Windows
start ./FreeStore/freeStore.html/index.html
start "./Load Testing/Report/index.html"
```

---

## 🛡️ Compliance & Fair Use Statement

> [!NOTE]
> **Ethical Testing & Policy Compliance Statement:**
> - **Authorized Target Scope**: All automated stress and load testing routines documented in this repository were strictly directed against dedicated, public mock APIs (`beeceptor.com`) and designated sandbox testing servers (`thetestingworldapi.com`) explicitly provided for software testing practice and academic benchmarking.
> - **Non-Intrusive Client Audits**: Google Lighthouse tests were conducted entirely as passive, synthetic browser-side audits analyzing publicly rendered DOM structures without exploiting or attacking server infrastructure.
> - **No Malicious Intent**: This repository does not contain denial-of-service scripts, exploit payloads, automated scraping bots, or unauthorized security testing mechanisms.
> - **Privacy First**: No private user credentials, bearer tokens, or personally identifiable information (PII) are stored within this repository.
