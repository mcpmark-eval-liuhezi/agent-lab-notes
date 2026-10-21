# Starred Research Digest

Quarterly open-source engagement summary, grounded in the GitHub activity I actually follow.

## Overview

- **Starred repositories reviewed:** 6
- **Chosen repository (most recently starred, with open issues/PRs):** [OpenBMB/AgentCPM](https://github.com/OpenBMB/AgentCPM)
- **Why chosen:** The most recently starred repository in my starred list; it had open issues and pull requests, so no fallback was needed.

## Deep-Dive Issue: #16 — "Release research benchmarks and Wiki2024 on Hugging Face"

**Issue link:** https://github.com/OpenBMB/AgentCPM/issues/16
**Status:** Open · **Comments:** 4

### Comment Thread Summary

- **@NielsRogge (Hugging Face open-source team, issue author)** opened the thread after seeing the AgentCPM paper featured on HF Daily Papers. He praised the team for already hosting the AgentCPM-Report checkpoints (including GGUF versions) on the Hub, and asked whether the **DeepResearch Bench**, **DeepConsult**, **DeepResearch Gym** benchmarks and the **Wiki2024** corpus (then only on ModelScope) could also be hosted on Hugging Face Datasets for better visibility and easier loading via `datasets.load_dataset`.
- **@Kaguya-19 (repository collaborator)** replied that DeepResearch Bench is already available at `muset-ai/DeepResearch-Bench-Dataset`; DeepConsult and DeepResearch Gym have no official HF dataset yet and they may upload a third version; and Wiki2024 is roughly **140 GB**, which is large, and they are suffering from an unstable connection to Hugging Face but will try to upload it anyway.
- **@NielsRogge** thanked them and offered HF's help, cc'ing **@adeenayakup**.
- **@adeenayakup (Hugging Face)** acknowledged and looped in **@xianbaoqian** to support the upload.
- **@xianbaoqian (Hugging Face)** closed the loop, offering help with uploading Wiki2024 or any other dataset if problems arise.

### Where the Discussion Stands

The thread is a friendly, cooperative coordination effort between the repository maintainers and the Hugging Face team to get AgentCPM's benchmark datasets and the large Wiki2024 corpus mirrored on the Hub. The maintainers have committed to attempting the uploads (the main obstacle being Wiki2024's ~140 GB size and connectivity), and multiple HF staff have volunteered support, but no upload has yet been confirmed as complete — the issue remains open pending that.

### Participants

- @NielsRogge (Hugging Face, issue author)
- @Kaguya-19 (AgentCPM collaborator/maintainer)
- @adeenayakup (Hugging Face)
- @xianbaoqian (Hugging Face)

## Pull Request Review Comments Examined

The most recently updated **open** pull request in OpenBMB/AgentCPM is **PR #17** — ["fix: replace bare except clauses with except Exception"](https://github.com/OpenBMB/AgentCPM/pull/17), which replaces 16 bare `except:` clauses across 12 files with `except Exception:` to avoid swallowing `SystemExit`/`KeyboardInterrupt` in the AgentDock, AgentRL, and AgentToLeaP modules.

- **Review comments on PR #17: none.** As of this digest, PR #17 has no inline review comments and no submitted reviews at all — it has been sitting unreviewed since it was opened on 2026-02-25.
- **Fallback check (recently merged PRs):** the only merged pull request in the repository is **PR #5 — "AgentCPM-Report"** (merged 2026-01-20), and it likewise has **zero review comments**.
- **Takeaway:** this repository's maintainers have not left any inline code-review feedback on pull requests so far; collaboration appears to happen primarily in issue threads (as seen in issue #16) rather than through PR review comments. There is no example yet of how these maintainers phrase review feedback.

---
*Generated as part of the quarterly open-source engagement summary.*
