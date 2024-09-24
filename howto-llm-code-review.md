You can use this to call claude/other llm to review your code.
this using the llm library

`$ git diff $(git merge-base HEAD origin/SNSR-96)..origin/SNSR-96 | llm -m claude-3.5-sonnet "code review this"`

of course, you can just stick the output in your favarite chat along with the proper prompt.

Also, invest in the prompt, don't just say code review this.
this can give you some ideas:

https://faqprime.com/en/ai-prompts-for-code-reviews/

