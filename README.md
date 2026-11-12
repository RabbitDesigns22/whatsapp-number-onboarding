# whatsapp-number-onboarding

**Connect a phone number to the WhatsApp Cloud API without the week of Meta dead ends.**

`whatsapp-number-onboarding` is an agent skill for Claude Code and any agent that reads `SKILL.md` skills. It is for agencies and developers who connect a client's number to their own WhatsApp bot.

API reference skills explain how to send messages. This one covers the part that actually breaks:
- the safe order of portfolio → WhatsApp account → number → app → token → webhook → register with PIN;
- the read-back check after every step;
- a troubleshooting table of real blocks.

The table covers cases like these:
- "all green but nothing arrives";
- duplicate messages;
- a webhook still on an old domain;
- "No se pudo asignar el socio";
- 133005, 133010, 133016;
- 131042 on a few templates.

Every row is tagged **official** (with the developers.facebook.com link) or **field-tested** (it happened in real onboardings and the fix was confirmed live). Nothing unproven is presented as Meta policy.

Tested with and without the skill on 3 real cases. Without it, the agent suggested the partner-sharing route that kept failing in practice, and missed the 10-per-72-h registration limit. With it, the agent found the cause in all 3 cases.

## See the difference

> **You:** Connect my client's number to our WhatsApp bot.

**Without the skill:** it suggests the partner-sharing route that keeps failing, misses the registration limit, and you spend a week in Meta dead ends.

**With the skill:** it follows the safe order (portfolio, account, number, app, token, webhook, PIN), reads back every step, and looks up real error codes in its table. In 3 real cases it found the cause every time.

**Skip it if** you only need to send messages from a number that is already connected.

**Status:** in daily use in the author's own setup. Plain instructions, no scripts, no network calls. MIT. Issues and suggestions welcome.

## Install

```bash
npx skills add RabbitDesigns22/whatsapp-number-onboarding
```

Or copy `skills/whatsapp-number-onboarding/` into `~/.claude/skills/`.

## Honest limits

- Meta changes screens and rules often. The official facts were checked in November 2026.
- Some blocks have a working way around them but no proven cause. They are tagged `[unconfirmed]` and listed under "Not verified".

## Works well with

- [`hands-on`](https://github.com/RabbitDesigns22/hands-on): the agent does every screen it can; you only give the SMS code, the PIN and the secrets.
- [`whatsapp-closer`](https://github.com/RabbitDesigns22/whatsapp-closer): once the number works, make the bot sell.

## Español

**Conecta el WhatsApp de tu cliente a la API de Meta sin perder una semana.** Trae:
- el orden seguro de los pasos;
- la comprobación después de cada paso;
- una tabla de los bloqueos reales con su código de error oficial y su arreglo, marcando qué es oficial y qué está probado en la práctica.

Instalar: `npx skills add RabbitDesigns22/whatsapp-number-onboarding`

## More skills from the same setup

These come from one real workflow: a small agency run with 15+ Claude Code sessions in parallel. Each skill fixes one problem that kept happening there.

| Skill | What it fixes |
|---|---|
| [one-pass](https://github.com/RabbitDesigns22/one-pass) | get it right the first time; stop paying tokens for rework |
| [hora-exacta](https://github.com/RabbitDesigns22/hora-exacta) | real date and time in every message, so nothing lands on the wrong day |
| [hands-on](https://github.com/RabbitDesigns22/hands-on) | the agent does what it can and only asks you for codes, keys and payments |
| [easy-for-them](https://github.com/RabbitDesigns22/easy-for-them) | steps people actually follow: direct link, one action per line |
| [one-answer](https://github.com/RabbitDesigns22/one-answer) | one thought-through answer instead of plan, fix, new plan |
| [never-twice](https://github.com/RabbitDesigns22/never-twice) | a shared error log so no session repeats a known mistake |
| [report-now](https://github.com/RabbitDesigns22/report-now) | status checked live this minute, stamped with the time |
| [sort-me-out](https://github.com/RabbitDesigns22/sort-me-out) | one ordered list of what is urgent, waiting and forgotten |
| [in-the-loop](https://github.com/RabbitDesigns22/in-the-loop) | a live board so parallel sessions know what the others changed |
| [study-first](https://github.com/RabbitDesigns22/study-first) | reads everything in full and answers point by point, no invented details |
| [session-watchdog](https://github.com/RabbitDesigns22/session-watchdog) | wakes the sessions that got stuck mid-task, leaves the rest alone |
| [skill-harvest](https://github.com/RabbitDesigns22/skill-harvest) | reads your sessions and finds the skills you are missing |
| [small-budget-ads](https://github.com/RabbitDesigns22/small-budget-ads) | Meta Ads rules for 1-5 USD a day ad sets |
| [whatsapp-closer](https://github.com/RabbitDesigns22/whatsapp-closer) | evidence-ranked rules for a WhatsApp sales assistant that closes |
| [proposal-pdf](https://github.com/RabbitDesigns22/proposal-pdf) | short PDF proposals with every price checked against its source |
| [published-vs-planned](https://github.com/RabbitDesigns22/published-vs-planned) | says "published" only for what it saw live on the public page, Facebook and Instagram checked apart |
| [source-every-fact](https://github.com/RabbitDesigns22/source-every-fact) | every price, phone and name on a post traced to its source, nothing added |
| [only-what-was-asked](https://github.com/RabbitDesigns22/only-what-was-asked) | "pause only Google Ads" pauses only Google Ads, and proves the rest did not move |
| [model-per-chat](https://github.com/RabbitDesigns22/model-per-chat) | the right model for each chat: top model where mistakes cost money, cheap or none where it only runs often |
| [music-by-niche](https://github.com/RabbitDesigns22/music-by-niche) | music that matches the client's business, never repeated for a client or across clients in 3 weeks |
| [full-power](https://github.com/RabbitDesigns22/full-power) | the best the model can do on high-stakes work: strongest model only for the hard step, best-of-N with a judge, fresh-eyes verifier |

If one of them saved you a redo, a star helps other people find it.

## License

MIT. Made by [Rabbit Designs](https://github.com/RabbitDesigns22).
