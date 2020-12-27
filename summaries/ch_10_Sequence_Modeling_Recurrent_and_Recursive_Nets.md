RNN are family of nn for processing sequential data.as CNN is specialized for processing a grid of values X
such as an image, RNN is specialized for processing sequence of values. just like CNN can scale to images
with large height and width, RNN can scale to much longer sequence.RNN can also process sequence of variable
length.

Parameter sharing makes it possible to extend and apply model to examples of different forms
and generalize across them. if there is separate parameters for each time index, it would be difficult to generalize
to different sequence length. A traditional fully connected feedforward network would have separate parameters
for each input features. so it would need to learn rules separately for each position in sentence.

In RNN, each member is a function of previous members of the output. Each member of output is produced 
using the same update rule applied to previous output. RNN may also be applied in  two dimensions across
spatial data such as an images and even when applied to data involving time, network have connections that 
go backward in time, provided entire sequence observed before it provided to network.

#### Unfolding Computational Graphs
A computational graph is the way to formalize the structure of the set of computations, such as those
involved in mapping inputs and parameters of outputs and loss.unfolding recursive and recurrent computation 
into computation graph that has repetative structure.any function involving recurrence can be considered
a RNN. when RNN is used to predict future from past, network learns to use h as kind of lossy summary
of task relevant aspect from past.Unfolding process thus has two advantages.
- Regardless of sequence length,learned model always have same input size.
- it is possible to use same transition function f with same parameters at every time step.

The recurrent graph is succinct. The unfolded graph provides an explicit description of which computation
to perform and also helps to understand information flow forward in time.

#### Recurrent Neural Networks
Some examples of important design patterns for recurrent neural networks include the following
- Recurrent networks that produce an output at each time step and have recurrent connections between hidden units.
- Recurrent networks that produce an output at each time step and have recurrent connections only from the output at
 one time step to the hidden units at the next time step
- Recurrent networks with recurrent connections between hidden units, that read an entire sequence and then produce a single output.<br />

any function computable by a Turing machine can be computed by such a recurrent network of a finite size
Computing the gradient of negative kog-likelihood loss function with respect to the parameters is an expensive operation. 
The gradient computation involves performing a forward propagation pass moving left to right followed by a backward 
propagation pass moving right to left through the graph.

#### Teacher Forcing and Networks with Output Recurrence
The network with recurrent connections only from the output at one time step to the hidden units at the next time step
is strictly less powerful because it lacks hidden-to-hidden recurrent connections. For example, it cannot 
simulate a universal Turing machine.Because this network lacks hidden-to-hidden recurrence, it requires that the 
output units capture all the information about the past that the network will use to predict the future.
The advantage of eliminating hidden-to-hidden recurrence is that, for any loss function based on comparing the prediction
at time t to the training target at time t, all the time steps are decoupled. Training can thus be parallelized, with 
the gradient for each step t computed in isolation.

Models that have recurrent connections from their outputs leading back into the model may be trained with teacher forcing.
The disadvantage of strict teacher forcing arises if the network is going to be later used in an closed-loop mode, with
the network outputs (or samples from the output distribution) fed back as input.

#### Recurrent Networks as Directed Graphical Models
As with a feedforward network, we usually wish to interpret the output of the RNN as a probability distribution, 
and we usually use the cross-entropy associated with that distribution to define the loss.Mean squared error is the 
cross-entropy loss associated with an output distribution that is a unit Gaussian, for example, just as with a 
feedforward network. The edges in a graphical model indicate which variables depend directly on other variables. 
Many graphical models aim to achieve statistical and computational efficiency by omitting edges that do not correspond 
to strong interactions. For example, it is common to make the Markov assumption that the graphical model should contain 
only edges that are dependent to variables, rather than containing edges from the entire history.

#### Modeling Sequences Conditioned on Context with RNNs
RNNs allow the extension of the graphical model view to represent not only a joint distribution over the y variables
but also a conditional distribution over y given x.

#### Bidirectional RNNs
All the recurrent networks we have considered up to now have a “causal” structure, meaning that the state at time t captures
only information from the past and the present input. Some of the models we have discussed also allow information from 
past y values to affect the current state when the y values are available.
In many applications, however, we want to output a prediction of y(t) that may depend on the whole input sequence like in
speech recognition. if there are two interpretations of the current word that are both acoustically plausible, we may 
have to look far into the future (and the past) to disambiguate them.

bidirectional RNNs combine an RNN that moves forward through time, beginning from the start of the sequence, with another
RNN that moves backward through time, beginning from the end of the sequence.

#### Encoder-Decoder Sequence-to-SequenceArchitectures
RNN can map an input sequence to a fixed-size vector.RNN can map a fixed-size vector to a sequence.encoder decoder can 
be trained to map an input sequence to an output sequence which is not necessarily of the same length.This comes up in many
applications, such as speech recognition, machine translation and question answering, where the input and output sequences
in the training set are generally not of the same length.

The idea is very simple: 
- An encoder RNN processes the input sequence. The encoder emits the context C, usually as a simple function of its final
 hidden state. 
- A decoder RNN is conditioned on that fixed-length vector to generate the output sequence Y.
 
 There is no constraint that the encoder must have the same size of hidden layer as the decoder.
 
 One clear limitation of this architecture is when the context C output by the encoder RNN has a dimension that is too
 small to properly summarize a long sequence.
  
#### Deep Recurrent Networks
 The computation in most RNNs can be decomposed into three blocks of parameters and associated transformations
 - from the input to the hidden state
 - from the previous hidden state to the next hidden state, and
 - from the hidden state to the output.
 
 each of these blocks corresponds to a shallow transformation meaning transformation that would be represented by a single 
 layer with in a deep MLP. The experimental evidence is in agreement with the idea that we need enough depth to perform the required mappings.

#### Recursive Neural Networks
Recursive neural networks represent yet another generalization of recurrent net-works, with a different kind of computational 
graph, which is structured as a deep tree, rather than the chain-like structure of RNNs.
Recursive networks have been successfully applied to processing data structures as input to neural nets in natural language processing 
as well as in computer vision.

One clear advantage of recursive nets over recurrent nets is that for a sequence of the same length τ, the depth 
(measured as the number of compositions of nonlinear operations) can be drastically reduced from τ to O(log τ), which 
might help deal with long-term dependencies.