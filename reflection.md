# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?  good
- List at least two concrete bugs you noticed at the start  
If I guess 60 and the secret is 50, it should say "Too High." The game says "Too Low"
The secret number should stay the same until I win or lose.the same until I win or lose.	Every time I click the "Submit" button, the game picks a brand new secret number, making it impossible to win.

The score should decrease by 10 points every time I make a wrong guess.points every time I make a wrong guess.	The score either stays at 100 forever or disappears from the screen entirely.
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project: copilot
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
The AI correctly identified that the starter code was intentionally converting the secret number to a string on even-numbered attempts (str(secret)), which broke the numerical comparison logic. I verified this by checking the "Developer Debug Info" and seeing the type change in real-time. 


- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

The AI suggested using a relative import (from ..logic_utils) in my test file, which caused an ImportError. I verified this was wrong when pytest failed in the terminal, and I had to manually fix it to an absolute import (from logic_utils) to get the tests to pass.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?
I decided a bug was fixed only when the "Developer Debug Info" matched the UI hints and the pytest suite returned all green. I ran a manual test where I intentionally guessed a high number to see if the "Go LOWER" message appeared correctly and stayed consistent across multiple clicks. The AI helped me design the test_guess_too_high_with_string_secret_type_mismatch test, which specifically checked that the game could handle the previous string-conversion glitch.
---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
Streamlit is like a "Flipbook" that redraws the entire page from scratch every time you touch a button. "Session State" is like a sticky note you put on the side of the flipbook to remember important numbers (like the secret number or your score) so they don't get erased when the page turns. Without that sticky note, the app "forgets" everything it did a second ago.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
  
  One strategy I will reuse is the "Targeted Agent Refactor," where I move logic functions out of the main UI file to keep the code clean and testable. Next time, I will be more careful about reviewing AI-generated import statements, as the AI often gets the folder structure wrong. This project changed my perspective by showing me that AI-generated code can look perfect but contain "intermittent" logic traps that only a human detective can catch.