# Luale Club

Landing do Luale Club, a partir do [react-landpage-template](https://github.com/PHChemin/react-landpage-template): **Vite + React + TypeScript + Tailwind CSS v4**, motion (Magic UI / Originkit) e deploy no **GitHub Pages**.

O visual ainda é o demo do template. O próximo passo é preencher a documentação abaixo — sem isso, não personalize `src/App.tsx` nem os tokens.

## Documentação a preencher

Campos em branco são esperados. Não invente dados do cliente: o que não souber, deixe vazio. A skill `.cursor/skills/design-landing/` infere o resto e registra como hipótese.

| Arquivo | O que escrever agora |
| --- | --- |
| [docs/CLIENT_BRIEF.md](docs/CLIENT_BRIEF.md) | Dados, negócio e frases. Só a seção **Dados** é essencial. |
| [docs/PRD.md](docs/PRD.md) | O que a landing precisa comunicar e quais contatos linkar. |
| [docs/REFERENCES.md](docs/REFERENCES.md) | Links e prints. Arquivos de imagem vão em `docs/references/`. |
| [docs/ART_DIRECTION.md](docs/ART_DIRECTION.md) | Deixar em branco até a skill `design-landing`. |
| [docs/SDD.md](docs/SDD.md) | Stack já descrita. Ajustar só se a decisão técnica mudar. |
| [docs/UI_GUIDANCE.md](docs/UI_GUIDANCE.md) | Regras gerais. Ajustar só com uma exceção deste projeto. |
| [docs/DEPLOY.md](docs/DEPLOY.md) | Domínio, quando existir. Pages: `https://phchemin.github.io/luale-club/`. |

## Stack

| Camada | Escolha |
| --- | --- |
| UI | React 19 + TypeScript |
| Estilo | Tailwind v4 (`@tailwindcss/vite`) + tokens shadcn |
| Motion bank | Magic UI (via shadcn) + Originkit (pré-baixado) + handmade |
| Build | Vite → `dist/` estático |
| Deploy | GitHub Actions → GitHub Pages |

## Começar

```bash
npm install
npm run dev
```

Abra o endereço do terminal (geralmente `http://localhost:5173`).

Depois da documentação:

1. Ajuste tokens/cores em `src/styles/main.css`.
2. Troque textos, links e CTAs em `src/App.tsx` (e `index.html` title/description).
3. Coloque logo/fotos em `public/` se precisar.
4. `npm run build` → `npm run preview`.
5. Deploy: `docs/DEPLOY.md`.

Contato só via links (`wa.me`, `mailto:`, redes) — Pages é estático.

## Banco de componentes

Código já versionado no repo (sem fetch no dia a dia):

| Origem | Pasta | Política |
| --- | --- | --- |
| **Originkit** | `src/components/originkit/` | Salvo no template (limite free ~3 fetches/dia) |
| **Magic UI / shadcn** | `src/components/ui/` | Starter set; no projeto: `npx shadcn add @magicui/<nome>` |
| **Handmade** | `src/components/handmade/` | Efeitos próprios (ex.: `ClickEffects`) |

Detalhes: [`src/components/README.md`](src/components/README.md).

```bash
npx shadcn@latest add @magicui/<nome>
npx shadcn@latest add button

npx originkit login
npx originkit add <nome>
```

Config: `components.json` (shadcn + registry `@magicui`) e `originkit.components.json`.

Não commite a pasta `.originkit/` (login/cache local). Já está no `.gitignore`.

## Deploy

1. **Settings → Pages → Source → GitHub Actions**.
2. Push na `main` (workflow `.github/workflows/deploy.yml`).
3. Se CSS/JS quebrarem em `phchemin.github.io/luale-club/`, descomente `VITE_BASE_PATH: /luale-club/` no workflow.
4. Domínio: `docs/DEPLOY.md`.

## Scripts

```bash
npm run dev       # desenvolvimento
npm run build     # gera dist/
npm run preview   # testa o build localmente
```

## O que não versionar

- `.env` / secrets / API keys
- `.originkit/` (credenciais/cache do CLI)
- `node_modules/`, `dist/`
