# Hacker Test History

The [Hacker Test](http://www.mit.edu/people/mjbauer/Purity/hackpure.html) was an old test of how much of a 'hacker' (as in 'nerd', not 'cracker') you are. Since it came out in 1990, almost all of the questions are obsolete. That makes it a really neat historical document of what people considered cool at the time. Let's explain all the references!

If there's something you recognize, just make a pull request with the explanation. If there's an explanation you want to improve, just make a pull request with some history and links. We're not picky.

# [The Test](http://www.mit.edu/people/mjbauer/Purity/hackpure.html)

####  0000 Have you ever used a computer?

####  0001 ... for more than 4 hours continuously?

####  0002 ... more than 8 hours?

####  0003 ... more than 16 hours?

####  0004 ... more than 32 hours?

####  0005 Have you ever patched paper tape?

Paper type, also called [punched tape](https://en.wikipedia.org/wiki/Punched_tape) or perforated tape, was an early, inexpensive storage media, consisting of a long, thin strip of paper, divided into a fine grid (typically 5 or 8 columns). Each cell of this grid corresponded to one bit of information. If the grid was punched, the corresponding bit would be 1, otherwise it would be zero (or vice-versa).

Since paper is inexpensive and malleable, and the reading mechanism was usually optic, it would be very easy to "patch" paper tape: one could either punch holes, or cover erroneously punched holes by gluing electric tape or pieces of paper on top of them. However, doing so was fairly tedious and error prone, and you had to find it easy to "read" and "write" binary. Furthermore, finding out exactly *which* bits to toggle in this manner usually meant being able to read machine code dumps of the code -- not an easy feat!


####  0006 Have you ever missed a class while programming?

####  0007 ... Missed an examination?

####  0008 ... Missed a wedding?

####  0009 ... Missed your own wedding?

####  000A Have you ever programmed while intoxicated?

####  000B ... Did it make sense the next day?

####  000C Have you ever written a flight simulator?

####  000D Have you ever voided the warranty on your equipment?

####  000E Ever change the value of 4?  000F ... Unintentionally?  0010 ... In a language other than Fortran?

This question refers to a famous, occasionally abused (but often unintentionally hit) [pitfall in Fortran](https://www.ibiblio.org/pub/languages/fortran/ch1-8.html#01).

Fortran II, introduced in 1958, supported user-written subroutines and functions, but all parameters were passed by reference, including values not bound to any variable (or constant) name. In other words, a function call like this:

    READ INPUT TAPE 5, 501, IA, IB, IC
    CALL MYFUNC(IA, IB, IC, 4)

would result in code that stored the 4 at some memory location, and then passed its location to `MYFUNC`, along with references to IA, IB, and IC.

MYFUNC therefore operated not on "dummy" values on the stack, as in C, but on the original values of its parameters, and any change, to any parameters, even those passed as literal values, would be reflected in the original value.

Consequently, a bug in functions that used some of their parameters as output parameters could result in the wrong value being updated.

Two things made matters worse though.

First, many Fortran compilers ran on systems without a MMU and virtual memory support. On these systems, not only would literal values be modified, but *constants* could be modified as well.

Second, most Fortran compilers would "pool and reuse" constants -- that is, store a particular, often-used value in a single memory location, and pass that wherever it was required. Thus, if MYFUNC above changed a pooled instance of 4 to 5, all other calls that passed a reference to that memory location (and therefore expected a 4) would get 5 instead.

While this was definitely a source of unpleasant bugs, it could also serve as a base for some clever optimizations (or obfuscation). Particularly creative programmers would have adapted this mechanisms in languages other than Fortran, probably much to the frustration of everyone else.


####  0011 Do you use DWIM to make life interesting?

From the Jargon File, [DWIM] stands for "Do What I Mean", and in particular a specific tool that attempted to correct typos and spelling errors. Since general-purpose AI had not been invented at the time of the Hacker Test's creation, any automatic "correction" was as likely to be harmful as productive, thus making life "interesting" if (for example) the DWIM tool decided what you *really* meant was to delete all your files.

[DWIM]: http://www.catb.org/jargon/html/D/DWIM.html

####  0012 Have you named a computer?

####  0013 Do you complain when a "feature" you use gets fixed?

A precursor to [XKCD 1172](https://xkcd.com/1172/).

####  0014 Do you eat slime-molds?

A reference to [NetHack](https://www.nethack.org/), one of the most popular roguelikes of all time. One item is the [fruit](https://nethackwiki.com/wiki/Slime_mold), which you could configure to be whatever food you like. If you do not configure it, the default is "slime mold".

####  0015 Do you know how many days old you are?

####  0016 Have you ever wanted to download pizza?

####  0017 Have you ever invented a computer joke?

####  0018 ... Did someone not 'get' it?

####  0019 Can you recite Jabberwocky?  001A ... Backwards?

The [Jabberwocky](http://www.jabberwocky.com/carroll/jabber/jabberwocky.html) is a famous nonsense poem by Lewis Carroll. Most of the words are made up.


####  001B Have you seen "Donald Duck in Mathemagic Land"?

####  001C Have you seen "Tron"?

####  001D Have you seen "Wargames"?

####  001E Do you know what ASCII stands for?

The [American Standard Code for Information Interchange][ASCII] assigns a number from 0 to 127 to alphabetic, numeric and punctuation characters widely used in the United States of America, plus a variety of mostly-obsolete control characters that represent things like paragraph breaks. First standardized in 1963, it forms the basis of nearly every modern character set, including Unicode.

[ASCII]: https://en.wikipedia.org/wiki/ASCII

####  001F ... EBCDIC?

The [Extended Binary Coded Decimal Interchange Code][EBCDIC] is another character set like ASCII, designed around the same time as ASCII by IBM for their System/360 line of mainframe computers. It is used almost nowhere else, but since IBM mainframes live forever and the software they run lives even longer, EBCDIC is still a thing.

[EBCDIC]: https://en.wikipedia.org/wiki/EBCDIC

####  0020 Can you read and write ASCII in hex or octal?

####  0021 Do you know the names of all the ASCII control codes?

####  0022 Can you read and write EBCDIC in hex?

####  0023 Can you convert from EBCDIC to ASCII and vice versa?

####  0024 Do you know what characters are the same in both ASCII and EBCDIC?

####  0025 Do you know maxint on your system?

Although the smallest possible unit of storage is a single bit, and modern computers have gigabytes or even terabytes of memory, a computer has a much narrower range of sizes it's comfortable working with. The smallest is a byte, normally 8 bits, and the largest is typically 32 or 64 bits. To process a larger amount of memory, the computer works its way through 32 (or 64) bits at a time.

On a computer that can process at most 32 bits of data at a time, those 32 bits have 2³² possible values, which you can treat as an integer between 0 and 2³² - 1. MAXINT is a predefined name for the largest possible integer on a given system; on a 32-bit system it would be 2³² - 1, or 4,294,967,295 (about 4.3 billion).

####  0026 Ever define your own numerical type to get better precision?

####  0027 Can you name powers of two up to 2**16 in arbitrary order?

####  0028 ... up to 2**32?

####  0029 ... up to 2**64?

####  002A Can you read a punched card, looking at the holes?

####  002B ... feeling the holes?

####  002C Have you ever patched binary code?

####  002D ... While the program was running?

####  002E Have you ever used program overlays?

####  002F Have you met any IBM vice-president?

####  0030 Do you know Dennis, Bill, or Ken?

[Dennis Ritchie][dmr] and [Ken Thompson][ken] created the Unix operating system at Bell Labs in the 1970s. After the Unix source code was made available to various universities, a student at the University of California, Berkeley named [Bill Joy][bill] helped create the BSD variant of Unix, and in particular the `vi` editor. He later went on to co-found tech giant Sun Microsystems.

[dmr]: https://en.wikipedia.org/wiki/Dennis_Ritchie
[ken]: https://en.wikipedia.org/wiki/Ken_Thompson
[bill]: https://en.wikipedia.org/wiki/Bill_Joy

####  0031 Have you ever taken a picture of a CRT?

####  0032 Have you ever played a videotape on your CRT?

####  0033 Have you ever digitized a picture?

####  0034 Did you ever forget to mount a scratch monkey?

A "scratch pad" is a notepad used for unimportant notes, a "scratch disk" is a storage device containing no important data; the idea is that if you're about to do something that might damage important data, you unmount the important disk and mount a scratch disk so that if something does go wrong, nothing of value is lost.

The Jargon File relates the story of a field technician who ran a diagnostic on a faulty computer without realising it was normally used to experiment on a monkey, and said monkey was still physically wired up to it, so he didn't think to mount a [scratch monkey] before starting to tinker.

[scratch monkey]: http://www.catb.org/jargon/html/S/scratch-monkey.html

####  0035 Have you ever optimized an idle loop?

An idle loop is what a computer executes when it has nothing better to do. Optimizing an idle loop cannot make anything go faster, since if there were anything to do, the computer would be doing it instead of idling.

That said, although an idle loop cannot run *faster*, it can run more *efficiently*. In this modern age of battery-powered computers, when a computer enters an idle loop it will often slow down or even turn parts of itself off to conserve power. In that sense, it does make sense to optimize an idle loop: if you can get the computer to slow down more or turn off more things, that will extend the battery life.

####  0036 Did you ever optimize a bubble sort?

Sorting a list of items is a well-studied problem, and there are many sorting algorithms available with various trade-offs. Bubble Sort is one of the uniformly worst-performing sorting algorithms, and any effort put towards optimizing it would be much better spent replacing it entirely with a smarter algorithm like Quick Sort.

(_That said_, there are [some situations](https://cs.stackexchange.com/a/53228) where Bubble Sort is the right algorithm, in which case you should probably optimize it.)

####  0037 Does your terminal/computer talk to you?

####  0038 Have you ever talked into an acoustic modem?

####  0039 ... Did it answer?

####  003A Can you whistle 300 baud?

####  003B ... 1200 baud?

####  003C Can you whistle a telephone number?

####  003D Have you witnessed a disk crash?

####  003E Have you made a disk drive "walk"?

Once upon a time, a "disk drive" was a unit about the size of a washing-machine. Like a washing machine, it involved spinning a heavy metal core at high speeds, and (like a washing machine) any imbalance of the payload could cause the unit to shake from side to side, and (under the right circumstances) rattle its way across the floor.

The Jargon File [also mentions](http://www.catb.org/jargon/html/W/walking-drives.html) that certain patterns of disk accesses could cause a drive to walk.

####  003F Can you build a puffer train? (0040: ...Do you know what it is?)

A [puffer train](https://en.wikipedia.org/wiki/Puffer_train) is a particular type pattern in a finite automaton (like [Conway's Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life)) which spontaneously moves across the cell space, leaving smaller structures (akin to debris) behind.

Cellular automata are still a very popular pastime among hackers. Puffer trains, though, have particular cultural significance: the first known puffer train in Conway's Game of Life was discovered by [Bill Gosper](https://en.wikipedia.org/wiki/Bill_Gosper).

#### 0041 Can you play music on your line printer? (0042 ... Your disk drive? 0043 ... Your tape drive?)

The music in this case is not a metaphor: it's literal music. Devices like dot printers or disk drives used stepper motors for accurate positioning of their print heads or, respectively, disk heads. By carefully manipulating the speed and position of these motors, one could modulate their vibration so as to, quite literally, [make them sing](https://www.youtube.com/watch?v=u8I6qt_Z0Cg).

Doing so required not only a pretty good understanding of electronics, programming and music, but also quite a fair deal of creativity. Printer drivers, naturally, do not natively support making printers sing, and indeed some of the sounds occur when the hardware is pushed beyond its safe (or standard) operational parameters. Consequently, creating these sounds sometimes required careful programming and a lot of trial-and-error.

####  0044 Do you have a Snoopy calendar?

####  0045 ... Is it out-of-date?

####  0046 Do you have a line printer picture of...

####  0047 ... the Mona Lisa?

####  0048 ... the Enterprise?

####  0049 ... Einstein?

####  004A ... Oliver?

####  004B Have you ever made a line printer picture?

####  004C Do you know what the following stand for?

####  004D ... DASD

####  004E ... Emacs

####  004F ... ITS

####  0050 ... RSTS/E

####  0051 ... SNA

####  0052 ... Spool

####  0053 ... TCP/IP

## Have you ever used
####  0054 ... TPU?

####  0055 ... TECO?

####  0056 ... Emacs?

####  0057 ... ed?

####  0058 ... vi?

####  0059 ... Xedit (in VM/CMS)?

####  005A ... SOS?

####  005B ... EDT?

####  005C ... Wordstar?

####  005D Have you ever written a CLIST?

## Have you ever programmed in
####  005E ... the X windowing system?

####  005F ... CICS?

####  0060 Have you ever received a Fax or a photocopy of a floppy?

####  0061 Have you ever shown a novice the "any" key?

####  0062 ... Was it the power switch?

## Have you ever attended
####  0063 ... Usenix?

####  0064 ... DECUS?

####  0065 ... SHARE?

####  0066 ... SIGGRAPH?

####  0067 ... NetCon?

####  0068 Have you ever participated in a standards group?

####  0069 Have you ever debugged machine code over the telephone?

####  006A Have you ever seen voice mail?

####  006B ... Can you read it?

####  006C Do you solve word puzzles with an on-line dictionary?

####  006D Have you ever taken a Turing test?

####  006E ... Did you fail?

#### 006F Ever drop a card deck? (0070 ... Did you successfully put it back together? 0071 ... Without looking?)

The card deck here does not refer to playing cards, but to [punched cards](https://en.wikipedia.org/wiki/Punched_card). Punched cards were small pieces of stiff paper or cardboard, which could be used as storage media, encoding ones and zeroes through the presence (or absence) of holes at pre-determined grid locations.

The small information density (depending on format, a punched card could represent anywhere from a few characters to a few tens of bytes) meant that a single program needed tens, hundreds, or even thousands of punched cards, which would often be punched somewhere other than in the machine room, where they would be fed to the computer.

Naturally, the worst thing that could happen when carrying a deck of cards across the campus was to drop it. Putting them back together in their correct order was not an easy task when you had hundreds of cards. Putting them back together without looking, just by feeling the hole pattern with your fingers -- thus reading it much like a computer would have -- was an even more impressive feat.

In practice, this was enough of a problem that IBM sold [card sorters](http://www.columbia.edu/cu/computinghistory/sorter.html) that would put a dropped deck back in order for you.

####  0072 Have you ever used IPCS?

####  0073 Have you ever received a case of beer with your computer?

####  0074 Does your computer come in 'designer' colors?

####  0075 Ever interrupted a UPS?

####  0076 Ever mask an NMI?

####  0077 Have you ever set off a Halon system?

####  0078 ... Intentionally?

####  0079 ... Do you still work there?

####  007A Have you ever hit the emergency power switch?

####  007B ... Intentionally?

####  007C Do you have any defunct documentation?

####  007D ... Do you still read it?

####  007E Ever reverse-engineer or decompile a program?

####  007F ... Did you find bugs in it?

####  0080 Ever help the person behind the counter with their terminal/computer?

####  0081 Ever tried rack mounting your telephone?

####  0082 Ever thrown a computer from more than two stories high?

####  0083 Ever patched a bug the vendor does not acknowledge?

####  0084 Ever fix a hardware problem in software?

####  0085 ... Vice versa?

####  0086 Ever belong to a user/support group?

####  0087 Ever been mentioned in Computer Recreations?

####  0088 Ever had your activities mentioned in the newspaper?

####  0089 ... Did you get away with it?

####  008A Ever engage a drum brake while the drum was spinning?

####  008B Ever write comments in a non-native language?

####  008C Ever physically destroy equipment from software?

####  008D Ever tried to improve your score on the Hacker Test?

####  008E Do you take listings with you to lunch?

####  008F ... To bed?

####  0090 Ever patch a microcode bug?

####  0091 ... around a microcode bug?

####  0092 Can you program a Turing machine?

####  0093 Can you convert postfix to prefix in your head?

####  0094 Can you convert hex to octal in your head?

####  0095 Do you know how to use a Kleene star?

####  0096 Have you ever starved while dining with philosophers?

####  0097 Have you solved the halting problem?

####  0098 ... Correctly?

####  0099 Ever deadlock trying eating spaghetti?

####  009A Ever written a self-reproducing program?

####  009B Ever swapped out the swapper?

####  009C Can you read a state diagram?

####  009D ... Do you need one?

####  009E Ever create an unkillable program?

####  009F ... Intentionally?

####  00A0 Ever been asked for a cookie?

####  00A1 Ever speed up a system by removing a jumper?

## Do you know...
####  00A2 Do you know who wrote Rogue?

####  00A3 ... Rogomatic?

####  00A4 Do you know Gray code?

####  00A5 Do you know what HCF means?

####  00A6 ... Ever use it?

####  00A7 ... Intentionally?

####  00A8 Do you know what a lace card is?

####  00A9 ... Ever make one?

####  00AA Do you know the end of the epoch?

####  00AB ... Have you celebrated the end of an epoch?

####  00AC ... Did you have to rewrite code?

####  00AD Do you know the difference between DTE and DCE?

####  00AE Do you know the RS-232C pinout?

####  00AF ... Can you wire a connector without looking?

####  00B0 Do you have a copy of Dec Wars?

[DEC Wars](https://www.netfunny.com/rhf/jokes/87/14917.9.html) was a [DEC](https://en.wikipedia.org/wiki/Digital_Equipment_Corporation)-themed parody of Star Wars. It was posted on USENET, in various groups, in 1983, and was written by Alan Hastings, Steve Tarr, Dave Borman and Barak Pearlmutter.

####  00B1 Do you have the Canonical Collection of Lightbulb Jokes?

####  00B2 Do you have a copy of the Hacker's dictionary?

####  00B3 ... Did you contribute to it?

####  00B4 Do you have a flowchart template?

####  00B5 ... Is it unused?

####  00B6 Do you have your own fortune-cookie file?

[fortune](https://en.wikipedia.org/wiki/Fortune_(Unix)) is a famous Unix passtime. When invoked, it would display various funny quotes from one of several files that shipped with it or were circulated in the hacker community. Particularly dedicated hackers would, of course, have such a file of their own.

####  00B7 Do you have the Anarchist's Cookbook?

####  00B8 ... Ever make anything from it?

####  00B9 Do you own a modem?

####  00BA ... a terminal?

####  00BB ... a toy computer?

####  00BC ... a personal computer?

####  00BD ... a minicomputer?

####  00BE ... a mainframe?

####  00BF ... a supercomputer?

####  00C0 ... a hypercube?

####  00C1 ... a printer?

####  00C2 ... a laser printer?

####  00C3 ... a tape drive?

####  00C4 ... an outmoded peripheral device?

####  00C5 Do you have a programmable calculator?

Programmable calculators like the [TI-59](https://en.wikipedia.org/wiki/TI-59_/_TI-58) were some of the earliest personal programmable devices. For many hackers, this would have been the first exposure to programming, and an occasional fun pastime.

Some of them, like the [HP-16C](https://en.wikipedia.org/wiki/HP-16C) were primarily aimed at programmers, but many hackers came from other fields, such as Physics or various other branches of engineering, where handheld scientific calculators are nearly impossible to live without.

####  00C6 ... Is it RPN?

Notably, many of these scientific calculators used [RPN notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation); in particular, HP's line of scientific calculators, which were held in highest regard, used RPN from the very beginning, starting with the [HP-35](https://en.wikipedia.org/wiki/HP-35), the first scientific handheld calculator.

RPN did not become a tradition by accident or taste alone; the RPN model had a number of advantages relevant to early hardware, and implementing such a scheme in software was at the very least cleaner, if not easier. Programming languages like Lisp, Forth and PostScript used it extensively, too.

####  00C7 Have you ever owned more than 1 computer?

####  00C8 ... 4 computers?

####  00C9 ... 16 computers?

####  00CA Do you have a SLIP line?

####  00CB ... a T1 line?

####  00CC Do you have a separate phone line for your terminal/computer?

####  00CD ... Is it legal?

####  00CE Do you have core memory?

####  00CF ... drum storage?

####  00D0 ... bubble memory?

####  00D1 Do you use more than 16 megabytes of disk space?

####  00D2 ... 256 megabytes?

####  00D3 ... 1 gigabyte?

####  00D4 ... 16 gigabytes?

####  00D5 ... 256 gigabytes?

####  00D6 ... 1 terabyte?

####  00D7 Do you have an optical disk/disk drive?

####  00D8 Do you have a personal magnetic tape library?

####  00D9 ... Is it unlabelled?

####  00DA Do you own more than 16 floppy disks?

####  00DB ... 64 floppy disks?

####  00DC ... 256 floppy disks?

####  00DD ... 1024 floppy disks?

####  00DE Do you have any 8-inch disks?

####  00DF Do you have an internal stack?

####  00E0 Do you have a clock interrupt?

####  00E1 Do you own volumes 1 to 3 of _The Art of Computer Programming_?

####  00E2 ... Have you done all the exercises?

####  00E3 ... Do you have a MIX simulator?

####  00E4 ... Can you name the unwritten volumes?

####  00E5 Can you quote from _The Mythical Man-month_?

####  00E6 ... Did you participate in the OS/360 project?

####  00E7 Do you have a TTL handbook?

####  00E8 Do you have printouts more than three years old?

## Career
####  00E9 Do you have a job?

####  00EA ... Have you ever had a job?

####  00EB ... Was it computer-related?

####  00EC Do you work irregular hours?

####  00ED Have you ever been a system administrator?

####  00EE Do you have more megabytes than megabucks?

By [1985](http://www.mkomo.com/cost-per-gigabyte) hard drives were under $100/mb, so this question's a bit of a gimme.

####  00EF Have you ever downgraded your job to upgrade your processing power?

####  00F0 Is your job secure?

####  00F1 ... Do you have code to prove it?

####  00F2 Have you ever had a security clearance?

## Games
####  00F3 Have you ever played Pong?

####  00F4 ... Spacewar?

####  00F5 ... Star Trek?

####  00F6 ... Wumpus?

####  00F7 ... Lunar Lander?

####  00F8 ... Empire?

## Have you ever beaten
####  00F9 ... Moria 4.8?

####  00FA ... Rogue 3.6?

####  00FB ... Rogue 5.3?

####  00FC ... Larn?

####  00FD ... Hack 1.0.3?

####  00FE ... Nethack 2.4?

####  00FF Can you get a better score on Rogue than Rogomatic?

####  0100 Have you ever solved Adventure?

####  0101 ... Zork?

####  0102 Have you ever written any redcode?

####  0103 Have you ever written an adventure program?

####  0104 ... a real-time game?

####  0105 ... a multi-player game?

####  0106 ... a networked game?

####  0107 Can you out-doctor Eliza?

## Hardware
####  0108 Have you ever used a light pen?

####  0109 ... did you build it?

## Have you ever used
####  010A ... a teletype?

####  010B ... a paper tape?

####  010C ... a decwriter?

####  010D ... a card reader/punch?

####  010E ... a SOL?

## Have you ever built
####  010F ... an Altair?

####  0110 ... a Heath/Zenith computer?

## Do you know how to use
####  0111 ... an oscilliscope?

####  0112 ... a voltmeter?

####  0113 ... a frequency counter?

####  0114 ... a logic probe?

####  0115 ... a wirewrap tool?

####  0116 ... a soldering iron?

####  0117 ... a logic analyzer?

####  0118 Have you ever designed an LSI chip?

####  0119 ... has it been fabricated?

####  011A Have you ever etched a printed circuit board?

## Historical
####  011B Have you ever toggled in boot code on the front panel?

####  011C ... from memory?

####  011D Can you program an Eniac?

####  011E Ever seen a 90 column card?

## IBM
####  011F Do you recite IBM part numbers in your sleep?

####  0120 Do you know what IBM part number 7320154 is?

####  0121 Do you understand 3270 data streams?

####  0122 Do you know what the VM privilege classes are?

####  0123 Have you IPLed an IBM off the tape drive?

####  0124 ... off a card reader?

####  0125 Can you sing something from the IBM Songbook?

## Languages
####  0126 Do you know more than 4 programming languages?

####  0127 ... 8 languages?

####  0128 ... 16 languages?

####  0129 ... 32 languages?

####  012A Have you ever designed a programming language?

####  012B Do you know what Basic stands for?

####  012C ... Pascal?

####  012D Can you program in Basic?

####  012E ... Do you admit it?

####  012F Can you program in Cobol?

####  0130 ... Do you deny it?

####  0131 Do you know Pascal?

####  0132 ... Modula-2?

####  0133 ... Oberon?

####  0134 ... More that two Wirth languages?

####  0135 ... Can you recite a Nicklaus Wirth joke?

####  0136 Do you know Algol-60?

####  0137 ... Algol-W?

####  0138 ... Algol-68?

####  0139 ... Do you understand the Algol-68 report?

####  013A ... Do you like two-level grammars?

####  013B Can you program in assembler on 2 different machines?

####  013C ... on 4 different machines?

####  013D ... on 8 different machines?

## Do you know
####  013E ... APL?

####  013F ... Ada?

####  0140 ... BCPL?

####  0141 ... C++?

####  0142 ... C?

####  0143 ... Comal?

####  0144 ... Eiffel?

####  0145 ... Forth?

####  0146 ... Fortran?

####  0147 ... Hypertalk?

####  0148 ... Icon?

####  0149 ... Lisp?

####  014A ... Logo?

####  014B ... MIIS?

####  014C ... MUMPS?

####  014D ... PL/I?

####  014E ... Pilot?

####  014F ... Plato?

####  0150 ... Prolog?

####  0151 ... RPG?

####  0152 ... Rexx (or ARexx)?

####  0153 ... SETL?

####  0154 ... Smalltalk?

####  0155 ... Snobol?

####  0156 ... VHDL?

####  0157 ... any assembly language?

####  0158 Can you talk VT-100?

####  0159 ... Postscript?

####  015A ... SMTP?

####  015B ... UUCP?

####  015C ... English?

## Micros
####  015D Ever copy a copy-protected disk?

####  015E Ever create a copy-protection scheme?

####  015F Have you ever made a "flippy" disk?

####  0160 Have you ever recovered data from a damaged disk?

####  0161 Ever boot a naked floppy?

## Networking
####  0162 Have you ever been logged in to two different timezones at once?

####  0163 Have you memorized the UUCP map for your country?

####  0164 ... For any country?

####  0165 Have you ever found a sendmail bug?

####  0166 ... Was it a security hole?

####  0167 Have you memorized the HOSTS.TXT table?

####  0168 ... Are you up to date?

####  0169 Can you name all the top-level nameservers and their addresses?

####  016A Do you know RFC-822 by heart?

####  016B ... Can you recite all the errors in it?

####  016C Have you written a Sendmail configuration file?

####  016D ... Does it work?

####  016E ... Do you mumble "defocus" in your sleep?

####  016F Do you know the max packet lifetime?

## Operating systems
## Can you use
####  0170 ... BSD Unix?

####  0171 ... non-BSD Unix?

####  0172 ... AIX

####  0173 ... VM/CMS?

####  0174 ... VMS?

####  0175 ... MVS?

####  0176 ... VSE?

####  0177 ... RSTS/E?

####  0178 ... CP/M?

####  0179 ... COS?

####  017A ... NOS?

####  017B ... CP-67?

####  017C ... RT-11?

####  017D ... MS-DOS?

####  017E ... Finder?

####  017F ... PRODOS?

####  0180 ... more than one OS for the TRS-80?

####  0181 ... Tops-10?

####  0182 ... Tops-20?

####  0183 ... OS-9?

####  0184 ... OS/2?

####  0185 ... AOS/VS?

####  0186 ... Multics?

####  0187 ... ITS?

####  0188 ... Vulcan?

####  0189 Have you ever paged or swapped off a tape drive?

####  018A ... Off a card reader/punch?

####  018B ... Off a teletype?

####  018C ... Off a networked (non-local) disk?

####  018D Have you ever found an operating system bug?

####  018E ... Did you exploit it?

####  018F ... Did you report it?

####  0190 ... Was your report ignored?

####  0191 Have you ever crashed a machine?

####  0192 ... Intentionally?

## People
####  0193 Do you know any people?

####  0194 ... more than one?

####  0195 ... more than two?

## Personal
####  0196 Are your shoelaces untied?

####  0197 Do you interface well with strangers?

####  0198 Are you able to recite phone numbers for half-a-dozen computer systems

####  0199 ... but unable to recite your own?

####  019A Do you log in before breakfast?

####  019B Do you consume more than LD-50 caffeine a day?

####  019C Do you answer either-or questions with "yes"?

####  019D Do you own an up-to-date copy of any operating system manual?

####  019E ... every operating system manual?

####  019F Do other people have difficulty using your customized environment?

####  01A0 Do you dream in any programming languages?

####  01A1 Do you have difficulty focusing on three-dimensional objects?

####  01A2 Do you ignore mice?

####  01A3 Do you despise the CAPS LOCK key?

####  01A4 Do you believe menus belong in restaurants?

####  01A5 Do you have a Mandelbrot hanging on your wall?

####  01A6 Have you ever decorated with magnetic tape or punched cards?

####  01A7 Do you have a disk platter or a naked floppy hanging in your home?

####  01A8 Have you ever seen the dawn?

####  01A9 ... Twice in a row?

####  01AA Do you use "foobar" in daily conversation?

####  01AB ... "bletch"?

####  01AC Do you use the "P convention"?

####  01AD Do you automatically respond to any user question with RTFM?

####  01AE ... Do you know what it means?

####  01AF Do you think garbage collection means memory management?

####  01B0 Do you have problems allocating horizontal space in your room/office?

####  01B1 Do you read Scientific American in bars to pick up women?

####  01B2 Is your license plate computer-related?

####  01B3 Have you ever taken the Purity test?

####  01B4 Ever have an out-of-CPU experience?

####  01B5 Have you ever set up a blind date over the computer?

####  01B6 Do you talk to the person next to you via computer?

## Programming
####  01B7 Can you write a Fortran compiler?

####  01B8 ... In TECO?

####  01B9 Can you read a machine dump?

####  01BA Can you disassemble code in your head?

## Have you ever written
####  01BB ... a compiler?

####  01BC ... an operating system?

####  01BD ... a device driver?

####  01BE ... a text processor?

####  01BF ... a display hack?

####  01C0 ... a database system?

####  01C1 ... an expert system?

####  01C2 ... an edge detector?

####  01C3 ... a real-time control system?

####  01C4 ... an accounting package?

####  01C5 ... a virus?

####  01C6 ... a prophylactic?

####  01C7 Have you ever written a biorhythm program?

####  01C8 ... Did you sell the output?

####  01C9 ... Was the output arbitrarily invented?

####  01CA Have you ever computed pi to more than a thousand decimal places?

####  01CB ... the number e?

####  01CC Ever find a prime number of more than a hundred digits?

####  01CD Have you ever written self-modifying code?

####  01CE ... Are you proud of it?

####  01CF Did you ever write a program that ran correctly the first time?

####  01D0 ... Was it longer than 20 lines?

####  01D1 ... 100 lines?

####  01D2 ... Was it in assembly language?

####  01D3 ... Did it work the second time?

####  01D4 Can you solve the Towers of Hanoi recursively?

####  01D5 ... Non-recursively?

####  01D6 ... Using the Troff text formatter?

####  01D7 Ever submit an entry to the Obfuscated C code contest?

####  01D8 ... Did it win?

####  01D9 ... Did your entry inspire a new rule?

####  01DA Do you know Duff's device?

####  01DB Do you know Jensen's device?

####  01DC Ever spend ten minutes trying to find a single-character error?

####  01DD ... More than an hour?

####  01DE ... More than a day?

####  01DF ... More than a week?

####  01E0 ... Did the first person you show it to find it immediately?

## Unix
####  01E1 Can you use Berkeley Unix?

####  01E2 .. Non-Berkeley Unix?

####  01E3 Can you distinguish between sections 4 and 5 of the Unix manual?

####  01E4 Can you find TERMIO in the System V release 2 documentation?

####  01E5 Have you ever mounted a tape as a Unix file system?

####  01E6 Have you ever built Minix?

####  01E7 Can you answer "quiz function ed-command" correctly?

####  01E8 ... How about "quiz ed-command function"?

## Usenet
####  01E9 Do you read news?

####  01EA ... More than 32 newsgroups?

####  01EB ... More than 256 newsgroups?

####  01EC ... All the newsgroups?

####  01ED Have you ever posted an article?

####  01EE ... Do you post regularly?

####  01EF Have you ever posted a flame?

####  01F0 ... Ever flame a cross-posting?

####  01F1 ... Ever flame a flame?

####  01F2 ... Do you flame regularly?

####  01F3 Ever have your program posted to a source newsgroup?

####  01F4 Ever forge a posting?

####  01F5 Ever form a new newsgroup?

####  01F6 ... Does it still exist?

####  01F7 Do you remember

####  01F8 ... mod.ber?

####  01F9 ... the Stupid People's Court?

####  01FA ... Bandy-grams?

## Phreaking
####  01FB Have you ever built a black box?

####  01FC Can you name all of the 'colors' of boxes?

####  01FD ... and their associated functions?

####  01FE Does your touch tone phone have 16 DTMF buttons on it?

####  01FF Did the breakup of MaBell create more opportunities for you?

