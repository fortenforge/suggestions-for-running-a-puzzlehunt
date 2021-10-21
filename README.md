# Introduction

This document describes some of the design decisions and technical details involved in running a puzzlehunt. It attempts to summarize some opinions held by the puzzlehunting community and list some specific pitfalls to avoid when designing puzzles. Comments or suggestions? Pull requests welcome!

This project was inspired by PPP's guide "[Suggestions for Running a CTF](https://github.com/pwning/docs/blob/master/suggestions-for-running-a-ctf.markdown)."

# General Design

It's a good idea to play plenty of puzzlehunts so that you can know your target audience and be familiar with some of the decisions you will have to make. Remember that preparing and running a puzzlehunt always takes far more time and effort than expected, so make sure to budget plenty of time to work with :-).

## Timing

Use the [Puzzle Hunt Calendar](http://puzzlehuntcalendar.com/) to avoid scheduling conflicts. You can email [Dan Egnor](mailto:egnor@ofb.net) to include your event on the calendar. Continuously-run events are best scheduled to run through the weekend so that people don't have to skip work to participate.

## Scoring

Obviously whatever scoring system you use should be fair to all teams. Perhaps less obviously, your scoring system should incentivize teams to actually submit answers to solved puzzles. If your scoring system gives additional benefits to teams currently performing poorly, a strategic team may be incentivized to withhold answers to solved puzzles to acquire these benefits.

You'll also want to give some thought into how to break ties. This is easy in a Mystery Hunt-style event, where teams are ranked by the first to finish the final metameta. If you're running an Australian-style hunt, breaking ties using average solve time or (to a lesser extent) last-solve time, may give an advantage to solvers in optimal time zones.

# Writing a Hunt

In broad strokes here is how to write a puzzlehunt: First choose a theme and metameta that fits the theme, then write your metas, and then write your individual puzzles. Remember to testsolve and thoroughly factcheck your metameta and metas before you start assigning out answers for the puzzles or metas that feed into them. If you discover an error with a meta or metameta, you may have to rewrite all the puzzles under it.

## Managing Puzzle Writing

If you are not writing an entire hunt by yourself (or maybe if you are and your hunt is also really large), you'll want to closely monitor the status of all of your puzzles and make sure that they're all on track to be finalized by the time your hunt starts. If your hunt is relatively small you might be able to get by with a simple spreadsheet, but if you have 20 or more puzzles to write, we suggest you consider setting up [Puzzlord](https://github.com/galacticpuzzlehunt/puzzlord) to organize your process. Besides checking the status of all your puzzles, one major benefit Puzzlord provides is managing your testsolving sessions (more on this below).

Puzzlord is a redesigned version of [Puzzletron](https://github.com/mysteryhunt/puzzle-editing), the software that Mystery Hunt teams historically used to organize their puzzle-writing. Puzzlord is a Django app (Puzzletron uses PHP), and has a streamlined permission system and more modern UI. More information about Puzzlord's design can be found in [this post](https://blog.vero.site/post/2021-hunt).

## Testsolving

Testsolving is the process of having unspoiled solvers try out your puzzle. **Testsolving is the most important step in the puzzle writing process.** Even very experienced puzzle constructors routinely write puzzles which are too difficult to be solved.

Testsolving not only allows other people to give you valuable feedback, but also proves that your puzzle is actually solvable. Writing teams for the MIT Mystery Hunt usually require that all puzzles that end up in the hunt receive two successful, independent, unspoiled testsolves. Depending on how many people you have available for testsolving, this might be a high threshold to match, but you should be very wary of including a puzzle in your hunt which has received no successful testsolves.

If you have a lot of puzzles, puzzle authors, and testsolvers, it can be hard to manage the testsolving process. One of Puzzlord's most useful features is that it allows testsolvers to independently find a puzzle that they are unspoiled on and testsolve it. It also forces testsolvers to writeup a report of their efforts which will get relayed back to the author and editor.

It can be very hard to resist the temptation to interfere in an ongoing testsolving session for a puzzle that you wrote. Nevertheless, it's important to not intervene in any way to replicate the conditions that real solvers will be operating under in your hunt. If you must give a hint, try to emulate whatever hint-granting process you've agreed upon for your hunt (i.e. if you plan to have Y/N hints, allow testsolvers to ask you a Y/N question).

## Solution Writing

You want to be able to release well-written solutions to all your puzzles the moment the hunt is officially over. As such, writing a solution to your puzzle is the very first step after a puzzle has been successfully testsolved.

Solutions are primarily aimed at people who did not solve a puzzle, and as such there are several important considerations when writing them. Solutions should help someone understand the path to solving the puzzle, without making them feel bad about not solving it. Be mindful of the tone you strike when drafting your solution: we want to avoid being condescending or deprecating in any way.

Start by considering the path that a solver will take when solving your puzzle. Solutions that are presented in the order of solving accomplish two things:

1. They read more sensibly to someone who has worked on the puzzle but not solved it.
2. They can serve as a poor man’s hint source - read the solution until you get to the step you’re stuck on, and then go back to the puzzle. This isn’t a need, but it is nice to have.

For example, if solvers start by answering clues, you should list the answers to the clues. If solvers start by filling in a crossword grid, include an [image of the filled-in grid](https://2019.galacticpuzzlehunt.com/solution/a-crossword.html). If solvers start by identifying images, include the [images and their IDs](https://2019.galacticpuzzlehunt.com/solution/cross-lines.html).

For any step that includes an “aha” moment, it’s nice to include some sense of how the solvers might get that “aha”. See [this solution](https://2019.galacticpuzzlehunt.com/solution/observatory.html) for some good examples, e.g.

> From the flavortext ("year after year"), or by recalling the theming of last year’s hunt, we notice that the star field background seems reminiscent of last year's background.

You don’t want solvers to see a solution and think “what kind of sick person would make me try to make that connection?”.

Make sure your solution includes data for every step of your puzzle—include all answers to intermediate steps leaving nothing implicit. Feel free to include an [appendix](https://2019.galacticpuzzlehunt.com/solution/ministry-of-word-searches.html) if there is too much data and a step feels like it interrupts the flow of a solution. It’s also okay to have an overview of the solution first then the details afterwards, especially for long puzzles.

Keep in mind that when your puzzle is postprodded (see the next section), the solution will probably be converted to HTML. However, most people find it easier to iterate on solutions in a Google Doc. So don’t spend a lot of time formatting your Google Doc tables when they’re going to be short-lived anyway.

Many hunts conform to using first-person plural when referring to solvers (e.g. “we first notice that”). References to the puzzle author (yourself!) should generally be confined to a section at the end entitled “Author’s Notes” and written in first person.

Some advice specific to various puzzle types:
* **Logic Puzzles:** If your puzzle involves a logic puzzle, your solution should include a full logical reasoning path from start to finish. If writing out the full logical path is too long, you can consider [recording a video](https://perpendicular.institute/puzzle/the-greatest-jigsaw/solution/) instead.
* **Crossword Puzzles:** For straight clues, a table listing clues and their answers is generally sufficient (perhaps with a few links for more obscure or indirect answers).
* **Cryptic clues and other wordplay:** the clues should be deconstructed to explain the wordplays. Use [this guide](https://docs.google.com/document/d/1WecRZDhDC2x0iepjP3sjcccYWSc4kBJrjr2egvIPAMI/edit) as a reference.


## Post-Production

Once a puzzle has been successfully testsolved to your satisfaction, the next step is to do the work required to make it presentable to solvers, whether this means rendering it as a PDF or converting it to HTML. Postproduction is listed as step after factchecking on puzzletron, but it might make sense for you to do factchecking after postproduction, so that you can catch errors made during the puzzle rendering process.

The most important thing to keep in mind during post-production is to aim for a consistency of presentation among your puzzles. In the words of Dan Katz:

> This might not seem like a big deal, but it’s a bit like the brown M&M’s in the Van Halen rider… when an experienced solver sees that the constructors haven’t taken the time to give the puzzles a look that’s at least minimally consistent, it immediately makes them suspicious about whether there’s been attention to detail in other places.

If you're presenting your puzzles as HTML webpages, you should also make sure that they look good when printed, particularly for puzzles which would benefit solving with a paper copy. Another small quality-of-life change is to make the HTML page title the puzzle name, so that solvers with multiple tabs open on your website can distinguish between different puzzles.

Oftentimes you'll want to include a data table in your puzzle's solution. These can be laborious to write in HTML by hand, so you may find the [Table HTMLifier 3000](https://docs.google.com/spreadsheets/d/1eYyLOHWZfh574DPlfQWsWKl-xSlKo2T1DHuuHDf6BNE/edit#gid=0) a useful resource for converting a google sheets grid into an HTML table.

If your puzzle is dynamic, you'll want to make sure that solvers can't circumvent steps by inspecting the source code on your website. Consider passing your scripts through a [JS Obfuscator](https://obfuscator.io/), including red herrings for source code spelunkers, or simply explicitly asking solvers to not look at the source code on the puzzle itself.

## Factchecking

This process is designed to suss out any errors, trivial or puzzle-breaking, that may exist that neither you nor the testsolvers managed to catch. (These may include errors that were introduced between when the puzzle was written and when the hunt is slated to run, due to the state of the world changing and clues in your puzzle becoming inaccurate!) Fact-checking should be done by volunteers, not the puzzle authors themselves. It is the factchecker's responsibility to question every assumption and verify every step. Fact-checkers must check both the puzzle and the provided solution and make sure they are 100% consistent.

# Puzzle Design

Other resources on puzzle design: [dwilson's puzzlewriting page](http://web.mit.edu/dwilson/www/puzzles/puzzlewriting.html) and Foggy Brume's puzzling standards: [part 1](https://foggyb.livejournal.com/42978.html), [part 2](https://foggyb.livejournal.com/43107.html), and [part 3](https://foggyb.livejournal.com/43360.html).

## Answer Selection
To the extent possible, make your answers real English words or phrases. Well-known proper nouns or foreign phrases are usually fine, as are very long phrases, but random word mashes ("VIBRATING BANANA") are less ok, and keyboard mashes ("JDIELDNSDFJKLSD") are a no-no. Be careful when choosing thematic answers: if there are enough constraints imposed by the meta or the puzzle structure, solvers may be able to bypass large chunks of your puzzle by querying an engine for thematic answers.

## Cluephrases

Sometimes the answer you are assigned may not meet the constraints imposed by your proposed extraction. In this case, you'll want to have your extraction result in a *cluephrase*, a crossword-style clue that yields your assigned answer. For solvers, there are few worse experiences during a puzzlehunt than being stuck on a cluephrase for a puzzle. Hence, you should put a lot of thought into selecting a good cluephrase. Before you sink a lot of time and effort into creating your puzzle, run your cluephrase by an editor or another person first, to make sure that they are able to solve it. Also: if your puzzle doesn't involve cryptic clues, your cluephrase shouldn't be a cryptic clue.

If your chosen cluephrase proves too hard to parse during testsolving, consider providing an enumeration for the phrase on the puzzle itself. For example, see the blanks at the bottom of [this puzzle](https://2018.galacticpuzzlehunt.com/puzzle/exceptional-expedition.html).

## Random Anagrams

There is a widespread puzzlehunting convention that no particular step in your puzzle should involve an unclued unscrambling of a string of letters to produce a word or phrase. (Novice puzzle authors violate this rule all the time, and it's become something of a [running joke](http://web.mit.edu/puzzle/www/2015/puzzle/a_puzzle_consisting_entirely_of_random_anagrams/) in the community).

To be clear: *clued* anagrams, where you're given some additional means of confirming that you have the correct unscramble (such as the definition-half of a cryptic clue), are perfectly reasonable. Even unclued anagrams of short words is often permissible, as long as it's not the final step in a puzzle.

## Meta Design

As a rough rule, metas should generally be solvable with 80% of the puzzles, and should not lead to backsolving more than 30% of the puzzles in a round. This should be reflected in your testsolving process: randomly omit several of the answers to your meta when you give it to testsolvers. If they get stuck and need a hint, you can give them a couple additional answers.

# Running your Hunt

## Errata

Almost inevitably, despite your meticulous testsolving and factchecking, some errors will remain in your hunt. During the hunt, you should have a way for solvers to report these errors to you (an email address that you monitor regularly tends to work best). When one of these reports comes in, your first job is to verify that the error is actually present! Issuing an erratum feels bad, but issuing an incorrect erratum is worse. If you believe the report is incorrect, it's best to respond with something that yields no additional information. We've found "the puzzle is correct as written" tends to work well.

If the report is correct, first acknowledge the error in your reply to the report and promise that you'll have a fix up as soon as possible. Then, correct the error and simultaneously announce and describe the correction made somewhere else on the website. A page devoted to "Errata / Updates" suffices. If the error is significant (use your discretion), you'll also want to alert solvers via some other communications pathway (usually a mass email).

## Answer Checking

Strip non-alphabetic characters from your answers and convert them to uppercase before checking them.

Some hunts accept multiple different answers for a puzzle, but provide the solver with a "canonical answer" to use for the meta when the solver submits one of the other answers. This is generally viewed as inelegant / bad form by the puzzlehunting community, but does have the advantage of tolerating ambiguous clue phrases. Some other hunts have answer checkers that respond to particular incorrect answers with messages, from mere confirmational messages like "Keep going!" to explicit instructions on what the next step is, which may be useful especially for hunts for inexperienced puzzlers but is also considered inelegant by many. The best solution is to ensure that your puzzle has only one unique answer; sometimes the right way to do this is to provide an explicit answer enumeration or sequence of blanks at the end of the puzzle.

## Hints

There's a wide disparity in skill level of puzzlehunting teams. It's likely that some teams participating in your hunt won't be able to complete it without relying on hints. There are several different ways to provide hints. Probably the easiest way operationally are "canned (pre-written) hints". One problem with canned hints is that the hint will often help with a part of the puzzle that a team has already figured out. It might be useful to generate multiple canned hints per puzzle and annotate them with the rough stage of the puzzle it corresponds to.

If you're feeling ambitious, you can offer some form of dynamic hinting, where you allow teams to receive a personalized hint based on their current progress on a puzzle. We've found it helpful to give teams an empty textbox which they can use to ask for a nudge, confirm data, ask a specific question, or simply link a spreadsheet with their current work.

One system popularized by the 2015 MIT Mystery Hunt is Y/N hinting, in which teams get to ask any Yes / No question about the puzzle that they would like. This ensures that every team with the hint receives exactly 1 bit of information from it, while allowing teams stuck on different parts of the puzzle to receive different pieces of information. Some people also find crafting a good Y/N question to ask on a puzzle to be a fun exercise, and something of a puzzle in and of itself. If you do give out Y/N questions, don't be too stingy with them! 1 Y/N question tends to not help very much, but a series of carefully targeted Y/N questions can often get teams unstuck, without ever feeling like you're spoiling major parts of the puzzle for them.

Y/N hints have fallen out of favor since 2015, largely because the teams that make use of them the best tend to be the ones who are already doing well on the hunt in the first place. Inevitably, there will be teams that will need a specific nudge forward, and you should have some provision of your hint system that allows them to get help.



# Tech

*See also: [A Puzzlehunt Tech Checklist](https://www.alexirpan.com/2020/03/16/puzzlehunt-tech.html)*.

## Hosting

You have a number of options for hosting your puzzlehunt depending on your level of technical savvy. On one end, it's perfectly reasonable to release your hunt as a pdf and have people email you guesses to check. This doesn't scale well to large numbers of teams, but at least has the benefit of simplicity.

If you're comfortable building a static website, you can host your hunt website using [Github Pages](https://pages.github.com/) or some equivalent service. This wouldn't let you have any unlocking logic or rate limit answer submissions, but it does add some level of polish. You can use [puzzlehunt.net](https://www.puzzlehunt.net)'s [Client-Side Answer Checker](https://www.puzzlehunt.net/checker) (or something equivalent) to allow teams to check their own answers, and just have teams email you for the answer to the final puzzle.

However, if you want team accounts, custom unlocking, or a live leaderboard, you probably need to build and host a dynamic website. [gph-site](https://github.com/galacticpuzzlehunt/gph-site) and [puzzlehunt_server](https://github.com/dlareau/puzzlehunt_server) are two open-source applications that allow you to run a custom puzzlehunt. Both are written in Django and both have been used in multiple online hunts.

One route a handful of puzzlehunts have taken is to host their hunt in a [Discord](https://discord.com/) server. You can use roles to give each team their own personal channel and create a Discord bot that will control answer submissions and puzzle unlocks. If you comfortable with Discord and bot programming, and you have fewer than ~100 teams, this could be a reasonable solution.

## Email

Email is a surprisingly tricky aspect of puzzlehunts to get right. It's useful to distinguish between two different use cases. Emails to **everyone** and emails to **a single team**.

Counterintuitively, emailing each member of a certain team may be the easier of the two. [gph-site](https://github.com/galacticpuzzlehunt/gph-site) and [puzzlehunt_server](https://github.com/dlareau/puzzlehunt_server) uses Django's built-in email functionality, and it's relatively easy and cheap to hook it up to a transactional email service like [Mailgun](https://www.mailgun.com/) and configure your website to send an email whenever a team registers or solves a metapuzzle.

Emailing all the participants at once (say, if you want to announce an erratum or declare a winner) is trickier. If you try to use a service like Mailgun, you'll find that many clients like Gmail will reject a large fraction of the emails you send as a spam-prevention measure. Even sending the emails in batches will still cause you trouble. Instead, you're better off using a dedicated email marketing service like [Mailchimp](https://mailchimp.com/) or [Sendgrid](https://sendgrid.com/). These are both pretty pricey (~$30 a month), but you get what you pay for.

If you're using an automated email system like Mailchimp, make sure you set the reply-to address to an address you can receive emails to (like a Gmail account). If you're sending mass emails by hand, make sure you BCC participants' emails.
