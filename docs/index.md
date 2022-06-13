# Introduction

Double Open aims to automate open source compliance for the
[Yocto Project](https://www.yoctoproject.org/).

## Overview

Below is a high-level overview of the compliance workflow:

```mermaid
sequenceDiagram
  autonumber

  Build Environment ->> Build Environment: Build the product with Yocto, create SPDX Document for the product
  Build Environment ->> Fossology: Upload source archives of the open-source components
  Fossology ->> Fossology: Scan the source for license and copyright data
  Build Environment ->> Fossology: Query for license and copyright data with file hash values
  Fossology ->> Build Environment: Return license and copyright data for the files
  Build Environment ->> Build Environment: Populate SPDX Document with the license and copyright data
  Build Environment ->> Build Environment: Convert SPDX Document to ORT's data format
  Build Environment ->> Build Environment: Evaluate compliance with ORT's Evaluator
  Build Environment ->> Build Environment: Create notice file and report with ORT's Reporter
```
