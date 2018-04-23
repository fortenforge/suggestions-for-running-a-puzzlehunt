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

If you are not writing an entire hunt by yourself (or maybe if you are and your hunt is also really large), you'll want to closely monitor the status of all of your puzzles and make sure that they're all on track to be finalized by the time your hunt starts. If your hunt is relatively small you might be able to get by with a simple spreadsheet, but if you have 20 or more puzzles to write, we suggest you consider setting up [puzzletron](https://github.com/mysteryhunt/puzzle-editing) to organize your process. Besides checking the status of all your puzzles, one major benefit of puzzletron provides is managing your testsolving sessions (more on this below).

## Testsolving

## Solution Writing

You want to be able to release well-written solutions to all your puzzles the moment the hunt is officially over. As such, writing a solution to your puzzle is the very first step after a puzzle has been successfully testsolved. Try to make sure your solution includes data for every step of your puzzle - include all answers to intermediate steps leaving nothing implicit. Also, be mindful of the tone you strike when drafting your solution: you want to avoid being condescending or deprecating in any way.

## Factchecking

## Post-Production

Once a puzzle has been successfully testsolved and factchecked to your satisfaction, the final step is to do the work required to make it presentable to solvers, whether this means rendering it as a PDF or converting it to HTML. (Postproduction is listed last step after factchecking on puzzletron, but it might make sense for you to do factchecking after postproduction, so that you can catch errors made during the puzzle rendering process.)

The most important thing to keep in mind during post-production is to aim for a consistency of presentation among your puzzles. In the words of Dan Katz:

> This might not seem like a big deal, but it’s a bit like the brown M&M’s in the Van Halen rider… when an experienced solver sees that the constructors haven’t taken the time to give the puzzles a look that’s at least minimally consistent, it immediately makes them suspicious about whether there’s been attention to detail in other places.

If you're presenting your puzzles as HTML webpages, you should also make sure that they look ok when printed, particularly for puzzles which would benefit solving with a paper copy. Another small quality-of-life change is to make the HTML page title the puzzle name, so that solvers with multiple tabs open on your website can distinguish between different puzzles.

# Puzzle Design

## Answer Selection
To the extent possible, make your answers real English words or phrases. Well-known proper nouns or foreign phrases are usually fine, as are very long phrases, but random word mashes ("VIBRATING BANANA") are less ok, and keyboard mashes ("JDIELDNSDFJKLSD") are a no-no. Be careful when choosing thematic answers: if there are enough constraints imposed by the meta or the puzzle structure, solvers may be able to bypass large chunks of your puzzle by querying an engine for thematic answers.

## Cluephrases

Sometimes the answer you are assigned may not meet the constraints imposed by your proposed extraction. In this case, you'll want to have your extraction result in a *cluephrase*, a crossword-style clue that yields your assigned answer. For solvers, there are few worse experiences during a puzzlehunt than being stuck on a cluephrase for a puzzle. Hence, you should put a lot of thought into selecting a good cluephrase. Before you sink a lot of time and effort into creating your puzzle, run your cluephrase by an editor or another person first, to make sure that they are able to solve it. Finally: if your puzzle doesn't involve cryptic clues, your cluephrase shouldn't be a cryptic clue.

## Random Anagrams

There is a widespread puzzlehunting convention that no particular step in your puzzle should involve an unclued unscrambling of a string of letters to produce a word or phrase. (Novice puzzle authors violate this rule all the time, and it's become something of a [running joke](http://web.mit.edu/puzzle/www/2015/puzzle/a_puzzle_consisting_entirely_of_random_anagrams/) in the community).

To be clear: *clued* anagrams, where you're given some additional means of confirming that you have the correct unscramble (such as the definition-half of a cryptic clue) are perfectly reasonable. Even unclued anagrams of short words is often permissible, as long as it's not the final step in a puzzle.

## Meta Design

As a rough rule, metas should generally be solvable with 80% of the puzzles, and should not lead to backsolving more than 30% of the puzzles in a round. This should be reflected in your testsolving process: randomly omit several of the answers to your meta when you give it to testsolvers. If they get stuck and need a hint, you can give them a couple additional answers.

# Running your Hunt

## Errata

Almost inevitably, despite your meticulous testsolving and factchecking, some errors will remain in your hunt. During the hunt, you should have a way for solvers to report these errors to you (an email address that you monitor regularly tends to work best). When one of these reports comes in, your first job is to verify that the error is actually present! Issuing an errata feels bad, but issuing an incorrect errata is worse. If you believe the report is incorrect, it's best to respond with something that yields no additional information. We've found "the puzzle is correct as written" tends to work well.

If the report is correct, first acknowledge the error in your reply to the report and promise that you'll have a fix up as soon as possible. Then, correct the error and simultaneously announce and describe the correction made somewhere else on the website. A page devoted to "Errata / Updates" suffices. If the error is significant (use your discretion), you'll also want to alert solvers via some other communications pathway (usually a mass email).

LIST OF THINGS
* Testsolve, testsolve, testsolve
* Factcheck, factcheck, factcheck
* Hints
