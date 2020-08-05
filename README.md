<p align="center">
    <br>
    <img src="https://github.com/SforAiDl/genrl/blob/master/assets/images/genrl.png" width="200"/>
    <br>
<p>
    
[![pypi](https://img.shields.io/badge/pypi%20package-v0.0.1-blue)](https://pypi.org/project/genrl/)
[![GitHub license](https://img.shields.io/github/license/SforAiDl/genrl)](https://github.com/SforAiDl/genrl/blob/master/LICENSE)
[![Build Status](https://travis-ci.com/SforAiDl/genrl.svg?branch=master)](https://travis-ci.com/SforAiDl/genrl)
[![Total alerts](https://img.shields.io/lgtm/alerts/g/SforAiDl/genrl.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/SforAiDl/genrl/alerts/)
[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/SforAiDl/genrl.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/SforAiDl/genrl/context:python)
[![codecov](https://codecov.io/gh/SforAiDl/genrl/branch/master/graph/badge.svg)](https://codecov.io/gh/SforAiDl/genrl)
[![Documentation Status](https://readthedocs.org/projects/genrl/badge/?version=latest)](https://genrl.readthedocs.io/en/latest/?badge=latest)
[![Maintainability](https://api.codeclimate.com/v1/badges/c3f6e7d31c078528e0e1/maintainability)](https://codeclimate.com/github/SforAiDl/genrl/maintainability)
![Lint, Test, Code Coverage](https://github.com/SforAiDl/genrl/workflows/Lint,%20Test,%20Code%20Coverage/badge.svg)

---

[![](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/images/0)](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/links/0)[![](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/images/1)](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/links/1)[![](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/images/2)](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/links/2)[![](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/images/3)](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/links/3)[![](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/images/4)](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/links/4)[![](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/images/5)](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/links/5)[![](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/images/6)](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/links/6)[![](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/images/7)](https://sourcerer.io/fame/Sharad24/Sharad24/genrl/links/7)

---

**GenRL is a PyTorch reinforcement learning library centered around reproducible and generalizable algorithm implementations.** 

Reinforcement learning research is moving faster than ever before. In order to keep up with the growing trend and ensure that RL research remains reproducible, GenRL aims to aid faster paper reproduction and benchmarking by providing the following main features:

- **PyTorch-first**: Modular, Extensible and Idiomatic Python
- **Unified Trainer and Logging class**: code reusability and high-level UI
- **Ready-made algorithm implementations**: ready-made implementations of popular RL algorithms.
- **Faster Benchmarking**: automated hyperparameter tuning, environment implementations etc.

By integrating these features into GenRL, we aim to eventually support **any new algorithm implementation in less than 100 lines**.

**If you're interested in contributing, feel free to go through the issues and open PRs for code, docs, tests etc. In case of any questions, please check out the [Contributing Guidelines](https://github.com/SforAiDl/genrl/wiki/Contributing-Guidelines)**


## Installation

GenRL is compatible with Python 3.6 or later and also depends on `pytorch` and `openai-gym`. The easiest way to install GenRL is with pip, Python's preferred package installer.

    $ pip install genrl

Note that GenRL is an active project and routinely publishes new releases. In order to upgrade GenRL to the latest version, use pip as follows.

    $ pip install -U genrl

If you intend to install the latest unreleased version of the library (i.e from source), you can simply do:

    $ git clone https://github.com/SforAiDl/genrl.git
    $ cd genrl
    $ python setup.py install

## Usage
To train a Soft Actor-Critic model from scratch on the `Pendulum-v0` gym environment and log rewards on tensorboard
```python
import gym

from genrl import SAC, QLearning
from genrl.classical.common import Trainer
from genrl.deep.common import OffPolicyTrainer
from genrl.environments import VectorEnv

env = VectorEnv("Pendulum-v0")
agent = SAC('mlp', env)
trainer = OffPolicyTrainer(agent, env, log_mode=['stdout', 'tensorboard'])
trainer.train()
```

To train a Tabular Dyna-Q model from scratch on the `FrozenLake-v0` gym environment and plot rewards:
```python

env = gym.make("FrozenLake-v0")
agent = QLearning(env)
trainer = Trainer(agent, env, mode="dyna", model="tabular", n_episodes=10000)
episode_rewards = trainer.train()
trainer.plot(episode_rewards)
```
