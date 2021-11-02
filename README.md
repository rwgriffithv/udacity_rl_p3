# Udacity Deep Reinforcement Learning<br>Project 3 Submission
Robert Griffith

## Project Details

The goal of this project is to use multi-agent deep reinforcement learning  
techniques to learn policies for two agents each with continuous control  
over their movement to hit a ball back and forth over a net while keeping the  
ball within the field of play. Training is done within the described "Tennis"  
UnityEnvironment, and this environment is provided by Udacity and follows the  
architecture of the open-source Unity plugin **Unity Machine Learning Agents  
(ML-Agents)**.

In this Tennis environment, an agent receives a reward of +0.1 when it hits the  
ball over the net, and receives a reward of -0.01 if it lets a ball hit the  
ground or it hits the ball out of bounds. The goal of an agent in this  
environment is to maximize its rewards over the course of an episode, thus it  
attempts to position itself such that it repeatedly hits the ball over the net  
to the other agent without hitting it out of bounds.

The state space that the agent perceives to perform actions in the environment  
has 8 dimensions and contains the position and velocity of the ball and agent  
racket. Each agent receives its own local observation. Each action has only 2  
dimensions, corresponding to horizontal (perpendicular to the net) and vertical  
(parallel to the net) movement.

This task is episodic, and the environment is considered "solved" upon the  
maximum earned agent score (the maximum is taken over the earned agent episode  
scores) averaged over 100 consecutive episodes being greater than or equal to  
+0.5. An individual agent score for an episode is the cumulative sum of that  
agent's reward from each time step in the episode.


## Repository Contents

| directory | contents |
| ----------| -------- |
| model | saved model weights and recorded scores |
| src | python source files used to train model |

| source file | description |
| ----------- | ----------- |
| todo.py | TODO: class responsible for policy and/or critic gradients |
| nn.py | Neural network utility functions |
| plot.py | Plotting function for csv output from training routine |
| replay.py | Experience replay buffer class |
| train.py | Main function for training an agent to solve a UnityEnvironment |

`Report.md` contains the project report that is required for the submission of  
this project, and contains more detailed descriptions of the methods used in the  
source files listed above.

`src/train.py` utilizes capitalized constants defined at the top of `train(...)`  
and accepts a path to a UnityEnvironment executable; so while its  
hyperparameters and required average score are tuned for the environment used  
in this project specifically, it is designed to be somewhat generalizable. The  
executable path is taken as a command line argument when run as the main  
script. This is done to prevent the need to modify the file when running on  
various machines where the executable path will naturally differ.


## Getting Started

### Step 1: Clone the DRLND Repository
Follow the [instructions in the DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) provided by Udacity to  
set up your Python environment. These instructions are found in the repository's  
own `README.md` file. For this project submission, **steps 2, 4, 5 are not required**  
as OpenAI gym is not utilized and neither are any IPython notebooks.  
**The required steps 1, 3** will install PyTorch, the ML-Agents toolkit, and other  
dependencies.

### Step 2: Download the Unity Environment
You will **not** need to install Unity; only the executable itself is required.  
The following links all correspond to version 2 of this project.  
You will need to select the environment binary that matches your operating system:
* Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
* Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
* Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
* Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)

These links are provided and maintained by Udacity.  
You can unzip this executable wherever you wish. As described earlier, `train(...)`  
from `src/train.py` will take the executable path as an argument.

With this, all dependencies will have been installed. To make your PyTorch  
installation specific to a particular CUDA toolkit version `XY.Z`, within Anaconda  
run the following command: 

`conda install pytorch cudatoolkit=XY.Z -c pytorch`


## Instructions

`src/train.py` contains the function `train(...)` that will be used to train an  
agent to solve this environment. This function can of course be invoked from  
within a Python interpreter, or be invoked from the command line in the following  
way from the root of this repository:

`python -m src.train <PATH_TO_UNITY_ENVIRONMENT_BINARY>`

Upon the completion of training, the following files are written to the working  
directory:
* `TODO`: define all files written here