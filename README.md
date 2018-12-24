# project1_n
PROJECT 1 - NAVIGATION:

For this project, one will train an agent to navigate (and collect bananas!) in a large, square world.



A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of the agent is to collect as many yellow bananas as possible while avoiding blue bananas.
The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:

0 - move forward.

1 - move backward.

2 - turn left.

3 - turn right.

The task is episodic, and in order to solve the environment, the agent must get an average score of +13 over 100 consecutive episodes.

GETTING STARTED:

In order to get started one has to install some packages which are in the python folder. 
One also has to import UnityEnvironment from unity agents and select the “Banana.x86_64”  environment.  The steps needed to accomplish all of the above are given at the start of the notebook. This assumes folks are running this in the workspace provided by Udacity.
Otherwise, people should following the instructions given here.

https://classroom.udacity.com/nanodegrees/nd893/parts/6b0c03a7-6667-4fcf-a9ed-dd41a2f76485/modules/4eeb16ab-5ac5-47bf-974d-12784e9730d7/lessons/69bd42c6-b70e-4866-9764-9bfa8c03cdea/concepts/319dc918-bd2c-4d3b-80a5-063bb5f1905a

HOW TO RUN THE CODE AND TRAIN THE AGENT: 

The jupyter notebook “Navigation_solved.ipynb” is fully contained notebook which can be used to train the agent. 

The step by step instructions for training the model are below:

(1) First install dependencies given in the ./python folder by running "!pip -q install ./python"

(2) Then import unityagents from UnityEnvironment  by using "from unityagents import UnityEnvironment"

(3) After importing numpy we load he banana collector environment by using the following assignment - "env = UnityEnvironment(file_name="/data/Banana_Linux_NoVis/Banana.x86_64")"

(4) Environments contain brains which are responsible for deciding the actions of their associated agents. Here we check for the first brain available, and set it as the default brain we will be controlling from Python by using the followin code - 
"brain_name = env.brain_names[0]"
"brain = env.brains[brain_name]"

(5) After this we figure out the action_size and state size of the environement by probing the "vector_action_space_size" and "vector_observations[0]" attribute.

(6)The solution invovles a DQN model made up of a local and target Q Network. The Q Netwok is a simple neural network with two hidden layers each with 64 elements. 

(7) In addition to the Q Networks, the DQN model also uses a Replay Buffer which is used to break the correleations present when data is used directly from the environment

(8) The DQN algorithm is provided in the "dqn function". The function resets the environment, samples an action based on the initial state. After that the environment is stepped using the action as a result the next_state, reward and done are obtained. The state,action,next_state,reward,done tuple is added to a ReplayBuffer and then a sample from the ReplayBuffer is used to train the local Q Netowrk.  The target Q Network gets updated by weights of the local Q Network using the "soft_update" function which uses the parameter TAU to balance how much of the local network weigths get transferred to the target network.

(9) The DQN algorithm is run for a number of episodes and the average output is compared against a threshold of 13. Whenever the average across last 100 episodes exceeds 13, the environment is considered solved.

That is pretty much it.
