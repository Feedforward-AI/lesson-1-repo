---
name: parallel-analyze
description: Analyze documents using parallel sub-agents for faster processing
---

# Parallel Analyze

Analyze documents using parallel sub-agents for faster processing.

## Usage

```
/parallel-analyze [folder-path]
```

If no folder path is provided, defaults to `docs/`.

## What This Does

This command invokes the `parallel-analyzer` agent, which:

1. Inventories all documents in the folder
2. Divides them into batches of 3-5 documents
3. Dispatches `document-batch-analyzer` sub-agents for each batch
4. Synthesizes results into a unified analysis

## When to Use

- Large document collections (10+ files)
- When you want faster analysis
- When documents can be analyzed independently before synthesis

## Compared to /analyze-documents

| Aspect | /analyze-documents | /parallel-analyze |
|--------|-------------------|-------------------|
| Speed | Sequential | Parallel |
| Best for | Small collections | Large collections |
| Approach | Single pass | Batch + synthesize |

## Output

Same format as `/analyze-documents`, but processed through parallelization.

## Behind the Scenes

This demonstrates **agent orchestration**—a coordinator breaking work into pieces, dispatching workers, and synthesizing results.

$ARGUMENTS
folder_path: Path to folder containing documents (default: docs/)
