# Overview, Design concepts, Details: Game modelling
## Agent Based Modelling and Simulation

Amelia Hoyos and Aura Carolina Serna  
*25 August, 2023*

Four distinct games were conducted within the classroom, each characterized by unique rules. The intention behind these games was to generate an understanding of agent-based modeling and simulation. Subsequently, the games were to be described with the ODD procedure and then modeled.

The initial three games share a lot of similarities, particularly Design Concepts, Initialization, Input Data, and certain submodels. These aspects are presented in general at the end of the descriptions for the three games, with specific differences given for each individual game.

\section {First Game}
\subsection{General Description}
A group of individuals gathers within an open area. Each individual is assigned a number ranging from one to three, with their assigned numbers kept secret from others. The objective is to form groups with individuals who share the same number. Different approaches are taken to achieve this goal: some openly announce their group affiliation, while others hop between people until they find a match. Some remain stationary until distinct groups emerge and subsequently seek out their respective groups. As a result, three distinct groups are eventually formed by the end of the activity.
\subsection{Purpose}
The primary goal of this model is to provide a descriptive framework for understanding the dynamics of group formation in scenarios where agents are able to communicate over long distances. It aims to explain how individual behaviours affect interaction patterns and ultimately the organization of agents into distinct groups.
\subsection{Entities, state variables and scales}
Our entities will be composed of individual agents and agent collectives (already formed groups) that will behave differently. Patches will be used only for positioning. 

\noindent State variables are listed on the following tables.

\begin{center}
\begin{tabularx}{\textwidth}{p{3.4cm}p{1.5cm}p{3.5cm}p{3cm}X}
    \toprule
    \textbf{Variable name} & \textbf{Type} &\textbf{Description} & \textbf{Possible Values} & \textbf{Units} \\
    \midrule
    ID & Constant & Identifies the agent in the whole population & 0 to number of turtles & - \\
    x-coordinate & Variable & Defines the position of the agent relative to the x-axis & [-40, 40] & - \\
    y-coordinate & Variable & Defines the position of the agent relative to the y-axis & [-15, 15] & - \\
    Heading & Variable & Direction the agent is facing & [0, 360] & degrees \\
    Random attribute & Constant & A random attribute separating agents into three groups such as color or number & Green, Orange, Brown & - \\
    Personality & Constant & Type of personality affecting interactions & Leader, Participant, Follower & - \\
    In-group & Variable & Boolean variable indicating if agent is in a group & Boolean & - \\
    Size & Constant & Physical size of the agent & 3 & - \\
    Shape & Constant & Shape of the agent & turtle & - \\
    \bottomrule
\end{tabularx}
\captionof*{table}{Agent Attributes}
\end{center}

\noindent In the real games, the groups where divided according to some number between 1 and 3. Nonetheless, in the simulation we will use color as the random attribute, as it will allow the user to distinguish between groups easily. Personality is a special attribute that will determine individual behaviour. Each personality is described below.
\begin{itemize}
    \item Leader: An agent that communicates with the group regardless of distance from other members. It communicates using long range messages.
    \item Participant: An agent that communicates with other agents only when they are close. The agent approaches the closest agents and questions them.
    \item Follower: An agent that doesn’t actively participate, but waits until somebody questions him to take action or until specific groups are formed.
\end{itemize}


\begin{center}
\begin{tabularx}{\textwidth}{p{3.4cm}p{1.5cm}Xp{1.5cm}}
    \toprule
    \textbf{Variable name} & \textbf{Type} &\textbf{Description} & \textbf{Possible Values}\\
    \midrule
    Agent set & Variable & Group of agents with the same random attribute & - \\
    Random attribute (Identification)  & Constant & A random attribute characterizing the group & Green, Orange, Brown\\
    Leader & Variable & An agent that will determine where the group moves & - \\

    \bottomrule
\end{tabularx}
\captionof*{table}{Group Attributes}
\end{center}

\noindent The spatial resolutions of the model will be 40 x 15 and temporal ones will be until the objective is completed or until one hour has passed. The model will use discrete steps. 

\subsection{Process overview and scheduling}
\begin{center}
\includegraphics[scale=0.35]{ActionDiagram1stGame.png}
\end{center}

## First Game

### General Description

A group of individuals gathers within an open area. Each individual is assigned a number ranging from one to three, with their assigned numbers kept secret from others. The objective is to form groups with individuals who share the same number. Different approaches are taken to achieve this goal: some openly announce their group affiliation, while others hop between people until they find a match. Some remain stationary until distinct groups emerge and subsequently seek out their respective groups. As a result, three distinct groups are eventually formed by the end of the activity.

### Purpose

The primary goal of this model is to provide a descriptive framework for understanding the dynamics of group formation in scenarios where agents can communicate over long distances. It aims to explain how individual behaviors affect interaction patterns and ultimately the organization of agents into distinct groups.

### Entities, state variables and scales

Our entities will be composed of individual agents and agent collectives (already formed groups) that will behave differently. Patches will be used only for positioning.

State variables are listed on the following tables.

**Agent Attributes**

| Variable name | Type      | Description                                          | Possible Values | Units |
|---------------|-----------|------------------------------------------------------|-----------------|-------|
| ID            | Constant  | Identifies the agent in the whole population       | 0 to number of turtles | -     |
| x-coordinate  | Variable  | Defines the position of the agent relative to the x-axis | [-40, 40] | -     |
| y-coordinate  | Variable  | Defines the position of the agent relative to the y-axis | [-15, 15] | -     |
| Heading       | Variable  | Direction the agent is facing                         | [0, 360] | degrees |
| Random attribute | Constant | A random attribute separating agents into three groups | Green, Orange, Brown | -     |
| Personality   | Constant  | Type of personality affecting interactions           | Leader, Participant, Follower | -     |
| In-group      | Variable  | Boolean variable indicating if agent is in a group   | Boolean | -     |
| Size          | Constant  | Physical size of the agent                            | 3       | -     |
| Shape         | Constant  | Shape of the agent                                   | turtle  | -     |

In the real games, the groups were divided according to some number between 1 and 3. Nonetheless, in the simulation, we will use color as the random attribute, as it will allow the user to distinguish between groups easily. Personality is a special attribute that will determine individual behavior. Each personality is described below.

- Leader: An agent that communicates with the group regardless of distance from other members. It communicates using long-range messages.
- Participant: An agent that communicates with other agents only when they are close. The agent approaches the closest agents and questions them.
- Follower: An agent that doesn't actively participate but waits until somebody questions them to take action or until specific groups are formed.

**Group Attributes**

| Variable name | Type     | Description                                     | Possible Values |
|---------------|----------|-------------------------------------------------|-----------------|
| Agent set     | Variable | Group of agents with the same random attribute | -               |
| Random attribute (Identification) | Constant | A random attribute characterizing the group | Green, Orange, Brown |
| Leader        | Variable | An agent that will determine where the group moves | -               |

The spatial resolutions of the model will be 40 x 15, and temporal ones will be until the objective is completed or until one hour has passed. The model will use discrete steps.

### Process overview and scheduling

![Action Diagram](path-to-image/ActionDiagram1stGame.png)

## Third Game

### General Description

A group of individuals gathers in a designated space, with each participant blindfolded. Each individual is assigned a number ranging from one to three, with their assigned numbers kept secret from others. The objective was to form groups with individuals who share the same number. As they come across another agent, they whisper to inquire about each other's assigned numbers. Then they integrate the group. The difference between the first and second games is apparent, interactions between two agents are at random, and there is no sensing apart from two agents touching.

### Purpose

The central objective of this model is to computationally describe a situation where agents cannot sense their environment and interactions occur at random. This will allow the user to comprehend the mechanisms governing the emergence of group formations with these limitations.

### Entities, state variables and scales

Our entities will be individual agents and agent collectives. Patches are used as a grid. State variables are listed in the following tables.

**Agent Attributes**

| Variable name | Type      | Description                                          | Possible Values | Units |
|---------------|-----------|------------------------------------------------------|-----------------|-------|
| ID            | Constant  | Identifies the agent in the whole population       | 0 to number of turtles | -     |
| x-coordinate  | Variable  | Defines the position of the agent relative to the x-axis | [-40, 40] | -     |
| y-coordinate  | Variable  | Defines the position of the agent relative to the y-axis | [-15, 15] | -     |
| Heading       | Variable  | Direction the agent is facing                         | [0, 360] | degrees |
| Random attribute | Constant | A random attribute separating agents into three groups | Green, Orange, Brown | -     |
| In-group      | Variable  | Boolean variable indicating if agent is in a group   | Boolean | -     |
| Size          | Constant  | Physical size of the agent                            | 3       | -     |
| Shape         | Constant  | Shape of the agent                                   | turtle  | -     |

In the real games, the groups were divided according to some number between 1 and 3. Nonetheless, in the simulation, we will use color as the random attribute, as it will allow the user to distinguish between groups easily. Unlike the first two games, personality will not be modeled, and groups will not move (As one can experience with the real-life game, groups don't usually move when they can't see).

**Group Attributes**

| Variable name | Type     | Description                                     | Possible Values |
|---------------|----------|-------------------------------------------------|-----------------|
| Agent set     | Variable | Group of agents with the same random attribute | -               |
| Random attribute (Identification) | Constant | A random attribute characterizing the group | Green, Orange, Brown |

The spatial and temporal resolutions of the model will be the same as in the first game.

### Process overview and scheduling

![Action Diagram](path-to-image/ActionDiagram3rdGame.png)

## General Concepts for First Three Games

### Design Concepts

The basic principles involve individual decision-making strategies to achieve an individual goal, which is belonging to a group. This causes the formation of whole collectives, that have for objective to merge. Some of the properties of the collectives are determined randomly and others by a set of imposed rules. There is no learning and no prediction.

#### Emergence

Based on individual strategies, each agent seeks membership in a specific group, leading to the emergence of collectives. The specific characteristics of the groups are not predetermined but rather result as a consequence of individual interactions. The number of formed groups, the group sizes, and the overall pace of group formation are all outcomes shaped by agents' decision-making processes in all three games.

#### Adaptation

In the first two games, individuals adjust their actions in response to environmental changes, including interactions with other agents or groups, as well as external cues like verbal announcements only on the first. Additionally on the three games, within a group, individuals modify their behavior to ensure they remain on it.

#### Objectives

In the games, at the individual level, the primary objective is for each agent to connect with a group sharing the same color as itself. Collectively, the overarching goal shifts towards group expansion as collectives strive to merge their existing groups with those within their field of vision, resulting in a broader and more interconnected network of affiliations. The success of the objectives varies with each game, but the essential goal is the same.

#### Sensing

In the first two games, individuals perceive immediately the presence of other groups and agents within their field of view. In the first game, they can receive auditory signals about the identity of others. The differentiating factor of the third game is that there is no long-range sensing. Individuals can only know the state of the word in their close vicinity (when another agent is touching it).

#### Interaction

Direct interactions occur between individuals (or groups in case of game 1 and 2) when they encounter each other and compare their assigned colors in every game. Indirect interactions happen only in the first game when agents openly announce their color and others hear them.

#### Stochasticity

There might be some stochasticity in:
- Initial placements (position on the grid and assigned colors)
- Movement patterns, especially in the third as there is no clue on where to go so agents move randomly.
- Choosing of the leader inside collectives (First and Second games).
- The leader's decision to send an auditory signal at any moment in time.

#### Collectives

The individuals form groups based on shared color. When formed, agent sets behave as collectives, moving in the direction the leader chooses. To facilitate modeling, agents will be at a set distance from all others in the group.

#### Observation

The data collected from the model includes: the composition of the formed groups, the number of groups, and the number of individuals in each group, at all ticks during the simulation.

### Initialization

In the model, users are granted the flexibility to determine the population size within the simulation. In the first game, this is facilitated through the user's ability to specify the quantity of leaders, participants, and followers present in the simulation.
In the second game, by the number of leaders and followers. And in the third game, simply by specifying the number of people.

The positions, heading, and color of each agent are determined randomly.

### Input Data

No input data is given to the models while running.

### Submodels

Each agent will be able to walk in the following ways:
- In the first two games, an agent will locate the nearest group/agent in its field of view (Approx. central field of view of a human is ± 60° horizontally). It will move toward it. If the group does not coincide with its color, then it will turn around and identify the next nearest group.
- In the first game, if an agent receives an auditory signal, it will turn its heading toward the signal and move forward.
- In the third game, each agent will continuously walk, choosing a random change in heading of ± 15° (To walk smoothly).

Groups will behave as follows:
- In the first two games, if a group has less than a certain number of members (Determined by the number of people in the simulation), then the group will move together (following a leader that will make the decisions) to try to find other groups/agents with their attribute and merge. When groups have sufficient size, they will stop moving.
- Leaders are chosen in groups according to the following criteria. The leader will be the agent with the highest level of sociability (Leader < Participant < Follower for the first game or Leader < Follower for the second). If there are two or more at the same level, they are chosen at random.
- In the last game, groups will not move.

Asking will be modeled as follows:
- If an agent or group encounters another one and asks, it will initiate an interchange of information where the agent that asks compares their attributes. If they are the same, they join the same group. If not, the agent that asks leaves.
- In the first game, a leader might want to produce a generalized audible signal. This will be done randomly. The signal will be generated in all directions.

## Fourth Game

### General Description

A group of individuals gather in an area, initially forming three distinct groups. The objective for each is to unify by color. In each time step, individuals whose colors deviate from the majority are expelled and must search for new groups. Stability in a group is achieved if a group possesses an equal number of green and orange agents or if all members share the same color. The simulation concludes either when all groups are stable or within a one-hour duration.

### Purpose

The main aim of this model is to describe the dynamics of a social game where groups intend to create a color-based unification. The model intends to provide insights into the complex behavior of groups following basic rules.

### Entities, state variables and scales

Our entities will be composed of individual agents and agent formed groups. State variables are listed in the following tables.

**Agent Attributes**

| Variable name | Type      | Description                                          | Possible Values |
|---------------|-----------|------------------------------------------------------|-----------------|
| ID            | Constant  | Identifies the agent in the whole population       | 0 to number of turtles |
| x-coordinate  | Variable  | Defines the position of the agent relative to the x-axis | [-40, 40] |
| y-coordinate  | Variable  | Defines the position of the agent relative to the y-axis | [-15, 15] |
| Heading       | Variable  | Direction the agent is facing                         | Up, Down |
| Random attribute | Constant | A random attribute that will determine if the agent remains in the group or is expelled | Green, Orange |
| In-group      | Variable  | Boolean variable indicating if agent is in a group   | Boolean |
| Size          | Constant  | Physical size of the agent                            | 3 |
| Shape         | Constant  | Shape of the agent                                   | turtle |

**Group Attributes**

| Variable name | Type     | Description                                     | Possible Values |
|---------------|----------|-------------------------------------------------|-----------------|
| Agent set     | Variable | Group of agents with the same random attribute | - |
| Number with green | Variable | Number of agents with green attribute | Z ∈ [0, N] |
| Number with orange | Variable | Number of agents with orange attribute | Z ∈ [0, N] |

N refers to the number of agents in the agent set. The spatial and temporal resolutions of the model will be the same as in the first game.

### Process overview and scheduling

![Action Diagram](path-to-image/ActionDiagram4thGame.png)

### Design Concepts

The model gives information about the three collectives. This information is sometimes determined by randomness and others by the set of rules imposed. There is no learning, no prediction, and no adaptation by the agents.

#### Emergence

Emergence will be apparent in the interactions of each agent to the collective they belong to. The agents will produce the composition of the group and its future actions. This will affect the rest of the model.

#### Objectives

This game differs from the first three games as it is more directed towards group decision-making strategies to achieve stability. Still, each agent has the basic objective to belong to a group.

#### Sensing

Within the group, every individual can know the color of its peers and can have immediate knowledge of what the majority is.

#### Interaction

There is no interaction between the agents themselves, but an interaction between each agent and the collective to exchange information. The agent tells the collective its color, and in turn, it orders the agent to stay or leave.

#### Stochasticity

The type of agent (Green or orange) and the number of agents in the three initial groups are random. Additionally, the initial heading of the agents and the heading once they enter a group are chosen at random.

#### Collectives

The model is all based on the three initial collectives and on the interactions of agents with the collectives. The collectives will be separated by three horizontal borders, and agents will organize on a straight line within the group (heading North or South). The model will not have borders, so agents in the top group can move to the bottom one without passing through the middle one and vice-versa.

#### Observation

Data collected includes the composition of each of the three groups and the number of agents in each at any point in time.

### Initialization

In the model, users are given the possibility to determine the number of people in each group. Apart from this, they will be able to determine the probability of a given agent being Green or Orange.

### Input Data

No input data is given to the model while running.

### Submodels

A group will determine each time a new member arrives which agents to expel, counting the number of agents being green and the number of agents being orange. All the agents belonging to the minority will be expelled (Their "In-group" variable will be set to false). If there is an equal number of both types, then the group is stable for the moment and does not expel anyone.

This will force agents to move a specific number of steps into the next group (Either north or south depending on their heading).

