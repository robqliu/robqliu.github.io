---
title:  "criminal cupbearers"
---
I did a riddle from [here](https://www.ocf.berkeley.edu/~wwu/riddles/hard.shtml).

The idea is pretty simple. We build a decision tree to figure out what the poisoned bottle is.
Since we have 10 prisoners we can build a tree with 1024 leaf nodes.

In practice, this is actually implemented by something like this:

* $$p_0$$ drinks the first $$500$$ bottles
* $$p_1$$ drinks the first $$250$$ bottles and then bottles $$501-750$$
* $$p_2$$ drinks $$1-125, 251-375, 501-625, 751-875$$
* ...
* $$p_9$$ drinks every odd bottle

We can prove this works by just showing that every subset of prisoners that dies maps to a unique
bottle. In other words, take a subset $$S_1$$ and say it differs at prisoner $$p_i$$ from $$S_2$$.
WLOG suppose that $$p_i$$ survives in $$S_1$$ and dies for $$S_2$$. Then we know the poisoned bottle
is _not_ in some subset of the bottles that $$p_i$$ drank for $$S_1$$ but _is_ in the subset of
the bottles that $$p_i$$ drank for $$S_2$$. Since $$p_i$$ drinks the same subset of bottles always then
we know that the poisoned bottle cannot be the same for $$S_1$$ and $$S_2$$.

The intuition hand-wavy proof is basically that at every prisoner we reduce the number of possible
bottles by half. If the first prisoner dies then we know the poison bottle is in the first half.
If the second prisoner dies we know it's the first half of the first half (meaning, the first quarter).
If the second prisoner doesn't die then we know it's the second half of the first half (i.e. the
second quarter). This continues until we get to the final prisoner at which point we've narrowed the
number of targets to two adjacent bottles. The final prisoner has consumed exactly one of those two
bottles by definition so we'll know in 4 weeks what's up!

Math is a force for evil once again...
