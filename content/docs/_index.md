---
title: "Documentation"
---

Seebom is a Kubernetes-native SBOM visualization and governance platform.

Official docs: [docs.seebom.dev](https://docs.seebom.dev)

## What Seebom Solves

Seebom helps engineering and platform teams understand software composition risk at scale.
It combines SBOM ingestion, vulnerability intelligence, VEX context, and license governance in one workflow.

- Ingest large SPDX inventories (1000+ files)
- Evaluate vulnerabilities via OSV batch queries
- Apply OpenVEX statements to mark effective vs suppressed findings
- Track license posture with policy and exception files

## Architecture Overview

The monorepo is split into focused runtime components:

- `ingestion-watcher`: cron-driven source scanner that hashes files and enqueues jobs
- `parsing-worker`: scalable workers parsing SBOM and VEX payloads
- `api-gateway`: stateless REST layer exposing dashboard, SBOM, vulnerability, and license endpoints
- `cve-refresher`: background refresh job that rechecks known PURLs for newly published CVEs

ClickHouse stores analytical tables for SBOM metadata, package arrays, vulnerabilities,
license compliance, queue status, VEX statements, and CVE refresh logs.

## Data Flow

1. Sources are discovered from local files or S3-compatible buckets.
2. Files are deduplicated by SHA256 and queued in ClickHouse.
3. Workers parse SPDX/OpenVEX and enrich package risk via OSV.
4. Results are written to SBOM, vulnerability, license, and VEX tables.
5. API endpoints aggregate these views for the dashboard and search features.

## Key Capabilities

- **Cross-project CVE impact** using PURL lookups and dependency relationships
- **License compliance** with permissive/copyleft classification and exceptions
- **Dependency health insights** including archived GitHub repository indicators
- **Fast search and analytics** powered by ClickHouse arrays and materialized views

## Deployment Modes

- Docker Compose for quick local start
- Kubernetes with Helm templates for production-style deployment
- Config-driven customization for theme and UI text without rebuilds

For full setup guides and endpoint-level details, use [docs.seebom.dev](https://docs.seebom.dev).


