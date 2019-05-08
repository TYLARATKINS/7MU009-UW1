# 7MU009-UW1
MAXMSP VOCODER ASSIGNMENT

![alttext](https://i.gyazo.com/3941a2009a2bdbc12dbe11503ec9b1ea.png)

Video Demo of Vocoder: https://youtu.be/nNvoi7yH0NQ

Video of How Vocoder Works: https://youtu.be/72ItGXn5fJc

1.	Research & Development

The purpose of this project is to create an innovative software tool to enable the user to manipulate their voice through the use of digital synthesis. The initial idea for research and development is a vocoder, Roland (2019) outlines a vocoder as a synthesiser that produces sounds through analysis of speech. Max MSP is used to create this project due to its flexibility; inclusion of DSP orientated features alongside its user friendly development structure provides a user friendly development platform. One of the many benefits to this selection of software allows for future developers to further progress and expand upon this project to suit their needs. The initial idea of the project sketched out on paper looked like this...

![alttext](https://i.gyazo.com/f3d245a7cc5afdc6a1741a6b38b331b8.png)

1.1.	Pfft Creation

T. Carney (2012) outlines that a vocoder works by taking spectral characteristics of speech and imprinting them onto a tone, such as a sine wave through the use of a Fourier Transform. C. Zhu (2014) defines an FFT as one of the most useful tools in digital signal processing, providing analysis of amplitude variants in the frequency domain. In order to create a working vocoder, the use of FFT to define amplitude characteristics of speech in the frequency domain will allow this data to be applied to a tone. In relation to Max MSP a sub-patch will be created and called upon through the use of the [Pfft~] object, the sub-patch will define the analysis and conversion of amplitudes to the frequency domain that will then be applied to the tone generated from the synthesiser. Each [Fftin~] object run into a [Cartopol~] object which plots coordinates into frequency information as the [Fftin~] object does not do this alone. Each [Cartopol~] object run in parallel into a multiplication object, which multiplies amplitude in the frequency domain, alongside the phase of each input. The [Poltocar~] object is then used to convert the input information into a signal pair, that then runs into [Fftout~] which outputs this information to [Pfft~].

![alttext](https://i.gyazo.com/82cc81991a108cfa4064f1b9c04588ac.png)

1.2.	Pfft Implementation with Sine Wave

The next step in this process is to apply the information collected through the [Pfft~] sub-patch to a synthesised waveform, this is done through the use of the following patch. 

![alttext](https://i.gyazo.com/fc723dd02259c482c91bb59a05458023.png)
 
A Keyslider object is used to output midi information into an [Mtof] object which converts midi information into a frequency. This frequency information is then fed into a [Cycle~] object which generates a sine wave at a reference point of 440Hz. The [Zerox~] object that feeds into the two mathematical definitions attenuates the amplitude and natural harmonics of the human voice, to further compliment the vocoder alongside the [Noise~] object which compliments the output with noise. Each of these objects are fed through a [Selector~] object and run back into the [Pfft~] sub-patch. 

1.1.	Vocoder with Sample Loader

![alttext](https://i.gyazo.com/2f0386765644296892e466e19404fe61.png)
 
The addition of a sampler was included to ensure the user could manipulate a waveform without the use of a microphone if they did not have one. This was done using two messages [open] and [loop 1] and the [sfplay~] object. The [open] message prompts the user to select a file of their chose to play using [sfplay~] and the [loop 1] message will loop the waveform. This feature was added to ensure this tool is as user friendly as possible. 

1.2.	Vocoder with Polyphony and Waveform Selector

![alttext](https://i.gyazo.com/93cf34cbeb0275fc613f33bfae3a6c03.png)

The next step in the project is to add an option to allow the user to select different waveforms for the vocoder. This is done through the use of a drop down menu that contains sine, saw, square and triangle waveforms, that are fed into a [Selector~] object. This selection of objects are duplicated and placed into the [Pfft~] three times to allow for three voices to be used with the vocoder, this gives the user the ability to use polyphony. 

1.3.	Vocoder with Midi and Chords

After further testing of the project, it is determined that an interesting addition to the vocoder would be to enable the program to play chords using only a single note input. Zebrakeys (2006) outlines the basis of playing major chords on a piano using +2 and +4 spacing between notes, for several of the basic chords. This idea is implemented through the use of the [Notein] object placed three times, routing out into a number display object, applying [+2] to voice 2 and [+4] to voice 3, allowing major chords to be played using a single note input. 

![alttext](https://i.gyazo.com/ccefc22d5589e8efcd8ecdb9cf67eb1a.png)
 
2.	Conclusion

Upon completion of the project, the patch window is cleared up, wires are aligned and key notes are placed accordingly throughout the patch window to allow for future developers to gain an understanding of how the project works at first glance. 

![alttext](https://i.gyazo.com/43c8e5fdda7c8dcaf2766e8b117d1334.png)
 
The project is then organised and placed into presentation mode to provide a more user friendly interface with key points and features displayed across the UI. The initial designs for the presentation mode looked like this...

![alttext](https://i.gyazo.com/a71b03c7a2bdbcbf3351a0f34bb1a0e2.png)

The image used as a background is created in Microsoft Paint and compliments the playful yet advanced technicality of the software.

![alttext](https://i.gyazo.com/3941a2009a2bdbc12dbe11503ec9b1ea.png)
 
At the point of submission, the vocoder works as intended by providing the user with the ability to manipulate their voice using synthesis alongside the ability to manipulate samples in the same way. The software has a multitude of different waveforms to choose from alongside control of what is let through the output. The software also allows the user to input their data using a midi keyboard to ‘play their voice’, which was the overall aim of this project. In reflection, the project could be improved if given more time, through the addition of an ADSR, Reverb, Delay and other effects alongside the ability to play different types of chords. Further ideas for improvement would include more variables to manipulate alongside the inclusion of an arpeggiator. In result, the software works as intended and the overall aims of this project have been achieved. 

3.	References

Roland. (2019). What Is a Vocoder?. Available: http://www.roland.co.uk/blog/what-is-a-vocoder/. Last accessed 12/04/2019.

Zebrakeys. (2006). Playing the Major Chord. Available: http://www.zebrakeys.com/lessons/beginner/chords/?id=9. Last accessed 13/04/2019.

T. Carney. (2012). The Vocoder. Available: https://ses.library.usyd.edu.au/bitstream/2123/8296/2/311107435%20Technology%20Review%20-%20Vocoder.pdf. Last accessed 13/04/2019.

C. Zhu. (2014). Frequency domain analysis. Available: https://www.sciencedirect.com/topics/engineering/fast-fourier-transform. Last accessed 13/04/2019.
