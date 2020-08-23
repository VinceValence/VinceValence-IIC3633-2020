I like how the authors are really careful when dealing with interpretations of the different parts of the model, such as being aware of
the fact that they are extracting preference information with certain confidence, which is very different from a rating. They also are aware
of having no negative feedback (although there could be). This notions are essential for the conclussions that can be drawn afterwards.

The model supervises itself with the computed confidence and preference (c and p in the paper). The authors propose and tested more than
one way to calculate these values from the data. About this topic, I think that it is extremely hard to find the "correct" extracting 
functions for these values and this probably explains why the study just tests different options. However, this is also an area where
further inspection could be done, trying to find and explain theoretically and/or empirically how to compute confidence and preference.

It would be insteresting to have an idea of the nature of the resulting latent vectors (e.g. with PCA). If I am not wrong, the fact that p_ui
is either 0 or 1 forces the dot product to be close to either one of those values. This means the angle between x_u and y_i should either
be close to 0 or be close to 90 degrees. Confidence levels provide some flexibility to this because it allows us to have greater angles
for lower confidences when a user does not prefer an item (i.e. the latent x_u and y_i may have a big angle between them, but the error may
be low because we may not have enough confidence on p_ui being 0). Of course, the converse would also be true. Visualising the latent vectors
would give much grater insight into the behaviour of the latent factors and the relationships between factors of users and items (or users and
users or items and items, for that matter), adding value to the explanation or interpretations of the algorithm.

The authors are aware of the feedback not having information about disliking a programme, but I think there could be some information in the
action of turning off the TV. The show airing when the TV is turned off may have a negative impact on the user. Maybe a similar, but reverse,
approach with confidence and dislinking (instead of confidence and liking) could be utilised. There might be some worth in looking into that.

And well, no RecSys discussion could end without mentioning the cold start problem, of which this algorithm suffers. At least the training time
increases linearly!
