# Mint Skills

This folder contains a small set of Codex skills for processing Mintlify MDX documents.

## Recommended Entry Point

Use `mint-blog-document-processor` as the main orchestrator. It runs a required formatting pass first, then delegates to companion skills when the document contains matching content.

## Structure

```text
mint-skills/
├── mint-blog-document-processor/
└── companion-skills/
    ├── mint-blog-formatter/
    ├── mint-graph-to-mermaid/
    ├── mint-interview-questions-processor/
    ├── mint-navigation-processor/
    ├── mint-reference-processor/
    ├── mint-directory-tree-formatter/
    └── mint-workflow-to-steps/
```

## Skill Index

| Skill | Role |
|---|---|
| `mint-blog-document-processor` | Main orchestrator for Mintlify MDX files |
| `mint-blog-formatter` | Inserts or updates the `Written: YYYY.MM` badge after the first body heading |
| `mint-directory-tree-formatter` | Formats directory trees as titled `text` code fences with a folder-tree icon |
| `mint-graph-to-mermaid` | Converts rough diagrams, PNG flowcharts, and text flows into VectorPeak-style Mermaid |
| `mint-interview-questions-processor` | Converts interview Q&A sections into collapsed accordions |
| `mint-navigation-processor` | Maintains `docs.json` tabs, groups, page order, and route validation |
| `mint-reference-processor` | Converts reference sections into categorized Tabs and Cards |
| `mint-workflow-to-steps` | Backup skill only; converts workflows into Mintlify `<Steps>` when explicitly requested, and is not invoked by the main processor by default |

## Installation

To use the full bundle, copy `mint-blog-document-processor/` and `companion-skills/` together into a Codex skills directory.

The main processor uses relative paths such as `../companion-skills/...`, so keep the folder layout intact.

## Notes

- These skills target Mintlify MDX documents
- Chinese MDX content should be read and written as UTF-8
- The bundle is not a Mintlify official plugin or npm package
