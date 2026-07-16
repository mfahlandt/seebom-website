---
title: "Documentation"
description: "BOMHort documentation: SBOM management, vulnerability checks via OSV, license compliance, VEX, and Cyber Resilience Act (CRA) readiness on Kubernetes."
keywords: "SBOM management, vulnerability check, Cyber Resilience Act, CRA, SPDX, CycloneDX, VEX, OSV, license compliance, software supply chain security"
---

BOMHort is a Kubernetes-native SBOM visualization and governance platform.

> **BOMHort** (formerly known as **SeeBOM**) is the same project with a new name.
> Read more: [Why we renamed SeeBOM to BOMHort](https://docs.bomhort.dev/docs/getting-started/rename/).

BOMHort is an [OpenSSF](https://openssf.org) **Sandbox Project**.

Official docs: [docs.bomhort.dev](https://docs.bomhort.dev)

## What BOMHort Solves

BOMHort helps engineering and platform teams understand software composition risk at scale.
It combines SBOM ingestion, vulnerability intelligence, VEX context, and license governance in one workflow.

- Ingest large SPDX and CycloneDX inventories (1000+ files)
- Evaluate vulnerabilities via OSV batch queries
- Apply OpenVEX statements to mark effective vs suppressed findings
- Track license posture with policy and exception files (CNCF policy by default)

## Architecture Overview

The monorepo is split into focused runtime components:

- `ingestion-watcher`: cron-driven source scanner that hashes files and enqueues jobs
- `parsing-worker`: scalable workers parsing SBOM and VEX payloads (SPDX, CycloneDX, in-toto envelopes)
- `cve-refresher`: daily background job that rechecks known PURLs for newly published CVEs
- `api-gateway`: stateless REST layer with 19 endpoints for dashboard, SBOM, vulnerability, and license data
- `ui`: Angular 19 dashboard with virtual scrolling, dark mode, and CSS-variable theming

ClickHouse stores analytical tables for SBOM metadata, package arrays, vulnerabilities,
license compliance, queue status, VEX statements, and CVE refresh logs.

## Data Flow

1. Sources are discovered from local files or S3-compatible buckets (S3-native by default).
2. Files are deduplicated by SHA256 and queued in ClickHouse.
3. Workers parse SBOM/OpenVEX, resolve unknown licenses via GitHub, and enrich risk via OSV.
4. Results are written to SBOM, vulnerability, license, and VEX tables.
5. API endpoints aggregate these views for the dashboard and search features.

## Key Capabilities

- **Cross-project CVE impact** using PURL lookups and dependency relationships
- **License compliance** with permissive/copyleft classification and CNCF exceptions
- **Dependency health insights** including archived GitHub repository indicators
- **Version skew detection** across projects
- **Fast search and analytics** powered by ClickHouse arrays and materialized views

## Tech Stack

- **Backend:** Go 1.25, net/http (stdlib)
- **Database:** ClickHouse (MergeTree family)
- **Frontend:** Angular 19, CDK Virtual Scrolling
- **Vulnerability Scanning:** OSV.dev API
- **VEX:** OpenVEX Spec v0.2.0
- **Deployment:** Helm 3, Docker Compose

## Deployment Modes

- Docker Compose for quick local start
- Local Kubernetes with Kind
- Production Kubernetes with Helm charts
- Config-driven customization for theme and UI text without rebuilds

For full setup guides and endpoint-level details, use [docs.bomhort.dev](https://docs.bomhort.dev).





