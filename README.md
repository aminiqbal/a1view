# A1View [Windows x64 only]
A viewer for the A1V markdown language [Windows x64 only].

## Showcase
![](https://github.com/aminiqbal/a1view/blob/main/A1VIEW/view/a1view.png)

## Credits
* The web engine used in the application is the Java based port ```(JCEF)``` of the Chromium Embedded Framework (CEF):
  * https://github.com/chromiumembedded/java-cef

* The font used for the editor is ```Cascadia Mono```, a superset of ```Cascadia Code```:
  * https://github.com/microsoft/cascadia-code

* This program was compiled using a ```Java v17.0.1``` OpenJDK distribution packaged by ```BellSoft```:
  * https://bell-sw.com

## About The A1V Format
The __A1V__ format is an extremely simple form of markdown language I came up with. Initially created for personal use, the aim of this format is to provide a convenient way for organized and efficient text-based documentation and note-keeping. Different types of text data are grouped and color coded - keeping the view space clean, and the different data elements easily identifiable.

The end of this document introduces __A1V__ syntax. This information is also included in the file ```A1VGuide.a1v``` file located in a folder named ```info``` in __A1View__'s main directory.

The __A1V__ format is a work in progress, and work is being done on display of mathematical symbols, tables and images - albeit at a very slow pace.

## Program Setup Instructions
* Download the most recent version of the ```A1View.zip``` file from the [__Releases__](https://github.com/aminiqbal/a1view/releases) section.
* Extract the zip file and place the extracted folder named ```A1View``` to a desired location.
  * Recommendation: A location that does not require administrator privilege, for instance:```C:/Users/YourUserName/```
* __Do not__ change the name of the extracted folder or its contents.
* __Do not__ shift the contents _inside_ the extracted folder.
* Open the ```A1View``` folder and right-click ```Install.bat``` file, and select _Run as administrator_. Approve the run, and this will set proper registry values for __A1V__ files to be associated with __A1View__. Alternatively, if you wish to remove __A1View__ and remove its file associations, you are able to execute the ```Uninstall.bat``` file the same way to remove registry values associated with __A1View__ only and disassociate __A1V__ files with the program.
* Now you should be able to launch any file with the ```.a1v``` extension with the program. The folder named ```info``` contains an ```.a1v``` file named ```A1VGuide.a1v``` which highlights basic __A1V__ syntax and which you may open to verify that __A1View__ is working properly.
* The ```.bat``` files only create or remove registry values associated with __A1View__ and will not alter nor compromise your system. You may examine the contents of the ```.bat``` files to verify this.
* Simply edit your ```.a1v``` files with a text editor, and view them using the program. Make sure the file extension is ```.a1v```!

## Troubleshooting
* In case of issues where you have associated ```.a1v``` files with some other program or are unable to open them anymore by just launching the files, simply run ```Uninstall.bat``` and then ```Install.bat``` to reset the program registry values.
* The program __will not launch in and of itself__. The executable either accepts a valid file path as a command line parameter or will launch when a file with extension ```.a1v``` is opened.
* Direct questions/ comments to ```amintwosixfoursix@gmail.com```.

## Program Preferences

* You are able to customize the color scheme by editing the file ```a1viewpref``` that is created when you __first open__ an ```.a1v``` file with __A1View__.
* The ```a1viewpref``` file is located at ```C:/Users/YourUserName/A1View/```
* There are currently __7__ options to edit:
	* ```area-border-color```: Specify the color of the border of __code-blocks__.
	* ```area-color```: Specify the color of the background of __code-blocks__.
	* ```topic-border-color```: Specify the color of the border of __topic heading__.
	* ```topic-color```: Specify the color of the background of __topic heading__.
	* ```defn-color```: Specify the color of the _highlight_ of __highlighted elements__.
	* ```barline-color```: Specify the color of the __horizontal line__.
	* ```main-topic-color```: Specify the color of the __foremost header text__.
* __Only edit__ the digits of the _RGB_ values to correspond to the color you want, if a _R, G or B_ value is less than 100, __prefix 0 to it so that the length of the value is 3__. For example, to set the color of _brick red_, which has values ```R=184, G=42, B=78```, set the field exactly as ```rgb(184, 042, 078)```.
* Preferences will not apply if the aforementioned rule is not followed. It might even mess up __A1V__ rendering. Simply delete the ```a1viewpref``` file and __A1View__ will generate a new one with default values on the next launch.
* You can also change the font by replacing the ```a1font.ttf``` file with another ```.ttf``` font file and simply renaming the font file to ```a1font.ttf```. It would be best to use only __monospaced__ fonts. To reset the font, simply delete the font file and __A1View__ will generate a the default one on the next launch.

## Program Hotkey Controls
* ```Ctrl + Scroll Up``` Increase display zoom level.
* ```Ctrl + Scroll Down``` Decrease display zoom level.
* ```Ctrl + 0``` Reset the display zoom level.


# A1View Syntax

* A line starting with an ```~``` followed by a ```SPACE``` is interpreted as a heading.

* A line starting with an ```@``` followed by a ```SPACE``` is interpreted as a topic heading.

* Characters in a line enclosed within ```[[``` and ```]]``` are highlighted.

* Insert a ``` ` ``` followed by a ```SPACE``` to display a __bullet point__ ```•```. The bullet point will always be followed by a ```SPACE```, so you don't need to insert another one.

* Writing is intuitive:

	* Press ```ENTER``` for a new line, up to as many as you need.
		* A ```TAB``` character will indent regular text blocks upto four levels. This will continue upto ```END OF LINE```.
		Hence, for indentation of consequent lines, a ```TAB``` character should preceed any other text on those lines.

	* __Embolden__ text by enclosing the text within ```@B{text}```

	* _Italicize_ text by enclosing the text within ```@I{text}```

	* <u>Underline</u> text by enclosing the text within ```@U{text}```
	
	* The 3 aformentioned items can be nested along with highlight syntax to produce all 4 effects: ```[[@I{@U{@B{text}}}]]```

	* A line consisting _only_ of ```/--/``` will produce a horizontal line.

	* Insert a specific character using its unicode number. For example, ```\000025EE\``` will translate to ```◮```.
		* The unicode number __must be exactly 8 characters in length, and contain only digits and uppercase alphabets__. Unicode numbers shorter than 8 characters should be __prefixed with zeroes__ to make it that length.

	* Insert a __space__ using ```@/```. This way, more than 1 space can be consecutively inserted in text.

* It might be necessary to sometimes display A1V syntax as is. To prevent the program from parsing a syntax element, the padding element ```@{}``` is used in between the syntax element to essentially invalidate it. For example, in order to write out ```[[```, the circumvention would be ```@{}[@{}[@{}```.
* Note that the aforementioned features will only function as long as the text is not within a __code-block__.
* __Code-blocks__ are defined by beginning the block with ```[[``` on a line by itself, and ending the block by ```]]``` on a line by itself:
* Even if your general text is indented, the code-block __should not be__. The code-block will automatically follow indentation up to __4 levels__.
