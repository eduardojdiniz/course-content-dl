# Tutorial 1: Gradient Descend and AutoGrad

Representational Learning (Lee et al., 2009)

Key Components:
1. Objective Function: 
What is the goal of the computation?

2. Learning Rule:
How will weights change to improve the objective function?

3. Architecture
What are the components and connectivity?

4. Initialisation
What are the initial weight values?

It is an hyperparameter.

5. Environment
What is the data provided during learning?

Gradient Descent is like the Braille alphabet.


Nodes in the graph correspond to intermediate variables
Foward pass: compute nodes 

Edges in the graph store partial derivative of head with respect to tail
Backward pass: compute edges

Gradient: multiple edges in the path from output to partial input 

... 0 --0--> 0 --0--> 0 --0--> 0

model.foward(x)
... a --0--> b --0--> c --0--> e

optimizer.zero_grad()
... a --0--> b --0--> c --0--> e

loss.backward()
... a --db/da--> b --dc/db--> c --de/dc--> e

optimizer.step()
... da --db/dx--> b --dc/db--> c --de/dc--> e

Why there is no overfit for the simple regression? The function is too soft.

# Tutorial 2: Learning Hyperparameter
Global minima manifold!

Atractor manifold of the saddle point.

Simmetry breaking initialization to avoid saddle points.

https://losslandscape.com/explorer


Video 5: Why we get a transition point in deep networks? Maybe the weights start converging to 1, and the gradient stop vanishing.

Aim for the maximum stable learning rate.

Hyperparameters interact.

Sees like a log(lr) x depth
log(epoch) x depth relationship.

Initializations that preserve variance across depth are known as "dynamic isometry" initializations (i.e., they maintain similar magnitude of activity and gradients across the network).

Beware of the stochastisist with SGD in the loss error over epochs that is different from the one introduced for too large of learning rates.

# Tutorial 3: Deep Linear Neural Networks

model.parameters() returns all weights in a layer!

Depth (serial processing) derive their power through learning useful internal representations. 

Hierarchical structural in the environment comes from evolution.

See Saxe et al.,  2019, Rogers & McClelland, 2004, Rumelhart & Todd, 1993.

The bumps are just like "clicks"!

The bumps, or state-like transitions, or sigmoid drops, are like the devil's starcase.

These bumps are like bifurcations!

Weight initialization has a large impact on the internal representations and speed of learning.

SVD decouple the wideness of the network into several threads of deep linear networks.

Gradient descent guides the network to first learn the features that carry more information (one chain at a time)

Large initialization puts a random representation in the network to beggin with and bias your representational learning.

The features of a given model are interpreted as a potential hypothesis about the features that a given brain area might be using to represent the stimulus.

Illusory correlations: transient overgeneralizations. Shallow networks don't suffer from illusory correlations. Should we train two types of networks to id illusory correlations?


The Deep Learning Framework:
***
_Objective function:_ Cross entropy loss
_Learning rule:_ Gradient descent with momentum
_Architecture:_ Deep Convolutional ReLU network
_Initialization:_ He et al. (Scaled Gaussian)
_Environment:_ ImageNet dataset
***
The correct for GD training loop in PyTorch:

***
π: optimizer.zero_grad()
Ω:  predictions = model(features)
ß: loss = loss_fun(predictions, targets)
ø: loss.backward()
∆: optimizer.step()
********
Tuning up training:
***
You want **deep, wide, smallish-initialization variance, maximum stable learning rate regime**.

You will know you are there when:
* You see a hint of sigmodal learning trajectory.
* you see internal reps change substantially through learning.
* multiple retrainings yield nearly identical trajectories and internal reps (especially for wide nets).
***
# Outro

In 11:00 in W1D2 outro it seems the network learns the low frequency Fourier components first and then proceeds to learn the high frequency ones.

* More complex assumptions of the input (manifold disentanglement): Chung et al., 2018; Cohen, 2020.
* Rich generative models (input lies in a low-D, curved manifold): Goldt et al., 2019.
* Training dynamics in nonlinear networks: Jacot et al., 2018; Lee et al., 2019; Arora et al., 2019.