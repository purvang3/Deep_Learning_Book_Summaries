we want our model to perform well on unseen data. there are many approches that is designed to reduce test error at 
the cost of training error. and these methods are known as regularization. "Any modification we make to learning
algorithm that is intended to reduce generalization error but not training error". some methods directly applied
on parameters, while some on objective function. sometimes they are designed to encode specific kind of
prior knowledge. sometimes they define preference over simpler model. sometime they use to make underdetermined problem
determined. ensembles are also used as regularization, which combine multiple hypotheses to explain training data.

#### Bias-Variance effect
most regularization methods are applied for regularizing estimator. it works as increasing bias for reducing variance.
making model more simple then over fitted. overly complex model family doesnot include true target 
generating process. good regularizer should make profitable trade, reducing varience significantly and not increasing
bias too much.

#### Parameter Norm Penalties
Many regularization methods are based on limiting capacity of models by parameter norm penalty to objective 
function and it is weighting by parameter alpha. One important point is that we only interested to regularize 
weights which includes affine transformation of two variables than bias requires less data to fit. so unregularizing bias
doesn't include high variance and regularizing bias can lead to underfitting.<br />

sometimes it is also desirable to have seperate penalty with different alpha for each layer of the network.

#### L2 parameter regularization
commonly known as weight decay. addition of weight decay is simply multiplicatively shrink weight vector by constant
factor on each step just before performing gradient update. effect of weight decau is to rescale parameter along the 
axes defined by eigen vectors of H. where eigen value of H is higher than alpha, effect of regularization is
relatively small and when is smaller, weights will shrunk to zero mangnitude.means only direction in which parameters 
contribute significantly to reducing objective functions are preserved and other will be decayed away due to less
contribution in gradient analyzed from eigen values of H.

#### L1 Regularization
adds weighted sum of absolute values of individiual parameters to objective function. L1 regularization results in solution
that is more sparse meaning that some parameters have optimal value as zero. and it can be used extensively for feature 
selection mechanism by making subset of weights zero. 

many regularization methods can be interpreted as MAP bayesian inference. specifically L2 reg is equivalent
to MAP bayesian inference with Gaussoan Prior on weights and L1 regularization is equivalent to log prior
term that is maximized in MAP bayesian inference.

#### Data Augmentation
best way to make ML model to generalize is to train on more data.in limited data situation, one way is to
create fake data with augmentation. Translation of pixels of data in each direction can be useful even though
network is translation invariant. out of plane rotation cannot be implemented but can be effective for augmentation.
Data augmentation can be effective to speech recognition as well. Though nn is robust against noise, but training
nn on noise injected dataset can increase robustness. Noise injection can also work when it is added
 to hidden layers. some unsupervise learning methods like denoising autoencoder to remove noise.

#### Noise Robustness
for some models, addition of noise with infinitesimal variance can act as penalty on the norm of weights.
noise can also be added to weights. it can be interpreted as stochastic implementation of bayesian inference.
this will be bayesian learning where model weights are uncertain and representable via PDF that reflects its uncetainity.

#### Injecting noise at the output targets
maximizing log(y|x) is harmful when y is mistake. by including noise on labels, label y is correct with 1 -eps probability 
otherwise other label is correct.this can be done into cost function in which model with k softmax outputs with 0 and 1 replaced
by 1-eps and eps/k-1 , known as label smoothing. maximum likelihood learning with softmax classifier
and hard targets may never converge and weights might keep increasing, though it can be eliminated by
weight decay, but label smoothing does provide advantage.

#### Semi-Supervised Learning
both unlabelled and labelled examples are used to estimate p(y|x). in semi supervised learning, goal is
to learn class wise representation h. this approach avoid having seprate supervised and unsupervised models.
but instead it can have generative and descriminative model. one can then tradoff supervised criterion
-log(p|x) with unsupervised or generative one -logP(x).

#### Multitask Learning
improve generalization by pooling examples arising from several task(soft contrain impose). when part of 
model is shared across the tasks, that part of model is more constrained towards good values. It can be though
as having multiple objective function to learn multiple things from same output by sharing parameters.


