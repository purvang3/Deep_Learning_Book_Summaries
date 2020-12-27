Also known as Multilayer perceptron and goal of ffn is to approximate function. ffn maps x to y and learns parameters value
that gives best function approximation. when ffn is extended to use feedback connection from h, then it is callled
recurrent nueral network. they are conposed of many different functions. Model is composed of direct
acyclic graph discribing how functions are composed together.by building ffn, we try to approximate function as close as 
original function which discribe our input data.

Linear problems are easy to be solved by ffn, either in closed form or with convex optimization. but their capacity is
limited by linear functions and model cannnot understand interaction between two variables.
Instead we can apply linear model to transformed x, which is non linear. in neural network, this transformation 
is learned by network, which is known as hidden layer. This gives up convexity problem. 

#### Gradient-Based Learning
Largest difference between linear models and nueral network is non linearity, which causes loss function
to become non-convex. nn usually trained using iterative algorithm, sole goal is to minimize 
cost function.stochastic gradient descent applied on nonconvex loss functions has no such convergence guarantee compared to
linear model which does have irrespective of weight initialization. That is why for ffn, it is important to
initialize weights to small random values.

#### cost functions
parametric models defines a distribution p(y|x;w) and we use principle of maximum likelihood. instead of predicting
complete prob distribution over y, we can also predict statistic of y based on specific loss function.

#### Learning Conditional Distribution with Maximum Likelihood
there is equivalence between maximum likelihood estimation with output distribution and minimization of mean squared error
holds.advantage of using cost function from maximum likelihood is that it removes burden of designing cost function for
each model. also cost function that we choose, gradient of that should be large and predictable enough. negative log
likelihood helps to avoid saturation problem.log function in negative log likelihood also removes exp of some output units.

#### Linear units for Gaussian Output Distribution
simplest output is affine transformation with no nonlinearity known as linear units. linear output layers always used to produce mean of 
conditional gaussian distribution.maximum likelihood framework can also be used to learn covarience of gaussian too.

#### Sigmoid units for Bernoulli Output Distribution
task which requires classification of binary variable. maximum likelihood is to define bernoulli distribution over y 
conditioned x.bernoulli distribution is defined by just a single number.but with linear units, any deviation in output 
will result in zero gradient. so we can use it with sigmoid function which gives output as unnormalized probabilities, also
known as logits. this approch of predicting probabilities in log space also help in maximum likelihood learning.
saturation of sigmoid function can affect training without maximum likelihood.using softplus can help to avoid saturation
where it doesn't shrink gradient.
