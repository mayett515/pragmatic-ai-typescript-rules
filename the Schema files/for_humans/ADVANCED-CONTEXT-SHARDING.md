# Advanced Context Sharding & The "15 Rule" Limit Explained

### 1. Does "Under 15" mean 15 Files?

**No. It means 15 *Rules per file*.** You can have 30, 40, or 50 different markdown files in your `.ai-rules` folder! The limit only applies to the *inside* of the files.

If you open `01-core.md`, there should be no more than 15 bullet points inside the `<absolute-constraints>` and `<positive-directives>` tags combined. If you put 50 bullet points in one file, the AI's attention window gets exhausted and it starts ignoring the bottom half of the file.

**How to prevent information loss:** When you need to "flatten the folder," it doesn't mean "delete the extra files." It means **merge them**.
If your `01-core/` folder has 5 files, and each file has 3 rules in it, you just copy and paste all 15 rules into a single `01-core.md` file. You lose **zero** information, but the AI now reads the whole thing in one single, clean shot instead of getting lost looking for sub-files.

If a domain is just too massive and has 40 rules, you don't delete them. You just split the domain horizontally:

* `01A-core-mental-model.md` (15 rules)
* `01B-core-decision-algorithm.md` (15 rules)
* `01C-core-ceremony-vs-meaning.md` (10 rules)

As long as your master router points to them, the AI will read them perfectly.

---

### 2. Can you have multiple `.folders` for different scenarios?

**Yes, absolutely.** This is actually a highly advanced enterprise pattern called **Context Sharding**.

If you have a massive monorepo (e.g., a Next.js frontend, a Python FastAPI backend, and a Rust WebAssembly module), keeping all those rules in one `.ai-rules` folder can get messy for humans to look at.

You can create different hidden folders for different environments:

* `.ai-rules-frontend/`
* `.ai-rules-backend/`
* `.ai-rules-devops/`

### How to link them together

You link them exactly the same way you link anything else: **The Master Router.**

You keep **ONE** `00-system-index.md` file at the very root of your whole project. That Master Router acts as the traffic cop for the entire monorepo. You just change the `<routing-logic>` paths to point to the different hidden folders.

Here is exactly what that looks like:

```xml
<routing-logic>
IF the task touches UI components, React hooks, or the Next.js directory:
THEN you MUST explicitly reference, read, and comply with: `.ai-rules-frontend/01-react-rules.md`.

IF the task touches the database, Python API, or FastAPI routes:
THEN you MUST explicitly reference, read, and comply with: `.ai-rules-backend/01-python-api.md`.

IF the task involves Docker, GitHub Actions, or deployment scripts:
THEN you MUST explicitly reference, read, and comply with: `.ai-rules-devops/01-ci-cd.md`.
</routing-logic>
```

By doing this, the AI wakes up, reads the Master Router, looks at your prompt ("Fix the Docker container"), and immediately knows to ignore the frontend and backend folders completely and dive straight into `.ai-rules-devops/`.

You lose no information, you keep your folders hyper-organized by scenario, and the LLM never gets confused.
