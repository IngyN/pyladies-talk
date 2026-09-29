# Intro to Reinforcement Learning

Slides and demo notebooks for a PyLadies talk introducing reinforcement learning — from a tabular Q-learning agent on a tiny grid, up to how RL (specifically RLHF) shapes the LLMs we use every day.

**Speaker:** Ingy ElSayed-Aly, PhD
**Event:** PyLadies — September 30, 2026

## About this talk

Reinforcement learning has powered game-playing agents, robotics, and recommendation systems for years — and it's now also the mechanism behind aligning large language models with human preferences. This talk walks through the core RL loop (agent, environment, reward, policy), tabular and deep Q-learning, multi-agent RL, and how the same ideas show up in the LLM training pipeline via RLHF — then puts it into practice with two live demo notebooks.

## Repo contents

```
.
├── notebooks/
│   ├── rl_games_demo_emoji.ipynb       # GridWorld Q-learning + LunarLander PPO
│   └── rlhf_mini_demo_unicorn.ipynb    # Tiny RLHF-style demo with GRPO
└── checkpoints/                        # Contents created when the notebooks run
```

## Getting started

Both notebooks are built to run in Google Colab — click a badge below to open one directly (update the badge URLs once this repo is pushed):

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/IngyN/pyladies-talk/blob/main/notebooks/rl_games_demo_emoji.ipynb)
&nbsp;`rl_games_demo_emoji.ipynb`

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/IngyN/pyladies-talk/blob/main/notebooks/rlhf_mini_demo_unicorn.ipynb)
&nbsp;`rlhf_mini_demo_unicorn.ipynb`

They also run locally (Mac/Linux/Windows) — each notebook auto-detects whether it's on Colab and adjusts font/GPU setup accordingly. See each notebook's first cell for details.

### `rl_games_demo_emoji.ipynb`

Two classic RL demos, both rendered graphically:

- **GridWorld (tabular Q-learning):** a 🦄 unicorn agent learns to reach a 💰 coin while avoiding 🐙 octopus pits. Trains in seconds, so you can watch the policy (arrows) and the learned Q-value table update live, then watch an animated rollout of the final policy.
- **LunarLander (PPO, via `stable-baselines3`):** a random agent vs. a trained agent, with checkpoints saved along the way and a pretrained fallback checkpoint in case live training doesn't fully converge in the time available.

All checkpoints are saved to `checkpoints/`.

### `rlhf_mini_demo_unicorn.ipynb`

A minimal RLHF-style demo using [`trl`](https://github.com/huggingface/trl)'s `GRPOTrainer` (the algorithm behind DeepSeek-R1) on a small model (`Qwen2.5-0.5B-Instruct`). No separate reward model — just a plain Python reward function that specifically favors the unicorn emoji 🦄, with a smaller bonus for any other emoji and a length-shaping term. Compares model outputs before and after a short training run. Requires a GPU runtime.

## Topics covered

- The agent–environment loop: state, action, observation, reward
- Rewards, cumulative reward, and discounting (γ)
- Exploration vs. exploitation
- Q-learning and Deep Q-learning
- Multi-agent reinforcement learning (cooperation/competition, credit assignment, scalability)
- The LLM training pipeline: pre-training → supervised fine-tuning → alignment → optimization
- Reinforcement Learning with Human Feedback (RLHF) and Proximal Policy Optimization (PPO)

## References

1. Lukas Brunke, Melissa Greeff, Adam W Hall, Zhaocong Yuan, Siqi Zhou, Jacopo Panerati, and Angela P Schoellig. "Safe learning in robotics: From learning-based control to safe reinforcement learning." *Annual Review of Control, Robotics, and Autonomous Systems*, 5:411–444, 2022.
2. Marc G. Bellemare, Will Dabney, and Mark Rowland. *Distributional Reinforcement Learning*. MIT Press, 2023. http://www.distributional-rl.org
3. Aske Plaat, Max van Duijn, Niki van Stein, Mike Preuss, Peter van der Putten, and Kees Joost Batenburg. "Agentic large language models, a survey." *arXiv preprint arXiv:2503.23037* (2025).
4. Ahsan Bilal, Muhammad Ahmed Mohsin, Muhammad Umer, Muhammad Awais Khan Bangash, and Muhammad Ali Jamshed. "Meta-thinking in LLMs via multi-agent reinforcement learning: A survey." *arXiv preprint arXiv:2504.14520* (2025).
5. Josef Dai, Xuehai Pan, Ruiyang Sun, Jiaming Ji, Xinbo Xu, Mickel Liu, Yizhou Wang, and Yaodong Yang. "Safe RLHF: Safe Reinforcement Learning from Human Feedback." In *The Twelfth International Conference on Learning Representations*, 2023.
6. Leslie Pack Kaelbling, Michael L Littman, and Andrew W Moore. "Reinforcement learning: A survey." *Journal of Artificial Intelligence Research*, 4:237–285, 1996.

### Resources to learn more

- [Ahead of AI blog by Sebastian Raschka](https://magazine.sebastianraschka.com/)
- [Hugging Face Deep RL Course](https://huggingface.co/learn/deep-rl-course/en/unit0/introduction)
- [Berkeley CS188 course](https://inst.eecs.berkeley.edu/~cs188/archive/su25/)

## About the speaker

Ingy ElSayed-Aly : Research Engineer at Saint-Gobain Recherche, Aubervilliers, France. Previously Lead AI Engineer at REEV (Toulouse, France); PhD and Master's in Computer Science from the University of Virginia; Bachelor's in Computer Science from the American University in Cairo.
