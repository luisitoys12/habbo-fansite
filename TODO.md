# Habbo Fansite - TODO

## ✅ Completado
- [x] Next.js 14 + TypeScript + Tailwind setup
- [x] ThemeProvider (light/dark/system)
- [x] Header con navegación responsive
- [x] RadioPlayer con Audio HTML5 + SSE (EventSource)
- [x] Home page con Hero, Stats, News, Events, Sidebar (Staff, Radio, Quick Links)
- [x] Layout global + Footer
- [x] CSS variables + design system (colores, botones, cards, badges, inputs)
- [x] SSE hook (`useSSE`) + `useRadioSSE` para tiempo real
- [x] API routes structure (`/api/sse/stream`, `/api/radio/status`)

## 🔄 En progreso / Próximos

### Backend (API - Express/Node)
- [ ] Prisma schema: User, News, Event, EventRegistration, Staff, RadioTrack, RadioListener, Ranking, HabboProfile
- [ ] Auth: JWT + HttpOnly cookies (login, register, logout, me, refresh)
- [ ] Radio: Icecast/Shoutcast integration (`getStreamStatus`, `getNowPlaying`, `getListenerStats`)
- [ ] SSE endpoint real con autenticación opcional
- [ ] CRUD News, Events, Staff, Rankings
- [ ] Habbo API proxy (`/api/habbo/*`) → `https://habbo.es/api/public/`
- [ ] Rate limiting, CORS, Helmet, Zod validation
- [ ] Dockerfile + docker-compose (api, web, postgres, redis)

### Frontend (Next.js)
- [ ] `/news` list + `/news/[id]` detail
- [ ] `/events` list + `/events/[id]` detail + inscripción
- [ ] `/radio` página completa (historial, top songs, DJ schedule, chat)
- [ ] `/staff` grid con perfiles
- [ ] `/rankings` semanal/mensual (puntos, eventos, radio)
- [ ] `/habbo` buscador de perfiles + badge viewer + room viewer
- [ ] `/auth/login`, `/auth/register`, `/auth/forgot-password`
- [ ] `/admin` dashboard (CRUD news/events/staff, radio control, analytics)
- [ ] PWA: manifest, service worker, offline support
- [ ] SEO: sitemap.xml, robots.txt, Open Graph, JSON-LD

### Integración Habbo API (`habbo.es/api/public/api-docs`)
- [ ] `GET /users/:name` → perfil público
- [ ] `GET /users/:name/badges` → placas
- [ ] `GET /users/:name/rooms` → salas
- [ ] `GET /rooms/:id` → info sala
- [ ] `GET /rooms/:id/users` → usuarios en sala
- [ ] `GET /groups/:id` → grupo
- [ ] `GET /groups/:id/members` → miembros
- [ ] Cache en Redis (TTL 5-15 min)
- [ ] Fallback graceful si API cae

### DevOps / GitHub
- [ ] Repo en GitHub (public/private)
- [ ] GitHub Actions: lint, typecheck, test, build, docker push
- [ ] Issue template + PR template
- [ ] README con setup, env vars, deploy
- [ ] Deploy: Vercel (web) + Railway/Render/Fly.io (api) + PostgreSQL

### Calidad
- [ ] Tests: Vitest (unit) + Playwright (e2e)
- [ ] Storybook para componentes UI
- [ ] ESLint + Prettier + Husky
- [ ] Bundle analysis + performance budget

## 📝 Notas
- API Habbo: `https://habbo.es/api/public/api-docs` (OpenAPI/Swagger)
- Radio: Icecast `/status-json.xsl` o Shoutcast `/stats`
- SSE: usar `EventSource` nativo + reconexión automática
- Auth: cookies `SameSite=Lax`, `Secure` en prod, `HttpOnly`

## 🚀 Comandos útiles
```bash
# Desarrollo
docker-compose up -d
pnpm dev        # web + api concurrentemente

# DB
pnpm db:push    # Prisma push
pnpm db:studio  # Prisma Studio

# Build
pnpm build
docker build -t habbo-api ./apps/api
docker build -t habbo-web ./apps/web
```