# Built Young Skills

Open-source [Claude Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) for young builders.

Built Young teaches teenagers aged 10–18 to find a problem worth solving and ship a real product. These are the tools we use with our own students, released free for anyone to use.

---

## Skills

### `idea-stress-test`

Pressure-tests a startup or project idea and returns a straight verdict: **build it, narrow it, or not yet.**

Most idea-validation tools score you out of 100. A score feels like evidence and isn't — the model has never met your customer, and a confidently-worded bad idea scores well. This one asks the six questions a skeptical investor would ask, in order, and then commits to an answer you can argue with.

**The six tests**

| # | Test | The question |
|---|------|--------------|
| 1 | The sentence | Who struggles with what, and what changes after? |
| 2 | The person | Name one real person with this problem — someone you could message today |
| 3 | The substitute | What do they do instead right now, and what does it cost them? |
| 4 | The search | Is anyone looking for this, and where would you check? |
| 5 | The money | Has anyone, anywhere, ever paid for something adjacent? |
| 6 | The 48-hour test | What's the cheapest thing that would prove you wrong this weekend? |

Test 2 does most of the work. In our experience, not being able to name a single real person with the problem is the strongest predictor that a project won't make it.

---

## Installing

**Claude Code**

```bash
git clone https://github.com/BUILT-YOUNG/builtyoung-skills.git
mkdir -p ~/.claude/skills
cp -r builtyoung-skills/skills/idea-stress-test ~/.claude/skills/
```

Restart Claude Code. The skill loads automatically when you describe an idea and ask whether it's worth building.

**Claude.ai**

Settings → Capabilities → Skills → Upload, then select the `idea-stress-test` folder.

---

## Using it

Just describe your idea and ask. No command needed:

> *"I want to build an app that helps students find study groups. Is this a good idea?"*

Claude will work through the six tests conversationally, push back where your answers are vague, and finish with a verdict and one specific next step.

Be prepared for it to tell you not to build the thing. That's the point — finding out in an afternoon is a gift. Finding out after three months is expensive.

---

## Contributing

Issues and pull requests welcome. If you used this with students and something didn't land, we especially want to hear about it.

## Licence

MIT — see [LICENSE](LICENSE). Use it, fork it, teach with it.

---

**[Built Young](https://builtyoung.org)** · Build before everyone else.
