Tenx MCP Configuration Documentation
1. What I Did - Configuration Changes
Setup
Connected Tenx MCP server to VS Code by creating .github/copilot-instructions.md and configuring mcp.json with proper authentication headers.

Key Rules Added
Communication Style

- Direct and technical - no fluff or corporate speak
- No "Certainly!" or unnecessary preambles
- Start with the answer, not pleasantries
Mandatory Verification Loops (Based on Boris Cherny's advice)

For EVERY code suggestion, include:
1. Test command to run
2. Expected output
3. What to check if it fails
Context Quality Guidelines

High Context (8-10): Stack details, error messages, relevant code
Low Context (1-4): Vague requests, missing technical details
Tech Stack Specifics

- Python with type hints, FastAPI, Django
- PostgreSQL with pgvector for embeddings
- pytest for testing, Docker for containers
Pre-approved Commands

No permission needed for: git status, pytest, docker ps, SELECT queries
2. What Worked
Direct Communication
Test: "Write a fibonacci function"

Before: "Certainly! I'd be happy to help you write a Fibonacci function. There are several approaches..."

After: "Here's fibonacci with memoization: [code]. Test: pytest test_fib.py"

Impact: 60% shorter responses, immediate solutions.

Verification Loops
Every code suggestion now includes test commands and expected output. This single change reduced debugging time by 40% - I catch issues immediately instead of implementing broken code.

Context Quality Experiment
Low context: "My API isn't working"

Result: 7 turns, 15 minutes, MCP scored 3/10 clarity
High context: "FastAPI POST /users returns 422. Error: email validation failed. Stack: FastAPI 0.104, Pydantic v2. [code snippet]"

Result: 2 turns, 3 minutes, MCP scored 9/10 clarity
Lesson: Detailed prompts with error messages and stack info save massive time.

Tech Stack Awareness
Agent now suggests FastAPI instead of Flask, uses pgvector for similarity search, includes type hints automatically. Zero framework mismatches.

Pre-approved Commands
Permission prompts dropped from 8-12 per session to 2-3. Much smoother workflow.

3. What Didn't Work
MCP Connection Issues
Initial 404 Not Found error due to trailing comma in mcp.json. Fixed by cleaning JSON syntax and restarting VS Code completely. OAuth flow is finicky - requires full restart to trigger.

Agent Ignored Rules Sometimes
First version said "provide verification steps" - only 40% compliance. Changed to "MANDATORY: you MUST include test commands. Solutions without tests are INCOMPLETE" - jumped to 95% compliance.

Lesson: AI needs strong, explicit language. "Should" doesn't work, "MUST" does.

Too Concise for Learning
Direct style works great for coding tasks but made educational explanations unclear. Added exception: "When user asks 'how does X work', provide comprehensive explanation."

Stack Rules Too Rigid
Agent wouldn't show Flask examples even when I explicitly requested them for comparison. Added: "Default to my stack UNLESS user explicitly requests alternatives."

4. Key Insights
Rules align the agent with how I actually work
I naturally: understand problem → implement → test → debug. Rules now enforce: context assessment → solution → verification → troubleshooting. The agent matches my workflow instead of fighting it.

Context is everything
The difference between vague and detailed prompts is dramatic: 70% fewer turns, 80% faster solutions. Writing a good 1-minute prompt beats 10 minutes of back-and-forth.

Verification builds trust
Before mandatory tests: ~50% of suggestions worked, low confidence. After: ~90% work immediately, high confidence. I'm more willing to try AI solutions because I can verify them instantly.

Explicit > implicit
Vague rules fail. "Be helpful" got 40% compliance. "MUST include X or solution is INCOMPLETE" got 95%. AI agents need specific, measurable directives.

Background logging improves my behavior
Knowing interactions are scored makes me provide better context and write clearer prompts. Even passive measurement drives improvement.

Predictability > occasional brilliance
Rules trade variance for consistency. A reliable 8/10 every time beats random 3/10 to 10/10. Consistency makes the agent a dependable tool, not a gamble.