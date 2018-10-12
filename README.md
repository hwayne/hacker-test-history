# Hacker Test History

The [Hacker Test](http://www.mit.edu/people/mjbauer/Purity/hackpure.html) was an old test of how much of a 'hacker' (as in 'nerd', not 'cracker') you are. Since it came out in 1990, almost all of the questions are obsolete. That makes it a really neat historical document of what people considered cool at the time. Let's explain all the references!

If there's something you recognize, just make a pull request with the explanation. If there's an explanation you want to improve, just make a pull request with some history and links. We're not picky.

# [The Test](http://www.mit.edu/people/mjbauer/Purity/hackpure.html)

####  0005 Have you ever patched paper tape?

Paper type, also called [punched tape](https://en.wikipedia.org/wiki/Punched_tape) or perforated tape, was an early, inexpensive storage media, consisting of a long, thin strip of paper, divided into a fine grid (typically 5 or 8 columns). Each cell of this grid corresponded to one bit of information. If the grid was punched, the corresponding bit would be 1, otherwise it would be zero (or vice-versa).

Since paper is inexpensive and malleable, and the reading mechanism was usually optic, it would be very easy to "patch" paper tape: one could either punch holes, or cover erroneously punched holes by gluing electric tape or pieces of paper on top of them. However, doing so was fairly tedious and error prone, and you had to find it easy to "read" and "write" binary. Furthermore, finding out exactly *which* bits to toggle in this manner usually meant being able to read machine code dumps of the code -- not an easy feat!

####  0011 Do you use DWIM to make life interesting?

From the Jargon File, [DWIM] stands for "Do What I Mean", and in particular a specific tool that attempted to correct typos and spelling errors. Since general-purpose AI had not been invented at the time of the Hacker Test's creation, any automatic "correction" was as likely to be harmful as productive, thus making life "interesting" if (for example) the DWIM tool decided what you *really* meant was to delete all your files.

[DWIM]: http://www.catb.org/jargon/html/D/DWIM.html

####  0013 Do you complain when a "feature" you use gets fixed?

A precursor to [XKCD 1172](https://xkcd.com/1172/).

####  0014 Do you eat slime-molds?

A reference to [NetHack](https://www.nethack.org/), one of the most popular roguelikes of all time. One item is the [fruit](https://nethackwiki.com/wiki/Slime_mold), which you could configure to be whatever food you like. If you do not configure it, the default is "slime mold"

####  0019 Can you recite Jabberwocky?

The [Jabberwocky](http://www.jabberwocky.com/carroll/jabber/jabberwocky.html) is a famous nonsense poem by Lewis Carroll. Most of the words are made up.

####  001E Do you know what ASCII stands for?

The [American Standard Code for Information Interchange][ASCII] assigns a number from 0 to 127 to alphabetic, numeric and punctuation characters widely used in the United States of America, plus a variety of mostly-obsolete control characters that represent things like paragraph breaks. First standardized in 1963, it forms the basis of nearly every modern character set, including Unicode.

[ASCII]: https://en.wikipedia.org/wiki/ASCII

####  001F ... EBCDIC?

The [Extended Binary Coded Decimal Interchange Code][EBCDIC] is another character set like ASCII, designed around the same time as ASCII by IBM for their System/360 line of mainframe computers. It is used almost nowhere else, but since IBM mainframes live forever and the software they run lives even longer, EBCDIC is still a thing.

[EBCDIC]: https://en.wikipedia.org/wiki/EBCDIC

####  0025 Do you know maxint on your system?

Although the smallest possible unit of storage is a single bit, and modern computers have gigabytes or even terabytes of memory, a computer has a much narrower range of sizes it's comfortable working with. The smallest is a byte, normally 8 bits, and the largest is typically 32 or 64 bits. To process a larger amount of memory, the computer works its way through 32 (or 64) bits at a time.

On a computer that can process at most 32 bits of data at a time, those 32 bits have 2³² possible values, which you can treat as an integer between 0 and 2³² - 1. MAXINT is a predefined name for the largest possible integer on a given system; on a 32-bit system it would be 2³² - 1, or 4,294,967,295 (about 4.3 billion).

####  0030 Do you know Dennis, Bill, or Ken?

[Dennis Ritchie][dmr] and [Ken Thompson][ken] created the Unix operating system at Bell Labs in the 1970s. After the Unix source code was made available to various universities, a student at the University of California, Berkeley named [Bill Joy][bill] helped create the BSD variant of Unix, and in particular the `vi` editor. He later went on to co-found tech giant Sun Microsystems.

[dmr]: https://en.wikipedia.org/wiki/Dennis_Ritchie
[ken]: https://en.wikipedia.org/wiki/Ken_Thompson
[bill]: https://en.wikipedia.org/wiki/Bill_Joy

####  0034 Did you ever forget to mount a scratch monkey?

A "scratch pad" is a notepad used for unimportant notes, a "scratch disk" is a storage device containing no important data; the idea is that if you're about to do something that might damage important data, you unmount the important disk and mount a scratch disk so that if something does go wrong, nothing of value is lost.

The Jargon File relates the story of a field technician who ran a diagnostic on a faulty computer without realising it was normally used to experiment on a monkey, and said monkey was still physically wired up to it, so he didn't think to mount a [scratch monkey] before starting to tinker.

[scratch monkey]: http://www.catb.org/jargon/html/S/scratch-monkey.html

####  0035 Have you ever optimized an idle loop?

An idle loop is what a computer executes when it has nothing better to do. Optimizing an idle loop cannot make anything go faster, since if there were anything to do, the computer would be doing it instead of idling.

That said, although an idle loop cannot run *faster*, it can run more *efficiently*. In this modern age of battery-powered computers, when a computer enters an idle loop it will often slow down or even turn parts of itself off to conserve power. In that sense, it does make sense to optimize an idle loop: if you can get the computer to slow down more or turn off more things, that will extend the battery life.

####  0036 Did you ever optimize a bubble sort?

Sorting a list of items is a well-studied problem, and there are many sorting algorithms available with various trade-offs. Bubble Sort is one of the uniformly worst-performing sorting algorithms, and any effort put towards optimizing it would be much better spent replacing it entirely with a smarter algorithm like Quick Sort.

####  003E Have you made a disk drive "walk"?

Once upon a time, a "disk drive" was a unit about the size of a washing-machine. Like a washing machine, it involved spinning a heavy metal core at high speeds, and (like a washing machine) any imbalance of the payload could cause the unit to shake from side to side, and (under the right circumstances) rattle its way across the floor.

The Jargon File [also mentions](http://www.catb.org/jargon/html/W/walking-drives.html) that certain patterns of disk accesses could cause a drive to walk.

####  003F Can you build a puffer train? (0040: ...Do you know what it is?)

A [puffer train](https://en.wikipedia.org/wiki/Puffer_train) is a particular type pattern in a finite automaton (like ]Conway's Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life)) which spontaneously moves across the cell space, leaving smaller structures (akin to debris) behind.

Cellular automata are still a very popular pastime among hackers. Puffer trains, though, have particular cultural significance: the first known puffer train in Conway's Game of Life was discovered by [Bill Gosper](https://en.wikipedia.org/wiki/Bill_Gosper).

#### 0041 Can you play music on your line printer? (0042 ... Your disk drive? 0043 ... Your tape drive?)

The music in this case is not a metaphor: it's literal music. Devices like dot printers or disk drives used stepper motors for accurate positioning of their print heads or, respectively, disk heads. By carefully manipulating the speed and position of these motors, one could modulate their vibration so as to, quite literally, [make them sing](https://www.youtube.com/watch?v=u8I6qt_Z0Cg).

Doing so required not only a pretty good understanding of electronics, programming and music, but also quite a fair deal of creativity. Printer drivers, naturally, do not natively support making printers sing, and indeed some of the sounds occur when the hardware is pushed beyond its safe (or standard) operational parameters. Consequently, creating these sounds sometimes required careful programming and a lot of trial-and-error.

#### 006F Ever drop a card deck? (0070 ... Did you successfully put it back together? 0071 ... Without looking?)

The card deck here does not refer to playing cards, but to [punched cards](https://en.wikipedia.org/wiki/Punched_card). Punched cards were small pieces of stiff paper or cardboard, which could be used as storage media, encoding ones and zeroes through the presence (or absence) of holes at pre-determined grid locations.

The small information density (depending on format, a punched card could represent anywhere from a few characters to a few tens of bytes) meant that a single program needed tens, hundreds, or even thousands of punched cards, which would often be punched somewhere other than in the machine room, where they would be fed to the computer.

Naturally, the worst thing that could happen when carrying a deck of cards across the campus was to drop it. Putting them back together in their correct order was not an easy task when you had hundreds of cards. Putting them back together without looking, just by feeling the hole pattern with your fingers -- thus reading it much like a computer would have -- was an even more impressive feat.

#### 00B0 Do you have a copy of Dec Wars??

[DEC Wars](https://www.netfunny.com/rhf/jokes/87/14917.9.html) was a [DEC](https://en.wikipedia.org/wiki/Digital_Equipment_Corporation)-themed parody of Star Wars. It was posted on USENET, in various groups, in 1983, and was written by Alan Hastings, Steve Tarr, Dave Borman and Barak Pearlmutter.

#### 00B6 Do you have your own fortune-cookie file?

[fortune](https://en.wikipedia.org/wiki/Fortune_(Unix)) is a famous Unix passtime. When invoked, it would display various funny quotes from one of several files that shipped with it or were circulated in the hacker community. Particularly dedicated hackers would, of course, have such a file of their own.

#### 00C5 Do you have a programmable calculator?

Programmable calculators like the [TI-59](https://en.wikipedia.org/wiki/TI-59_/_TI-58) were some of the earliest personal programmable devices. For many hackers, this would have been the first exposure to programming, and an occasional fun pastime.

Some of them, like the [HP-16C](https://en.wikipedia.org/wiki/HP-16C) were primarily aimed at programmers, but many hackers came from other fields, such as Physics or various other branches of engineering, where handheld scientific calculators are nearly impossible to live without.

#### 00C6 ... Is it RPN?

Notably, many of these scientific calculators used [RPN notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation); in particular, HP's line of scientific calculators, which were held in highest regard, used RPN from the very beginning, starting with the [HP-35](https://en.wikipedia.org/wiki/HP-35), the first scientific handheld calculator.

RPN did not become a tradition by accident or taste alone; the RPN model had a number of advantages relevant to early hardware, and implementing such a scheme in software was at the very least cleaner, if not easier. Programming languages like Lisp, Forth and PostScript used it extensively, too.
