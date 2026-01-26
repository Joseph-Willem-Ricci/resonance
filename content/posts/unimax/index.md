---
title: "Unimax: Cooperative Algorithm"
date: "2024-11-29"
summary: "Unlearning Adversarial Paradigms of Computation & Imagining Alternatives"
language: "en"
authors: ["Joseph Willem Ricci"]
categories: ["Code"]
featured_image: "unimax.png"
draft: false
---

In the summer of 2024, I had the responsibility of leading a [recitation](https://youtu.be/KND_0edZ4WA) on Adversarial Games for [UPenn's AI Class](https://artificial-intelligence-class.org/). It is an exciting module of the course because  students get to apply algorithms towards making intelligent decisions in games for the first time. In this module, students learn about the Minimax Algorithm, applying it towards simulating a game of dominoes.

When I took the class, the novelty of programming my first AI was so exciting! But in preparing for this recitation, I started to notice that I was using the word "adversarial" *a lot*...

{{<figure src="unimax.png"
caption="Screenshot of the unimax chess engine.">}}
{{</figure>}}

"*Adversarial...*" this, "*...adversarial...*" that, "*...assume MAX will always choose the action that MIN's worst interest*"...

It makes sense that chess simulators were first developed through an adversarial lens. After-all, this is typically how you play chess. But I started to think... this is also the paradigm through which my students are learning to write software; learning what AI and computation *is for*. Board games are fun and interesting to explore, but one day my students will apply their knowledge to software that exists within — and influences — the rest of the world.

Have adversarial paradigms of computation been influencing the world? What would the world look like if cooperative paradigms of computation were used in their place?

To explore this question, I built a chess engine named [Unimax](https://unimax.run). It uses the same algorithm outlined in [Claude Shannon](https://www.juggle.org/claude-shannon-mathematician-engineer-genius-juggler/)'s seminal paper from 1950, [Programming a Computer for Playing Chess](https://vision.unipv.it/IA1/ProgrammingaComputerforPlayingChess.pdf), but with one key modification. Instead of *subtracting* the opponent's utility from the current player's utility as the heuristic for each board state, Unimax adds them together. There is one metric that both players seek to maximize: their collective utility.

I invite you to visit [unimax.run](https://unimax.run) and to watch a game of chess being played through a cooperative lens. For me, the game of chess is so familiar — the board, the pieces, the way it looks when being played — but the movements that emerge from this cooperative algorithm render the game almost unrecognizable. Unimax transforms chess from a game of combat, capture, and control into a beautiful, cooperative dance where each move is a gift of creating space.

I hope that witnessing this conjures other areas of life that are traditionally adversarial and that we unquestioningly perpetuate. And I hope it prompts your imagination on how different our movements in the world might look if we approach them from a different perspective. 