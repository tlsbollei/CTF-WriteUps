

```yaml
Someone sent me this weird file and I don't understand it.
It's freaking me out, this isn't a game! Please help me figure out what's in this file.
```

link to .txt file :
https://files.sunshinectf.org/forensics/golly_gee_willikers.txt

Only the first line seems to be unique. 
```yaml
x = 0, y = 0, rule = B3/S23
```

A simple google search of the unique phrase gives us the following results : 

```yaml
Life-like cellular automaton
https://en.wikipedia.org/wiki/Life-like_cellular_automaton
...Conway's Game of Life is denoted B3/S23....
```

!!Upon more research we stumble upon the following information : 
```yaml
The Run Length Encoded (or RLE for short) file format is commonly-used for storing patterns.
The first line is a header line, which has the form :

x = m, y = n

where m and n are the width and height of the pattern, respectively.
```
!!!The important thing we find here is this :
```yaml
Anything after the final ! is ignored.
It used to be common to put comments here (starting on a new line), but the usual method for adding comments is now by means of #C lines (see below).
```

Now we just need to find a website where we can import this template.
Below is example of one site.
```yaml
https://copy.sh/life/
```

Upon importing the .txt file contents onto the website, this is the result we get :

![screenshot](https://raw.githubusercontent.com/tlsbollei/CTF-Writeups/refs/heads/main/images/supa.png)

It`s just a bunch of characters, but theres no flag to be seen. 

The key to finding the flag lies in the important note that we have observed - 
```yaml
Anything after the final ! is ignored.
```

There are exactly two "!" symbols in the .txt file. Remove them, import the .txt with the exclamation marks and this is the result :

![screenshot](https://raw.githubusercontent.com/tlsbollei/CTF-Writeups/refs/heads/main/images/supa2.png)

flag :
```sun{th1s_w0nt_last}```
