# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
  1. The new game button was not working
  2. The hint was off. An example, if the secret number is 25 and I enter 2, it would say go lower.

**Answer** :
When I first ran the game using Streamlit, the interface loaded correctly and allowed me to start guessing numbers. However, I quickly noticed several issues with how the game behaved. The “New Game” button did not always reset the game properly, which caused the previous state to remain active. I also noticed that the hints sometimes gave incorrect feedback, such as telling me to guess lower even when my guess was already lower than the secret number. Additionally, the score sometimes behaved strangely and did not update consistently after guesses.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

**Answer** :
I used Chatgpt Codex as my AI teammate to help understand and debug the game code. One correct suggestion it gave me was explaining that the New Game button was not fully resetting the Streamlit session state. It pointed out that values like `status` and `history` were still being stored, which could make the game think it was already finished even after starting a new round. I verified this by reviewing the reset logic in `app.py` and confirming that only some variables were being reset. One suggestion that was slightly misleading was that the score variable might be part of the reset bug, because the score might actually be intended to continue across rounds depending on the design.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

**Answer** :
I decided a bug was really fixed by checking both the code and the game behavior after making changes. For the hint bug, I manually tested guesses above and below the secret number to make sure the messages matched the actual comparison. I also created and ran pytest tests for the check_guess function, and all three tests passed. AI helped me understand what kind of test to write by focusing on specific inputs and expected outcomes instead of trying to test the whole app at once.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

**Answer** :
I learned that Streamlit reruns the script whenever the user interacts with the app, so values can seem to change unless they are stored in st.session_state. The secret number could feel unstable because the app depended on reruns and some state was not being reset or managed correctly. I would explain reruns to a friend by saying the script keeps re-executing, while session state is what lets the app remember important values between runs. The change that helped stabilize the game was making sure the secret number stayed in session state and that the New Game button reset the correct values intentionally.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

**Answer** :
One strategy I want to reuse is focusing on one bug at a time and using AI to explain a specific problem instead of asking for a full rewrite. Next time I work with AI on a coding task, I would verify suggestions earlier by testing smaller changes before accepting them. This project changed the way I think about AI-generated code because it showed me that AI can be useful for debugging and planning, but I still need to review the logic and test everything myself.
