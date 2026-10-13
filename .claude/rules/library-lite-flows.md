# Library Lite flows (FigJam summary)

Source: [Library Lite Flows board](https://www.figma.com/board/6TADZXvo4PxMned1su6bZP/Library-Lite-Flows?node-id=39-247) (file key `6TADZXvo4PxMned1su6bZP`), section **"Library Lite V2 — Design Overview"** (`39:247`), the only section on the board. Built from the brief on 2026-10-13; the earlier "Initial Ideas" section was deleted the same day.

Read top to bottom. Key: green rounded = start/end, yellow diamond = decision, blue square = screen/action, violet parallelogram = input, teal cylinder = saved data, teal sticky = decision made, yellow sticky = still to decide (none open right now).

## 1 Who uses it (`39:284`)
School admin, class teachers, other staff (incl. the school admin after setup: no class), and the Library Lite team (approves schools). The school admin and class teachers can manage teachers and classes. Anyone with a login can loan to any child. Children and parents don't log in.

## 2 Site map (`39:311`)
Landing page (public) branches to:
- **Register school** (public) → school name → address & contacts → starting email address → Library Lite emailed to approve → starting email gets a unique link.
- **Log in** (public) → Scan Book, Books (search the whole library, see who has each book), Classes (own class only: class list with each child's name showing the colour of their oldest loan, weekly library day, loan limit, add children). Tapping a name opens the **Child view**: that child's books on loan now (colour-coded), borrowing history, remove the child once they've returned all their books.
- **Log in** also → **Teachers** (school admin and teachers): invite a new teacher for a class (email gets an invite link), change a class's teacher (from that class's page), remove a teacher, add or remove classes (a class can only be removed once it has no children).

## 3 Onboarding (`40:465`)
School registers → Library Lite approves by hand? (No → school doesn't go live) → starting email gets unique link (school admin) → admin sets up classes with teacher emails (saves as they go; invites only sent on Send invites) → each teacher gets an invite link → teacher sets up class and children → class ready.

## 4 Scan flow (`41:388`)
Tap Scan → camera access allowed? (No → remind them to allow it → try again) → scan barcode, or type the ISBN if it won't scan → what state is the book in?
- **Not in the library:** lookup finds it? (No → type title + author → saved against the barcode) → add to library → choose Fiction or Non-fiction → loan it now? (No → just added; Yes → loan branch).
- **Available:** loan it → choose class → choose child → at loan limit? (Yes → loan not allowed, no warning) → loan saved with today's date, starts green → on loan.
- **On loan:** return (loan closed → back in library) or renew (restarts from today, back to green → child keeps it another week).

## 5 Loan rules (`41:549`)
Green days 1–7, orange 8–14, red 15+; overdue after a week. Limit 2 by default (teacher can change). Renew resets to green. Weekly reminder email the day before library day. Books belong to the whole school.

## 6 End of the school year (`43:492`)
Loan history stays until a child leaves. Decided: classes move on by renaming them (e.g. Year 3 becomes Year 4). Decided: leavers must return all their books before they're removed from the school.

## 7 Decisions & out of scope (`41:580`)
The six answered questions (same as the brief's Decisions table) and the out-of-scope list.
