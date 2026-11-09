# Instagram agent skill

Instalación project-local del pack [instagram-agent-skill](https://github.com/Jakeschincariol/instagram-agent-skill)
de Jake Schincariol (licencia MIT). Trece skills de Claude Code para llevar una cuenta de Instagram.
Nada se publica solo: los skills escriben, tú publicas.

Instalado desde el commit upstream `d03c56b` (2026-09-13).

## Qué hay aquí

```
.claude/skills/ig-*/     los 13 skills (SKILL.md + herramientas Python)
templates/voice.md       plantilla de tu perfil de voz, rellénala primero
LICENSE                  MIT, del repositorio original
```

Al abrir este repo con Claude Code, los skills se cargan solos y se invocan como
comandos: `/ig-reel`, `/ig-caption`, `/ig-human`, etc.

| comando | qué hace |
| --- | --- |
| `/ig-reel` | Una idea a un Reel: 3 hooks de 26 fórmulas, puntuados, guion, texto en pantalla y beat sheet. |
| `/ig-viral` | Busca qué funciona en tu nicho y lo rankea por múltiplo sobre la mediana de cada cuenta. |
| `/ig-caption` | El caption, revisado. Muestra los 125 caracteres que el feed enseña antes del "... más". |
| `/ig-carousel` | Carruseles: portada, copy por slide y archivos 1080x1350. |
| `/ig-story` | Secuencia diaria de Stories, stickers y embudo a DM. |
| `/ig-profile` | Puntúa tu perfil sobre 100 con una rúbrica de 12 partes y reescribe lo que resta puntos. |
| `/ig-plan` | La semana: qué publicar, formato, cuándo y 10 cuentas con las que interactuar. |
| `/ig-human` | El humanizador: quita guiones largos, vocabulario "IA" y caracteres invisibles, y puntúa el resultado. |
| `/ig-comment` | Comentarios en posts ajenos, 9 tipos según el post. |
| `/ig-reply` | Respuestas al hilo de tu propio post, ordenadas por prioridad. |
| `/ig-dm` | DMs: entrega de keyword, primer mensaje, pitch de colaboración y dos seguimientos. |
| `/ig-repurpose` | Un vídeo, podcast o newsletter en una semana de reels y carruseles. |
| `/ig-audit` | Post-mortem de lo ya publicado, por múltiplo outlier y guardados por alcance. |

## Primer paso: tu voz

Copia `templates/voice.md` a `~/.claude/instagram/voice.md` y rellénalo, o pásale a
Claude tres de tus reels y dile "escribe mi voice.md con esto". Todos los skills leen ese archivo.

```bash
mkdir -p ~/.claude/instagram && cp templates/voice.md ~/.claude/instagram/voice.md
```

## Herramientas que se ejecutan (Python 3, sin dependencias ni red)

```bash
python3 .claude/skills/ig-reel/hookscore.py hooks.txt           # rankea hooks
python3 .claude/skills/ig-reel/beats.py script.txt --target 30  # cronometra el guion
python3 .claude/skills/ig-caption/caption.py caption.txt        # revisa el caption
python3 .claude/skills/ig-human/humanize.py draft.txt --report  # limpia el borrador
python3 .claude/skills/ig-human/detect.py draft.txt             # puntúa el borrador
python3 .claude/skills/ig-viral/swipe.py captured.tsv           # swipe file
```

## Instalación global (opcional)

Si quieres los skills en cualquier proyecto y no solo en este repo:

```bash
cp -r .claude/skills/ig-* ~/.claude/skills/
```
