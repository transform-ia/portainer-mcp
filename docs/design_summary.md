# Design Documentation Summary

This document provides a summary of key design decisions for the Portainer MCP
project. Each decision is documented in detail in its own file.

## Design Decisions

| ID                                                                 | Title                  | Date       | Description                 |
| ------------------------------------------------------------------ | ---------------------- | ---------- | --------------------------- |
| [202503-1](design/202503-1-external-tools-file.md)                 | External tools file    | 29/03/2025 | YAML-based tool definitions |
| [202503-2](design/202503-2-tools-vs-mcp-resources.md)              | Tools over MCP         | 29/03/2025 | Tool-based resource access  |
| [202503-3](design/202503-3-specific-update-tools.md)               | Specific update tools  | 29/03/2025 | Split update operations     |
| [202504-1](design/202504-1-embedded-tools-yaml.md)                 | Embedded tools.yaml    | 08/04/2025 | Binary-embedded config      |
| [202504-2](design/202504-2-tools-yaml-versioning.md)               | Tools.yaml versioning  | 08/04/2025 | Versioned tool configs      |
| [202504-3](design/202504-3-portainer-version-compatibility.md)     | Portainer version pin  | 08/04/2025 | Version compatibility       |
| [202504-4](design/202504-4-read-only-mode.md)                      | Read-only mode         | 09/04/2025 | Security restrictions       |

## How to Add a New Design Decision

1. Create a new file in the `docs/design/` directory following the format:
   - Filename: `YYYYMM-N-short-description.md` (e.g.,
     `202505-1-feature-toggles.md`)
   - Where `YYYYMM` is the date (year-month), and `N` is a sequence number for
     that date

2. Use the standard template structure:

   ```markdown
   # YYYYMM-N: Title

   **Date**: DD/MM/YYYY

   ### Context
   [Background and reasons for this decision]

   ### Decision
   [The decision that was made]

   ### Rationale
   [Explanation of why this decision was made]

   ### Trade-offs
   [Benefits and challenges of this approach]
   ```

3. Add the decision to the table in this summary document
