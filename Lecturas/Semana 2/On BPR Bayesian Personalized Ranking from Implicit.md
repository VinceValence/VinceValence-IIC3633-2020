# On "BPR: Bayesian Personalized Ranking from Implicit Feedback"

---

### About the study

"BPR: Bayesian Personalized Ranking from Implicit Feedback" appeared in 2009 in the Twenty-Fifth Conference on Uncertainty in Artificial Intelligence (UAI2009). It tackles the usage of optimisation criterions specifically designed for RecSys tasks from implicit feedback. In particular, they propose a criterion named BPR-Opt, which is the maximum a posteriori (MAP) estimator of the problem. Also, they present an optimisation algorithm made to work well with this criterion: LearnBPR.

Afterwards, the authors apply their optimization method and criterion to two well known implicit feedback recommender models: Matrix Factorization and Adaptive KNN. Then, they show how their method is better for training models that are focused on providing personalised rankings.

### Comments on the study

The following comments do not necessarily follow a single line of thought. They reflect my line of thought while I was reading the study and only regard some aspects of the theoretical conception of the model.

**On the paper's existence**

The fact of the existence of this paper suggests it is important (or at least of interest) to make faster optimisation methods to train recommender systems' models. I agree with this because in these problems, there usually is an incredible amount of data, and to train models it is often needed to use all of it. And concerning why there is a lot of data, there are usually too many users, items and interactions.

**On the ranking definitions**

The study defines each personalised ranking for a user $u$ as a total order $>_u$. I deemed this to be quite creative, because it is a clear, standard concept, but it also fits the nature of a ranking perfectly. More so, it is the basis of the way they obtain negative examples — due to the order's antisymmetry. In layman's terms, they can know when a user does not prefer an item because they are focusing on **relative preference** of a user over items, not on assigning an absolute score to the items for a user.

**On Dominating Items in Training**

The authors noticed that in a context of recommending systems, there are some predominating items that get much of users' attention — *i.e.* they are often interacted with. This influences the loss too greatly because the loss comprises all users and if all of them or many of them interacted with the item, the parameters dependent on such an item would be updated very much in gradient descent.

Stochastic Gradient Descent could help, as they mention, but it may not be enough if a non random way of selecting the training examples is employed (*e.g.* just looping over users or items).

The way the authors tackled this is both simple and powerful (or if you are into it, *elegant*): they performed Bootstrap Aggregating (Bagging) over the training examples. This reduces the chances of picking the same user-item pair in subsequent training batches. It must be highlighted that Bagging samples **with replacement**, but that is not so much of a problem because it has been demonstrated that about 63% of the examples can be sampled. With a lot of data, like in this case, this is not a problem. Moreover, it is essential to get a less skewed gradient.

### Final Words

There is more to this study than what I mentioned and than what meets the eye. I commented on some of its content that was of interest to me, but there are many other parts of the study that are important, so I will mention them here.

- The foundational method to obtain the optimisation criterion is A Posteriori Estimation. This mainly has two consecuences:
    1. Optimising the criterion will produce a good **probability distribution** over the parameters of whatever model is being used.
    2. There is an arbitrary incorporation of prior knowledge with an a priori distribution over the parameters. This adds flexibility to the model.
- The AUC curve relation with the criterion is really useful to explain the authors' proposal, because AUC is widely used in RecSys.
- The model is general. One can think of it as a *wrapper* over any other implicit feedback model.
- Its performance is noticeable.

Regrettably, we still experiment the cold start problem with this algorithm.