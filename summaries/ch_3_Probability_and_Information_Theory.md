probability theory is mathematical framework for representing and deriving uncertain statememts.
it should tell us how AI system should reason and based on that, we can analyze behavior of AI system.
on the other hand, information theory enable us to quantify amount of unceratianinty in probability distribution.

There are three possible sources of uncertainity.<br />
INHERENT STOCHASTICITY: in system itself.<br />
INCOMPLETETE OBSERVABILITY: when we cannot observe all variables responsible for system output. <br />
INCOMPLETE MODELING: when we use simpler model for prediction.

we need means of representing and reasoning about uncertainity from probability theory.
Rates at which an event occurs known as frequentist probability, while qualitative levels of certainity is known as Bayesian Probability.
Probability theory provides set of formal rules for determining likelihood of proportion being true given other likelihood.

####Random Variables
variable that can take on different values randomly it is description of all possible states and coupled with probability distribution about likelihood of getting each state.
DISCRETE R.V: can take finite or countably infinite number of states.
CONTINUOUS R.V: can take real values.

####Probability Distributions
it is description of how likely a random variable is to take on each of its possible states.

####Probability Mass Function 
probability distribution over discrete random variables. maps from state of a random variable to the
probability of that random variable taking on that state. if PMF acts on more than one random variable, known as
joint probability distribution.
properties of PMF for random variable x
- domain of P must be set of all possible value of x, lowest probability of any state is 0 and highest is 1, and we normalize probability
of many even occurring to 1.

####Probability Density Function
probability distribution over continuous variable. doesn't give probability of specific state directly but instead
it give probability of landing inside of specific range. 

####Marginal Probability
getting probability distribution over subset of variables from set of variables.

####Conditional Probability
when we are interested in probability of one event, given other event. we can't apply condition on the even that has never happpened.
can't be think as what would happen if some actions were undertaken.

####Chain Rule of Conditional Probability
Joint probability distribution over many variables can be decomposed into conditional distribution of one variable.

####Independence and Conditional Independence
Two random variables are independent if there probability distribution can be expressed as product of two factors.

####Expectation, Variance and Covariance
Expectation: Mean value that function f can take when x is drawn from P.<br />
Variance: How much value of function of x vary when x is drawn from P. low variance, values of f cluster near their expected value.<br />
Covariance: How much two variables are linearly related to each other.if +ve, both variable have high values and if
 -ve, one takes high and other variable takes low value. <br />
Correlation: normalizes contribution of each variable in order to measure how much each variable is related.

Two variables that are independent have zero covariance(Don't affect each other) and vice versa.
If there is no linear dependence between two variable, then they have 0 covariance. for being independent, they also need to exclude 
non linear relationship along with 0 covarience.

####Baye's Rule
It describes relationship between finding posterior knowing prior and likelihood.



