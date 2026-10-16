# Working notes for Claude (Library Lite V2)

Carried over from Claude's Cloud Shell memory on 2026-10-16 so a claude.ai/code session can continue the work. The full day-by-day history is in `notes/memory-history.md` (not auto-loaded; read the parts you need). Keep this file current: when something here changes, update it in the same pass as the other artifacts.

## How Dan wants me to work

- **Numbered questions.** End with a numbered list of questions Dan can answer by number. One question per number, never two under one number. No questions or "flags" buried in prose.
- **Ask if it's perfect, not "what's next".** When a piece of work is done, ask whether everything so far is right, item by item. Dan picks the next area himself.
- **Don't repeat suggestions.** Ask a suggestion once; if Dan passes, drop it. Never raise the usability test plan or laptop/desktop support unless he does.
- **Tablet only.** Design for the iPad in landscape (1194 × 834). Never build phone, desktop or portrait versions, breakpoints or mobile navs unless Dan asks. Don't present my own past additions as if he'd asked for them.
- **Sync every artifact in one pass.** A change is done only when the wireframe, Prototype V2, the brief (Claude Doc and repo export), the FigJam board and `library-lite-flows.md`, the data model, the IA map, the Read mes and `LOG.md` all match. Say so in one summary.
- **No assumptions in flows.** Never design a silent default or automatic assumption; ask the person at the point of action.
- **Diagnose before fixing.** When something renders wrong, diff it against a working sibling (including overrides and parents) and fix the real difference. Say clearly when something is a hypothesis.
- **Tokens.** Never bind Primitives or WF variables in Prototype V2 work, and never hardcode a value. Everything binds to Semantic tokens and Text styles; if no token fits, add a Semantic one that aliases a primitive. Wireframe page work uses WF Semantic (add a WF token if missing).
- **Components** live on the Design System page in the "Components" frame (`1056:7816`), tied to Semantic tokens + Text styles. On undesigned screens, swap wireframe instances for Design System ones screen by screen as each is designed. Never restyle the wireframe components.
- **Never reference earlier Library Lite versions** (old repo, old Figma work, old decisions). V2 is a fresh rebuild.
- **Don't delete a screen Dan made without asking.** Dan edits screens between turns, so re-read before overwriting.
- **Confirmations, not toasts.** Keep confirmation screens and steps; never propose toasts, Undo or a scan feed.
- **Log.** Each change goes in `LOG.md` under today's date (`## Month D, YYYY`, newest first, numbered items), then commit and push to `main`. Commit messages end with the Co-Authored-By line.

## Where things are

- **Repo:** GitHub `danmorgandesign/LibraryLiteV2` (`main`). Brief export `.claude/rules/library-lite-brief-v2.md`, flows export `.claude/rules/library-lite-flows.md`, `LOG.md`.
- **Brief (source of truth):** Claude Doc https://claude.ai/code/artifact/3435a4e0-fbde-453f-bf1a-b5bfe4725009 (tab body node `55fb1e4d-73d6`). The repo file is its export; edit both.
- **Figma file `ufE3h5LxKNO4XfMFR82cSt`:**
  - Wireframes V2 `752:2`: greyscale clickable wireframe, WF Primitives / WF Semantic tokens, Kit section, Read me `773:559`.
  - Prototype V2 `969:3749`: where visual design happens. Read me `969:5688`. No Kit section.
  - Design System `969:3747`: Primitives specimen, Semantic specimen, Components frame `1056:7816`, Icons (Phosphor) `994:3501`, Images (unDraw illustrations) `1004:3522`.
  - Information Architecture V2 `816:936`: data model section `822:824`, IA map `937:3440`.
  - Mood Board `790:703`: font trials (kept), second-colour and loan-pill options.
- **FigJam flows board `6TADZXvo4PxMned1su6bZP`:** one page; overview, site map, flows, decisions, states (section 8), IA (section 9), data model (section 10).
- **Variable collections:** Primitives (`972:3502`), Semantic (`983:3504`, Light/Dark), WF Primitives, WF Semantic, WF Prototype (`proto/no-class`). The Responsive collection was deleted on Oct 16.

## Visual design standards (Prototype V2)

- Fonts: Fjalla One headings, Cantarell body. Brand yellow `#FAFF2F` (yellow/500) with ink text; deep blue `#0150AF` (blue/700) for links, secondary buttons, focus and selected chips; green/orange/red for loans only.
- Card: white, 1px border/subtle, radius/container, lg padding. Overlay: white, 2px border/subtle, radius/container, xl padding, lg gap; header with the title (Text/Heading), a muted Text/Body line, Close on the right; fields size/field wide; buttons in a row below.
- Buttons and fields 48 tall; the nav buttons are 44 (size/touch-min). Edit forms show the current value (Text input Content=Filled).
- Status pills hug their text. Available = blue, On loan = green/orange/red, Retired/At limit/Pending = grey.
- Loan colour: green until the class's next library day; orange once one library day passes without return; red after two or more.

## Navigation (Oct 16)

- **Website nav:** Home · About · Pricing · Contact · Log in, then a yellow "Register your school" button (44 tall) → A3.
- **Signed-in nav:** yellow "Scan Book" button → C1 · Books · Classes · Switch user · Menu (icon only). On Teachers, Help and My account the Menu button has a white background.
- **Menu:** opens overlay **L0 Menu** (Prototype V2 `1066:7811`, wireframe `1066:8117`, section 12). It holds Teachers → G1, Help → J1, My account → L1, then Log out → H1 below one separator. While it's open, an X ("Close menu") sits exactly over the menu icon and closes it. The dropdown is flush with the screen's right edge and the nav's bottom line, with square top-left/top-right/bottom-right corners and no top/right border.
- The nav components live on the Design System page, so on Prototype V2 the Scan Book, Menu and Register your school links are set on each nav instance (82 signed-in navs). Wire them on any new screen. On the wireframe they're on the component.

## Figma Plugin API gotchas

- `overlayPositionType` and `overlayBackgroundInteraction` are read-only. Overlays default to CENTER; position and "close when clicking outside" must be set by hand in Figma.
- A component on another page can't hold a NAVIGATE/OVERLAY reaction to a frame on this page. Set the reaction on each instance instead.
- Cloning a variant drops its text layers' `componentPropertyReferences`; re-link them. Switching an instance to such a variant loses its text overrides; set them again.
- Cloning a frame copies its flow starting point; check `page.flowStartingPoints` after cloning.
- `frame.findAll` reaches inside instances (e.g. the Nav bar); scope text edits so you don't override nav text.
- Binding width/height on a main component turns instances' FILL into FIXED; check instances first.
- Load the node's own fonts before editing text. Bind colours with the real colour as the base paint.
- Prototype actions use `actions: [...]` (array).

## Resume point (Oct 16, end of session)

LOG.md has Oct 16 items 1–24 plus an "Open" line; everything is pushed.

**Ask Dan first:** "Will you set L0's overlay Position to Top right (and tick Close when clicking outside) by hand, or shall I make L0 full-screen again?"
- Both pages' L0 still read Position CENTER and no close-on-outside, so the menu opens in the middle of the screen.
- The setting is on the overlay frame, so one change covers all navs: select any nav Menu button → Prototype tab → its "Open overlay → L0 Menu" interaction → Position Top right, tick Close when clicking outside.
- Full-screen fallback: resize L0 to size/screen-w × size/screen-h, put the card at (834, 77) and the X at (1118, 16), and re-add a transparent Dismiss layer (CLOSE). This lines up only on the 59 screens that are 834 tall, not the 23 taller ones.

**Then:** once the menu is confirmed right, rebuild the Books Sort by dropdown (D1b `969:4764`) the same way (it opens centred too). After that, ask Dan whether everything is perfect.

**On hold:** free trial mechanics; Privacy page; who handles billing (outside the app, with the registrant).
