pi-bowl
=======

A Python (Tkinter, RPi.GPIO) program for running a scholars bowl buzzer hub from a Raspberry Pi, managing timing, scoring, and buzzer lockout.

More specifically, this program allows a Raspberry Pi to replace a commercial buzzer hub.  If you make your own buzzer devices (just a button closing a circuit), you can save hundreds of dollars by not purchasing a buzzer system at all.

The rules by which the program operates are found at http://www.kshsaa.org/Publications/ScholarsBowl.pdf (Section I).  These rules may differ in other states and countries.

The program interfaces directly to the Pi's IO pins.  I used a floppy drive ribbon cable to attach the required pins to the buzzer connectors, which all connect to the Pi's ground pin.  The buzzer connectors I mounted into a small box, to look similar to a commercial buzzer hub.  I did not use a Pi-face, or any other Pi addon.

The program needs super user privileges to manage the IO pins.


Features in common with commercial buzzer systems include:
Support for 10 buzzers split into 2 teams of 5
Sound and lockout on buzz-ins
Allows for a simple clear-buzzer functionality, disconnected to any scoring or timing system.  (Though using it in this manner defeats the whole purpose)


Features going beyond those of a commercial system include:
Automatic lockout at time
Customizable buzz-in sounds (default is a frog and a peacock)
Score recording, including a scrolling history and summed total
A countdown visible to the competing teams.  This is controversial, as such a feature is not addressed in the kshsaa rules, and significantly changes the gameplay.
Efficient handling of question interruptions
Simple mistake correction, including score modification within the history, near interrupts, false timer starts, and switching question.
Easy time limit modification in 5 second increments
Automatic timing, requiring only that the timer be started when the moderator finishes reading the question.  After, the timer will be paused on buzz-in, plus 5 and resumed on the first incorrect answer, and reset to ten seconds at the conclusion of the question.
Enables a location to be run by two individuals (judge and pi moderator) rather than four or five (judge, moderator, timer, scorer, and buzzer operator).
Virtualized testing.  In other words, you can modify and test the program on any computer, and by pressing the on-screen buttons, can simulate a buzzer press without having any actual buzzers.  This is very handy for debugging.
        


Disadvantages to a commercial buzzer system:
More complicated setup, requiring the pi be hooked up to power, video, powered sound, keyboard, and mouse.  This means a lot more wires, and more opportunity for technical disasters.  I have only run one high school meet with the pi-bowl, but there were no major glitches.
Less intuitive operation.
        

Bugs/TODO (Since the program is entirely functional for its intended use, I will not work at this list unless someone requests it):
I recently learned Python and know that I am inconsistent in my naming conventions, and possibly in other conventions that I am not yet aware of.  For example, no classes are used, and the code is entirely contained in the one file.  I don't know how much of this I will change.
Finish the configuration panel, which currently does nothing.
Layout is currently messy and somewhat disorganized.  Some buttons and labels are not entirely visible
Program must be restarted to clear scores.
Possibly allow for a longer visible score history.  The motive against this is that a team member who does not do well in a round could become more discouraged at individual failures rather than celebrate group success.
The program uses the system command "aplay soundfile.wav", which is linux-specific.  I don't think this is too much of an issue, given that it is intended to run on a Pi.  If there is a better/faster solution to sounds in Python, I will use it.
Tkinter lags just a little on the Pi.  I don't know if this is a programming fault, or just the limitations of the Pi.
Absolute paths used for sounds instead of relative.
Many debugging comments left in.





