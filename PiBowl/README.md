pi-bowl
=======

A Python (Tkinter, RPi.GPIO) program for running a scholars bowl buzzer hub from a Raspberry Pi, managing timing, scoring, buzzer lockout, and player recognition.

More specifically, this program allows a Raspberry Pi to replace a commercial buzzer hub, while being magnitudes more useful  If you make your own buzzer devices (just a button closing a circuit), you can save hundreds of dollars by not purchasing a buzzer system at all.

The rules by which the program operates are found at http://www.kshsaa.org/Publications/ScholarsBowl.pdf (Section I).  These rules may differ in other states and countries.  Note that the rules are not explicit about revealing the time remaining to the contestants.

The program interfaces directly to the Pi's IO pins.  I used a floppy drive ribbon cable to attach the required pins to the buzzer connectors, which all connect to the Pi's ground pin.  The buzzer connectors I mounted into a small box, to look similar to a commercial buzzer hub.  I did not use a Pi-face, or any other Pi addon.

The program needs super user privileges to manage the IO pins.


Features in common with commercial buzzer systems include:
1. Support for 10 buzzers split into 2 teams of 5.
2. Player Recognition and lockout on buzz-ins.
3. Allows for a simple clear-buzzer functionality, disconnected to any scoring or timing system.  (One would only use it in this manner when testing buzzers, or when following very different rules).


Features going beyond those of a commercial system include:
1. Automatic lockout when time is called.
2. Either immediate player recognition on buzzin (espeak 'Green 1'), or customizable buzzin sounds (frog, peacock).
3. Score recording, including a scrolling history and summed total.
4. A countdown visible to the competing teams.  This is controversial, as such a feature is not addressed in the kshsaa rules, and significantly changes the gameplay, leading to more last-second guesses.
5. Efficient handling of question interruptions.
6. Simple mistake correction, including score modification within the history, near interrupts, false timer starts, and switching questions.
7. Easy time limit modification by 5 second increments.
8. Automatic timing, requiring only that the timer be started when the moderator finishes reading the question.  After, the timer will be paused on buzz-in, plus 5 and resumed on the first incorrect answer, and reset to ten seconds at the conclusion of the question.
9. Enables a location to be run by two individuals (judge and pi moderator) rather than four or five (judge, moderator, timer, scorer, and buzzer operator).  I have done this at both a high school and junior high meet.
10. Virtualized testing.  In other words, you can modify and test the program on any computer, and by pressing the on-screen buttons, can simulate a buzzer press without having any actual buzzers or a raspberry pi.  This is very handy for debugging.  Remember to set VIRTUALIZED=False to enable buzzer devices.
        

Disadvantages of this over a commercial buzzer system:
1. More complicated setup, requiring the pi be hooked up to power, video, powered sound, keyboard, and mouse.  This means a lot more wires, and more opportunity for technical disasters.  I have run two official meets with the pi-bowl, and there were no major glitches that the system could not easily correct.
2. Less intuitive operation, though familiarity with the rules and a little experimentation will quicken understanding.
        

Bugs/TODO (Since the program is entirely functional for its intended use, I will not work at this list unless someone requests it):
1. I recently learned Python and know that I am inconsistent in my naming conventions, and possibly in other conventions that I am not yet aware of.  For example, no classes are used, and the code is entirely contained in the one file.  I don't know how much of this I will change.
2. Finish the configuration panel, which currently does nothing.
3. Layout is currently messy and somewhat disorganized.  Some buttons and labels are not entirely visible, or aesthetically placed.
4. Program must be restarted to clear scores.
5. Possibly allow for a longer visible score history.  The motive against this is that a team member who does not do well in a round could become more discouraged at individual failures rather than celebrate group success.
6. The program uses the system command "aplay soundfile.wav", which is linux-specific.  I don't think this is too much of an issue, given that it is intended to run on a Pi.  If there is a better/faster solution to sounds in Python, I will use it.
7. Tkinter lags just a little on the Pi.  I don't know if this is a programming fault, or just the limitations of the Pi or Tkinter.
8. Paths used for sounds files are not consistent (some absolute, some relative). The program should thus be run in the containing directory, and the file paths modified in PiBowl.py to reflect their location.
9. Many debugging comments left in.  I am not a very neat programmer
