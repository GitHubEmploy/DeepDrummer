# DeepDrummer

DeepDrummer is a drum loop generation tool that uses active learning to learn the preferences (or current artistic intentions) of a human user from a small number of interactions. The principal goal of this tool is to enable an efficient exploration of new musical ideas. We train a deep neural network classifier on audio data and show how it can be used as the core component of a system that generates drum loops based on few prior beliefs as to how these loops should be structured.

DeepDrummer is composed of three main components:
- the web interface (presenting the user with drum loops to be rated as either *like* or *dislike*)
- the critic (learning what the user likes, serving as filter for future generated loops)
- the generator (propose new drum loops to achieve a good score with critic)

The critic network takes a drum loop's raw audio preprocessed as MFCC features, and then applies successive layers of convolutions in order to finally output its prediction about the probability that the user will *like* the drum loop.

[Maybe put a sketch here with the 3 components? The kind of thing you wouldn't put in a scientific paper, but would ?put on a web site to keep people entertained while reading.]

The generator is a function that outputs random grid sequencer patterns with 16 time steps during which 4 randomly-selected drum sounds can be triggered. [Maybe put a sketch here too with the sequencer grid?]
We choose a very basic generator that does not have any trainable parameters, and constitutes a source of patterns that has few priors on musical structure.

Combined together, the feedback from the critic can serve as a powerful filter for the output of the generator. As a result, the interface will present only the most relevant drum loops to the user for rating.

We show a demonstration of all the pieces working together in the following YouTube video.

EMBED YOUTUBE VIDEO HERE.

[Should we explain the novelty in more explicit terms?]

# Experiment

We ran an experiment with 25 participants to demonstrate that DeepDrummer
that meaningful gains are made with only 80 interactions (binary *like* or *dislike*).
For each user we are interested in the proportion of drum loops that are *liked* at the beginning
(no training) versus at the end (after 80 ratings plus training).
We call these quantities `init_theta[i]` and `final_theta[i]` for user i.
We also look at `delta_theta[i] = final_theta[i] - init_theta[i]`,
which corresponds to the actual improvement for that user.

In the following plot we compare the distributions of `init_theta` and `final_theta`,
using smoothing kernel to represent the pdfs (i.e. it's just a smoothed histogram).
We can visually see that there was a general measurable improvement of the quality
of the drum loops over the interactions with the user.

<img src="images/distribution_user_probabilities_of_like_0.07.png" alt="init theta and final theta" width="500"/>

We can look at the individual differences `delta_theta[i]` as well
to see the improvements for each users.

<img src="images/distribution_delta_0.04.png" alt="delta theta" width="500"/>

In terms of actual experimental protocol, we had to split our experiment
into an interactive Phase I where learning took place, and an evaluation Phase II
during which we presented the user with drum loops for either init/final model at random.
This was done to compensate for possible shifts in the
attitude of the users, to make sure that our measurements were not
going to be biased positively (or negatively) by the possibility
that users might tend to rate drum loops higher (or lower) on average after
10 minutes of clicking. More on this can be found in our paper.

# Fun samples

Show best/worse samples from participants, and some of our own favorites.

# Dataset released

Briefly describe the dataset that we're publishing, and give the download link. Make it sound like it's a contribution in its own right, but don't sell it too hard because we don't want to eclipse the actual core DeepDrummer.

# Running the code

Reproducing the experiment.

Starting from pre-trained model.

# Links

Reminder about links for arXiv, github, youtube and dataset, even though the links were given in the previous sections.

bibtex to cite us

3
2
1

Je viens de penser à quelque chose. Je regardais les folders dans ISMIR2020 et j'ai constaté qu'on avait encore un setup avec "deepgroove" dans la structure.

The DeepDrummer experiment was run on a computer with a INSERTBRAND GPU, which is way more computational power than necessary.