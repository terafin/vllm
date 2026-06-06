# Fork tracking — intarweb/vllm (image: ghcr.io/intarweb/vllm-openai)

**Mirror-only** fork of [`vllm-project/vllm`](https://github.com/vllm-project/vllm). We mirror the official Docker Hub `vllm/vllm-openai` image into `ghcr.io/intarweb/vllm-openai` so the `llm` host pulls from our registry instead of Docker Hub. No build-from-source (the images are huge CUDA builds we'd never rebuild), no sync-upstream. See the `ghcr-fork-mirror` skill.

| Property | Value |
|---|---|
| Image | `ghcr.io/intarweb/vllm-openai` |
| Source | byte-identical copy of `docker.io/vllm/vllm-openai` |
| Tags | `latest` (float) + `v0.22.1` (pinned known-good anchor). Bump the pin in `TAGS` as you validate releases. |
| Workflow | [`.github/workflows/fork-publish.yml`](.github/workflows/fork-publish.yml) — hourly `39 * * * *` + `workflow_dispatch` |

**Why:** AI infra on the `llm` host (vllm-main + embeddings + reranker + ocr). Docker Hub pull-rate is real on multi-image rebuilds, and pinning a known-good digest while upstream churns is the point.

**Consume:** `image: ghcr.io/intarweb/vllm-openai:latest` (or pin `:v0.22.1`)

> Inherited vllm CI workflows are disabled — this is a mirror, not a build.
