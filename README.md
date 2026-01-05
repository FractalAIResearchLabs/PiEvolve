<h1 align="center">Pi-Evolve</h1>

<div align="center">


📄 **[Tech Report](https://github.com/baidubce/FM-Agent/blob/main/docs/FMAgent_TechReport.pdf)** |
📌  **[PiML (PiEvolve-Beta) at AutoML,25](https://openreview.net/pdf?id=Nw1qBpsjZz)**
</div>

![Pi-Evolve Architecture](assets/pievolve_arch_v3_background.png)


## Technical Details

### Introduction

Pi-Evolve is a persistent evolutionary framework for autonomous machine learning and scientific discovery. Pi-Evolve reframes algorithmic optimization as graph-structured evolutionary search over solution trajectories, where each node encodes reasoning, executable code, and empirical validation, and edges capture parent–child lineage across iterative improvement cycles. Unlike prior evolutionary agents that operate over unstructured populations, Pi-Evolve evolves a directed acyclic graph (DAG) of NodeChains, enabling explicit reasoning over historical dependencies and fine-grained credit assignment across evolving solution paths. At its core, Pi-Evolve employs a probabilistic action selection policy;balancing exploration and exploitation via adaptive priority scoring; to orchestrate the operations of specialized LLM-driven agents.

### 🧬 Evolutionary Search as Graph Expansion

PiEvolve maintains a growing directed acyclic graph (DAG) of solution states. Each node represents a concrete execution step such as drafting a new approach, refining an existing pipeline, or debugging a failure. Edges capture how one solution evolves from another. A sequence of connected nodes forms a solution chain, representing a coherent line of reasoning and experimentation. Multiple solution chains coexist, allowing PiEvolve to explore alternatives in parallel, preserve failed or partial attempts, and reuse intermediate insights instead of discarding them.

### 🤖 Action Space and Agentic Operations

At every iteration, PiEvolve selects a high-level action that determines how the solution graph is expanded. Actions include drafting new solutions, improving or debugging existing ones, merging ideas across chains, and applying small mutations to escape local optima. Each action is executed by an agent that produces reasoning, generates executable code, runs it, and records the outcome. The result is immediately fed back into the graph, closing the loop between reasoning, execution, and learning.

### 🎯 Probabilistic Control of Exploration and Exploitation

Action selection is governed by a probabilistic policy conditioned on the current solution graph. Each active solution chain maintains a priority score that reflects both its quality and recent progress. When overall performance is weak, PiEvolve favors exploratory actions that introduce new ideas. As strong solution chains emerge, the system increasingly focuses on refinement and debugging. This adaptive balance prevents premature convergence while maintaining steady improvement.

### 🧠 Persistent Memory and Continuous Optimization

All reasoning traces, code, execution results, and scores are stored persistently in the solution graph. Poorly performing or stagnant chains are automatically deprioritized or terminated, allowing computation to focus on more promising directions. By combining long-term memory with iterative feedback, PiEvolve enables continuous, robust optimization without restarting the search or relying on a single best guess.


## Performance Metrics

PiEvolve achieves state-of-the-art performance across difficulty tiers while maintaining competitive runtime efficiency. As shown in Table X, PiEvolve attains the highest overall success rate (61+%) among all evaluated agents, outperforming strong baselines such as Famou-Agent 2.0 and ML-Master 2.0 across Low/Lite, Medium, and aggregate settings. Notably, PiEvolve matches the best reported performance on High-difficulty tasks while exhibiting substantially stronger gains in Medium regimes, indicating robust optimization beyond easy cases.

From an efficiency perspective, PiEvolve demonstrates a favorable performance–compute tradeoff. Despite operating under a standard 24-hour budget, its results are competitive with or superior to agents requiring longer runtimes (e.g., Neo at 36h). Moreover, when considering shorter-horizon performance, PiEvolve ranks 3rd among all agents evaluated at a 12-hour runtime, highlighting its ability to discover high-quality solutions early in the search process. These results suggest that PiEvolve’s persistent evolutionary control and memory-driven refinement enable both scalable performance and efficient use of compute, outperforming prior agentic and AutoML baselines such as AIDE by a large margin.

![PiEvolve Performance](assets/pievolve_performance.png)


## Citation

If you use Pi-Evolve agent, cite us:

```bibtex
@misc{PiEvolve,
      title={Pi-Evolve: Long-Horizon Evolutionary Optimization for Autonomous Scientific Discovery}, 
      author={Sai Botla and Kirubanath Sankar and Abhishek Chopde},
      year={2025}
}
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact Us

- GitHub Issues: [Submit Issue](https://github.com/FractalAIResearchLabs/PiEvolve/issues)

---
