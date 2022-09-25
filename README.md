# RSS 2022 SCORE

The paper for our RSS 2022 submission on Second-order COnic RElaxation (SCORE)
for range-aided SLAM

## Tasks and Timelines

- [x] First collection of possible related works finished<sup>1</sup> (1/11)
- [x] First pass at lit review finished<sup>2</sup> (1/13)
- [x] Initial set of simulated experiments done<sup>3</sup> (1/13)
- [x] Final collection of possible related works finished<sup>5</sup> (1/17)
- [x] Final pass at lit review finished and written up<sup>6</sup> (1/19)
- [ ] Key experiments done and written up (1/19)
- [x] Make sure all symbols in the paper are defined (1/20)
- [x] First draft of paper (1/21)
- [x] Second draft of paper (1/23)
- [ ] Finished draft of paper (1/26)
- [ ] Submission deadline (1/28)

<sup>1</sup> we have an extensive list (at minimum 30 references) of related
  works based on title and possibly abstract  
<sup>2</sup> we have looked at all works from the first collection and have
  noted their contributions, relevance, and any connected related works not
  caught in the original list  
<sup>3</sup> we have a collection of simulated experiments and results that
  could form a reasonable basis for our paper. These experiments provide
  substantial evidence that our method is valuable under a range of settings and
  empirically demonstrate the usefulness of our method. In addition, we have
  some experiments which demonstrate our method failing and begin to provide an
  empirical basis for when this method does not necessarily succeed.  
<sup>4</sup> discussion should establish feasibility of these experiments in our
  paper - i.e. if we could possibly use their hardware, what the experimental
  setup would look like,  and timeline for performing these experiments  
<sup>5</sup> we have a fixed list of references and are no longer finding new
  relevant works  
<sup>6</sup> the related works section is now in a "finished" state. Basically,
  it now contains all content we would expect to see in the final version  

## NOTES / Things to be sure to state

- our method works for 2D and 3D RA-SLAM
- our method generalizes to the challenging multi-robot case and implicitly
  computes relative pose between multiple robots
- though the cost and constraints are refactored, in the noiseless case the true
  answer is a solution of the convex relaxation
- RA-SLAM can be much more efficient (many fewer variables necessary to track)
- should talk about the complexity of our algorithm (number of variables,
  constraints, etc.)
- in general the solution is not unique, though empirically we often find unique
  solutions. Theoretical analysis remains to be done but uniqueness of solution
  likely hinges on the stuff from the Tseng paper
- our approach is quite general and could be much faster if written uniquely for
  SO(2)
- valuable lesson in importance of intrinsic and extrinsic descriptions
- quadratic equality constraints are non-convex
- need to hype up the importance of our method and what the alternatives are
  (odometry, how do you find relative transform between other robots, etc.)
- need to introduce the name SCORE
- do we want to talk about the range measurement relaxation in more detail and
  provide some intuition for it?
- relaxation is very easy to implement, only requires simple off-shelf solvers
  and implicitly computes relative pose alignment between different robots

## Introduction feedback from David

- I say we use NLS because non-convex ; switch to local search methods (NLS is bc of statistical optimality)
- state that range measurements haven't been considered before in convex relaxations
- state that loss function is no longer quadratic in original problem variables (objective function is no longer convex)
- emphasize the contribution of writing the problem as a QCQP

## Chad feedback (verbal)

- QCQP contribution is not emphasized enough
- itemize contribution
- not clear that SCORE is not the QCQP
- maybe the smartfactors paper should be cited
- we talk about Dropping the constraints a lot, make sure it's clear what that means.
- under eq 7 it's not clear why the problem is non-convex, should explain
  convexity more
- need to help people understand RA-SLAM more, what do the range measurements do?
- might not want to say that we use "off the shelf software" in the abstract
- we say "quadratic and convex" - need to clarify on that.. what is quadratic
  and convex

## Chad feedback (email)

- May consider to itemize at least four contributions: initialization, QCQP, SCORE, multi-robot RA-SLAM experiment?
- At the beginning of introduction, try to distinguish the difference between optimization-based method, EKF-RA-SLAM, and RBPF-RA-SLAM. I feel reviewers that focus on range measurements can be more familiar with the last two methods.
- the sentence "which are both quadratic and convex" confused me. Consider expand it or remove it or move it to a later place?
- "This form is a non-convex, equality constrained QCQP". 'non-convex' isn't obvious to me. Maybe explain a bit and provide references about the convexity of SO(d)?
- consider a summary of bullets that explain why the relaxation still works, although it has been addressed at a few different places due to different reasons. Maybe put it after the experimental results?
- consider to make the "off-the-shelf" solver a bit more specific? something like first-order, second-order, or SDP?
- a figure highlighting the interior set, edge, and outside of an circle may be helpful for demonstrating the non-convexity and the main idea of the proposal.
- in the abstract, I suggest to rephrase "RA-SLAM is commonly represented as a nonconvex optimization" to "RA-SLAM can be represented ...". My concern is a filter guy may disagree with you and, especially, there are indeed  many different filtering methods customized for RA-SLAM.
