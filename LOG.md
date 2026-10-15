# Library Lite V2 log

## October 15, 2026

1. Admin rights, decided: only admins can make or remove admins, archive or restore teachers, and run End of year. Billing isn't an admin right; who handles it is still open.
2. Two new frames show what staff who aren't admins see. G1c Teachers has no End of year link. G4f Teacher has no Edit on the Admin card and no Archive teacher, with a note explaining why. G1 has a demo link to switch between the two views.
3. The Archive (G10) notes say restoring a teacher is admins only. Classes, children and books can still be restored by anyone.
4. Section 9 is now "9 Emails", with three new emails. I2 Password reset (the link works once and lasts 12 hours; the A2b demo link now goes through it to A2c). I3 Confirm new email, sent to the new address (button → L1). I4 Email changed notice, sent to the old address once the change is confirmed.
5. Email changes only take effect once the confirm link is opened, so a typo can't lock anyone out.
6. Approval, decided: A6 "Thanks, we've got your details" is the waiting page, and now says Library Lite may get in touch with the school's contacts first. A school that's turned down hears why by email after a conversation, outside the app. There's no approval queue in the app.
7. The FigJam flows board and its repo export (library-lite-flows.md) are brought up to date with Oct 14–15. Remove is now Archive throughout. New boxes cover My account, Archive and the activity log, End of year, books with no barcode, and different copies with their copy check. Section 6 shows the four-step End of year flow, and decisions 8–15 are added.
8. The brief (doc and repo export) is updated with all of the above, plus two new Decisions rows: admin rights and school approval.
9. Two more emails: I5 Invite (button → B3; the B2 demo link now goes through it) and I6 School approved, sent to the starting email (button → B0; the A6 demo link now goes through it). Every email Library Lite sends from the app is now laid out. School turned down is sent outside the app.
10. Billing, decided: handled outside the app, with the person who registered the school.
11. The setup link in I6 (school approved) works for 7 days.
12. A4 Register: confirm school & contacts gains a Contact email field. The data model's schools card now lists contact_name, contact_email and contact_phone.
13. A5 Starting email offers a choice between the contact email from A4 and a different email. Nothing is pre-picked, and Register is disabled until one is chosen. A5a shows the contact email chosen, A5b a different email with the email field. A6 moved right to make room.
14. Shared iPads, decided: a signed-in iPad logs out after 30 minutes without use, staff can switch user with a 4-digit PIN, and there's no lock screen hiding children's names. New section 13 Shared iPad: M1 Who's using this iPad? (staff who've used it), M1a Enter your PIN (keypad → Scan Book), M1b Logged out after 30 minutes. The signed-in nav gains "Switch user". My account (L1) gains a "PIN for switching user" card with a Set your PIN overlay (L1d), which asks for the account password first. Data model: users.pin_hash and a device_users table; loans.loaned_by is whoever is signed in.
15. The brief, the FigJam board (contacts, starting email choice, Switch user, decisions 16–17) and library-lite-flows.md are updated with all of this.
16. Present view fix: every email I cloned had copied I1's flow starting point, so the prototype listed six flows all called "9 Weekly reminder email". D1a, G1b and G1c had picked up duplicate flows the same way, and E1k had a stray "Flow 1". There's now one flow per section: "9 Emails" plus new flows for 10 Help, 11 End of year, 12 My account and 13 Shared iPad.
17. A6's demo link is renamed "Demo: open the school approved email" (it goes to I6, then B0).
18. A5, A5a and A5b intro now reads: "This person becomes your school's first admin. They'll get the link to set up classes and invite teachers."
19. PIN rules, decided: after 5 wrong PINs in a row, PIN log-in locks until the person logs in with email (M1c Too many tries; demo link on M1a). M1 only lists staff who have set a PIN. "Not listed? Email me a reminder to set up a PIN" on M1/M1b → M1d Get a PIN reminder → M1e Check your email → I7 Set up your PIN email (button → Log in, then Set your PIN).
20. B2 Invites sent is now an overlay on B1 (opened by Send invites), not a separate page. It keeps "Go to Library Lite" and the demo link to the invite email (I5).
21. Review section 3 (UX polish, screen sizes) is skipped for now.
22. Archiving a teacher with a class, decided: not allowed until someone takes over the class. G4's Archive teacher now opens G5a, which asks for the new teacher; Archive teacher stays disabled until one is chosen. Picking a teacher swaps to G5b, where Archive teacher → G1. There's no "No teacher" option. G5 stays for staff without a class, and its copy now says an admin can restore them.
23. Review section 4 decisions: loans keep counting through holidays; any staff member can see any child's history; each school chooses how long archived children are kept; days are counted in UK time. Success measures: the share of loans returned on time (one class or the whole school) and teachers active each week. The data model's open questions card is updated to match.
24. The brief (five new Decisions rows), the FigJam board (decisions 18–19) and library-lite-flows.md are updated.
25. After Send invites, the B2 overlay's "Go to Library Lite" now opens G1e Teachers: invites just sent. It shows the admin, the three invited teachers under "Pending invites" with a new Pending chip, and their classes as "Teacher invited (pending)". Every G1 version now says "Pending invites" with the chip, and the invite details are shortened to fit.
26. Archived children are deleted for good 30 days after they were archived (this replaces "the school chooses"). The wording on E5, G9b, G10, K3 and K4 says so, and G10's child rows show the days left.
27. New section 14 Stats, opened from a Stats link on Teachers: N1 whole school (Returned on time 82%, Teachers active each week 6 of 8, period picker, chart placeholders) and N1a one class (class picker; on-time share for that class).
28. Present view: two more duplicate flows from copied frames were removed (G1e, G5a). There are now 14 flows, one per section.
29. Brief, FigJam board and library-lite-flows.md updated; data model open question 4 is decided.
30. Loan colours now follow the class's library day instead of a count of days: green until the next library day, orange (late) once a library day passes without the book coming back, red after two or more. Renewing makes it due the next library day. Updated: Help (J1), the weekly reminder email (I1), the loan-row notes, the website note on H1, the data model and Stats ("on time" = back by the library day).
31. Stats is open to any staff member.
32. Deleted children: their name goes, but their past loans stay as "Deleted child", so each book keeps its borrow count. The book page (D2/D2e) now shows "borrowed 14 times", and one history row shows "Deleted child". The data model rule is updated.
33. Brief (loan rules + three new Decisions rows), FigJam board section 5 and library-lite-flows.md updated.
34. Library-day details, decided: a loan made on any day is due on the next library day (a loan on library day itself is due the following week). A child who moves class follows the new class's day. A class with no library day uses the loan's own weekday. Holidays still count, because schools want every book back by the end of term. These are in the brief, the data model, E1's note, the board and library-lite-flows.md.
35. Confirmed: if a teacher changes the library day, books already out become due on the new day.
36. Written-off book turns up: scanning it opens C14 Written-off book found (the copy, when and why it was written off, "Add it back to the library" or "Not now"). Adding it back opens C14a, a confirmation screen: the copy leaves the lost books report, the activity log records it, and there's "Loan it now" or "Scan another book". C1 has a demo link, "Written-off book".
37. Leftover days-based wording fixed: C8 Loan done and C11 Renewed now give the due library day ("due back on Class name 1's library day, Monday 20 Oct").
38. G10b Archive: not an admin, opened from Archive on G1c. Archived teachers have no Restore and say only admins can restore them.
39. Wireframe: 153 frames (108 screens, 45 overlays) in 14 sections.
40. States pass (Dan: all of them). New Kit components "Empty state" (title, body, optional button) and "Banner" (message), both bound to tokens. New section 15 States:
    - Empty: D1e Books: empty library ("Scan your first book" → C1), E1e Classes: no children yet (Add a child / Paste a list), E3e Child view: nothing borrowed, D2f Book: never borrowed, G10e Archive: empty, G11e Activity log: empty, K5e Lost books: none, N1e Stats: not enough loans yet.
    - No results: D1n Books, C12n Find by title (still offers adding without a barcode), C7n Choose child.
    - Errors: C1x no connection (banner, scanning and saving paused), A3x school lookup not working (→ type details, A3b), E1x save failed (shown on an Edit window), X1 Link expired (one shared page for every kind of link), A2x wrong email or password, A2y account archived.
    - Loading: C1l Finding this book.
    - Session: A2t phones log out after 30 minutes without use.
41. Brief: new "Empty and error states" paragraph.
42. Wireframe: 172 frames (126 screens, 46 overlays) in 15 sections.
43. Stats "Not enough loans yet" shows until 10 loans have come back (Dan confirmed).
44. Demo links from the main screens into their states: D1 → D1e, D1n; E1 → E1e; E3 → E3e; D2 → D2f; G10 → G10e; G11 → G11e; K5 → K5e; N1 → N1e; C12 → C12n; C7c → C7n; C1 → C1x, C1l; A3 → A3x; A2 → A2x, A2y, A2t, X1; and the E1a library-day window swaps to E1x. A few screens grew slightly, so their sections were made taller to fit.
45. FigJam board: new section "8 Empty, error and loading states" (82:482) with every state in four columns (Empty, No results & loading, Errors, Session), and the same summary in library-lite-flows.md.
46. Brief: a table of every state (state, where, what it shows) under "Empty and error states".

## October 14, 2026

Morning:

1. Teacher (G4) is now a page rather than an overlay, mirroring the class page: name and class are Setting cards with Edit overlays (G4a, G4b), and Remove teacher has a confirm overlay (G5).
2. Books (D1): Type and Status filter chips, a Sort by dropdown (D1b) and a filtered state (D1a), with a filter panel on the right.
3. Ran a design review of the whole wireframe. Section 1 (gaps that block the build) is worked through below.

Afternoon (review section 1):

4. Multiple copies, decided: no school barcode labels. When every copy of a book is on loan, the On loan screen (C9) offers "It's a different copy" (C9a), which loans it straight away. It also asks the other child's teacher to confirm in an in-app pop-up (E1k, answers E1l/E1m) that keeps coming back until they answer. If the scanner is that teacher, they're asked on the spot (C9b). Returns of a title with several copies out always ask which child (C9c).
5. Rule for every flow: never assume or default. When the app can't know something, it asks the person.
6. Books with no barcode: "No barcode? Find it by title" on C1 and C3 opens C12 (search by title or author). C13 adds a book with no barcode. As the title is typed, it suggests matching books already in the library (C13a), and picking one asks whether it's another copy (C13b).
7. Nothing is deleted any more: Remove is now Archive for teachers, classes and children. A new Archive page (G10, with a Restore class overlay G10a) lets anyone restore them, and an Activity log (G11) records every archive and restore. Nobody can archive themselves or the last admin.
8. End of year: a new section 11 holds a guided flow. K1 sets new class names, suggested by adding one to the year number, with an edit overlay K1a. K2/K2a handle the leavers' books still out. K3 confirms everything in one step, and K4 is the done screen.
9. Leavers' unreturned books are written off at End of year, one at a time by a person (K2b), never automatically. A new Lost books report (K5) lists each year's write-offs and can be downloaded as a CSV.
10. Invite links last 14 days. Teachers (G1) lists invites still waiting, with when they expire, and a Resend button. G1 also has new links to Archive, Activity log, End of year and Lost books.
11. Data model: books are split into titles and copies, with new copy_checks and activity_log tables. Archive columns were added to users, classes and children, plus users.name, invites.expires_at, loans.closed_as and copy write-off columns. New rules: one open loan per copy, nothing is assumed, write-offs are always chosen, and End of year is one transaction. Open question 1 (multiple copies) is closed.
12. Updated the brief (the Claude Doc and the repo export) for all of the above, with six new rows in the Decisions table.

Evening (review section 2, missing flows):

13. Library-day session: tried a scan session with toasts, Undo and a "Just scanned" list on C1, then rolled it all back. Loans, returns and renewals keep their confirmation screens (C8, C10, C11), and there's no separate Returns session.
14. Choosing the child (C7) is now a grid of big name tiles, 4 across the full width, built from a new Child tile component in the Kit. Search, sort (first name A–Z or Z–A, most books out, oldest loan first) and filters (can borrow or at limit, loan colour) are hidden until "Show search and filters" is tapped (C7c).
15. USB or Bluetooth barcode scanners are added to the brief: they work exactly like a camera scan.
16. New book page (D2), opened from Books: copies and who has them, borrowing history, edit title and author (D2a) and category (D2b). Any staff member can mark a copy lost or damaged at any time, after a confirm (D2c, then D2e). Archive book (D2d) is blocked while a copy is on loan, and archived books can be restored from the Archive (G10).
17. Books (D1, D1a) gained Loan colour and Class filters, so overdue books across the school are easy to find (shown, not wired).
18. Adding many children: "Paste a list of names" on Add a child (E2) and class setup (B4). Each line keeps the first name and the surname's first letter. A check screen lists every child before saving (E2a–E2d, B4a–B4d), and a name already in the class has to be answered: Add anyway or Skip.
19. Moving a child: the child view (E3) has a Class card. Edit opens Move to another class (E3h), and E3i shows the result. Their loans and history move with them, and the move goes in the activity log.
20. Inviting: G2 is now Invite someone, either a teacher for a class or staff without a class (G2a). Only the email is required. Staff without a class are listed with the teachers. Waiting invites can be cancelled after a confirm (G1a, then G1b), using a new optional second button on the List row component.
21. Job shares: class pages (G7, G7b, G8) have an optional Second teacher (G7e). Both teachers see the class as their own and get the reminder email.
22. My account: a new nav link and a new section 12 with My account (L1), plus overlays to edit your name (L1a), change your email (L1b, which only takes over once the confirm link is opened) and change your password (L1c).
23. Admins: the teacher page (G4) has an Admin card to make someone an admin (G4c, then G4d) or remove it (G4e). A school can have several admins and always keeps at least one.
24. Data model: archived titles, write-off reasons (lost, damaged, not returned), a second teacher per class, invites that can be cancelled or have no class, pending email changes, admins for any user, and new activity log actions (title edited, moved, invite cancelled, admin added and removed).
25. Updated the brief (the Claude Doc and the repo export) for all of the above, with seven new Decisions rows. The wireframe now has 128 frames (87 screens and 41 overlays) in 12 flow sections.

Still to do: the FigJam flows board and `library-lite-flows.md` don't show any of today's changes yet. Open: what admins can do that other staff can't, how long archived children's data is kept (UK GDPR), and the "add a written-off book back" screen on scan (in the annotations only). Next from the review: approval states and emails (items 13–14), then billing, empty and error states, and shared iPads.

## October 13, 2026

1. Set up the repo: `CLAUDE.md` loads the V2 brief and a summary of the flows board as Claude Code rules.
2. Answered the brief's six open questions:
    1. Staff can type an ISBN if a barcode won't scan, and the app reminds them to allow camera access if it's blocked.
    2. A child at their loan limit is blocked, with no warning step.
    3. Staff can search the whole library.
    4. New books are marked Fiction or Non-fiction only.
    5. The school admin is an extra user without a class.
    6. Loan history stays until a child leaves.
3. End of year: classes move on by renaming them, and leavers must return all their books before they're removed.
4. Classes page: a class list where each name shows the colour of the child's oldest loan, plus a child view with current loans, history and Remove child (only once all books are returned).
5. Added a Teachers area for the school admin and class teachers: invite a teacher for a class, change a class's teacher from the class page, remove a teacher, and add or remove classes (a class can only be removed once it has no children).
6. Renamed the signed-in pages to Scan Book, Books, Classes and Teachers.
7. FigJam flows board: rebuilt as one "Library Lite V2 — Design Overview" section with seven parts (roles, site map, onboarding, scan flow, loan rules, end of year, decisions). Deleted the old "Initial Ideas" section.
8. Figma wireframe ("Wireframes V2" page): 38 clickable greyscale iPad-landscape screens in 7 flows, built from a token-bound component kit, with 21 annotations, section notes and a Read me.

Afternoon:

9. Classes nav link now depends on who's logged in: teachers go to their own class, staff without a class get "Choose a class / Scan a book". The prototype tracks this with a variable set by the log-in buttons.
10. Save-as-you-go on long forms: admin class setup (now input fields), teacher class setup, invite teacher and add class. Changing a class's name or teacher saves straight away.
11. Passwords: a strength meter plus rules (at least 10 characters, a number, a special character, not a common password), used when teachers and the school admin create accounts and when resetting a password. Added a create-account step for the school admin.
12. Scanning: if a scan doesn't find the book, staff scan once more. If it still isn't found, the book is saved with its barcode and the typed title and author are attached to it; cancelling deletes it.
13. Loaning: a teacher's own class is chosen for them, with a Change class option. Staff without a class choose the class first. A child at their limit has an arrow that opens an overlay of the books they have out.
14. Teachers page is open to any staff member. A teacher opens as an overlay, with a confirmation overlay before removing them.
15. Classes are renamed on their page in Teachers. Removing a class is blocked while any child has a book out; otherwise a warning says it also removes the children and their history, and offers Rename instead.
16. Added a forgot-password flow from Log in.
17. Public website (Home, About, Pricing, Contact) with placeholder content and its own nav. Registration now starts from the website; the old landing page was removed. Pricing is still to decide.
18. Reviewed the wireframe against the brief and the FigJam board and fixed the gaps. The wireframe now has 51 frames (46 screens and 5 overlays) in 8 flows.
19. Added a mock-up of the weekly reminder email (new section 9): sent the day before library day, listing the class's books on loan, oldest first, colour-coded, with an Open Classes button. The wireframe now has 52 frames in 9 flows.
20. Added Help to the signed-in nav, between Teachers and Log Out.
21. Added a Help page (new section 10): quick answers on scanning, barcodes that won't scan, loan colours and loan limits, plus a placeholder contact line. Help in the nav opens it. The wireframe now has 53 frames in 10 flows.
22. Added Help to the brief and to the FigJam site map.
23. Added a data model (new "Data model" section on the Information Architecture V2 page): 8 tables, how they relate, what's calculated rather than stored, the rules the database enforces, the weekly reminder job, and 5 open questions (multiple copies, removing a teacher, school holidays, children's data, time zone).
24. Every wireframe screen now has a Development annotation saying what it reads from and writes to the database. The Read me points to them.
25. Registration now looks the school up instead of asking for its address. Staff search England's official list of schools (GIAS) by name, postcode or both, pick their school from the matches, and its address fills in. A school that's already registered is told to ask its admin for an invite. A school that isn't listed types its details in by hand. This added three screens (choose your school, enter details by hand, already registered) and a School card component. The wireframe now has 56 frames in 10 flows.
26. Data model: schools now store their URN (the school's unique reference number). A new gias_schools table holds the GIAS list of about 25,000 open schools, refreshed by a weekly import job. The database allows only one school per URN.
27. Updated the brief and the FigJam flows board for the school lookup. Looking up schools in Wales, Scotland and Northern Ireland is out of scope for now.

Evening:

28. Class page (E1): the weekly library day and loan limit are now read-only, each with an Edit button. Edit opens an overlay with a dropdown (Monday to Friday; 1 to 5 books) and Save or Cancel. Added Select and Setting components to the Kit.
29. Class page in Teachers (G7, G7b, G8): class name and teacher work the same way, through Rename class and Change teacher overlays. These changes now save on Save rather than as you type.
30. Children's names are now two fields, first name and an optional one-letter initial, on teacher class setup (B4) and Add a child (E2). Surnames are never stored. The data model's children table now has first_name and initial.
31. Returning books without scanning: the child view (E3) has a Return button on each book on loan, and children on the class list (E1) who have books out get a Quick view overlay of their loans with Return on each. Every return asks for confirmation first, and the screens after show the book moved into history. Once all books are back, Remove child is enabled.
32. Font pairs for a possible visual style, on the Mood Board page: Fjalla One with Cantarell, Roboto with Lora, Montserrat with Karla, and Fugaz One with Work Sans, each with its own text styles and tokens.
33. Updated the brief for all of the above. The wireframe now has 75 frames (54 screens and 21 overlays) in 10 flows.
