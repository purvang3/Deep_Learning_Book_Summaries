ML algorithm usually requires high computation because of solving problem by iterative method rather than analytical method.
#### Overflow and Underflow
for all numbers, we incur some approximation number when we do continuous math on digital computer. Underflow occcurs when
number near zero is rounded to zero and some function acts very different when argument is zero.
Overflow occurs when large values are converted to INFINITY. Developers of low level library must
take this into account and handle this situations.
#### Poor Conditioning
How rapidly function is changing when there is small change in input. when ration of largest and smallest eigen value
is high, function is more sensitive.

#### Gradient Based Optimization
optimization refers to either minimizing or maximizing function f(x) by alering x. derivative is useful for minimizing
function because it tells how to change x to improve cost(y).taking small step with opposite sign of derivative reduce f(x). f'(x) doesn't give information about which direction to move.
points where f'(x)=0 known as saddle point. local minimum is point where f(x) is lower than at all neighbourhood points. so it is not possible to 
decrease f(x) with very small steps and same goes for local maximum. some points know as saddle points which has higher and lower points on each side.
if there are more than one variables (inputs), we usually use partial derivatives. it tells how function f changes
with respect to individual variables.<br />

Directive derivative in direction u is slop of function f in direction of u.to minimize function, we would like to know direction in which
f decreases fastest.considering equation in book, when u points to opposite direction of gradient.
gradient descent converges when every element of gradient is zero.

#### Beyond the Gradient: Jecobian and Hessian Matrices
Defining input and ouput partial derivatives in terms of vector of function is termed as Jacobian matrix (J). Sometimes we are also
interested in derivative of derivative, known as Hessian Matrix (H). H will tell how J will change when we change input.
it tells about actual improvement based on gradient and measures the curvature. H being 0 gives no information.
if H is negative, function curves downwards, so cost function will decrease more than epsilon(momentum) and vice versa.

since H is symmetric, we can decompose into eigen values and eigen vectors. at critical point, we can use H to find
whether point is minimum, maximum or saddle point using eigen values. 

Optimization alg. that only uses gradient known as first order optimization algorithm, on other hand, optimization 
alg that uses Hessian for update known as second order opt alg.
In Machine learning, sometimes we gain guarantees by restricting ourself to functions to Lipschitz continuous.
This is useful because it enables us to quantify assumption that small change in input will lead to only small change in output. 
