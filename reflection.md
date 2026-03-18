# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").

The first time I ran the game, it looked like a normal number guessing game with a clean front, difficulty settings, and a score system. But once I started playing, I noticed that some of the hints and outputs did not make sense. One bug I noticed was that the hints were backwards. When my guess was too high the game told me "Go Higher!" instead of telling me to go lower, which was misleading. Another bug I found was that the game behaved inconsistently between guesses, sometimes hints did not match what I expected based on previous guesses, which made it feel like the logic of the game was breaking. A third bug I found was that the instructions always said "Guess a number between 1 and 100" even when I selected Easy or Hard mode, this is incorrect because the range changes depending on the difficulty, so the instructions are not matching the game settings. 

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

To help debug and refactor my code, I utilized AI, specifically ChatGPT and GitHub Copilot. One of the suggestions made by the AI was to move several functions related to game logic functions like 'check_guess', 'parse_guess', and 'update_score' from the app.py file to a separate file called logic_utils.py. I confirmed that this change resolved the error and did not impact any of the functionality of my application by running the app with numerous correct inputs and confirming that the games were still functioning correctly. However, I did find one issue associated with the AI regarding hint logic. Originally, the hint logic would tell users to "go higher" when their guess was already too high, and even after my refactor of the code, I had to manually confirm that hints were working correctly through my testing of multiple guesses in the game. I verified that, once the user's guess was made, they received a hint stating correctly to "go LOWER!" when their guess was greater than the secret number.

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

I was able to verify that a bug has been resolved through the completion of manual testing. I did multiple rounds of playtesting to see whether the game would act according to the logic defined in it; I also used pytest after all of my changes throughout coding to make sure the procedures performed as intended. One example of a successful test was checking that if a player guessed 60 and the secret number was 50, the output would provide the message: this guess was too high. This successful test confirms that the hint logic was working properly after changes were made. I got an idea from AI on how to write a quick example of a single test case directly related to the problem I was attempting to resolve and was confident that my changes were successful by having passed pytest.


## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

In the original app, the secret number kept being different due to the fact that when you interact with the Streamlit app, it is going to rerun the whole script which generates a new secret number each time the script is executed rather than keeping the same value until the round ends. Each time a user does something in the Streamlit app (like click a button) it will rerun the app from the top down therefore there is no way to maintain the existing value of the secret number if it is not stored in session state. Using session state allows you to store values so that they remain existent across reruns and can be considered a memory that remembers important values that will be shared across user interactions. The change made to fix this problem is to store the secret number and check if the secret number exists before generating a new secret number. The secret number can now be used throughout the round of the game.

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

I will integrate immediate testing into my coding practices instead of relying on assumptions regarding code corrections. While writing and executing simple tests allowed me to identify errors quickly, future interactions will require more caution when accepting any number of AI generated suggestions. While the AI provided assistance and suggestions, there still needed to be assurance and confirmation. The outcome from this experience has shown me that all AI generated code does not represent the totality of a solution as well as that while there is an efficiency gained from using AI, such efficiency must be supported by critical thinking and debugging to produce quality outputs at the end of each stage in developing software.