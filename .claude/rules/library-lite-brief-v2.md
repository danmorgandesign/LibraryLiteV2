# Library Lite Brief V2

Rewritten Oct 13, 2026 from Dan's notes, his Q&A answers and the Figma flows board. Open questions answered the same day.
Source of truth: the "Library Lite Brief V2" Claude Doc (https://claude.ai/code/artifact/3435a4e0-fbde-453f-bf1a-b5bfe4725009). This file is a markdown export of it; update it when the doc changes.

## What Library Lite is

In UK primary schools, lending library books to children is a rushed job squeezed into a busy day. Library Lite is a website that makes that job fast for teachers and other school staff.

Its heart is one action: scan a book's barcode on an iPad. The app works out what state the book is in and offers the next step: add it to the library, loan it to a child, take it back, or renew it. Around that, staff can see who has what, which loans are overdue, and what each child has borrowed in the past.

## Who uses it

It's for school staff only for now. Children and parents don't log in or see anything.

- **School admin:** the account that registered and pays for the school. Sets up the school's classes and invites teachers. After that they're an extra user without a class, like a teaching assistant, who can also manage teachers and classes. Any staff member can be made an admin too, from their page on Teachers, after a confirm. A school can have several admins and always keeps at least one. Only admins can make or remove admins, archive or restore teachers and run End of year. Billing isn't one of the admin rights: it's handled outside the app, with the person who registered the school.
- **Class teachers:** each is linked to a class. They manage their class's children, library day and loan limit, and get the weekly reminder email. They can also manage teachers and classes.
- **Other staff, such as teaching assistants:** these users don't need a class of their own. The school admin is one of them. They can also manage teachers and classes.

Anyone with a login at the school can scan books and loan them to any child in the school.

**Shared iPads.** Class iPads stay signed in, but log out after 30 minutes without use. Switch user in the nav lists the staff who have used that iPad and set a PIN: they tap their name and enter their 4-digit PIN, which they set in My account. Anyone not listed can ask for an email reminder to set one up. After 5 wrong PINs in a row, PIN log-in locks until they log in with their email. Every loan records who was signed in. Children's names stay visible while signed in; there's no separate lock screen.

Everyone has a **My account** page, linked from the nav, where they change their own name, email and password. A new email only replaces the old one once the person opens the confirm link sent to it, so a typo in the new address can't lock anyone out. The old address is then emailed to say the email has changed. A new password follows the same rules as at setup.

## The core flow: scan a book

One Scan button covers adding, loaning, returning and renewing. The app checks the book's barcode against the school's library and shows only the options that fit.

Scan flow (1 scan, 3 outcomes):

- **Not in the library** → add it → either just add it to the library, or go on to loan it.
- **In the library, available** → loan it → choose child (a teacher's own class is chosen for them, with an option to change class; staff without a class choose the class first).
- **In the library, on loan** → return it (or renew it).

**More than one copy.** Copies of a book share an ISBN, and schools don't stick their own labels on books. Library Lite finds extra copies as they turn up:

- If a free copy of the book exists, scanning it simply loans that copy.
- If every known copy is on loan, the On loan screen offers Return and Renew. Under them it asks "Do you suspect this may be a book that there are multiple copies of?", with the button "Yes, I reckon it's a different copy" to say **It's a different copy**. Choosing a different copy loans it straight away under the same title details. It also asks the teacher of the child who has the other copy to check that child still has it.
- That check pops up in the app the next time the teacher uses it, and keeps popping up until they answer. **Yes, they still have it** means the school now has two copies. **No, it's back in the library** means the first loan was never scanned back in, so it's closed as returned. An unanswered check is never decided automatically.
- If the person scanning is that child's own teacher, they're asked on the spot instead.
- When more than one copy of a title is on loan, a scan asks **who's returning this copy?** and staff pick the child. The app never guesses which loan to close, including when a teacher scans in a pile of returns for their class.

If a scan doesn't find the book, staff are asked to scan it once more. If the second scan still isn't recognised or found, the book is saved straight away with its barcode. When staff add the title and author, they're attached to that barcode, so the book is recognised the next time it's scanned. If they cancel instead, the saved book and its barcode are deleted. A new book can be loaned straight away or just added to the library.

When loaning a book, a teacher's own class is chosen for them, so they go straight to choosing the child, with an option to change class. Staff without a class choose the class first. Children show as a grid of big name tiles across the full width. They're in first-name order, A–Z. A search by name is hidden until staff tap Show search. There's no sort or filter here.

If a barcode won't scan, staff can type in the ISBN instead. If camera access is blocked on the iPad, the app reminds them to allow it when they try to scan. Staff can also use a USB or Bluetooth barcode scanner instead of the camera. It types the barcode like a keyboard, and the scan screen treats it exactly like a camera scan.

**Books with no barcode.** Some books have no barcode at all, such as old books and donations. This is rare, and these books simply never get one. From the scan screen, staff tap **No barcode? Find it by title** and search the library by title or author. Picking a book there works exactly like scanning it. If the book isn't in the library yet, staff add it by typing the title and author. As they type the title, the app suggests matching books already in the library. The search is short and forgiving: any word in the title or author, ignoring case, punctuation and small typos. If they pick a suggestion, the app asks **is this another copy of that book?** Yes adds it as another copy, and No adds it as a new book. The app never decides it's the same book on its own.

When a book is added, staff choose Fiction or Non-fiction. There are no sub-genres.

## Loan rules

- **Loan limit:** each child can have 2 books out at once by default. A class's teacher can change that limit at any time. A child at their limit can't borrow any more: the loan is blocked, with no warning step. Staff can tap that child to see which books they have out.
- **Colour coding:** books are due back on the class's library day. A loan is green until then. If that library day ends without the book coming back, it turns orange (late). If the next library day passes too, it turns red. The teacher sets the library day, and every loan is due on the next one, whatever day it was made (a loan made on library day is due the following week). If the teacher changes the library day, books already out become due on the new day. A child who moves class follows the new class's day. If a class has no library day yet, a loan is due on the same weekday a week later. Holidays still count, so books still out after a holiday are red: schools want every book back by the end of term. Days are counted in UK time.
- **Renewing:** this tells the app the teacher has seen the book and is happy for the child to keep it. The loan goes back to green and is due on the next library day.
- **Weekly reminder:** each teacher gets an email the day before their class's library day. It lists the books their class has on loan, with the same colour coding as the website.
- **Collection:** books belong to the whole school library, not to a class, so any child can borrow any book.

## Viewing books

Books lets any staff member search the whole school library and see who has each book. Filters narrow the list by type, available or on loan, loan colour (so overdue books across the school are easy to find) and class.

Tapping a book opens its page. Any staff member can:

- see each copy and who has it now, and the book's borrowing history
- edit the title and author, or change the category
- mark any copy **lost** or **damaged**, at any time of year, after a confirm. If the copy is on loan, that loan is closed. The copy goes in the lost books report with its reason, and scanning it later asks whether to add it back
- archive the book, after a confirm. It's blocked while any copy is on loan. Archived books leave Books and search, keep their history, and can be restored from the Archive

## Managing a class

Each teacher has a Classes page that only shows their own class. On it they can:

- see the class list, with each child's name showing the colour of their oldest loan, and open a quick view of a child's books to return them
- set the class's weekly library day, which most UK primary classes have on their timetable
- change the class's loan limit (both settings change through an Edit button and a dropdown)
- add the children in their class, as a first name plus a surname initial only when two children share a first name. Surnames are never stored
- add many children at once by pasting a list of names, one per line, from the school's records system. Only the first name and the first letter of the surname are kept. A check screen lists every child before anything is saved: staff can fix or remove any row, and a name that's already in the class is flagged and must be answered (add anyway or skip). This is offered both during class setup and on the class page

Tapping a child's name opens their child view. On it the teacher can:

- see which books the child has on loan now, colour-coded by age, and return any of them. Every return from the class list or child view asks for confirmation first
- see the child's borrowing history
- move the child to another class at any time. Their books on loan and borrowing history move with them, and the move is recorded in the activity log
- archive the child, but only once they've returned all their books

Staff without a class (other staff and the school admin) who open Classes are offered two choices: choose a class to view, or scan a book.

## Managing teachers

Any staff member can open Teachers. Everything on it is open to all staff except the two items marked admins only. On it they can:

- invite someone, either a teacher for a class or a staff member without a class (such as a teaching assistant). Only their email is needed, and the class is optional. Their email gets an invite link. Links last 14 days. Invites that haven't been accepted are listed on Teachers with when they expire. They can be resent with a fresh link, or cancelled after a confirm, which stops the link working
- see staff without a class in the same Teachers list, marked "No class"
- rename a class or change its teacher, from that class's page. A class can also have a second teacher for a job share. Both see the class as their own and both get the weekly reminder email
- admins only: make someone an admin, or remove admin from them, from their page, after a confirm. The last admin can't be removed
- admins only: archive a teacher, who then can't log in, or restore one. A teacher with a class can't be archived until someone takes over the class: archiving asks who the new teacher is first
- add or archive classes. Archiving a class archives its children and their loan history with it, so it always asks for confirmation first. A class can't be archived while any of its children have books out. If the class still has children, the warning says so and suggests renaming the class instead if it's just moving up a year
- open the **Archive** and restore any archived class, child or book as it was (restoring a teacher is admins only)
- open the **Activity log**: every archive and restore, with who did it and when, newest first
- open **Stats**: the share of loans returned on time, for the whole school or one class, over a chosen period, and how many teachers were active each week

**Nothing is deleted straight away.** Teachers, classes and children are archived, never removed, so they can be restored. Archived children are the one exception: they're deleted for good 30 days after they were archived, to keep children's data no longer than needed. Every archive and restore is written to the activity log, which can't be edited. Nobody can archive themselves, and the school always keeps at least one admin.

Invites and new classes save as a draft while they're typed, so nothing is lost if someone leaves the page. A class's name and teacher are changed through an Edit button that opens a small window, and save when Save is pressed.

## Schools, accounts and onboarding

This section comes from the Figma flows board.

1. A school registers on the public site. It searches England's official list of schools by name, postcode or both, then picks itself from the matches, so its address fills in. Up to five matching schools appear in a box beside the search as soon as three characters are typed, and update with every key. A Search button also gives the full list of matches. A school that isn't listed types its details in by hand. It then adds a contact name, contact email and phone, and chooses the starting email address: the contact email or a different one.
2. Library Lite approves the school by hand before it goes live. Until then, the person who registered sees a page saying the school is checked by hand and the starting email address will get a link once it's approved. If a school is turned down, Library Lite talks to them first, then emails them why, outside the app. There's no approval queue inside the app.
3. The starting email address gets a unique link, which works for 7 days. That person, the school admin, uses it to create their account, with the same password rules as teachers, then set up classes and give each one a teacher's email. Each class has its own Invite button, which emails that teacher straight away and marks the class as pending verification until they create their account. They can leave and come back to the link.
4. Each teacher gets their own invite link, creates a password and sets up their class and its children. Their setup also saves as they go. A strength meter shows how strong the password is, and they can't continue until it meets every rule: at least 10 characters, includes a number, includes a special character, and isn't a common password.

Nobody can sign up without an invite. The site has three parts: public pages (a website with Home, About, Pricing and Contact, plus register and log in), the school registration steps, and the logged-in app (Scan Book, Books, Classes, Teachers, Help).

Help in the logged-in nav opens a page of quick answers: scanning a book, what to do when a barcode won't scan or the camera is blocked, what the loan colours mean, and why a child can't borrow. It ends with a contact line for the Library Lite team (the address is still a placeholder).

Log in has a Forgot password link. Staff enter their email, get a reset link, and set a new password with the same rules as above. The reset link works once and stops working after 12 hours.

**Emails.** Designed so far: the weekly reminder, password reset, confirm new email, the email changed notice to the old address, invite, school approved and the PIN reminder. The school turned down email is sent outside the app. Pricing on the website is still to decide.

**Empty and error states.** Every list has an empty state that says what to do next; the most important is an empty library at first login, which leads straight to scanning the first book. Searches that find nothing offer to clear the search. With no connection, a banner shows on every page and scanning and saving pause until the connection is back (nothing is queued). If a save fails, what was typed stays so it can be saved again. Every old, used or cancelled link opens one shared "This link has expired" page. Log in says when the email and password don't match (never which one), or when an account is archived. Phones log out after 30 minutes without use, like shared iPads.

| State | Where | What it shows |
| --- | --- | --- |
| Empty library | Books | "Your library is empty" and a Scan your first book button |
| No children yet | A class on Classes | Add a child, or paste a list of names |
| Nothing borrowed | A child's page | Their loans and history will show here, and a Scan a book button |
| Never borrowed | A book's page | Borrowing history says "Not borrowed yet" |
| Nothing archived | Archive | An explanation of what will show there |
| No activity yet | Activity log | An explanation of what will show there |
| No lost books | Lost books report | No books written off this school year; no download |
| Not enough loans | Stats | Shown until 10 loans have come back |
| No results | Books, choosing a child | Clear search |
| No results | Find by title | Still offers adding the book without a barcode |
| Finding this book | Scan Book | Shown between a scan and its result; no answer leads to typing title and author |
| No connection | Every signed-in page | A banner; scanning and saving pause until the connection is back, nothing is queued |
| School lookup not working | Registration | Type your school's details instead |
| Didn't save | Any Edit window or form | What was typed stays so it can be saved again |
| Link expired | Any old, used or cancelled link | One shared page with Log in and Back to the website |
| Wrong email or password | Log in | Says they don't match, never which one |
| Account archived | Log in | Ask your school's admin to restore it |
| Logged out after 30 minutes | Shared iPads, phones | iPads: tap your name and enter your PIN. Phones: log in again |

## End of the school year

A child's loan history stays with them as their class moves up. At the end of the year, an admin runs **End of year** from Teachers. It moves every class up in one step:

1. **New class names.** Each class gets a suggested new name, made by adding one to the number in its name (Year 4 → Year 5). Staff check every class and can change the name, keep it, change the teacher, or mark the class as leaving. A class with no number in its name gets no suggestion and must be set by hand.
2. **Leavers.** Any books the leaving classes still have out are listed. This is the point where the school accepts that a leaver's unreturned book is gone. For each book, staff either mark it returned or **write it off**, which closes the loan, takes the book out of the library's count and adds it to the lost books report. The flow can't finish until every book is one or the other. Nothing is written off automatically.
3. **Check and confirm.** A summary of every change, then **Move everyone up** applies it all at once: classes renamed, teachers moved, books written off, and leavers archived with their history. It's recorded in the activity log.

**Lost books report.** It lists every book written off in the school year, with who had it, when, and why (not returned, lost or damaged), and can be downloaded as a spreadsheet for school records. It opens at the end of the flow and from Lost books on Teachers. If a written-off book turns up, scanning it asks whether to add it back to the library.

Afterwards staff add next year's new class from Teachers. Any part can be put right later by renaming a class or restoring leavers from the archive. A single class can still be renamed on its own page at any time.

## Information architecture

The site has 14 areas. The full map, with every screen, the overlays it opens and its states, is on the [Information Architecture V2 page in Figma](https://www.figma.com/design/ufE3h5LxKNO4XfMFR82cSt/Library-Lite?node-id=937-3440).

**Signed-in nav:** Scan Book · Books · Classes · Teachers · Help · My account · Switch user · Log Out. Teachers also links to Archive, Activity log, End of year (admins only), Lost books and Stats.

**Public nav:** Home · About · Pricing · Contact · Log in.

| Area | Who sees it | Main screens |
| --- | --- | --- |
| Log in and registration | Public | Log in, forgot password, find your school, contacts, starting email, registered |
| Invite setup | Anyone with a set-up or invite link | Admin account, school set-up, invites sent, teacher account, set up your class |
| Scan a book | Any staff | Scan, type the ISBN, add a book, choose the child, loan done, on loan, return, renew, different copy, find by title, written-off book |
| Books | Any staff | Books (search, filters, sort), book page (copies, history, lost or damaged, archive) |
| Classes | Teachers see their own class | Class (library day, loan limit, children, quick view), add or paste children, child view (loans, history, move, archive), copy check |
| Staff without a class | Staff without a class | Choose a class to view, or scan a book |
| Teachers | Any staff; some actions admins only | Teachers and pending invites, invite someone, teacher page, class pages, add class, Archive, Activity log |
| Website | Public | Home, About, Pricing, Contact |
| Emails | Sent by Library Lite | Weekly reminder, password reset, confirm new email, email changed, invite, school approved, PIN reminder |
| Help | Any staff | Quick answers and a contact line |
| End of year | Admins only (Lost books: any staff) | New class names, leavers, check and confirm, done, lost books report |
| My account | Your own account | Name, email, password, PIN |
| Shared iPad | Anyone on a shared iPad | Who's using this iPad, enter your PIN, logged out, PIN locked, PIN reminder |
| Stats | Any staff | Whole school, one class |

Every area also has the empty, error and loading states listed under Empty and error states.

## Data model

Library Lite stores its data in 14 tables. The full model, with every column, is on the [Information Architecture V2 page in Figma](https://www.figma.com/design/ufE3h5LxKNO4XfMFR82cSt/Library-Lite?node-id=822-824), with a card showing which tables each area uses. Every table is limited to one school.

| Table | What it holds |
| --- | --- |
| schools | Each school: name, address, contacts, starting email, and whether it's approved |
| gias_schools | A read-only copy of England's official list of schools, refreshed weekly |
| users | Staff: name, email, password, PIN, whether they're an admin, and when they were archived |
| invites | Invite and set-up links: who for, which class, and when they expire, were accepted or cancelled |
| password_resets | Reset links, which work once for 12 hours |
| sessions | Who is signed in on which device, ending after 30 minutes without use |
| device_users | Which staff have used each shared iPad, for Switch user |
| classes | Name, teacher, second teacher, library day and loan limit |
| children | First name and optional initial. Deleted for good 30 days after they're archived |
| titles | Each book title: barcode, title, author and category |
| copies | Each physical book, and whether it has been written off and why |
| loans | One row each time a book goes out: who loaned, returned or renewed it, and when |
| copy_checks | Questions to a teacher about whether a child still has a copy |
| activity_log | Every archive, restore, write-off and End of year. It can't be edited |

**The database enforces:**

- one open loan per copy, and the loan limit, checked as the loan is saved
- every save is all-or-nothing, and nothing is queued while offline
- nothing is assumed: when the app can't know something, a person is asked
- teachers, classes, children and books are archived rather than deleted. Archived children are the one exception, deleted after 30 days; their past loans stay without a name, so book borrow counts stay right
- End of year happens in one step, or not at all

**Worked out, not stored:** loan colours (from the class's library day, in UK time), each child's colour on the class list, scan results, Stats and whether a link still works. Working them out each time means they're never out of date.

## Out of scope for now

- Logins or views for parents or children
- Library cards for children
- Working offline (the site needs a connection)
- Looking up schools in Wales, Scotland and Northern Ireland (they can still register by typing their details in)

## Decisions

The brief's open questions, answered by Dan on Oct 13, 2026. The sections above include these answers.

| Question | Decision |
| --- | --- |
| Camera blocked, or barcode won't scan | Staff can type in the ISBN. If camera access is blocked, the app reminds them to allow it. |
| Child at their loan limit | The loan is blocked. No warning step. |
| Search the whole library | Yes. Staff can search every book and see who has each one. |
| Category when adding a book | Yes, Fiction or Non-fiction only. No sub-genres. |
| School admin's role | An extra user without a class, like a teaching assistant. Any staff member can also be made an admin. A school can have several admins and always has at least one (Oct 14). |
| Job shares | A class can have a second, optional teacher. Both see it as their own class and both get the reminder email (Oct 14). |
| My account | A My account link in the nav lets everyone change their own name, email and password. A new email only takes over once its confirm link is opened (Oct 14). |
| Moving up a year | A guided End of year flow moves every class up at once: suggested names that staff check, leavers' books returned first, then one confirm. Leavers are archived with their history (Oct 14). |
| Password rules | At least 10 characters, includes a number and a special character, and isn't a common password. |
| Finding the school at registration | Looked up in the DfE's Get Information about Schools list, England only for now, refreshed weekly. One account per school: a school that's already registered is told to ask its admin for an invite. A school that isn't listed types its details in, and Library Lite checks them by hand. |
| Children's names | First name plus an optional surname initial, in two separate fields. Surnames are never stored. |
| Adding many children | Paste a list of names, one per line, during class setup or from the class page. Each line keeps the first name and the surname's first letter. Every child is checked on one screen before saving, and duplicates are flagged and asked about (Oct 14). |
| Multiple copies of a book | No school barcode labels. Staff say when a scanned book is a different copy; it's loaned straight away and the other child's teacher confirms in an in-app pop-up. Returns of a title with several copies out always ask which child. Nothing is assumed or decided automatically (Oct 14). |
| Books with no barcode | Found and added by title. Typing a title suggests matching books in the library; picking one asks whether it's another copy. It's rare, so there's no labelling (Oct 14). |
| Removing teachers, classes and children | Never deleted: they're archived and can be restored (teachers by admins only). Every archive and restore goes in an activity log. Nobody can archive themselves or the last admin. Archived children are deleted for good after 30 days (Oct 14–15). |
| Leavers' unreturned books | Written off at End of year, one book at a time by a person, never automatically. Written-off books go in a yearly lost books report (Oct 14). |
| Lost or damaged books | Any staff member can mark a copy lost or damaged at any time from the book's page, after a confirm. It's written off with that reason and goes in the lost books report (Oct 14). |
| Editing and archiving books | Any staff member, from the book's page. Archiving is blocked while a copy is on loan, and archived books can be restored (Oct 14). |
| Invite links | Last 14 days and can be resent or cancelled from Teachers (Oct 14). |
| Inviting staff without a class | Invite asks whether they're a teacher for a class or staff without a class; only the email is required. They're listed with the teachers. The page keeps the name Teachers (Oct 14). |
| Admin rights | Only admins make or remove admins, archive or restore teachers and run End of year. Billing isn't one of them: it's handled outside the app with the person who registered the school (Oct 15). |
| School approval | The person who registered sees a "we've got your details" page until approval. A school that's turned down hears why by email after a conversation, outside the app. No in-app approval queue (Oct 15). |
| Starting email | Registration asks for a school contact email. The starting email is then chosen: the contact email or a different one. Nothing is pre-picked. The setup link works for 7 days (Oct 15). |
| Shared iPads | Log out after 30 minutes without use. Switch user: tap your name, enter a 4-digit PIN; only staff with a PIN are listed, others can get a reminder email; locks after 5 wrong tries. No lock screen hiding children's names (Oct 15). |
| Loan colours | Based on the class's library day, not a count of days: green until the next library day, orange once one is missed, red after two or more (Oct 15). |
| Deleted children's records | After 30 days the child's name is deleted. Their past loans stay without a name ("Deleted child") so each book keeps its borrow count (Oct 15). |
| Stats access | Any staff member can open Stats. On time = back by the library day, while still green (Oct 15). |
| Archiving a teacher with a class | Not allowed until someone takes over the class. Archiving asks for the new teacher, who then gets the class's reminder email (Oct 15). |
| School holidays | Loans keep counting through holidays. No term dates are stored (Oct 15). |
| Children's history | Any staff member can see any child's borrowing history (Oct 15). |
| Time zone | Days are counted in UK time (Oct 15). |
| Success measures | The share of loans returned on time, for one class or the whole school, and teachers active each week, shown on a Stats page (Oct 15). |
| Invites after setup | After Send invites, the admin lands on Teachers with each invite marked Pending (Oct 15). |
