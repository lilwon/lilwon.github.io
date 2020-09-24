---
name: AI Checkers 
tools: [C++, Artificial Intelligence]
image: https://images.unsplash.com/photo-1551198581-aec5c1556d7c?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80 
description: An AI that plays checkers in C++.
---

# AI Checkers 

The checkers game was a project for CS-171 Introduction to
Artificial Intelligence during the Fall 2019 school year.

The class repo can be found [here](https://gitlab.ics.uci.edu/ai-projects/Checkers_Student).


## Rules & Limitations

* Must be written in Python, Java, or C++
* 8 minute time limit per player (16 min games max)
* Tournament Games are best out of 3
* American/British Checkers ruleset

## Approach to creating a smart AI 

![AI vs Me](https://i1.lensdump.com/i/0Zc3mQ.png "AI vs Me")
 
For the first deadline of our project, we had to make our AI smart enough
to beat RandomAI and PoorAI. RandomAI was an AI that did any valid 
random moves during its turn. PoorAI performed minimax (more info below)
but with a very small game tree value. 

The hardest part of the project was, of course, getting started
on it. My partner and I had to read through all of the files that were 
given and break down each functions to understand what it did. Once we 
knew what functions we needed to use, it was pretty easy to code our own 
AI.

#### Minimax algorithm 

![Minimax Example](https://i1.lensdump.com/i/0Zc7Qk.png "Minimax Example")

My partner and I first implemented the 
[minimax algorithm](https://en.wikipedia.org/wiki/Minimax) to defeat RandomAI.
To summarize what the algorithm does, the AI chooses its optimal move (which
would be its max) and assumes that the opponent would also choose its
own optimal move (opponent would have its own max). 

What my partner and I chose to do was let the AI play its own game and
perform minimax before making its best move against the opponent.
We chose a small arbitrary number, 10, for our game tree. 
We chose heuristic values for capturing(+5), losing(-3), and 
kinging(+7) pieces. Using the minimax algorithm beat RandomAI easily. 

We tested our algorithm against PoorAI, and it won about ~80% of the time,
but to ensure it won every time against the AI, we changed our game tree
number to 20, so it would predict the better move further into the game.
This was enough to beat PoorAI.

#### Alpha-beta pruning algorithm

![Alpha-beta Pruning Example](https://i1.lensdump.com/i/0ZcOex.png "A-B Pruning")

[Alpha-beta pruning](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning)
wasn't a difficult algorithm to code since it has the same features as 
minimax, but more in depth.
 
What alpha-beta pruning does is obtain a max node of an alpha value that's
greater than your beta value, then prune all nodes/values that are
less than that alpha value. 
The same thing would be for update the  min node to with the beta value.

With alpha-beta pruning, it allows more of the game tree to be searched 
since the pruning was fast compared to the simple minimax algorithm.

Our algorithm beat SimpleAI and GoodAI easily, so my partner and I
were pretty much done with this project after we implemented 
alpha-beta pruning.

#### Adding a few tweaks

We added our own game timer for our AI because if it kept looking deeper into a
single move, the game timer would eventually run out. So we gave our AI
a 6 minute time limit to think about all of its move, and if it reaches over
6 minutes, it would make random moves for the remainder of the game. 

We also reduced time by making our AI choose moves that were obviously
advantageous (like capturing two or three pieces) and put more priority
into those moves. 

## Class Tournament (Results!)

Near the end of the quarter, the TAs would host a tournament where 
everyone's AI would play against each other. Our AI was tied for **3rd
out of 70 groups** (the tournament was between two lecture sections, so 200+ 
students). 

It definitely made us happy because the top 10 groups would
receive extra credit. Our hard work of trying to make our 
AI smarter and faster paid off.
