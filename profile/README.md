## Kenotic Labs

**The continuity layer for AI systems.**

Store from Claude. Retrieve from ChatGPT. Reconstruct from Cursor. Same memory, same device.

---

### Install

```bash
pip install kenotic
```

```python
from sdk import Kenotic

k = Kenotic(user_id=0)
k.ingest(text="I moved to Detroit in January to start Kenotic Labs.", speaker="Sam")
k.ingest(text="My dog Kobe is a 2-year-old golden retriever who loves swimming.", speaker="Sam")

result = k.retrieve(query="What is Sam's dog's name?")
print(result.text)  # "a golden retriever named Kobe"
```

Or connect any AI via MCP / REST:

```bash
python -m mcp.http_server --port 7130
```

```bash
curl -X POST http://localhost:7130/api/v1/retrieve \
  -H "Content-Type: application/json" \
  -d '{"query": "What is Sam building?"}'
```

---

### What It Does

Every message is decomposed into **5 structured traces** — episodic, emotional, temporal, relational, schematic — and stored in on-device SQLite.

Retrieval is **reconstruction, not search**. The system doesn't find similar chunks. It rebuilds the answer from converging traces using MINERVA 2 resonance dynamics. No LLM in the retrieval loop. Deterministic. Sub-second.

---

### How It's Different

|  | Vector RAG | Mem0 | Kenotic |
|--|-----------|------|---------|
| Storage | Chunks + embeddings | Key-value facts | 5 structured traces |
| Retrieval | Cosine similarity | Keyword lookup | Multi-dimensional resonance |
| LLM in loop | Yes (reranking) | Yes (extraction) | No |
| Update handling | Overwrite | Overwrite | Supersession chain |
| Temporal reasoning | None | None | Built-in |
| Emotional state | None | None | Built-in |
| Model independence | No | Partial | Full (store on Claude, read from GPT) |
| Runs on | Cloud | Cloud / local | 100% on-device |

---

### Repos

| Repo | What |
|------|------|
| [**reconstruct**](https://github.com/Kenotic-Labs/reconstruct) | DTCM engine + MCP server + REST API. The product. |
| [**ATANT**](https://github.com/Kenotic-Labs/ATANT) | Evaluation framework for AI continuity. 250 stories, 1835 questions. |
| [**continuity-layer**](https://github.com/Kenotic-Labs/continuity-layer) | Research paper. arXiv:2604.17273 |
| [**kenoticlabs.com**](https://github.com/Kenotic-Labs/kenoticlabs.com) | Website source. |

---

### The 7 Properties of Continuity

1. **Persistence** — Survives restarts, app closes, device changes.
2. **Update Handling** — Reality changes. Memory updates without breaking history.
3. **Temporal Ordering** — When, in what sequence, with what current status.
4. **Disambiguation** — Two people, two events, two feelings — correctly separated.
5. **Reconstruction** — Not "search results." The current living state.
6. **Model Independence** — One model writes. Another reads. The layer is below the model.
7. **Operational Usefulness** — Works in clinics, libraries, robots — not just chat.

---

### Links

[kenoticlabs.com](https://kenoticlabs.com) | [Docs](https://github.com/Kenotic-Labs/reconstruct/tree/master/docs) | [API Quickstart](https://github.com/Kenotic-Labs/reconstruct/blob/master/docs/api-quickstart.md) | sam@kenoticlabs.com

[LinkedIn](https://linkedin.com/company/kenotic-labs) | [Reddit](https://reddit.com/r/Kenoticlabs)
