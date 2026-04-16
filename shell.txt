The following shell scripts are necessary if you would like Kilo Code, or other AI coding interfaces, to work properly with your keys.

---

On Mac OS, place the following below existing code in your .zshrc or .bashrc file.

export GROQ_API_KEY="YOUR_GROQ_KEY_HERE"
export OPENROUTER_API_KEY="YOUR_OPENROUTER_KEY_HERE"
export OPENCODE_API_KEY="YOUR_OPENCODE_KEY_HERE"

To do this, open your terminal and type:

code ~/.zshrc or nano ~/.zshrc

or

code ~/.bashrc or nano ~/.bashrc

Then paste the above code and save the file by pressing CTRL+X, then Y, then ENTER.

Then, run the following command to reload your terminal:

source ~/.zshrc

or

source ~/.bashrc

---

On Windows, place the following below existing code in your .bashrc file.

export GROQ_API_KEY="YOUR_GROQ_KEY_HERE"
export OPENROUTER_API_KEY="YOUR_OPENROUTER_KEY_HERE"
export OPENCODE_API_KEY="YOUR_OPENCODE_KEY_HERE"

To do this, open your VS Code terminal and type:

code $PROFILE or nano $PROFILE

Then paste the above code and save the file by pressing CTRL+S.

Then, restart your terminal or run the following command to reload your terminal:

source $PROFILE

---

If you are using a custom API key for Claude Code, Codex, Gemini CLI, or Mistral CLI, you will need to add the following to your .zshrc or .bashrc file:

export CLAUDE_API_KEY="YOUR_CLAUDE_KEY_HERE"
export CODEX_API_KEY="YOUR_CODEX_KEY_HERE"
export GEMINI_API_KEY="YOUR_GEMINI_KEY_HERE"
export MISTRAL_API_KEY="YOUR_MISTRAL_KEY_HERE"