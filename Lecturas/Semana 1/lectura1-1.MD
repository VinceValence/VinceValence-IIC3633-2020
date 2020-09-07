
In Sarwar et al work, Item-Based Collaborative Filtering Recommendation Algorithms, CF methods that base their recommendations on the relationships between items, rather than the ones between users, are analised and compared with the classic user-based method.

In the paper, they introduce two main challenges for collaborative filtering algortithms: improving their scalability and their quality. These challenges opose each other.

They could have been more specific when explaining each similarity or prediction computation. I mean, they could have specified every variable involved for clarity’s sake.

They say their item-based CF algorithm is model-based, but I think it is memory-based, because the only different thing they do is precompute similarity values. I find the idea to be clever, however. It does improve the scalability of CF algorithms at the cost of little quality.

The paper results are well presented and organised. Although, they could have incorporated users with less than 20 ratings, to see how the model worked for them. Cold start is still a problem.
