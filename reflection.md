# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

- The game looks to be a guessing game where you have a limited number of attempts to guess the secret number before the game is over. Any number can be in the range between 1 and some number depending on the difficulty.
- One bug that I encounted in the program is that everytime I try to input a number that is greater than the secret number, the hint tells me to go higher when it instead the hint should tell me to go lower.
- Another bug that I encountered was when I'm setting a difficulty, let's say hard the range should be smaller, but the display is not showing for 1-20 in hard mode.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

- I used Claude Code on this project
- Claude Code gave suggestions about the errors I found while experimenting the guessing game. For example, Claude Code identified the correct code in the bug where the function to get the range for the difficulty. It turns out that there was a bug in the Hard difficulty if statement where it should be from 1 to 100, not from 1 to 50.


---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

- I ran `pytest tests/ -v` which executed three tests: `test_winning_guess`, `test_guess_too_high`, and `test_guess_too_low`. The first run revealed that `check_guess` was returning a tuple `("Win", "🎉 Correct!")` instead of just the string `"Win"`. The assertion error `assert ('Win', '🎉 Correct!') == 'Win'` made it clear the function's return value didn't match what the tests expected, which led us to simplify the return to a single string.
- AI (Claude Code) didn't design the tests — they were already written in `test_game_logic.py`. However, AI helped in two ways: it diagnosed why the tests couldn't even run (the `ModuleNotFoundError`) and fixed it by adding `conftest.py` to put `logic_utils` on the Python path. It also misread the situation once — it assumed the tests would pass after fixing the import, but running pytest proved that wrong. The test output itself was more reliable than the AI's assumption.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
