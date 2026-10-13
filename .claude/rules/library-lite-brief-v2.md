# Library Lite Brief V2

Rewritten Oct 13, 2026 from Dan's notes, his Q&A answers and the Figma flows board. Open questions answered the same day.
Source of truth: the "Library Lite Brief V2" Claude Doc (https://claude.ai/code/artifact/3435a4e0-fbde-453f-bf1a-b5bfe4725009). This file is a markdown export of it; update it when the doc changes.

## What Library Lite is

In UK primary schools, lending library books to children is a rushed job squeezed into a busy day. Library Lite is a website that makes that job fast for teachers and other school staff.

Its heart is one action: scan a book's barcode on an iPad. The app works out what state the book is in and offers the next step: add it to the library, loan it to a child, take it back, or renew it. Around that, staff can see who has what, which loans are overdue, and what each child has borrowed in the past.

## Who uses it

It's for school staff only for now. Children and parents don't log in or see anything.

- **School admin:** the account that registered and pays for the school. Sets up the school's classes and invites teachers. After that they're an extra user without a class, like a teaching assistant, who can also manage teachers and classes.
- **Class teachers:** each is linked to a class. They manage their class's children, library day and loan limit, and get the weekly reminder email. They can also manage teachers and classes.
- **Other staff, such as teaching assistants:** these users don't need a class of their own. The school admin is one of them. They can also manage teachers and classes.

Anyone with a login at the school can scan books and loan them to any child in the school.

## The core flow: scan a book

One Scan button covers adding, loaning, returning and renewing. The app checks the book's barcode against the school's library and shows only the options that fit.

Scan flow (1 scan, 3 outcomes):

- **Not in the library** → add it → either just add it to the library, or go on to loan it.
- **In the library, available** → loan it → choose child (a teacher's own class is chosen for them, with an option to change class; staff without a class choose the class first).
- **In the library, on loan** → return it (or renew it).

If a scan doesn't find the book, staff are asked to scan it once more. If the second scan still isn't recognised or found, the book is saved straight away with its barcode. When staff add the title and author, they're attached to that barcode, so the book is recognised the next time it's scanned. If they cancel instead, the saved book and its barcode are deleted. A new book can be loaned straight away or just added to the library.

When loaning a book, a teacher's own class is chosen for them, so they go straight to choosing the child, with an option to change class. Staff without a class choose the class first.

If a barcode won't scan, staff can type in the ISBN instead. If camera access is blocked on the iPad, the app reminds them to allow it when they try to scan.

When a book is added, staff choose Fiction or Non-fiction. There are no sub-genres.

## Loan rules

- **Loan limit:** each child can have 2 books out at once by default. A class's teacher can change that limit at any time. A child at their limit can't borrow any more: the loan is blocked, with no warning step. Staff can tap that child to see which books they have out.
- **Colour coding:** every loan shows its age by colour. It's green for days 1 to 7, orange for days 8 to 14 and red from day 15. A loan counts as overdue once it's past a week.
- **Renewing:** this tells the app the teacher has seen the book and is happy for the child to keep it. The loan goes back to green and the week starts again from that day.
- **Weekly reminder:** each teacher gets an email the day before their class's library day. It lists the books their class has on loan, with the same colour coding as the website.
- **Collection:** books belong to the whole school library, not to a class, so any child can borrow any book.

## Viewing books

Books lets any staff member search the whole school library and see who has each book.

## Managing a class

Each teacher has a Classes page that only shows their own class. On it they can:

- see the class list, with each child's name showing the colour of their oldest loan, and open a quick view of a child's books to return them
- set the class's weekly library day, which most UK primary classes have on their timetable
- change the class's loan limit (both settings change through an Edit button and a dropdown)
- add the children in their class, as a first name plus a surname initial only when two children share a first name. Surnames are never stored

Tapping a child's name opens their child view. On it the teacher can:

- see which books the child has on loan now, colour-coded by age, and return any of them. Every return from the class list or child view asks for confirmation first
- see the child's borrowing history
- remove the child, but only once they've returned all their books

Staff without a class (other staff and the school admin) who open Classes are offered two choices: choose a class to view, or scan a book.

## Managing teachers

Any staff member can open Teachers. On it they can:

- invite a new teacher for a class, whose email gets an invite link
- rename a class or change its teacher, from that class's page
- remove a teacher
- add or remove classes. Removing a class also removes its children and their loan history, so it always asks for confirmation first. A class can't be removed while any of its children have books out. If the class still has children, the warning says so and suggests renaming the class instead if it's just moving up a year

Invites and new classes save as a draft while they're typed, so nothing is lost if someone leaves the page. A class's name and teacher are changed through an Edit button that opens a small window, and save when Save is pressed.

## Schools, accounts and onboarding

This section comes from the Figma flows board.

1. A school registers on the public site. It searches England's official list of schools by name, postcode or both, then picks itself from the matches, so its address fills in. A school that isn't listed types its details in by hand. It then adds contacts and a starting email address.
2. Library Lite approves the school by hand before it goes live.
3. The starting email address gets a unique link. That person, the school admin, uses it to create their account, with the same password rules as teachers, then set up classes and give each one a teacher's email. This setup saves as they go, class by class, so they can leave and come back to the link. Invites are only emailed when they press Send invites.
4. Each teacher gets their own invite link, creates a password and sets up their class and its children. Their setup also saves as they go. A strength meter shows how strong the password is, and they can't continue until it meets every rule: at least 10 characters, includes a number, includes a special character, and isn't a common password.

Nobody can sign up without an invite. The site has three parts: public pages (a website with Home, About, Pricing and Contact, plus register and log in), the school registration steps, and the logged-in app (Scan Book, Books, Classes, Teachers, Help).

Help in the logged-in nav opens a page of quick answers: scanning a book, what to do when a barcode won't scan or the camera is blocked, what the loan colours mean, and why a child can't borrow. It ends with a contact line for the Library Lite team (the address is still a placeholder).

Log in has a Forgot password link. Staff enter their email, get a reset link, and set a new password with the same rules as above. Pricing on the website is still to decide.

## End of the school year

A child's loan history stays until they leave the school. Classes move on by renaming them on the class's page in Teachers: for example, Year 3 becomes Year 4, and its children and their history stay.

Leavers must return all their books before they're removed from the school.

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
| School admin's role | An extra user without a class, like a teaching assistant. |
| Moving up a year | Loan history stays until a child leaves. Classes move on by renaming them. Leavers return their books before they're removed (see End of the school year). |
| Password rules | At least 10 characters, includes a number and a special character, and isn't a common password. |
| Finding the school at registration | Looked up in the DfE's Get Information about Schools list, England only for now, refreshed weekly. One account per school: a school that's already registered is told to ask its admin for an invite. A school that isn't listed types its details in, and Library Lite checks them by hand. |
| Children's names | First name plus an optional surname initial, in two separate fields. Surnames are never stored. |
