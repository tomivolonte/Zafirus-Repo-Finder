---
Task ID: 1
Agent: main
Task: Code reorganization, remove language selector, remove settings, update favorites

Work Log:
- Created /src/lib/types.ts — Central type definitions (ScoredRepo, QualitySignals, TrustLevel, etc.)
- Created /src/lib/constants.ts — Default settings, trending data, localStorage helpers
- Created /src/lib/ui-utils.ts — trustColor, trustLabel, badgeStyle, langColor utilities
- Created /src/components/QualityRing.tsx — SVG score ring component
- Created /src/components/Navbar.tsx — Top navigation (removed "Ajustes", added "Mi Perfil")
- Created /src/components/SearchBar.tsx — Search input with suggestions (no language selector)
- Created /src/components/RepoCard.tsx — Repo result card with compare mode
- Created /src/components/WhyDrawer.tsx — AI explanation drawer
- Created /src/components/ComparePanel.tsx — Bottom comparison drawer
- Created /src/components/AuthModal.tsx — Google login modal
- Created /src/components/ProfileView.tsx — Profile with card-style favorites + GitHub links
- Rewrote /src/app/page.tsx — Clean orchestrator (no spaghetti, ~500 lines vs 1646)
- Removed: Language selector (UI + state + dropdown)
- Removed: Settings page (SettingsView component + nav link)
- Updated: Profile favorites now displayed as mini-cards with GitHub links
- Updated: Navbar has Inicio / Explorar / Mi Perfil (no Ajustes)
- SCORING: NOT MODIFIED AT ALL — all scoring files untouched

Stage Summary:
- Build passes successfully
- page.tsx reduced from 1646 lines to ~500 lines
- All UI logic extracted into 8 separate components
- 3 shared lib modules for types, constants, and utilities
- Language selector completely removed
- Settings page completely removed
- Favorites in profile now show as card-style repos with GitHub links
