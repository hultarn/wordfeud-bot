# Wordfued Bot - 2024

## Introduction
This is an alpha version of an automated Wordfued bot. Currently created in Jupyter for easy development but intended to be exported for a more permanent solution.

## How It Works
The project is seperated into two parts.

### Dictionary
Before performing any Wordfued actions, a valid dictionary is needed. Since Wordfued in Swedish uses SAOL, this is the dictionary I will be using.

Since it's not available in any easy-to-use format for the public, I scraped it myself.

### Wordfeud
The algorithm first generates all possible combinations the letters on hand can be shuffled into. Since the hand consists of seven letters, this can be calculated using the following formula:

$\sum_{i=1}^{7} \frac{7!}{(7-i)!} \cdot i = 82,201$

If all positions were valid to place, this would give us, considering two directions can be played:

$\sum_{i=1}^{7} \frac{7!}{(7-i)!} \cdot i \cdot 15^2 \cdot 2 = 36,990,450$

The starting points are defined as all positions right or below an existing letter, or left or above within a range from the existing letter to \(i\) distance offset.

After all moves and starting points have been calculated, the algorithm will try to place them one by one in both directions and check if the placement is valid by comparing the main word with the dictionary. If it's valid, the algorithm will continue to check if all subwords are valid. If they are, finally the algorithm will calculate the score of the word and add it to a list containing valid words.

After the moves are calculated, the best move (score-wise) will be played.

## TODO
+ Refactor and finalize code.
+ Extend the usage of the API.
+ Add greedy agent.
+ Add smart agent that takes into account letters in the pool, openings on the board, and more.

