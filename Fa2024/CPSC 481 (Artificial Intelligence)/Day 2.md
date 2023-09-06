Chapters 2.1-2.3
# Intelligent Agents
*agent*- anything that receives input and acts upon it
- has a function mapping from perception sequence to actions:
- $f:P*\rightarrow A$
- with functions we can **quantify** the performance of an agent's actions

<u>Vacuum Cleaner Example</u>
Perception: location, contents
Actions: TurnLeft, TurnRight, Suck, NoOp


*rationality*- decision making "side-"parameters that leads agents closer to goal
- performance score
- prior knowledge
	- a vacuum might explore its home to learn the layout
- rationality won't lead to perfection, but it should try to maximize the performance score towards its goal

PEAS - example with auto taxi driver
- **P**erformance - safe, fast, legal, comfortable, profits
- **E**nvironment - roads, traffic, pedestrians, weather
- **A**ctuators - steering, engine power, brakes, signal
- **S**ensors - cameras, radar, GPS, in/external sensors


# In-Class Activity: rational agent design
Fraud Detection in Financial Transactions
Performance - measuring how well we're doing
- low \# of user reports
- well-secured systems
Environment
- end-user devices
- public systems (ie. ATM)
Actuators
- debit cards
- cash
Sensors
- camera
- fingerprint reader

# Environment Characteristics
Fully observable
- agent has access to complete and accurate information to make decisions
- ie. chess
Partially observable
- agent has access to limited (and often noisy) information
- ie. poker
**Fully observable environments are easier** to work with, since we don't need to make inferences about our environment

Single agent
- operates autonomously and independently
Multi-agent
- involve multiple agents interacting, collaborating, or competing with each other
	- cooperative: improve others' situation, as well as your own
	- competitive: improve other situations while potentially worsening your own
**Single agent situations are easier** to work with.

Deterministic
- next state of the environment can be completely determined by current state
Stochastic
- future state may not be determined by current state & inputs; **uncertainty**
- independent variables can contribute to the stochastic nature

Episodic
- actions and decisions are **independent** of each other
Sequential
- actions and decisions are influenced by previous actions/events

Static
- state of system **does not change over time** while operating/making decisions
Dynamic
- state of system **changes over time** while operating/making decisions

Discrete
- variables/states can take on a finite/countable set of distinct values
Continuous
- variables/states can take **infinite** number of values

Known
- all outcomes for actions are given
Unknown
- outcome for all actions are not known

<u>Example: soccer</u>
Partially observable
- hard to track other agents due to POV
Multi-agent
Stochastic
Sequential
Continuous


<u>Example: CAPTCHA</u>