# Homomorphic Encryption Logistic Regression with OpenFHE

> **Status: planned rewrite — no OpenFHE implementation has been added or verified in this repository.**

## Overview

This repository is intended to develop a new implementation of logistic regression with homomorphic encryption using [OpenFHE](https://github.com/openfheorg/openfhe-development). It is motivated by and links to the earlier [HELR (Homomorphic Logistic Regression on Encrypted Data)](https://github.com/reneroliveira/HELR) project.

The goal is to investigate how the encrypted-training workflow of the original project can be rebuilt against OpenFHE's APIs, while keeping any eventual implementation, tests, and results clearly documented separately from the historical HELR codebase.

## Original HELR project

The [original HELR repository](https://github.com/reneroliveira/HELR) is a C++ project for logistic-regression training on encrypted data. Its source uses the HEAAN approximate-arithmetic homomorphic-encryption library and NTL. The code includes data loading and normalization, ciphertext preparation, encrypted and plaintext training paths, and evaluation routines. In the encrypted training logic, the sigmoid-related computation uses a cubic polynomial approximation suitable for approximate arithmetic.

The original repository contains source under `src/`, build files under `Debug/`, a `HEAAN/` dependency tree, example datasets under `data/`, and experiment logs under `logs/`. Its README documents a historical MNIST experiment; those figures are claims from the original project, **not** measurements or results for this OpenFHE rewrite.

## Planned OpenFHE rewrite

The intended work is to:

1. Design an OpenFHE-based approach to encrypted logistic-regression training, including an appropriate approximate-arithmetic scheme and parameter choices.
2. Reimplement necessary operations such as encrypted vector arithmetic, polynomial sigmoid approximation, and iterative model updates using OpenFHE interfaces.
3. Add a plaintext reference path and automated correctness tests for comparison.
4. Document data formats, dependency versions, building, execution, limitations, and reproducible evaluation **after** they are implemented and tested.
5. Assess numerical accuracy, cryptographic parameters, and resource use only when supported by reproducible experiments.

These are **plans, not completed features**. This initial repository contains documentation and a license only: there is currently no OpenFHE application code, validated build procedure, benchmark, or demonstrated encrypted-training result here.

## Relationship, attribution, and licensing

- Original project: [reneroliveira/HELR](https://github.com/reneroliveira/HELR).
- The reviewed original HELR repository has **no top-level LICENSE file**. This means the redistribution or relicensing rights for its own source files are not established by a repository-wide license; public availability alone does not grant permission to reuse them.
- Its `HEAAN/` component includes a license identified as **Creative Commons Attribution-NonCommercial 3.0 Unported**, with copyright attributed in the component's README to **CryptoLab Inc.** That noncommercial license must not be represented as MIT-compatible permission for wholesale inclusion or relicensing.
- For these reasons, **no source code, bundled HEAAN files, datasets, logs, or substantive README text from the original repository have been copied into this project**. This README provides a new, independently written description and link for attribution.
- The MIT license in this repository covers **new original contributions to `helr-openfhe` only**. It does not relicense the original HELR repository, HEAAN, OpenFHE, or any other third-party materials. Any future third-party contributions or dependencies must retain their applicable notices and licensing terms.

## Current contents

- `README.md` — project context, intended scope, and current status.
- `LICENSE` — MIT license for original material in this new repository.

## References

- [Original HELR repository](https://github.com/reneroliveira/HELR)
- [OpenFHE project](https://github.com/openfheorg/openfhe-development)
- [HEAAN upstream repository](https://github.com/snucrypto/HEAAN)
