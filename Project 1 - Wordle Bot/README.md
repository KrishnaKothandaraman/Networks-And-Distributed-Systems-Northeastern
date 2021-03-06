# CS3700_Projects

## Project 1

Implement socket connection to play the game Wordle

### Journey through my Wordle game logic development

#### Iteration 1(Submitted)

The motivation for the strategy is based on how I play the game of Wordle. In a nutshell, each guess is made such that is 
does not waste any intelligence gathered from previous guesses. The next guess is filtered based on these three rules:

- Next guess has past green letters(server response code 2) in the same position
- Next guess has past orange letters(server response code 1), but in different positions to those guessed before
- Next guess has no past grey(server response code 0) letters 


### Tricks I have used

#### First
The first guess is strategically chosen as "about" because of the appearance of common vowels and common consonants
to minimize the size of the maximum set of possible words to guess.

For example:

First Guess: "about"

Server Response: [2,0,0,1,0]

Now, the only candidates for the next guess are words that have 'a' in the first position, 'u' not in the 4th position 
and no 'b', 'o' and 't'.

#### Second

For the first 4 guesses, the program tries to make guesses with no repeated letters. If this is not possible, it makes a 
guess that has a repeated letter. This is done to make maximum use of each letter in each guess. If duplicate
letters are used, there may be some redundancy which does not make for the most efficient learning from each guess.


Pros
- Easy to implement
- Low number of guesses to get the right answer. Average 5.93 guesses per answer taken over 30 games
- Designed to imitate how humans solve Wordle.

Cons
- Word lookup is slow
- Use basic data structure list to represent wordlist so O(n) for each guess