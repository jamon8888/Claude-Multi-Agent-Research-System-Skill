# Skill Activation Tests
**Date**: 2025-11-25
**Purpose**: Verify skill-rules.json properly triggers/excludes multi-agent-researcher skill

---

## Test Cases

### ✅ SHOULD TRIGGER (Research Queries)

These queries should activate the multi-agent-researcher skill:

1. **"Research quantum computing advances"**
   - Keyword: "research"
   - Intent: Web research needed

2. **"What are the latest developments in AI?"**
   - Keyword: "what are the latest"
   - Intent: Current events research

3. **"Comprehensive analysis of blockchain scalability"**
   - Keyword: "comprehensive", "analysis"
   - Intent: Deep research needed

4. **"Find information about climate change solutions"**
   - Keyword: "find"
   - Intent: Information gathering (not code-related)

5. **"Tell me about best practices for remote work"**
   - Keyword: "tell me about", "best practices"
   - Intent: General knowledge research

6. **"Deep dive into machine learning frameworks"**
   - Keyword: "deep dive"
   - Intent: Comprehensive research

7. **"Investigate cybersecurity trends"**
   - Keyword: "investigate"
   - Intent: Research task

8. **"Study the landscape of cloud providers"**
   - Keyword: "study", "landscape of"
   - Intent: Market research

9. **"Gather data on renewable energy adoption"**
   - Keyword: "gather"
   - Intent: Data collection research

10. **"Explore cryptocurrency regulations"**
    - Keyword: "explore"
    - Intent: Research topic (not codebase)

---

### ❌ SHOULD NOT TRIGGER (Code/File Operations)

These queries should NOT activate the skill (excluded by patterns):

1. **"Search for the authentication function in the code"**
   - Excludes: "search...function...code"
   - Reason: Code search, not web research

2. **"Find all files that contain 'API'"**
   - Excludes: "find...files"
   - Reason: File system operation

3. **"Explore the codebase structure"**
   - Excludes: "explore...codebase"
   - Reason: Code exploration

4. **"Look for the implementation of UserService"**
   - Excludes: "look for...implementation"
   - Reason: Code navigation

5. **"Search in the repository for database migrations"**
   - Excludes: "search in...repository"
   - Reason: Repo search

6. **"Where is the login function defined?"**
   - Excludes: "where...defined"
   - Reason: Code location query

7. **"Find references to the User class"**
   - Excludes: "find...references"
   - Reason: Code reference search

8. **"Show me the main.py file"**
   - Excludes: "show...file" + ".py"
   - Reason: File viewing

9. **"Read the config.json file"**
   - Excludes: "read...file" + ".json"
   - Reason: File reading

10. **"Analyze the code architecture"**
    - Excludes: "analyze...code architecture"
    - Reason: Code analysis

11. **"Search for syntax examples of async/await"**
    - Excludes: "search for syntax"
    - Reason: Programming syntax lookup

12. **"Find the variable where the API key is stored"**
    - Excludes: "find...variable...stored"
    - Reason: Code variable search

13. **"Debug the authentication error"**
    - Excludes: "debug"
    - Reason: Debugging task

14. **"Write a function to handle user login"**
    - Excludes: "write...function"
    - Reason: Code writing task

15. **"Review the pull request changes"**
    - Excludes: "git...pull request"
    - Reason: Git operation

16. **"Install the dependencies"**
    - Excludes: "install"
    - Reason: Setup operation

17. **"Show API documentation for the endpoints"**
    - Excludes: "api...documentation"
    - Reason: API reference lookup

18. **"List all functions in the utils module"**
    - Excludes: "list...functions"
    - Reason: Code listing

19. **"Check the implementation in server.ts"**
    - Excludes: ".ts" + "implementation"
    - Reason: Code file inspection

20. **"Test the new feature"**
    - Excludes: "test"
    - Reason: Testing task

---

## Testing Procedure

### Manual Testing
To test these patterns manually:

1. **Test a trigger query**:
   ```
   User: "Research quantum computing advances"
   Expected: Skill activates
   ```

2. **Test an exclusion query**:
   ```
   User: "Search for the login function in the code"
   Expected: Skill does NOT activate
   ```

### Automated Testing (Future)
Consider implementing automated tests that:
- Parse skill-rules.json
- Run regex patterns against test cases
- Verify expected activation/exclusion
- Report pass/fail for each case

---

## Exclude Pattern Categories

The 16 exclude patterns cover these categories:

1. **Code/File Search** (Patterns 1-3)
   - Searching within codebase
   - Finding functions/classes/variables
   - Exploring code structure

2. **File Operations** (Patterns 4-5)
   - Reading/viewing files
   - Locating code definitions

3. **Code References** (Patterns 6-7)
   - Finding references/usages
   - Syntax examples

4. **File Listings** (Patterns 8-9)
   - Listing files/functions
   - File extensions (.js, .py, etc.)

5. **Development Tasks** (Patterns 10-13)
   - Debugging
   - Writing/modifying code
   - Testing
   - Git operations

6. **Setup/Infrastructure** (Patterns 14-16)
   - Installation/configuration
   - API documentation lookup
   - Code documentation

---

## Success Metrics

The exclude patterns are successful if:

✅ No false positives: Research queries still trigger normally
✅ Reduced false negatives: Code-related queries don't trigger
✅ User satisfaction: Skill activates when expected, not unexpectedly
✅ Performance: Minimal impact on query processing time

---

## Future Improvements

1. **Add confidence scoring**: Instead of binary trigger/exclude, use confidence levels
2. **Machine learning**: Train model on user feedback to improve patterns
3. **User feedback loop**: Allow users to mark false positives/negatives
4. **Context awareness**: Consider previous conversation context
5. **Hybrid approach**: Combine pattern matching with semantic analysis

---

## Pattern Explanation

### Example Pattern Breakdown

**Pattern**: `(search|find|look|grep|locate)\\s+(for|in|through|within)\\s+(the\\s+)?(code|codebase|file|files|directory|function|class|variable|method|implementation|repository|repo)`

**Matches**:
- "search for the function"
- "find in the codebase"
- "look through files"
- "grep within directory"
- "locate the implementation"

**Doesn't Match**:
- "search for information about" (no code-related keyword)
- "find trends in AI" (no code-related keyword)

---

## Notes

- Exclude patterns use regex, so escaping is important
- Patterns are case-insensitive (regex flag should be set)
- Order doesn't matter - any match excludes activation
- Patterns should be maintained as coding terminology evolves
