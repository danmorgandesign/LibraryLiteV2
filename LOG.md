# Library Lite V2 log

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

Still to do: the FigJam flows board and `library-lite-flows.md` don't show any of today's afternoon changes yet. Open: how long archived children's data is kept (UK GDPR), whether books can be marked lost during the year, and the "add a written-off book back" screen on scan (in the annotations only). Next from the review: section 2 (missing flows), starting with the library-day session.

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
