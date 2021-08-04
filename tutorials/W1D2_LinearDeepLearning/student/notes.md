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

