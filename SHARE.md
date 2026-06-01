# 🧭 ui-ergonomics — a Claude Code skill for usability audits

## 🇬🇧 English

Hey! I built a little **Claude Code skill** called **`ui-ergonomics`** and wanted to share it.

**What it does:** point it at any screen/component and it audits the UI against **18 usability
dimensions** (~128 concrete rules) — things like prompting, feedback, legibility, error messages,
information density, user control, consistency, and more. It then exports:

- ✅ a **markdown report** of every rule the screen passes / fails / that doesn't apply
- 📋 a **prioritized list of next steps** (worst dimensions first)
- 📊 a **0–100 score** so you can re-run it after fixes and literally watch your UI quality go up

It's just a folder you drop into `~/.claude/skills/` and it works in any project. The rules live in
one `rules.json` file, the scoring is a tiny Node script, and the report is plain markdown.

**About the rules:** I adapted them from a **Brazilian university usability study** (a classic set
of ergonomic criteria used in UI evaluation). They're a great starting point — but they're not
sacred. The whole thing is one JSON file, so **change, add, remove, or edit any rule** to match
your product, your design system, or your company's standards. Make it yours.

Want it? It's free — copy the `ui-ergonomics` folder into `~/.claude/skills/` and ask Claude to
"run a usability audit on <my screen>".

---

## 🇧🇷 Português

E aí! Criei uma **skill do Claude Code** chamada **`ui-ergonomics`** e quis compartilhar.

**O que ela faz:** você aponta para qualquer tela/componente e ela audita a UI contra **18
dimensões de usabilidade** (~128 regras concretas) — coisas como presteza, feedback, legibilidade,
mensagens de erro, densidade informacional, controle do usuário, consistência e muito mais. Depois
ela exporta:

- ✅ um **relatório em markdown** com cada regra que a tela atende / falha / que não se aplica
- 📋 uma **lista priorizada de próximos passos** (piores dimensões primeiro)
- 📊 uma **nota de 0 a 100** pra você rodar de novo depois das correções e ver a qualidade da UI subir

É só uma pasta que você joga em `~/.claude/skills/` e funciona em qualquer projeto. As regras ficam
num único arquivo `rules.json`, a pontuação é um script Node pequenininho, e o relatório é markdown
puro.

**Sobre as regras:** eu adaptei de um **estudo de usabilidade de uma universidade brasileira** (um
conjunto clássico de critérios ergonômicos usado em avaliação de UI). É um ótimo ponto de partida —
mas não é sagrado. Tudo é um arquivo JSON só, então **mude, adicione, remova ou edite qualquer
regra** pra encaixar no seu produto, no seu design system ou no padrão da sua empresa. Deixa do seu
jeito.

Quer? É de graça — copia a pasta `ui-ergonomics` pra dentro de `~/.claude/skills/` e pede pro Claude
"rodar uma auditoria de usabilidade na <minha tela>".
