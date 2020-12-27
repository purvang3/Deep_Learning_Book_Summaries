Successfully applying deep learning techniques requires more than just a good knowledge of what algorithms exist and
the principles that explain how they work. During day-to-day development of machine learning systems, practitioners 
need to decide whether to gather more data, increase or decrease model capacity, add or remove regularizing features, 
improve the optimization of a model, improve approximate inference in a model, or debug the software implementation of 
the model. In practice, one can usually do much better with a correct application of a common place algorithm than by 
sloppily applying an obscure algorithm. 

Practical design process should be following
- Determine your goals: what error metric to use, and your target value for this error metric. These goals and error
 metrics should be driven by the problem that the application is intended to solve.
- Establish a working end-to-end pipeline as soon as possible, including the estimation of the appropriate performance
 metrics.
- Instrument the system well to determine bottlenecks in performance. Diagnose which components are performing worse 
than expected and whether poor performance is due to overfitting, underfitting, or a defect in the dataor software.
- Repeatedly make incremental changes such as gathering new data, adjusting hyperparameters, or changing algorithms, 
based on specific findings from your instrumentation.

####Performance Metrics
Determining your goals, in terms of which error metric to use, is a necessary first step because your error metric will
guide all your future actions. You should also have an idea of what level of performance you desire. for most applications, 
it is impossible to achieve absolute zero error. The Bayes error defines the minimum error rate that you can hope to
achieve, even if you have infinite training data and can recover the true probability distribution. In the real-word setting, 
we have some idea of the error rate that is necessary for an application to be safe,cost-effective, or appealing to consumers.
Sometimes it is much more costly to make one kind of a mistake than another where we may wish to weight cost based
on requirement.

accuracy is a poor way to characterize the performance of such a system.Precision is the fraction of detections reported 
by the model that were correct, while recall is the fraction of true events that were detected. By varying the threshold, 
we can trade precision for recall. In many cases, we wish to summarize the performance of the classifier with a single 
number rather than a curve. To do so, we can convert precision p and recall r into an F-score.

In some applications, it is possible for the machine learning system to refuse to make a decision especially when
if a wrong decision can be harmful and if a human operator is able to occasionally take over. A natural performance metric 
to use in this situation is coverage. Coverage is the fraction of examples for which the machine learning system 
is able to produce a response. It is possible to trade coverage for accuracy.

#### Default Baseline Models
After choosing performance metrics and goals, establish a reasonable end-to-end system. Depending on the complexity of 
your problem, you may even want to begin without using deep learning and if see problem can be solved
choosing a few linear weights correctly. For AI related problem, First, choose the general category of model based on 
the structure of your data. If you want to perform supervised learning with fixed-size vectors as input,use a feedforward 
network with fully connected layers. If the input has known topological structure (for example, if the input is an image), 
use a convolutional network. In these cases, you should begin by using some kind of piecewise linear unit (ReLUs or
their generalizations, such as Leaky ReLUs, PreLus, or maxout). If your input or output is a sequence, use a gated 
recurrent net (LSTM or GRU).A reasonable choice of optimization algorithm is SGD with momentum witha decaying learning rate.
Batch normalization can have a dramatic effect on optimization performance,especially for convolutional networks
and networks with sigmoidal nonlinearities.

Unless your training set contains tens of millions of examples or more, you should include some mild forms of regularization
from the start. Early stopping should be used almost universally. Dropout is an excellent regularizer that is easy to 
implement and compatible with many models and training algorithms. Batchnormalization also sometimes reduces 
generalization error and allows dropout tobe omitted, because of the noise in the estimate of the statistics used to 
normalize each variable.

Some domains, such as natural language processing, are known to benefit tremendously from unsupervised learning techniques, 
such as learning unsupervised word embeddings. Inother domains, such as computer vision, current unsupervised learning 
techniques do not bring a benefit, except in the semi-supervised setting, when the number of labeled examples is very small.