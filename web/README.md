# Idea Stress-Test web page

Built Young's `idea-stress-test` skill as a web form. A visitor answers six questions and gets the six-part report: Idea Fit, Competitor Snapshot, Opportunity, Startup Score (out of 100), Customer Targeting and One Thing to Do, followed by the Built Young call to action.

| File | What it is |
|---|---|
| `index.html` | The page: form, loading state and report, with an EN / 中文 toggle. It works on its own and shows a sample report until the API is connected. |
| `supabase/functions/validate-idea/index.ts` | The server function. It calls the Claude API so the API key never reaches the browser. |

## Connect it

1. **Create a Claude API key** in the Claude Console ([API docs](https://platform.claude.com/docs/en/api/overview)).
2. **Deploy the function.** Use one of these:
   - **Lovable Cloud.** Ask Lovable: *"Create an edge function called validate-idea with this code, and add a secret named ANTHROPIC_API_KEY."* Then paste `index.ts`.
   - **Supabase CLI.**
     ```bash
     supabase functions deploy validate-idea --no-verify-jwt
     supabase secrets set ANTHROPIC_API_KEY=sk-ant-...
     ```
3. **Optional secrets:**
   - `ALLOWED_ORIGINS`: which sites may call the function. Default `https://builtyoung.org,https://www.builtyoung.org`.
   - `ANTHROPIC_MODEL`: default `claude-sonnet-5-5`.
   - `MAX_REQUESTS_PER_HOUR`: per visitor IP. Default `5`.
4. **Point the page at the function.** In `index.html`, set:
   ```js
   API_URL: "https://YOUR-PROJECT.supabase.co/functions/v1/validate-idea",
   API_KEY: "",   // your project's anon (public) key, only if JWT verification is on
   ```
5. **Put the page on the site.** The simplest way is to add `index.html` to the site's `public/` folder as `idea-test.html`. It is then live at `builtyoung.org/idea-test.html`. You can also ask Lovable to rebuild it as a React page that calls the same function.
6. **Test it once with a real idea** before you link to it.

## How a report is made

1. **Research.** Claude runs up to 4 web searches for competitors, demand signals and things people already pay for.
2. **Report.** Claude applies the skill's rubric and returns strict JSON through `output_config.format`.
3. **Checks in code.**
   - Each score line is clamped to its maximum.
   - The total and the verdict band (70+ build it, 40–69 narrow it, under 40 not yet) are computed by the function, not the model.
   - Every link in the report must come from the search results.
   - The page shows all text as plain text, so pasted HTML or script can't run.

## Cost and limits

- **Cost.** Each report makes 2 Claude calls and up to 4 web searches. Web search costs $10 per 1,000 searches, on top of normal token costs. See the [web search tool docs](https://platform.claude.com/docs/en/agents-and-tools/tool-use/web-search-tool).
- **Rate limit.** The per-IP limit lives in memory, so it is best effort only. If the page gets abused, add a CAPTCHA (for example Cloudflare Turnstile) or a database-backed limit.
- **Time.** A report can take a minute or two. Check your plan's edge-function time limit.
- **Sample report.** "See a sample report" shows the Echo (回响) example. To hide it, set `SHOW_SAMPLE_LINK: false` or replace `SAMPLE` in `index.html`.
- **Privacy.** The function stores nothing. It only logs errors. The form tells visitors their answers go to Built Young's server and to Claude.
