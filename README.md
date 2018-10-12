# Hacker Test History

The [Hacker Test](http://www.mit.edu/people/mjbauer/Purity/hackpure.html) was an old test of how much of a 'hacker' (as in 'nerd', not 'cracker') you are. Since it came out in 1990, almost all of the questions are obsolete. That makes it a really neat historical document of what people considered cool at the time. Let's explain all the references!

If there's something you recognize, just make a pull request with the explanation. If there's an explanation you want to improve, just make a pull request with some history and links. We're not picky.

# [The Test](http://www.mit.edu/people/mjbauer/Purity/hackpure.html)

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
