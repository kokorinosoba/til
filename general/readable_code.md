# Chapter 1: Code Should Be Easy to Understand
- Code should be easy to understand
- Code should be written to minimize the time it would take for someone else to understand it
  - Minimizing the time-till-understanding is a better goal even though having fewer lines of code is a good goal

# Chapter 2: Packing Information into Names
1. Choose Specific Words
   - Like get, size, send find, start, make etc.
   - Use more colorful words
   - It's better to be clear and precise than to be cute
2. Avoiding Generic Names Like `tmp` and `retval`
   - Pick a name that describes the entity's or purpose
   - The name `retval` doesn't pack much information. Instead, use a name that describes the variable's value.
   - The name `tmp` should be used only in cases when being short-lived and temporary is the most important fact about that variable
   - Choosing the precise name for loop indexes make the spotting bug easier
   - If you're going to use a generic name like `tmp`, `it` or `retval`, have a good reason for doing so.
3. Prefer Concrete Names over Abstract Names
   - Describe things in more detail
   - `DISALLOW_EVIL_CONSTRUCTORS` => `DISALLOW_COPY_AND_ASSIGN`
   - `--run_locally` => `--extra_logging`
   - Naming after the thing the code do is better than after circumstance where it was typically used
4. Attaching Extra Information to a Name, by Using a Suffix or Prefix
   - Attaching a units as a suffix
   - Attaching a variable state prevent security exploit
   - Attach important details
5. Deciding How Long a Name Should Be
   - Shorter names are okay for shorter scope
   - Use longer names for larger scopes
   - Project-specific acronyms and abbreviations are intimidating to those new to the project
   - Throwing out unneeded words
6. Using name formatting to pack extra information
   - Formatting conventions lead us to make the codes easy to understand
   - Use capitalization, underscores, and so on in a meaningful way
   - Be consistent across your project