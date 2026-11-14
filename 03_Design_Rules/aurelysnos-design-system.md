---
id: rule.design.aurelysnos-design-system
type: rule
scope: global
lane: work
canon_layer: user_canon
status: active
strength: hard
aliases: ["AureLysnOS Design System", "he thong thiet ke aurelysnos", "quy tac giao dien os", "os design rules", "aurelysnos ui matrix"]
related: ["[[_ATELIER-MOC]]", "[[core]]", "[[palette-core]]", "[[_RULES-MOC]]"]
source:
  type: user_input
  ref: "Wireframe App (23 pages), Color Audit Bản 60–69 (00_Kiểm màu, chỉ tiêu.pdf), and Design Reference sets 2026-11-01"
authority: user
confidence: 1.0
always_load: false
tags: []
legacy_tags: [d/rule, k/design, p/atelier, p/app]
last_updated: 2026-11-12
---

# AureLysnOS — Desktop Application Suite Design System

Authoritative design system specification for the unified desktop workspace shell and its 3 bundled applications: **Trạm Dịch (Nexus)**, **Kệ Sách (Library)**, and **Atelier (Studio)**.

---

## 1. Shell Architecture & Structural Grids

AureLysnOS uses a desktop window layout governed by fixed horizontal and vertical anchors:

| Component | Dimensions | Role & Behavior |
|---|---|---|
| **Window Frame** | Base `1440 × 900` px (min `1024 × 700`) | Native Windows desktop framing with custom chrome. |
| **Titlebar** | Height `32px` | Drag region, global search trigger (`Ctrl+K`), quick status indicators (`3/3`), theme toggle, standard window control buttons (`–`, `▢`, `✕`). |
| **App Rail** | Width `72px` | Primary navigation rail: `Tổng quan` (Home), `Trạm Dịch` (Translate), `Kệ Sách` (Library), `Atelier` (Studio), `Cài đặt` (Settings), and Connection status dot (`● đã kết nối`). |
| **Inner App Sidebar** | Width `200px` (collapses to `56px`) | Secondary navigation within the active app. On viewports between `900px` and `1199px`, collapses to a 56px icon-only rail with tooltips on hover. |
| **Main Content Stream** | Dynamic width (Fluid) | Core application view (Library grid, Editor, Kanban board, Settings panels). |
| **Status Column / Inspector** | Width `300–360px` | Right-hand context panel (TTS controls, metadata, recent tasks, system health). |

---

## 2. System Screen Matrix (33 Wireframe Screens)

Across the three constituent applications and the OS shell:

1. **AureLysnOS Shell (6 screens):**
   - `os.home`: Tổng quan (T4-B layout with continue reading/translating cards, Crimson "Cần xử lý" panel, quick notes, and quick expenses).
   - `os.palette`: Command Palette (S3, activated via `Ctrl+K`).
   - `os.notes`: Floating Quick Note widget (360 × 560 px, pinned across windows via `Ctrl+Shift+N`).
   - `os.settings`: Global OS Settings (Theme, Font scale, Motion preferences).
   - `os.boot`: Boot / Splash Screen (S4 with 4-pointed star, port health checks for 5173, 5174, 5175).
   - `os.empty`: Global empty and error state templates (Sleeping Fox motif).

2. **Trạm Dịch · Nexus (9 screens):**
   - `td.library`: Translation Book Library (T1-A compact list with 62px rows, import dropzone).
   - `td.book`: Book Overview (chapter count, translated count, reviewed count, vault sync banner).
   - `td.edit`: Bilingual Editor (T3-C side-by-side view with synchronized paragraph alignment).
   - `td.vault`: Vault Markdown Chapter Importer (3-step stepper: Select project → Select files → Configure import).
   - `td.quick`: Quick Translation Scratchpad (T6-A, `Ctrl+Shift+D` global shortcut).
   - `td.names`: Proper Names Dictionary (T7-A table with search, scope assignment, and batch export).
   - `td.terms`: Terminology Replacement Rules.
   - `td.export`: Multi-format Book Exporter (EPUB 3, TXT, MD).
   - `td.settings`: Translation Engine & API Settings.

3. **Kệ Sách · Library (8 screens):**
   - `ks.library`: Visual Bookshelf (T1-B cover grid, 160px cards, 3:4 aspect ratio, read-only Drive mirror).
   - `ks.series`: Series View (chapter list, reading history, collections manager).
   - `ks.reader.text`: Text Reader (72 chars/line reading column, 8 themes, TTS audio narrator).
   - `ks.reader.comic`: Manga Reader (vertical webtoon scroll, 2-page spread, half-page split for landscape).
   - `ks.comments`: Reader Comments & Annotations timeline.
   - `ks.senses`: Sense Dictionary (Từ điển nghĩa — in-situ word sense replacement rules).
   - `ks.search`: SQLite full-text search across all book contents and notes.
   - `ks.settings`: Library Drive folder path configuration & scan options.

4. **Atelier · Studio (10 screens):**
   - `at.ban`: Project Board (Kanban view with 5-stage pipeline: Ý tưởng → Dàn ý → Viết → Sửa → Đăng).
   - `at.project`: Single Project Workspace.
   - `at.open`: Open Tasks Inspector (T1-A expandable task list).
   - `at.vault`: Vault Integration & Bidirectional Link Hub.
   - `at.health`: System Health Dashboard (6 automated verification gates, Exit codes 0, 1, 2).
   - `at.cli`: CLI Tool Manager & Command Runner.
   - `at.notes`: Markdown Note Editor (T7-A).
   - `at.money`: Personal Expense Tracker (Monthly budget, categorized logs).
   - `at.rhythm`: Habit & Rhythm Tracker (2-week cadence grid).
   - `at.settings`: Studio Preferences & Privacy Locks.

---

## 3. Interaction Tokens & Usability Invariants

Every screen in AureLysnOS conforms to the following audited invariants:

1. **One Bold Button Per Panel (C14):**
   - Each panel has at most **one** bold orange (`#FF9A5C`) CTA button representing the primary action.
   - Secondary actions use outline buttons (`nút viền`).
   - Destructive / cancellation actions use neutral muted buttons (`nút xám`), with a safety confirmation prompt if permanent.
2. **Never Color Alone (C6):**
   - State indicators always pair a symbolic icon (`⚠`, `!`, `ⓘ`, `✓`) with descriptive text.
   - Status badges: Success (`#8FDDB0` with `Đã cài` / `Hoàn tất`), Warning (`#FF9A5C` with `Cảnh báo`), Error (`#8E1B3A` with `Lỗi`).
3. **High-Risk Action Safety Nets:**
   - Permanent deletion modals (e.g., `P · Xoá có tên vật`) clearly state the item name, provide a 30-day trash recovery window, and highlight the safe "Huỷ" button by default.
   - Actions in lists trigger a floating toast notification (`N1`) with a 4–6 second `Hoàn tác` (Undo) opportunity.
4. **Focus Rings (C5 & WCAG 2.4.11):**
   - Focus rings are rendered as a 2px solid border offset by 2px (`viền 2px cách 2px`).
   - Scrollable containers maintain `scroll-padding-top` and `scroll-padding-bottom` equal to the height of sticky headers/footers to prevent focused elements from being occluded.
5. **Motion Limits (C11):**
   - All standard interface transitions are bounded to `≤ 200ms`.
   - The book page-turn animation is bounded to `0.6s`.
   - All animations automatically disable when `prefers-reduced-motion` is active.
