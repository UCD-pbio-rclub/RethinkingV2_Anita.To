---
title: "RethinkingLecture2_hw"
author: "Anita To"
date: "4/12/2019"
output: 
  html_document:
    keep_md: yes
---



## Easy Problems

2E1.

Which of the expressions below correspond to the statement: the probability of rain on Monday?

(1) Pr(rain)
(2) Pr(rain|Monday)
(3) Pr(Monday|rain)
(4) Pr(rain,Monday)/Pr(Monday)

Answer: (2) Pr(rain|Monday)

2E2.

Which of the following statements corresponds to the expression: Pr(Monday|rain)?

(1) The probability of rain on Monday.
(2) The probability of rain, given that it is Monday.
(3) The probability that it is Monday, given that it is raining.
(4) The probability that it is Monday and that it is raining.

Answer: (3) The probability that it is Monday, given that it is raining.

2E3.
 
Which of the expressions below correspond to the statement: the probability that it is Monday,
given that it is raining?

(1) Pr(Monday|rain)
(2) Pr(rain|Monday)
(3) Pr(rain|Monday)Pr(Monday)
(4) Pr(rain|Monday)Pr(Monday)/Pr(rain)
(5) Pr(Monday|rain)Pr(rain)/Pr(Monday)

Answer: (2) Pr(rain|Monday)

## Medium Problems

2M1. 

Recall the globe tossing model from the chapter. Compute and plot the grid approximate posterior distribution for each of the following sets of observations. In each case, assume a uniform prior for p.
(1) W,W,W
(2) W,W,W,L
(3) L,W,W,L,W,W,W

Answer:

2M2. 

Now assume a prior for p that is equal to zero when p < 0.5 and is a positive constant when p ≥ 0.5. Again compute and plot the grid approximate posterior distribution for each of the sets of observations in the problem just above.

Answer:

2M3. 

Suppose there are two globes, one for Earth and one for Mars. The Earth globe is 70% covered in water. The Mars globe is 100% land. Further suppose that one of these globes—you don’t know which—was tossed in the air and produced a “land” observation. Assume that each globe was equally likely to be tossed. Show that the posterior probability that the globe was the Earth, conditional on seeing “land” (Pr(Earth|land)), is 0.23.

Answer:

2M4. 

Suppose you have a deck with only three cards. Each card has two sides, and each side is either black or white. One card has two black sides. The second card has one black and one white side. The third card has two white sides. Now suppose all three cards are placed in a bag and shuffled. Someone reaches into the bag and pulls out a card and places it flat on a table. A black side is shown facing up, but you don’t know the color of the side facing down. Show that the probability that the other side is also black is 2/3. Use the counting method (Section 2 of the chapter) to approach this problem. This means counting up the ways that each card could produce the observed data (a black side facing up on the table).

Answer:

2M5. 

Now suppose there are four cards: B/B, B/W, W/W, and another B/B. Again suppose a card is drawn from the bag and a black side appears face up. Again calculate the probability that the other side is black.

Answer:

