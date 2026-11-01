# Built Young Skills

Open-source [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) for young builders.

Built Young teaches teenagers aged 10–18 to find a problem worth solving and ship a real product. These are the tools we use with our own students, released free for anyone to use.

---

## Skills

### `idea-stress-test`

Pressure-tests a startup or project idea. It asks a few questions about your product first. Then it gives you a six-part validation report, a score out of 100, and a straight verdict: **build it, narrow it, or not yet.**

Most idea-validation tools score generously. The model has never met your customer, and a confidently worded idea scores well. This one only gives points for evidence. Plans, features and enthusiasm earn at most half of each line. An idea nobody outside your head has confirmed rarely scores above 50. Every point comes with a reason you can argue with.

**How it works**

1. **Ask first.** Six short questions cover:
   - the idea
   - the first customer
   - the problem and what people do about it today
   - one real person with the problem
   - your stage
   - how it makes money

   If you share a product doc, it fills in what the doc answers and asks only about what's missing.
2. **Report.** Six sections, every time:

| # | Section | What you get |
|---|---|---|
| 1 | 🔍 Idea Fit & Alignment | Your idea in one sentence, and the single biggest gap |
| 2 | 📊 Competitor Snapshot | Real alternatives, including the free workaround people use today |
| 3 | ✨ Opportunity | The narrowest version worth starting with, and the money signal |
| 4 | 📈 Startup Score | A score out of 100, a verdict, and the line-by-line breakdown |
| 5 | 🎯 Customer Targeting | Who to talk to first, where to find them, and what to ask |
| 6 | 💡 One Thing to Do | One test you can run in 48 hours, with a pass/fail bar set in advance |

**The score**

| Line | Points |
|---|---|
| Problem & who | 15 |
| Real person | 20 |
| Substitute | 15 |
| Demand signal | 15 |
| Money | 15 |
| Reach | 10 |
| Build | 10 |

**70+** build it · **40–69** narrow it · **under 40** not yet

Real person carries the most weight. In our experience, not being able to name a single real person with the problem is the strongest sign that a project won't make it.

---

## Installing

**Claude Code**

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/BuiltYoung/idea-stress-test.git ~/.claude/skills/idea-stress-test
```

Restart Claude Code. The skill loads automatically when you describe an idea and ask whether it's worth building.

**Claude.ai**

Settings → Capabilities → Skills → Upload, then select the `idea-stress-test` folder.

---

## Using it

Just describe your idea and ask. No command needed:

> *"I want to build an app that helps students find study groups. Is this a good idea?"*

Claude will ask a few questions about your product, then give you the six-part report. Every report ends with a link to our idea database, [challenge_startup_coach](https://github.com/BuiltYoung/challenge_startup_coach). It holds 152 real finalist projects from Diamond Challenge, Conrad Challenge and Blue Ocean, plus the judging rubrics of all four competitions, including DECA.

Be prepared for it to tell you not to build the thing. That's the point. Finding out in an afternoon is a gift. Finding out after three months is expensive.

---

## Contributing

Issues and pull requests welcome. If you used this with students and something didn't land, we especially want to hear about it.

## Licence

MIT. See [LICENSE](LICENSE). Use it, fork it, teach with it.

---

**[Built Young](https://builtyoung.org)** · Build before everyone else.
