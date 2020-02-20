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

Paper tape, also called [punched tape](https://en.wikipedia.org/wiki/Punched_tape) or perforated tape, was an early, inexpensive storage media, consisting of a long, thin strip of paper, divided into a fine grid (typically 5 or 8 columns). Each cell of this grid corresponded to one bit of information. If the grid was punched, the corresponding bit would be 1, otherwise it would be zero (or vice-versa).

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

If you want to work with numbers larger than maxint, one approach is to treat regular machine integers as "digits", store numbers as a sequence of those digits, and teach your computer how to add, subtract, multiply and divide those numbers using the traditional "longhand" algorithms. This is much, much slower than using your computer's normal arithmetic functions, but it means you can operate precisely on numbers as large as available memory.

####  0027 Can you name powers of two up to 2**16 in arbitrary order?

####  0028 ... up to 2**32?

####  0029 ... up to 2**64?

####  002A Can you read a punched card, looking at the holes?

####  002B ... feeling the holes?

####  002C Have you ever patched binary code?

Computer programs are hugely complex, with many small details that need to kept consistent in thousands or millions of places. Unsurprisingly, computer programmers fairly quickly taught computers themselves to keep track of those details, so a program could be written in a "high level", human-friendly format (the "source code"), and then automatically converted to the "low-level" format the machine could understand. Typically, the high-level format is a text file with readable English keywords like "if" and "while", and the low-level format is a sequence of instructions represented by numbers stored as binary.

When a problem is found in a program, the sensible thing to do is to modify the high-level version, and reconvert it to the low-level format. Unfortunately, that's not always possible - sometimes, the original source is lost, or destroyed, or illegal to distribute - and so it is necessary to modify the binary directly. This is massively more difficult than modifying the source, since the program is in a very different format, and because a change in one place might require many changes in other places to keep things consistent, changes that would ordinarily be handled automatically during the conversion process.

####  002D ... While the program was running?

As well being more difficult to attempt (there are lots of ways to edit a file on disk, editing a program in memory sometimes isn't even possible), this is more difficult to get right. If you edit a program on disk, the modified version only needs to be consistent with itself, since a running program will either be the original or the modified version. If you edit a program as it's running, the program is a combination of the two, so it the original and modified versions need to be compatible with themselves and with each other.

####  002E Have you ever used program overlays?

Normally, when a program runs, the entire thing is loaded into memory where the CPU can get at it. However, a very large program might not fit into the computer's memory, especially if the program also needs to work with a large amount of data. "Overlays" are one solution to this problem: divide the program into smaller chunks, and have the "main" program unload one chunk and load another when it's needed. This works best with programs that have different modes of operation, like a game with a "strategy" phase and a "tactics" phase, or an office suite with a "word processor" mode and a "spreadsheet" mode.

Most operating systems only provide a way to run a single, entire program at once, so an overlay system is much more complex, and often involves doing a lot of work the operating system would normally do on your behalf.

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

####  0038 Have you ever talked into an acoustic modem? (0039 ... Did it answer?)

A "modem" (short for "modulator/demodulator") is a device that can turn a digital signal into an analogue waveform and back. When two computers need to communicate, but they are too far apart to be connected directly, they can be connected to modems wired up to the telephone network, and talk to each other like an ordinary human conversation. However, prior to 1984, when Bell Systems held a monopoly in the United States, they didn't allow unauthorised equipment to be wired up to the telephone network. Instead, an acoustic modem had a little speaker and a little microphone; a human would dial the telephone number of a computer on an ordinary phone, then attach the phone handset to the acoustic modem so the computer could communicate.

Talking into an acoustic modem is easy, if you can find one, but not very useful.

####  003A Can you whistle 300 baud?  (003B ... 1200 baud?)

When two modems connect to each other, they play [a particular pattern of tones](https://www.windytan.com/2012/11/the-sound-of-dialup-pictured.html) and listen for that same pattern, to verify that the other end is also a modem, and is speaking a compatible dialect. The tones for the original modem protocol (300 baud) are the simplest, and might plausibly be possible for a skilled human to replicate.

[Baud](https://en.wikipedia.org/wiki/Baud) is a measurement of communication speed, expressed as symbols per second. A communication at 300 baud means 300 changes to the signal being sent per second, so it's not practical for a human to reproduce actual 300 baud communications.

####  003C Can you whistle a telephone number?

[Dual-Tone Multi-Frequency signalling](https://en.wikipedia.org/wiki/Dual-tone_multi-frequency_signaling) is a way for a telephone to communicate to a telephone exchange. On a 4x4 keypad, a particular frequency is associated with each row and column, so pressing a particular key plays the tones associated with the row and column it appears in. On most consumer equipment, the last column of the keypad is omitted, leaving only the 10 digits, `*` and `#`.

The various tones required by DTMF signalling are all within the range of human speech (because they must be transmitted over telephone lines), and humans [can sing chords](https://en.wikipedia.org/wiki/Overtone_singing), so it's at least theoretically possible to whistle a telephone number.

####  003D Have you witnessed a disk crash?

Old magnetic disk drives didn't have automatic protection against the head falling onto the platter.
Such an event could leave a deep scratch on a platter and render it unusable. It also made a distinctive and scary sound.
Also known as a [head crash](https://en.wikipedia.org/wiki/Head_crash).

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

Since line printers could draw arbitrary text on large pieces of paper, they were quickly used for what we would today call [ASCII art](https://en.wikipedia.org/wiki/ASCII_art).

####  0047 ... the Mona Lisa?

If you're going to adopt old images to a new medium, why not start with [the greats](http://artscene.textfiles.com/asciiart/monalisa.art)?

####  0048 ... the Enterprise?

Probably the [original USS Enterprise (NCC-1701)](http://artscene.textfiles.com/asciiart/enterp.art) from the original Star Trek TV series, although by the time of the Test's publication it might also have been the Enterprise A from the Star Trek movies, or the Enterprise D from Star Trek: The Next Generation.

Star Trek would have had many fans among the MIT hackers who created the Test.

####  0049 ... Einstein?

[Albert Einstein](https://en.wikipedia.org/wiki/Albert_Einstein), famous physicist and hero to scientifically-inclined people everywhere.

####  004A ... Oliver?

[Oliver Wendell Jones](http://artscene.textfiles.com/asciiart/oliver.art), child genius and computer hacker from the comic strip Bloom County. 

####  004B Have you ever made a line printer picture?

####  004C Do you know what the following stand for?

####  004D ... DASD

"**D**irect **A**ccess **S**torage **D**evice" is an IBMism for a disk drive,
reflecting the fact that any part of the disk may be accessed directly.

This was in contrast to a SASD - a *Sequential* Access Storage Device,
which could only have its data accessed sequentially. These were usually
things like paper or magnetic tape.

####  004E ... Emacs

"Emacs" stands for "**E**ditor **MAC**ro**S**".

This is because Emacs started out as a collection of macros for the
[TECO](https://en.wikipedia.org/wiki/TECO_%28text_editor%29).  TECO was an
incredibly versatile and complex text editing system, with a Turing-complete
macro language that used every single available character.

Emacs was eventually rewritten, with TECO replaced by C and Lisp, but the
name lived on.

####  004F ... ITS

ITS stands for the **I**ncompatible **T**imesharing **S**ystem.

[ITS](https://en.wikipedia.org/wiki/Incompatible_Timesharing_System)
was an incredibly influential operating system for DEC's 36-bit PDP-6 and
PDP-10 minicomputers.

It was developed mostly by members of MIT's Artificial
Intelligence Laboratory as a rejection of the then-current
[Multics](https://en.wikipedia.org/wiki/Multics) project. (Where Multics
was large, written mostly in a high-level language, and contained strict
security features, ITS was small, written in assembly, and was permissive
to the point of anarchy.)

ITS was never widely deployed, but many early hackers were ITS users and
many ITS machines were connected to the early ARPANET and thus it left a
long shadow.  It was the birthplace of Emacs, Scheme, and device-independent
terminal output, among many other innovations taken for granted today.

Its name was a pun on that of the earlier [Compatible Time-Sharing
System](https://en.wikipedia.org/wiki/Compatible_Time-Sharing_System),
with which it shares no code.

####  0050 ... RSTS/E

####  0051 ... SNA

[Systems Network Architecture](https://en.wikipedia.org/wiki/IBM_Systems_Network_Architecture), a proprietary protocol stack from the pre-Internet era.

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

[CICS](https://www.ibm.com/it-infrastructure/z/cics) is a transaction processing framework for IBM mainframes.

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

####  006D Have you ever taken a Turing test? (006E ... Did you fail?)

The [Turing test](https://en.wikipedia.org/wiki/Turing_test) was proposed by mathematician and early computer scientist Alan Turing as a practical test for artificial intelligence. A human judge is given two computer terminals: one is connected to the computer being tested, and the other is connected to another terminal in another room, where a human sits. The judge can type any message on either terminal, and must decide which terminal is talking to a computer and which terminal is talking to a human.

The [Loebner Prize](https://en.wikipedia.org/wiki/Loebner_Prize) is an annual competition run in the style of Turing's test, but it was first held in 1990, the year after this Test was created.

To fail a Turing test would mean an impartial observer judged your personality to be more mechanical and artificial than an actual computer.

#### 006F Ever drop a card deck? (0070 ... Did you successfully put it back together? 0071 ... Without looking?)

The card deck here does not refer to playing cards, but to [punched cards](https://en.wikipedia.org/wiki/Punched_card). Punched cards were small pieces of stiff paper or cardboard, which could be used as storage media, encoding ones and zeroes through the presence (or absence) of holes at pre-determined grid locations.

The small information density (depending on format, a punched card could represent anywhere from a few characters to a few tens of bytes) meant that a single program needed tens, hundreds, or even thousands of punched cards, which would often be punched somewhere other than in the machine room, where they would be fed to the computer.

Naturally, the worst thing that could happen when carrying a deck of cards across the campus was to drop it. Putting them back together in their correct order was not an easy task when you had hundreds of cards. Putting them back together without looking, just by feeling the hole pattern with your fingers -- thus reading it much like a computer would have -- was an even more impressive feat.

In practice, this was enough of a problem that IBM sold [card sorters](http://www.columbia.edu/cu/computinghistory/sorter.html) that would put a dropped deck back in order for you.

####  0072 Have you ever used IPCS?

####  0073 Have you ever received a case of beer with your computer?

####  0074 Does your computer come in 'designer' colors?

####  0075 Ever interrupted a UPS?

An [Uninterruptible Power Supply](https://en.wikipedia.org/wiki/Uninterruptible_power_supply) is basically a big battery: one end plugs into the wall to obtain regular, erratic mains power, and the other end plugs into your computer to supply pristine, smooth power to the delicate electronics. In the event of a blackout or power surge, the UPS usually gives you a few minutes to shut down the computer cleanly instead of the power cutting out suddenly.

####  0076 Ever mask an NMI?

A computer's CPU normally processes instructions in a steady stream, but sometimes a higher-priority event occurs (for example, a key is pressed on the keyboard, or a timeout occurs) and the CPU is _interrupted_ so it can go handle the situation, and eventually it can go back to what it was originally doing. Sometimes if the CPU is doing something very important or timing sensitive and it needs to not be interrupted, it will temporarily _mask_ interrupts, and if any interrupt events that occur won't be processed until the CPU unmasks them again.

However, some interrupts are so important they cannot be masked, they are Non Maskable Interrupts (NMIs). Usually they represent hardware failures, or some kind of "reset" button.

####  0077 Have you ever set off a Halon system?

A computer data centre involves a lot of electricity and a lot of computers made from volatile substances, so the odds of an electrical fire are high. Electrical fires can't be safely extinguished with water because it conducts electricity, so the usual scheme is to have a button or lever by the door that floods the entire room with [halon gas](https://en.wikipedia.org/wiki/Halomethane#Fire_extinguishing).

Setting off a halon system and refilling it is cheaper than reconstructing a burned-down data centre, but it's not cheap, and probably not something you want to do unless you can actually see flames.

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

Computer Recreations was a regular column about computing and mathematical puzzles and problems, published in Scientific American.

####  0088 Ever had your activities mentioned in the newspaper?

####  0089 ... Did you get away with it?

####  008A Ever engage a drum brake while the drum was spinning?

[Drum memory](https://en.wikipedia.org/wiki/Drum_memory) consisted of a large metal cylinder coated in magnetic material. To read or write data, a magnetic head would be moved to the correct position along the length of the drum, and then wait for the relevant portion of the drum to pass beneath it. This meant that the faster the drum could spin, the faster the computer could access stored data, and so the drum was kept at its maximum speed as much as possible.

Needless to say, engaging the brake while the drum was spinning would be _bad idea_.

####  008B Ever write comments in a non-native language?

####  008C Ever physically destroy equipment from software?

It may sound funny now, but back in the days hardware wasn't as smart and it was possible to physically damage certain CRT displays by switching them into unusual modes, for example.

####  008D Ever tried to improve your score on the Hacker Test?

####  008E Do you take listings with you to lunch? (008F ... To bed?)

In the days of punch cards and paper tape, programs were not written interactively at a terminal, they were written offline, then typed into a card punch and submitted to the computer operators to be run at the next available opportunity. Eventually the operators would contact you with (if you were lucky) the completed output of your program, or (more likely) an error message. Debugging the program involved staring at a printout ("listing") of the program's source code, trying to puzzle out what went wrong.

Such puzzle solving counted as "work", but particulary dedicated hackers might keep puzzling away and neglecting more important tasks like eating or sleeping.

####  0090 Ever patch a microcode bug?

The instruction sets for the very first CPUs directly mapped onto the functionality available, but newer CPUs needed to be compatible with the older CPUs while adding new functionality and redesigning the implementation to be more efficient. Most modern CPUs implement their standard instruction sets by converting each incoming instruction into one or more processor-specific _micro instructions_, so they can implement a complex instruction set without dedicating silicon to each slightly-different variant of a rarely-used instruction. A CPU's _microcode_ is the complete program that executes standard instructions by converting them to micro instructions.

Because microcode is so fundamental to a CPU's operation, it is very well tested by the manufacturer, and any errors tend to show up immediately so they are fixed quickly. That said, microcode bugs are not unheard of.

Many big iron machines such as DEC PDP-10 came with a micro-assembler and the microcode source, so patching bugs and adding new instructions wasn't unheard of either.

####  0091 ... around a microcode bug?

####  0092 Can you program a Turing machine?

A [Turing machine](https://en.wikipedia.org/wiki/Turing_machine) is a mathematical model of computation described by Alan Turing, which he used to explore what kinds of things could possibly be computed, given infinite time and resources.

You can't write a program for a Turing machine the same way you could write a program for a real machine (for one thing, it doesn't have "instructions" as such, just a frustratingly large set of arbitrary "states"), but it's instructive to think about how a Turing machine might go about simple tasks like adding numbers.

####  0093 Can you convert postfix to prefix in your head?

####  0094 Can you convert hex to octal in your head?

####  0095 Do you know how to use a Kleene star?

In the pattern-matching syntax of regular expressions, the Kleene star means "zero or more of the preceeding item". For example, if the pattern `ab` matches the string "ab", then the pattern `ab*` would match the strings "a", "ab", "abb", "abbb", and so forth.

####  0096 Have you ever starved while dining with philosophers?

The [Dining Philosophers problem](https://en.wikipedia.org/wiki/Dining_philosophers_problem) is a traditional example problem used to teach concurrent algorithm design. 

Let's say a bunch of philosophers are seated around a table. Each philosopher has plate of spaghetti in front of them, and between each pair of plates is a chopstick. A philosopher can be doing one of a few things:

  - philosophizing, in which case they put down their chopsticks, making them available for the philosophers to their left and right
  - waiting, either for any chopstick to become avalable, or (if they already have one) for the other chopstick to become available
  - eating, once they have two chopsticks

The problem is to come up with a protocol for all the philosophers to follow that allows all the philosophers to eat. For example, let's say we use the rule "take the chopstick to your left, then wait for the chopstick to your right to become available". All the philosophers take the chopstick to their left, then wait forever because the philosopher on their right has the chopstick on their right and is waiting forever.

A sufficiently sophisticated scheme can work, but people trying to solve the problem for the first time are often dismayed at how frequently one of their philosophers winds up starving.

####  0097 Have you solved the halting problem? (0098 ... Correctly?)

Given a Turing machine (that is, some kind of program) and an input for that program, feeding the input into the machine and turning it on will produce one of two results: either the machine will (eventually) finish its calculation and halt, or it will get stuck in a loop and keep calculating forever. The Halting Problem is to create a Turing machine that takes another Turing machine and its input as inputs, and figures out whether that machine will halt or loop forever, without actually running it and waiting forever to see what happens.

As it turns out, Turing proved that it's not possible to solve the Halting problem, so anyone who answers "yes" to question 0097 will answer "no" to question 0098... unless they're lying.

That said, solving the halting problem for a _specific program_ or class of programs rather than an arbitrary program is possible and may be necessary to prove that it always finishes in finite time (e.g. that a mission critical system doesn't hang).

####  0099 Ever deadlock trying eating spaghetti?

See question 0096.

A "deadlock" is when two or more actors are prevented from making progress because they are each waiting for a resource another actor is using. The example from question 0096, where each philosopher takes the chopstick on their left and waits forever for the chopstick on their right, is an example of a deadlock.

####  009A Ever written a self-reproducing program?

####  009B Ever swapped out the swapper?

####  009C Can you read a state diagram?

####  009D ... Do you need one?

####  009E Ever create an unkillable program?

####  009F ... Intentionally?

####  00A0 Ever been asked for a cookie?

####  00A1 Ever speed up a system by removing a jumper?

Before hardware auto-discovery (ala Plug'n'Play) was common, users often had to use [jumpers](https://en.wikipedia.org/wiki/Jumper_(computing)) to configure their mainboards, disk drives etc. to use specific interrupts, modes and so on.

Most of the time wrong arrangement of jumpers simply rendered a peripheral or the whole system unusable rather than just slow though.

## Do you know...
####  00A2 Do you know who wrote Rogue?

####  00A3 ... Rogomatic?

####  00A4 Do you know Gray code?

####  00A5 Do you know what HCF means?

[Halt and Catch Fire](http://www.catb.org/jargon/html/H/HCF.html), a CPU instruction useful for question 008C.

####  00A6 ... Ever use it?

####  00A7 ... Intentionally?

####  00A8 Do you know what a lace card is?

A punched card with every hole punched. Such cards would sometimes cause the reader to jam.

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

A stencil for quckly drawing flowchart shaped on paper. Like [this](http://ferretronix.com/march/ibm_publications/ibm_flowchart_template_1.jpg).

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

IBM 3270 was a block-oriented rather than a character-oriented video terminal, much harder to communicate with than a VT100.

####  0122 Do you know what the VM privilege classes are?

####  0123 Have you IPLed an IBM off the tape drive?

IPL = Initial Program Loader, the mainframe for a bootloader. You can experience it for yourself in the [Hercules](http://www.hercules-390.org/) emulator.

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

A well-known one: "you can call me by name, Niklaus Wirth, or by value, Nickels Worth".

####  0136 Do you know Algol-60?

####  0137 ... Algol-W?

####  0138 ... Algol-68?

####  0139 ... Do you understand the Algol-68 report?

Algol-68 is a vastly more complex language than the simple Algol-60. That report is a _long_ read.

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

The standard [5.25" floppy
disk](http://www.obsoletemedia.org/5-25-inch-minifloppy-disk/) (called a
"minifloppy" at the time, to distinguish it from the larger 8" disks that
preceeded it) could be *single-sided* or *double-sided*.

A single-sided disk could be read and written only on one side, while a
double-sided disk could be read and written on both sides.  (If the drive
itself didn't have two read/write heads, you'd have to actually take the
disk out and flip it over to read the other side.)

Disks were expensive in those days, and single-sided disks were often
significantly cheaper than double-sided ones.  However, it was often possible
to convert a single-sided disk to a double-sided one by the simple expedient
of cutting out a notch on the other side of the disk sleeve.

These notches were used to tell the drive whether or not the disk was
writable.  For a single-sided disk, there was only one notch, so when it
was flipped over, the disk could not be written to.

A "flippy" disk was simply a single-sided floppy disk that had an extra notch
cut out on the other side, effectively converting it to a double-sided disk.
This could be a real money-saver, provided you didn't accidentally cut
the disk itself while you were cutting out the new notch...

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

Known as [z/VM](https://www.ibm.com/it-infrastructure/z/zvm) now. Originally it included the hypervisor (VM) and a small, single-user guest OS named CMS (Conversational Monitor System). A CMS virtual machine would be spawned for every user who logged in, much like Virtual Desktop Infrastructure solutions today.

####  0174 ... VMS?

Known as OpenVMS now. A VAX version can run in the [SIMH](http://simh.trailing-edge.com/).

####  0175 ... MVS?

Known as [z/OS](https://en.wikipedia.org/wiki/Z/OS) these days. MVS 3.8j is available free of charge and runs in Hercules.

####  0176 ... VSE?

Also known as DOS/360 at some point. A mainframe OS for people who couldn't afford MVS. Still exists as [z/VSE](https://www.ibm.com/it-infrastructure/z/zvse).

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

Common Lisp and some other languages use the "p" suffix for predicates, e.g. `(numberp 42)`. Newer lisps like Scheme and Clojure usually go with more intuitive "?" instead, like `(string? "foo")`.

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

"News" or "Netnews" is (but, sadly, mostly *was*) a worldwide collection of
"bulletin-board" style discussion system.  Discussions were organized into
conversations and conservations were organized into various *newsgroups*.

Different sites (usually, large shared computers) would
transfer collections of conversations among each other using the
Unix-to-Unix Copy ([UUCP](https://en.wikipedia.org/wiki/UUCP))
mechanism and, later, the Network News Transfer Protocol
([NNTP](https://en.wikipedia.org/wiki/Network_News_Transfer_Protocol)).

(Other mechanisms, like the venerable
[FidoNet](https://en.wikipedia.org/wiki/FidoNet), were also used, but
more rarely.)

News was usually distributed on a site-by-site basis: one site would connect
to another, transfer all of its new articles, and then disconnect. The
called site would then call other sites and distribute the news, and so on

(Other mechanisms, like the venerable
[FidoNet](https://en.wikipedia.org/wiki/FidoNet), were also used, but
more rarely.)

News was usually distributed on a site-by-site basis: one site would connect
to another, transfer all of its new articles, and then disconnect. The
called site would then call other sites and distribute the news, and so on.

Newsgroups were organized into a hierarchy, with names like
"comp.lang.python" for Python programming language-related
discussions. When the Internet became more open, many newsgroups
were renamed in an action that became known as [The Great
Renaming](http://www.catb.org/jargon/html/G/Great-Renaming.html).

The collection of all sites that participated in the distribution
of public netnews became known as "Usenet".  Usenet was
distinct from (though it connected with at some points) the
[ARPANET](https://en.wikipedia.org/wiki/ARPANET). Unlike the ARPANET (and
the nascent Internet at the time), Usenet was ostensibly open to the public:
all that was required was one of the sites let you connect and transfer
news articles.

Usenet was the first taste of what would become "the Internet" for many
people, and originated many terms that are still in use today: "spam",
"flame", and "FAQ".

####  01EA ... More than 32 newsgroups?

Users could subscribe to as many newsgroups as they liked.  In the early
days of Usenet, 32 would not be considered an unsual number, but after
the rise of the Internet, 32 might be considered "a lot".

####  01EB ... More than 256 newsgroups?

256 newsgroups would be a lot of newsgroups at any point in history.

####  01EC ... All the newsgroups?

Unless you were acting as a distribution site, archivist, aggregator,
or are [KIBO](http://www.catb.org/jargon/html/K/KIBO.html) himself, it
would be unusual to subscribe to *all* the newsgroups.

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

Back when telephone switches (the computers that control the telephone
network) worked on mechanical electical relays, they would use a change
in voltage on a phone line to determine when the phone had been picked
up. When a phone was on-hook, the voltage would be different than when it
was off-hook.

The billing for a call would only begin when the receiver answered the
phone by taking it off the hook. A "black box" was a simple electical
device that, when attached to a phone, would prevent the associated drop
in voltage and thus prevent the call from being billed.

####  01FC Can you name all of the 'colors' of boxes? (01FD ... and their associated functions?)

Other devices were often constructed to manipulate the phone network.
By analogy with the black box above, they were often named after colors.
Common colors of "boxes" in the phreaking community included:

- black - prevent incoming calls from being billed
- blue - simulated a telephone operator's console
- green - manipulated payphones (but only from the phone called by the payphone)
- red - simulated the insertion of coins into a payphone
- beige - acted as a [lineman's handset](https://en.wikipedia.org/wiki/Lineman%27s_handset)
- clear - allowed the use of post-pay payphones without paying
- gold - allowed the bridging of two phone lines
- magenta - generated a ring signal (usually not used on its own)
- orange - [spoofs caller ID](https://en.wikipedia.org/wiki/Caller_ID_spoofing)
           information
- vermillion - a combination of a magenta and orange box
- violet - simulate a phone being off-hook
- silver - used to simulate the DTMF tones on the Defense Switched Network
           (the now obsolete phone network used by the United States
            Department of Defense)

The use of "colored box" terminology expanded outside the phreaking community
to be applied to other devices that were used to manipulate systems.
For example, the "chrome box" was used to manipulate traffic signals
("traffic lights").

####  01FE Does your touch tone phone have 16 DTMF buttons on it?

DTMT is "Dual-Tone Multi-Frequency", and is the mechanism by which
"touch-tone" phones originally operated. The buttons on a phone were arranged
in a grid pattern; consumer phones had four rows and three columns. When
pressed, two tones (corresponding to the row and the column pushed) would
be generated. The telephone switch (the computer responsible for connecting
phones to the phone network) would recognize these tones as numbers and
other symbols and complete the call.

Operator sets (that is, phone keypads used by operators of the telephone
network) had an additional four buttons, meaning sixteen total. These
four buttons produced additional tones that were recognized by telephone
switches and performed special operator-only functions like initiating
free long-distance calls to other stations.

The phone network for many years solely used [in-band
signalling](https://en.wikipedia.org/wiki/In-band_signaling) and as a result,
anyone who could generate the appropriate tones could act as "operators"
on the phone network.

The phone network eventually evolved to not recognize
certain tones on certain lines, meaning that this practice
came to an end. Essentially all telephone networks today use [out-of-band
signalling](https://en.wikipedia.org/wiki/Signaling_%28telecommunications%29#In-band_versus_out-of-band_signaling),
meaning that similar tricks today cannot work.

####  01FF Did the breakup of Ma Bell create more opportunities for you?

"Ma Bell" ("ma" meaning "mother" in this case) was an
affectionate nickname for the [American Telephone and Telegraph
Company](https://en.wikipedia.org/wiki/AT%26T_Corporation), which was the
final corporate identity of the original National Bell Telephone Company
(itself a merger between the Bell Telphone Company and the New England
Telephone and Telegraph Company).

AT&T owned and operated many interlinked regional telephone companies
(referred to as the "Bell System") in the United States and Canada. These
companies together held a practical monopoly on phone service in the United
States and Canada for most of the 20th Century.

In 1974, the United States federal government opened an investigation into
AT&T's monopolistic practices. After a decade in court, AT&T settled with
the government and split itself into seven Regional Bell Operating Companies
(RBOCs), themselves affectionally known as "Baby Bells".

(Funnily enough, four of the original seven Baby Bells were eventually
**re**acquired by AT&T over the course of the 90's and early 2000's.)
