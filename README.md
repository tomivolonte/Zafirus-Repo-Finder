# Zafirus Repo Finder

Este proyecto tiene como objetivo facilitar el encuentro de repositorios de alta calidad en GitHub, evitando el ruido de repos obsoletos o puramente populares.

## 🚀 Cómo correr el proyecto

El proyecto está construido con **Next.js 15 (App Router)** y **TypeScript**.

### 1. Clonar y configurar
```bash
git clone <url-del-repo>
cd workspace-zafirus
```

### 2. Variables de Entorno
Crea un archivo `.env` en la raíz (puedes copiar el `.env.example` si existe) y agrega tu GitHub Token para evitar el rate limit:

```env
GITHUB_TOKEN=tu_token_aqui
# Opcional: para las comparaciones inteligentes con IA
GEMINI_API_KEY=tu_api_key
```

### 3. Instalar y ejecutar
Recomiendo usar `bun` por velocidad, pero funciona perfecto con `npm` o `pnpm`.

```bash
# Con Bun
bun install
bun dev

# Con NPM
npm install
npm run dev
```

La app estará corriendo en [http://localhost:3000](http://localhost:3000).

---

## 🧠 Mi Fórmula de Scoring: V8 Scope Intelligence

Para este desafío, decidí no confiar solo en las estrellas de GitHub. Implementé un motor de búsqueda propio que evalúa cada repositorio bajo **11 capas de señales**:

1.  **Relevancia Semántica**: Qué tan bien matchea con la intención de búsqueda real.
2.  **Mantenimiento (Fuerza)**: Commits recientes, frecuencia de updates y gestión de issues.
3.  **Salud del Proyecto**: Ratio estrellas/forks (indica uso real vs solo "likes").
4.  **Ecosystem Authority**: ¿Es este repo un estándar de la industria (ej. PyJWT)?
5.  **Ecosystem Gravity**: Los repos core tienen "gravedad" para no ser desplazados por repos menores en búsquedas generales.
6.  **Scope Awareness**: El algoritmo detecta si buscas algo "General" o "Específico" y ajusta los pesos de autoridad.
7.  **Production Readiness**: Estabilidad, antigüedad y número de releases.
8.  **Documentación**: Calidad del README y presencia de documentación oficial.
9.  **Riesgo Técnico**: Penaliza repositorios abandonados (más de 1 año sin actividad) o archivados.
10. **Categorización Automática**: Clasifica si es una librería core, un boilerplate o un adaptador de nicho.
11. **Hidden Gems**: Bonus para repositorios con pocas estrellas pero actividad y calidad técnica altísima.

---

## ✨ Bonus Implementados
- **Comparador Inteligente**: Puedes seleccionar hasta 4 repos y ver una comparativa lado a lado.
- **Sugerencias en tiempo real**: Mientras escribes, el buscador sugiere términos técnicos comunes.
- **Filtros Avanzados**: Filtrado por estrellas, mantenimiento, licencia y exclusión de forks/archivados.
- **Detección de Intent**: El sistema entiende si buscas una librería, una herramienta CLI o un boilerplate.

---

## 📈 Escalabilidad a 100+ Devs
Para escalar esta solución en Zafirus, mi propuesta técnica incluye:
- **Redis Caching**: Compartir los resultados de búsqueda entre todos los devs para no repetir llamadas costosas a la API de GitHub.
- **Distributed Workers**: Procesar el enriquecimiento de datos de forma asíncrona para que la búsqueda inicial sea instantánea.
- **Personalización por equipo**: Permitir que cada equipo de Zafirus (Frontend, Backend, DevOps) tenga sus propios "Ecosystem Standards" preferidos.
