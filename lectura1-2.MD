# FunkSVD

I would like to preface this small commentary by citing the author when he refers to generality and compression in machine learning.

"A fun property of machine learning is that this reasoning works in reverse too: If meaningful generalities can help you represent your data with fewer numbers, finding a way to represent your data in fewer numbers can often help you find meaningful generalities. Compression is akin to understanding and all that."

I mention this part of the article because it has shown to be quite relevant indeed in machine learning. Quite literally, models such as [Autoencoders]( https://en.wikipedia.org/wiki/Autoencoder) try to learn concepts by compressing examples into representative embeddings.

Now, with respect to FunkSVD, reading the article I found the author explaining mathematical concepts (such as decomposing a matrix into a multiplication of two other matrices) only with words. I think that many concepts were missing a reinforcement, and when such a reinforcement was provided, it was in a programming language. Since the concepts of matrices, derivatives and root mean squared error are not, in essence, programming constructs, I would deem it necessary to include some sort of mathematical representation. For example, when he speaks of how elements of the ratings matrix are calculated, he writes:

    ratingsMatrix[user][movie] = sum (userFeature[f][user] * movieFeature[f][movie]) for f from 1 to 40

In my opinion, it would have been clearer to just write

<img src="https://render.githubusercontent.com/render/math?math=R_{ij} = u_i \cdot m_j">

I digress. 

My main critisisms of this algorithm are three things:
1. It still suffers from the cold start problem
2. The latent factors are of the same fixed length for users and items
3. Unless there is something I am not understanding well, when a new user or movie is incorporated to the user or movie pool, the model would increase its number of parameters and they would have to be optimised as well.

The first problem is straightforward: if there are no true examples, nothing can be learned. This renders this method useless for a brand new recommender system. Some other method reliant on some other kind of information would have to be used in the beginning.

The second problem aludes to the amount of latent factors. How can it be known how many there should be? In each application, the model would have to be trained with different numbers of latent factors and just see which is better.

And the third problem affects the adaptability of the model to changes in the database. It cannot adapt without being trained again.

Despite these disadvantages, the fact of incorporating prior knowledge and pre-computing means is a clever way to significantly speed up training time. This may compensate for the little adaptability of the algorithm.
