This chapter focuses on special case of optimization: finding parameter w, that reduces cost function, which is performance measure on trainin set.
#### How Machine Learning optimization differs from Pure optimization:
In ML, we care about metric P, which is defined on test set and also intractable, by reducing cost function. on the other hand
in pure optimization, we just want to minimize cost function.
#### Empirical Risk Minimization
Reducing expected generalization error over true underlying distribution known as Risk. if we knew distribution, then it is solvable optimization problem.
since we don't know true data distribution and we have data, we need to solve for minimizing expected loss over empirical distribution defined by training data.
minimizing average training error known as Empirical Risk Minimization. In Ml, we focus to reduce Empirical Risk in hope to reduce risk.
But this can lead to overfitting and some loss function has no useful derivative. so in ML, we optimize for quantity which is 
slightly different then actual. 

#### Surrogate Loss Funtions and Early stopping
As mentioned, minimizing some loss functions(0-1 loss) is exp in input dimension,in that case, we optimize surrogate function like negative log-likelihood.
and in some cases, it can lead to better result. One important differece of ML optimization is that training function do not halt at local minimum, but 
minimize loss function and halts when convergence criterian based on early stopping is satisfied.
early stopping is measered on true underlying loss function and designed to halt algorithm when surrogate function still has
large derivates and pure optimization has small gradient.

#### Batch and Minibatch gradient
one key aspect: objective function usually decomposes as sum over data.each update is calculated based on expected
value over subset of data.Evaluating model on every example is expensive, so in general we take average over small subset of examples.
standard error of estimated mean generally decrease with more example in substet, but it also incerase computation.
if algorithm gives good estimates of gradient, it converge faster. Also gradient estimation over small subset helps from redundency in training data.
it can compute correct gradient with small suset which can be equal to entire dataset if there is redundency.

BATCH/DETERMINISTIC GRADIENT DESCENT: uses entire training set to compute gradient.
STOCHASTIC/ONLINE GRADIENT DESCENT: uses single example at time(examples taken from continous stream). <br />
MINIBATCH GRADIENT DESCENT: uses more than one but fewer than entire dataset.

##### In practice, one should start with MINIBATCH GRADIENT DESCENT because of following reasons.
- larger batch size provide more accurate estimates of gradient.
- small batch size is generally slow and make under utilize multi-core architectures but small batch size can provide regularization effect due to noise updates.
- it is common to use power of 2 of batch size for some arch. for better runtime.
Always needed to select minibatches randomly to avoid bias and we also want subsequent gradient to be independent.
also recommended to shuffle data after every epochs.
Interesting fact that minibatch gradient descent follows gradient of true generalization error if no examples are repeated.this
can not be achieved sometimes due to implementation of minibatch gradient descent. that is why stochastic gradient descent have
better generalization error and reduce over fitting. but minibatch gradient descent is still useful even only first pass is unbiased because for 
stochastic gradient descent, we need infinite of data which is sometimes difficult.

#### Challenges in Nueral Network Optimization
Training nn, optimization problem is mostly non-convex.

#### Ill conditioning
happens when even very small steps increase cost function and when Hessian matrix becomes to big.

#### Local Minima
Any local minimum is guaranteed to be global minimum and for optimizing convex function, if we find critical point, we 
know that we have reached to good solution. but since nn is non-convex opt problem, any deep nn can have many local minima.
Due to model unidentifiable problem  because of multiple equivalent parametrized latent variables in nn, model can have multiple local minima. also if cost funtion 
doesn't contain weight decay, every local minima can lie in high dimensional hyperbola.
However all these local minima is equivalent for cost function, so it is not much problematic.
Problem arises when local minima is higher cost than global minimum. in many deep neural networks, mostly local 
minima's are of low cost. but to check whether local minima is causing problem in training, if norm of gradient does not become 
too small, then problem is not local minimum problem.

#### Plateaus, Saddle Points and Other Flat Regions
Random functions have found the saddle point if gradient becomes zero. at saddle point H matrix have both positve and negative eigen values.
In high dimention space, local minima are rare but saddle points are more common. one good property of random functions is,
eigenvalues of H is positive when we reach lower cost regions meaning local minima is more likely to have low cost and
saddle point more likely to have high cost. for first order optimization of nueral network,gradient descent seems to be able to
escape saddle point where gradient becomes small. but for second order can be more useful if can scale to large nn with sadle-free
newton method.

#### cliffs and Exploding Gradients
When multiply large weights, nn often ends up to cliffs, where gradient update can move parameters very far, which can lead to
loss all optimization work done so far. can be avoided using gradient clipping, avoiding backpropogation of
large gradients. cliff structures are more common in cost function of recurrent nn, because of multiplication of 
many factors over time.

#### Long Term Dependencies
with many layers or when construction deep computational graph by applying same operation repeatedly, if eigen
value is not near 1,it can be exploding gradient situation if it is greater than 1, which make training unstable or could be vanishing gradient
problem if it is less than 1, which provide no information which direction parameters should move.

#### Inexact gradient
In practice, we usually have noisy, biased or sampling based estimates of gradients. sometimes gradients becomes
intractable because of cost functions.












