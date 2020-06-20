"# Helios-Arduino-Synth-V3" 

Let's add a low pass filter to our synth!

Text taken from;

https://bloghoskins.blogspot.com/2020/06/helios-one-arduino-synth-part-3.html

So in the third part of the tutorial for our little synth, we'll add a LPF.  We'll use two B10k pots, one for the Cut-off and one for the the resonance.  The cut-off pot also has a 220 ohm resistor on it's ground lug. 

The code...

Hopefully it should all be self-explanatory in the comments of the code.  The Arduino analog pots return a value of 0 - 1023, but the mozzi filter only needs a value of 0 - 255.  Originally I converted this using the map function, but then after reading through Arduino for Musicians by Brent Edstrom, I saw that it was quicker/less resource intensive to bit-shift the sum  &gt;&gt;2.  The original map function is still in the code (commented out)...  I think I could hear an audible difference but I could just be going mad (the bit shift version was smoother?).  Feel free to give it a try.

The part I struggled with was the updateAudio function... somehow you had to pass the output of the oscillator into the filter.  I did this by wrapping the original code into a new char, then passing that into the filter. Take a look at the code, or even better compare it to the old V2 code.  Playing with the mozzie examples, the Arduino book, and various other examples on the web, I managed to get it to work, but it would distort/cut out. So I added a resistor on the Cut-off pot, and also increased the bit shifting on the updateAudio function from 8 to 10.  It's a bit quieter now, but still usable.  We might end up adding an amp on the output to boost the signal, but we'll wait and see until it's finished.

Hopefully I shall have time to create part 4 soon...  but I haven't actually figured out what to add and we're running out of analog inputs (our last two!).  I think maybe an LFO...

Thanks!

Part 2;
https://bloghoskins.blogspot.com/2020/06/helios-one-arduino-synth-part-2.html

Part 1;
http://bloghoskins.blogspot.com/2019/07/helios-one-arduino-synth-part-1.html



