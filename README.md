# Sigstore Offline Test

This repository demonstrates offline verification of container images using Sigstore/Cosign in GitHub Actions workflows.

## Overview

This project tests the ability to verify container image signatures using Cosign in offline mode, ensuring that signature verification can work without internet connectivity by pre-caching the necessary TUF root metadata.

## Workflows

### Matrix Workflow ([matrix.yaml](.github/workflows/matrix.yaml))
- Sets up Cosign with an older version (v2.4.0) to test TUF root updates
- Downloads and caches the sigstore root metadata
- Verifies multiple container images in parallel using a matrix strategy
- Tests offline verification by pre-downloading the sigstore root

### Single job Workflow ([linear.yaml](.github/workflows/linear.yaml))
- Performs bulk verification of container images in a single job
- Uses offline mode with parallelized verification (15 max workers)
- Verifies that cosign-installer's own verification process prepares the TUF root for offline use
