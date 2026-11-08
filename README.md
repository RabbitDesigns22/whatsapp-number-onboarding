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

## License

MIT. Made by [Rabbit Designs](https://github.com/RabbitDesigns22).
