Our First Eight Colors

By combining different amounts of red, green, and blue lights, you can get any color you like. In computer colors, think of it like three knobs, and each knob controls one of the three colors.

Example

Let’s say that each of the three colors can be either on or off, i.e., each has two states.

    The red light can be either on or off
    The green light can be either on or off
    The blue light can be either on or off

These states give us 2 × 2 × 2 = 8, that’s eight different colors.

3 circles (red, green, and blue) overlapping.

If a computer were limited to 8 colors, it would only need to indicate which color is “switched on” and which is “switched off.” In fact, it can use three digits of 1 and 0 to represent the states of red, green, and blue. For example, 111 would be all 3 lights switched on, while 100 would be only the red switched on. This digit, which can be either 1 or 0, is called a bit.

Now, a computer can represent any of the 8 colors. If this is still unclear, a detailed list is shown in the table below.
Color Representation 	Representation Meaning 	Color Name
000 	All colors are off 	Black
001 	Only blue is on 	Blue
010 	Only green is on 	Green
100 	Only red is on 	Red
011 	Green and blue are on 	Cyan
101 	Red and blue are on 	Magenta
110 	Red and green are on 	Yellow
111 	All colors are on 	White

We just provided a way to represent a color in a palette of 8 colors.
From 8 to 16,000,000

Being limited to eight colors is inconvenient, as we prefer millions of colors. It would be convenient if each of the 3 lights (red, green, and blue) had 256 levels instead of just 2 (on or off). Let’s repeat the same math as earlier: 256 × 256 × 256 = 16,777,216. That’s more than 16 million colors; that covers most of our needs.

One bit is enough to represent 2 states: on and off. We need 8 bits to express 256 states. In most textbooks, a group of 8 bits is referred to as a byte; however, you can also use the term octet.

Putting all this together, you would realise that a color is now represented as 3 × 8 bits, or 3 bytes (24 bits). For example, one green color used on this page is represented as 10100011 11101010 00101010; that’s not a very convenient way to type or read color codes. Here comes the hexadecimal representation to the rescue!
Hexadecimal Representation

Hexadecimal representation makes it easy to combine 4 bits into a single character, a hexadecimal digit, to be specific. For now, please think of the hexadecimal digits as symbols where each symbol represents a set of 4 bits. We will revisit hexadecimal numbers in Task 3.
Hexadecimal Digit 	Binary Representation
0 	0000
1 	0001
2 	0010
3 	0011
4 	0100
5 	0101
6 	0110
7 	0111
8 	1000
9 	1001
A 	1010
B 	1011
C 	1100
D 	1101
E 	1110
F 	1111

Going back to the green color, instead of typing 10100011 11101010 00101010, we can type A3EA2A. In fact, that’s how you specify the color in graphics programs. For your convenience, the attached static site helps you convert a hex color into its binary and decimal representations, along with a color preview.

Color representation in binary, decimal, and hexadecimal systems.

To summarise what we have covered so far:

    In real-life applications, a color is represented in 24 bits, i.e., 3 bytes
    Each byte can represent 256 different values
    Each of the three bytes specifies the intensity of the red, green, and blue lights
    Every 4 bits are represented by one hexadecimal digit
    Each byte is represented as two hexadecimal digits


Our First Eight Colors

By combining different amounts of red, green, and blue lights, you can get any color you like. In computer colors, think of it like three knobs, and each knob controls one of the three colors.

Example

Let’s say that each of the three colors can be either on or off, i.e., each has two states.

    The red light can be either on or off
    The green light can be either on or off
    The blue light can be either on or off

These states give us 2 × 2 × 2 = 8, that’s eight different colors.

3 circles (red, green, and blue) overlapping.

If a computer were limited to 8 colors, it would only need to indicate which color is “switched on” and which is “switched off.” In fact, it can use three digits of 1 and 0 to represent the states of red, green, and blue. For example, 111 would be all 3 lights switched on, while 100 would be only the red switched on. This digit, which can be either 1 or 0, is called a bit.

Now, a computer can represent any of the 8 colors. If this is still unclear, a detailed list is shown in the table below.
Color Representation 	Representation Meaning 	Color Name
000 	All colors are off 	Black
001 	Only blue is on 	Blue
010 	Only green is on 	Green
100 	Only red is on 	Red
011 	Green and blue are on 	Cyan
101 	Red and blue are on 	Magenta
110 	Red and green are on 	Yellow
111 	All colors are on 	White

We just provided a way to represent a color in a palette of 8 colors.
From 8 to 16,000,000

Being limited to eight colors is inconvenient, as we prefer millions of colors. It would be convenient if each of the 3 lights (red, green, and blue) had 256 levels instead of just 2 (on or off). Let’s repeat the same math as earlier: 256 × 256 × 256 = 16,777,216. That’s more than 16 million colors; that covers most of our needs.

One bit is enough to represent 2 states: on and off. We need 8 bits to express 256 states. In most textbooks, a group of 8 bits is referred to as a byte; however, you can also use the term octet.

Putting all this together, you would realise that a color is now represented as 3 × 8 bits, or 3 bytes (24 bits). For example, one green color used on this page is represented as 10100011 11101010 00101010; that’s not a very convenient way to type or read color codes. Here comes the hexadecimal representation to the rescue!
Hexadecimal Representation

Hexadecimal representation makes it easy to combine 4 bits into a single character, a hexadecimal digit, to be specific. For now, please think of the hexadecimal digits as symbols where each symbol represents a set of 4 bits. We will revisit hexadecimal numbers in Task 3.
Hexadecimal Digit 	Binary Representation
0 	0000
1 	0001
2 	0010
3 	0011
4 	0100
5 	0101
6 	0110
7 	0111
8 	1000
9 	1001
A 	1010
B 	1011
C 	1100
D 	1101
E 	1110
F 	1111

Going back to the green color, instead of typing 10100011 11101010 00101010, we can type A3EA2A. In fact, that’s how you specify the color in graphics programs. For your convenience, the attached static site helps you convert a hex color into its binary and decimal representations, along with a color preview.

Color representation in binary, decimal, and hexadecimal systems.

To summarise what we have covered so far:

    In real-life applications, a color is represented in 24 bits, i.e., 3 bytes
    Each byte can represent 256 different values
    Each of the three bytes specifies the intensity of the red, green, and blue lights
    Every 4 bits are represented by one hexadecimal digit
    Each byte is represented as two hexadecimal digits


# DATA ENCODING

We already learned that digital computers only understand zeroes and ones. Starting from 0 and 1, how can we save and display text? For example, how can we save the text “TryHackMe” in a file? What will such a file contain?

To be able to answer this, we need to agree on what bits represent T, what bits represent r, what bits represent y, and so on. Let’s say that we all agree to represent T with the following stream of bits: 01010100. Then all computer systems should store T the same way, and later, when a computer encounters 01010100, it will recognize it as T. Of course, we need to do this for all letters in the alphabet, digits, and special characters. This approach requires a standard that computer manufacturers, designers, and programmers agree to adhere to. One of the earliest standards for English letters was ASCII.

ASCII stands for American Standard Code for Information Interchange, and it is an early character encoding from 1963 that uses numbers 0-127 to represent English letters, digits, punctuation, and some control characters. Remember that A stands for American, as this will come in handy later. As you might have noticed, the original ASCII was limited to seven bits. ASCII acts as a small bilingual dictionary between text and numeric codes. Consider the following samples from the original ASCII table. Since the table has 128 entries, we only made a brief selection to give you an idea of how things are represented in ASCII.
Decimal 	Hexadecimal 	Binary 	Symbol 	Description
… 	… 	… 	… 	…
48 	30 	00110000 	0 	Zero
… 	… 	… 	… 	…
57 	39 	00111001 	9 	Nine
… 	… 	… 	… 	…
65 	41 	01000001 	A 	Uppercase A
… 	… 	… 	… 	…
88 	58 	01011000 	X 	Uppercase X
89 	59 	01011001 	Y 	Uppercase Y
90 	5A 	01011010 	Z 	Uppercase Z
91 	5B 	01011011 	[ 	Opening bracket
92 	5C 	01011100 	\ 	Backslash
93 	5D 	01011101 	] 	Closing bracket
94 	5E 	01011110 	^ 	Caret - circumflex
95 	5F 	01011111 	_ 	Underscore
96 	60 	01100000 	` 	Grave accent
97 	61 	01100001 	a 	Lowercase a
98 	62 	01100010 	b 	Lowercase b
99 	63 	01100011 	c 	Lowercase c
… 	… 	… 	… 	…
122 	7A 	01111010 	z 	Lowercase z
… 	… 	… 	… 	…
127 	7F 	01111111 	DEL 	Delete

There are several things that you can observe. First, letters are in order. If you know the hexadecimal or decimal number for b, you can figure out the decimal number of a, c, and later lower-case letters. For example, a, b, and c are assigned the hexadecimal numbers 61, 62, and 63, respectively. Same for upper-case letters A to Z and digits 0 to 9. When using ASCII encoding, a computer system reads 41 in a file and displays A on the screen; when it reads 42, it displays B, and so on.

Secondly, each character has its own ASCII, for example, [ is represented by the hexadecimal number 5B.
“TryHackMe” in ASCII

Let’s say you open a text file, write “TryHackMe” and save it as file.txt. How will the file look on the bit level? Let’s find out.

If you are interested in seeing the storage on the disk, bit by bit, and assuming that it is using ASCII, you will see something similar to the following:

01010100 01110010 01111001 01001000 01100001 01100011 01101011 01001101 01100101 00001010

Obviously, this is not readable by any human being. These are the exact binary representations of all the letters in “TryHackMe” followed by a new line. When you open this file, your editor will read these bits and display the following characters: T r y H a c k M e \n; the \n is a new line that you get when you hit the Enter key.

Because reading binary numbers is cumbersome and error-prone for us, we prefer to use hexadecimal digits. As you remember from the previous room, we group 4 bits into a single hexadecimal digit. Our file looks like this in hexadecimal: 54 72 79 48 61 63 6b 4d 65 0a

And if you want to look up the decimal representation, it would be as follows: 124 162 171 110 141 143 153 115 145 012; however, it is uncommon to use decimal digits. It is more common to use hexadecimal digits when we want to show the bits.

You can use the attached static site yourself to experiment more.
European Languages

ASCII provided a way to encode the English alphabet; however, we need an encoding to support other European languages such as Spanish (ñ, ¿), German (ß, ü), Polish (ł, ń), Czech (č, ř), and Romanian (ș, ț), to name a few. ASCII uses 7 bits, and with an eighth bit, we get 128 more characters to cover. However, the reality is more challenging; the additional 128 characters are not enough to cover all the letters of the European languages. The ISO/IEC 8859 Series (International Standards) created several standards; each standard covered a set of languages:

    ISO-8859-1 (Latin-1): Covered Western European languages like German (ß, ü), French (é, ç), Spanish (ñ, ¿), Italian, Portuguese, Catalan, and Nordic languages (e.g., Icelandic ð/Ð). Check this link.
    ISO-8859-2 (Latin-2): Supported Central/Eastern European languages like Polish (ł, ń), Czech (č, ř), Hungarian (ő, ű), Croatian (đ), Romanian (ș, ț), and Slovak. Check this link.

In other words, if your document is saved using ISO-8859-1 and later read and displayed as if it were saved using ISO-8859-2, non-English letters are likely to be displayed differently

## unicode

We learned that ASCII is a 7-bit standard that defines 128 characters covering English letters, digits, and basic punctuation. We also noticed how ASCII, with its seven bits, didn’t have room for characters such as ñ, €, あ, or ب. Using eight bits, extended ASCII tried patching this with regional variants (ISO-8859-1, ISO-8859-2, Windows-1252, among many others), but this caused chaos! For example, if the sender writes and saves Ø using ISO 8859-1 (Latin 1) encoding and the recipient opens and reads the document using ISO 8859-2 (Latin 2) encoding, they will see Ř. Hence, it is clear how opening a document requires us to use the same encoding used when saving it; otherwise, various characters will not be displayed correctly, or even more confusingly, they might be incorrectly replaced.

Unlike English, which has 26 letters and needs 52 characters to cover upper-case and lower-case letters, Arabic needs more than 250 characters to cover its various ligatures and diacritics. Moreover, the number escalates rapidly when considering Japanese and Chinese. In Japanese, 2,136 Kanji (logographic characters) are considered daily-use characters, as mandated by Japan’s Ministry of Education. In fact, the JIS X 0208 standard defines 6,879 characters. In Chinese, educated natives recognize around 8,000 characters. Furthermore, the GB 18030-2022 defines more than 87,887 Hanzi (Chinese characters). And still, we have not considered encoding emoticons (emoji).

In other words, it is essential for both the sender and the recipient to use the same encoding; moreover, we need an encoding that can include all the characters from all languages. This situation brings us to Unicode.

Unicode is a universal character encoding standard. It assigns unique code points to characters from all modern and historical writing systems worldwide. Unicode supports the interchange, processing, and display of text in diverse languages. In other words, we don’t need to worry about picking a specific encoding standard that is compatible with the language we are using. Furthermore, this makes it easy to use different languages in a single file or message. And most importantly, because this is a standard that fits all, we don’t need to worry about the encoding used by the original author, as they will also be using Unicode.

Unicode is a character set standard that assigns a unique number to every character across all languages. Examples:

    U+0041 = Latin “A”
    U+03A9 = Greek “Ω”
    U+3042 = Japanese Hiragana “あ”

Unicode 17.0 is currently the latest version of the Unicode Standard. It defines close to 157 thousand characters, almost 4,000 of them are emoji sequences.
UTF-8, UTF-16, and UTF-32

Because you will encounter UTF-8, UTF-16, and UTF-32, we will briefly cover them without going into too much depth. What you need to know is that UTF-8 is very common on the modern web. It encodes Unicode points into 1 to 4 bytes dynamically. In other words, it decides on the number of bytes based on the character complexity. ASCII characters (U+0000 to U+007F) use exactly 1 byte, identical to the original ASCII, ensuring seamless backward compatibility. Non-ASCII characters like Ω (U+03A9) use 2 bytes, while complex scripts or emoji like 🔥 (U+1F525) require 4 bytes. This flexibility allows us to cover the Unicode standard without wasting bytes.

UTF-16 takes a different path; it uses either 2 or 4 bytes per character. Common characters, like most Latin, Cyrillic, or Chinese Hanzi, fit in 2 bytes; however, rarer ones, like emoji or ancient scripts, require a pair, i.e., two 16-bit units totaling 4 bytes. For example, the letter A is encoded as U+0041, while the emoji 🔥 needs two and is encoded as U+D83D U+DD25.

Finally, UTF-32 is the simplest but also the most wasteful; every Unicode code point uses exactly 4 bytes. For example, A is encoded as U+00000041 and 🔥 is encoded as U+0001F525.

Let’s explore a few more examples:

    龍: One of the Chinese characters that appear on offensive Linux distributions, such as Kali, is “龍”, 
    
    which means “dragon”. In Unicode, it is U+9F8D or U+00009F8D, depending on whether it is UTF-16 or UTF-32.
    😊: This smiley face is nothing more than U+0001F60A in UTF-32 for a computer; that’s literally 0000 0000 0000 0001 1111 0110 0000 1010.
    ツ: The Japanese letter “tsu” which some people use as a smiley face in some regions outside Japan; it has the code U+30C4 or U+000030C4 depending on whether it is UTF-16 or UTF-32.
    ت is the Arabic letter “taa,” and some people use it as a smiley outside the Arab world; it looks close enough to a smiley face. From a Unicode perspective, that’s U+062A.
    ♞: The black knight in chess uses the Unicode U+265E; in other words, the computer reads 0010 0110 0101 1110 and shows you a black knight, thanks to Unicode.

We have created a static site to help you look up characters and explore new ones available in most standard fonts.


# python

The program needs to start by picking a random secret number between 1 and 20. Then the user will begin making a guess after another till they get it right. This approach requires two variables: secret and guess. We can also track the number of tries (attempts) it took the user to find the number; for this, we will use the variable tries.

Python offers the random.randint() method, which returns a random integer within the specified bounds. For example, random.randint(1, 20) returns a random number between 1 and 20. Since the user has not made any attempts, we set tries to 0; moreover, we set guess to a value outside the valid range. To tell the user that the program picked a number, we use Python’s print() method to display an informational message on the screen. We show the current Python script below:

import random  # gives us tools for picking random numbers

secret = random.randint(1, 20)  # a <= secret <= b
tries = 0
guess = 0  # start with a value that cannot be the secret (since secret is 1..20)

print("I'm thinking of a number between 1 and 20")

This code snippet achieves the following:

    Use the random.randint() method from the random library to pick a random number between 1 and 20 and save it to secret.
    Creates two variables, tries and guess, and sets them to 0.
    Display a message on the screen to inform the user that a number has been picked.

With our variables ready, we prompt the user to make a guess and set guess accordingly. We begin by saving the user’s input to a temporary text variable, then use Python’s int() to convert it to an integer. Furthermore, we need to increment tries each time the user makes a guess.

text = input("Take a guess: ")  # input() returns text (a string)
guess = int(text)  # convert the text to a number

tries = tries + 1  # add 1 try (written long-form for clarity)

So far, our program does the following:

    Pick a random number between 1 and 20 and save it in secret.
    Ask the user to take a guess, convert it to an integer, and save it in guess.
    Increment tries by 1.

To check whether the user made a correct guess, we should be able to compare against various cases; this requires conditional statements and comparison operators.
The Incomplete Draft

In this task, we built a basic program that you can test for yourself and edit in the attached VM. Although this program picks a random number and reads the user’s input, it does not compare the two, which makes it practically useless as a game. In the next task, we upgrade this program so that it gives the user some feedback on how their guess compares to the secret number. The program below is saved as guess_v1.py in the /home/ubuntu/Python-Demo directory.

import random  # gives us tools for picking random numbers

secret = random.randint(1, 20)  # a <= secret <= b
tries = 0
guess = 0  # start with a value that cannot be the secret (since secret is 1..20)

print("I'm thinking of a number between 1 and 20")

text = input("Take a guess: ")  # input() returns text (a string)
guess = int(text)  # convert the text to a number


Next, we compare the user’s guess to the secret number and give a helpful hint: whether it is out of range, too low, too high, or if they got it right. It is like asking ourselves, “Is the number less than 1 or greater than 20?” If the answer is yes, we tell the user that the number is out of range. If the answer is no, we pose a second question: “Is the user’s guess less than the secret number?” If the answer is yes, we tell the user that the guess is too low. Let’s rephrase this in pseudo-code, i.e., English language that is closer to the programming language.

    If the guess is less than 1 or greater than 20, print “Out of range.” (If this is not the case, proceed to the next step.)
    Else if the guess is less than the secret number, print “Too low.” (If this is not the case, proceed to the next step.)
    Else if the guess is larger than the secret number, print “Too high.” (If this is not the case, proceed to the next step.)
    Else print “You got it.”

By reflecting on the above steps, it is only logical that if the guess is not less than or larger than the secret number, it would be equal to the secret number. In programming, whenever the condition after the “if” is not true (written as if CONDITION: in Python), the program checks the condition after the “else if” (written as elif CONDITION: in Python), and if it is also false, it checks the next “else if”. If there are no more “else if” statements left, the program executes the final “else” (written as else: in Python). Let’s convert the above pseudo-code to working Python code.

# Give a hint using if / elif / else.
if guess < 1 or guess > 20:
    print("That number is out of range. Try again.")
elif guess < secret:
    print("Too low, try again.")
elif guess > secret:
    print("Too high, try again.")
else:
    print("You got it in", tries, "tries!")

In this implementation, comparing the user’s guess to the chosen secret will lead to various cases:

    The user makes a guess outside the allowed bounds, i.e., 1 and 20
    The user’s guess is less than secret
    The user’s guess is greater than secret
    The user’s guess is correct

If the above looks confusing, consider the following numerical examples.

Numerical Example 1

We assume that the secret number is 10. If the user inputs 30, the first if condition will evaluate to true, and Python will execute the part after if guess < 1 or guess > 20: and print “That number is out of range. Try again.”

Numerical Example 2

We assume that the secret number is 10. Suppose the user inputs 5, the first if condition will evaluate to false because 5 is neither less than 1 nor greater than 20. Python will check the condition following the first elif and it will evaluate to true because 5 is indeed less than 10. Consequently, the program will print “Too low, try again.”

Numerical Example 3

We assume that the secret number is 10. Suppose the user inputs 15, the first if condition will evaluate to false because 15 is neither less than 1 nor greater than 20. The program will check the condition following the first elif and it will also evaluate to false because 15 is not less than 10. The program will check the condition following the second elif, and this one will evaluate to true, because 15 is larger than 10. As a result, the program will display, “Too high, try again.”
The First Draft

In this task, we built a working program that you can test for yourself and edit in the attached VM. The main limitation is that this program gives the user one chance. In the next task, we upgrade this program to allow the user an infinite number of tries to make the correct guess. The program below is saved as guess_v2.py in the /home/ubuntu/Python-Demo directory.

import random  # gives us tools for picking random numbers

secret = random.randint(1, 20)  # a <= secret <= b
tries = 0
guess = 0  # start with a value that cannot be the secret (since secret is 1..20)

print("I'm thinking of a number between 1 and 20")

text = input("Take a guess: ")  # input() returns text (a string)
guess = int(text)  # convert the text to a number

tries = tries + 1  # add 1 try

# Give a hint using if / elif / else.
if guess < 1 or guess > 20:
    print("That number is out of range. Try again.")
elif guess < secret:
    print("Too low, try again.")
elif guess > secret:
    print("Too high, try again.")
else:
    print("You got it in", tries, "tries!")

    
    It is too hard to guess the number when given a single chance. To make this game more interesting, it should provide the user with at least a few chances. We will be highly tolerant and allow the user as many attempts as needed to find the secret number. To give the user more than one chance, we need to use our secret weapon: loops! In programming, loops, or more formally, iterations, allow us to execute the same lines of code multiple times. In more formal phrasing, we can iterate over the same code block as long as a specific condition holds.

Let’s look at a few examples of iteration in our daily lives. Consider the case where you want to buy a new t-shirt: you will see one shop after another until you find one that suits you. The condition here is finding a suitable t-shirt. Consider another example where you are searching for an empty parking space in a vast parking lot. You will check one row of cars after another until you finally find a space. The condition here is finding a suitable parking space.

Back to our game, we will keep repeating the code we wrote in Task 3 until the user’s guess matches the secret number. In Python, “does not equal” is written as !=. In other words, the condition “guess does not equal secret” is written as guess != secret. To write this as a while loop, we use the form while CONDITION:; in our case, it is while guess != secret:.

Let’s paste the code from Task 3 in the body of our while loop.

# Repeat until the user guesses the secret number.
while guess != secret:
    text = input("Take a guess: ")  # input() returns text (a string)
    guess = int(text)  # convert the text to a number
    
    tries = tries + 1  # add 1 try

    # Give a hint using if / elif / else.
    if guess < 1 or guess > 20:
        print("That number is out of range. Try again.")
    elif guess < secret:
        print("Too low, try again.")
    elif guess > secret:
        print("Too high, try again.")
    else:
        print("You got it in", tries, "tries!")

The code above will execute as follows. First, Python will check the condition after the while; if it is true, it will run all the indented lines. If the condition is false, it terminates.

Numerical Example 1

We assume that the secret number is 10. In the first run, the guess is 0. The while condition will evaluate to true because 10 is not equal to 0. The program will ask the user to “Take a guess,” and it will proceed from there.

Numerical Example 2

We assume that the secret number is 10. If the user entered 5 earlier, it means they did not guess the number in the previous attempt. The while condition will evaluate to true because 10 is not equal to 5. The program will give the user another chance and prompt them to “Take a guess.”

Numerical Example 3

We assume that the secret number is 10. If the user entered 10 earlier, it means they successfully guessed the number in the previous attempt. Let’s see if the program will prompt them for another guess. The while loop will evaluate to false because 10 is equal to 10; in other words, 10 != 10 is false. The indented code block within the while statement will no longer execute.
The Second Draft

In this task, we have completed coding our game. You can test it for yourself and edit in the attached VM. The program below is saved as guess_v3.py in the /home/ubuntu/Python-Demo directory.

import random  # gives us tools for picking random numbers

# ----------------------------
# Guess the Number (Beginner Demo)
# ----------------------------
# The computer picks a secret number.
# The player keeps guessing until they find it.

secret = random.randint(1, 20)  # a <= secret <= b
tries = 0
guess = 0  # start with a value that cannot be the secret (since secret is 1..20)

print("I'm thinking of a number between 1 and 20")

# Repeat until the user guesses the secret number.
while guess != secret:
    text = input("Take a guess: ")  # input() returns text (a string)
    guess = int(text)  # convert the text to a number
    
    tries = tries + 1  # add 1 try

    # Give a hint using if / elif / else.
    if guess < 1 or guess > 20:
        print("That number is out of range. Try again.")
    elif guess < secret:
        print("Too low, try again.")
    elif guess > secret:
        print("Too high, try again.")
    else:
        print("You got it in", tries, "tries!")


# javascript

Before starting, we should point out that JavaScript files can be executed in various ways; one way is to use your web browser, and another way is to use Node.js. However, for our purposes, the easiest way to get started is by using Node.js. It is easy to download for your system and run your JavaScript files from the command line.

If you are curious about running JavaScript in your web browser, it is pretty simple. In your favorite web browser, access the Web Developer Tools. For example, I need to press F12 in Firefox to open the console, where I can run my JavaScript code. A screenshot of a web browser running JavaScript code is shown below.

Running JavaScript code within a web browser

Note that in this room, we will test our JavaScript code exclusively using Node.js. This process can be run by typing node demo.js at the command line, where demo.js is the name of our JavaScript file.
Creating Variables

Going back to our “game”, we need to start by declaring variables. We think of a variable as a space in memory that stores a value and allows us to change this value later. For example, we want to keep track of the number of tries (attempts) a user has made, as well as the user’s guess. We can do this by declaring these two variables:

let tries = 0;
let guess = 0;

The let indicates that we are declaring variables. When the user starts, they have not made any attempts, so tries is set to 0; moreover, we initialize guess to a value that cannot accidentally be the secret number that the user is trying to guess. (On a side note secret is constant and will be covered in the next subsection.) Remember that the secret number is between 1 and 20.
Creating Constants

We use let to declare variables, whose value can change throughout the program; however, we use const to declare constants, whose value cannot change throughout the program.

The secret holds the number that we will try to find by guessing, and it should not change. As already mentioned, to declare a constant, we use the keyword const, for example, const secret = 12. To ensure that secret gets a new random value each time we run the program, we need to use JavaScript’s Math.random() method.

const secret = Math.floor(Math.random() * (20)) + 1;

Although the details of this expression are not the key purpose of this room, we will share a brief breakdown for the curious readers.

    Math.random() gives a random decimal between 0 (inclusive) and 1 (not including 1). Example: 0.372.
    * 20 stretches that range from 0 to (almost) 20. Example: 7.44.
    Math.floor() removes the decimal by rounding down. Example: 7.44 becomes 7.
    + 1 shifts the range from 0–19 to 1–20.

As a result, secret ends up being 1, 2, 3, …, up to 20.
Displaying Output

Once the secret number is picked, the program should inform the user that this step is complete. To display on the screen, console.log() can be used. In the example expression below, the string included between the double quotes will be displayed on screen.

console.log("I'm thinking of a number between 1 and 20");



Before starting, please note that you can download the attached zip file. It includes all versions of the program that are present on the target VM. This archive allows you to review the project's evolution, compare implementations, or test each version independently on your local machine. Having all iterations in one package should make your work more efficient.

In the previous task, we set our variables and constants; moreover, we picked a random secret number for the user to guess. Now, we need to prompt the user to take a guess and enter a number. In the first line, we wait for the user to input a value and save it in text. In the second line, we parse the text as an integer of base 10 using parseInt(text, 10). The parseInt() method takes the user input and converts it from text into an integer value.

const text = await rl.question("Take a guess: ");
guess = parseInt(text, 10);

 
Optional Notes

 
Putting it All Together

The first draft we have built so far is listed below and is also available on the system as guess_v1.js, which can be found in the /home/ubuntu/JavaScript-Demo directory.

import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";

const rl = readline.createInterface({ input, output });

try {
    const secret = Math.floor(Math.random() * (20)) + 1; // 1 <= secret <= 20
    let tries = 0;
    let guess = 0; // start with a value that cannot be the secret (since secret is 1..20)

    console.log("I'm thinking of a number between 1 and 20");

    const text = await rl.question("Take a guess: "); // rl.question() returns text (a string)
    guess = parseInt(text, 10); // convert the text to a number

    tries = tries + 1; // add 1 try

} finally {
    rl.close();
}

What’s Missing?

The most glaring missing component is that the user receives no feedback, even if they get the correct answer. Let’s get this implemented in the next task.

So far, you are playing the “guess the number” game, and the current program has no way to provide feedback on your choices. It asks you to make a guess, and it goes silent! Let’s make things more engaging and advance our program so it can evaluate user input and provide feedback.

We will follow the following logic steps:

    If it is outside the valid range, i.e., not between 1 and 20, we tell the user that their “number is out of range”
    If it is less than the secret number, we inform the user that it is “too low”
    If it is greater than secret, we inform the user that it is “too high”
    If it is not greater than and not less than the secret number, this means that it is equal to the secret number, and the user has successfully guessed it

From the above comparisons, you can see that if the first condition holds, there is no point in checking the second condition. Moreover, if the second condition holds and it is less than secret, there is no point in checking the third condition. Because the conditions are mutually exclusive, we can make use of else. We will present the conditions using JavaScript and discuss them afterwards.

// Give a hint using if / else if / else.
if (guess < 1 || guess > 20) {
    console.log("That number is out of range. Try again.");
} else if (guess < secret) {
    console.log("Too low, try again.");
} else if (guess > secret) {
    console.log("Too high, try again.");
} else {
    console.log("You got it in", tries, "tries!");
}

The above if, else if, and else statements will execute as follows:

    if (guess < 1 || guess > 20): If the guess is less than 1 or the guess is greater than 20, then use console.log() to tell the user that the “number is out of range”. Note that || represents "or" in JavaScript.
    else if (guess < secret): The else means that if the previous condition is not true, run this statement. if (guess < secret) will evaluate whether the guess is less than the secret. If this is the case, it will use console.log() to display “too low” on the screen
    else if (guess > secret): Similarly, the else will ensure that this statement won’t run unless the previous if has evaluated to false. Assuming that the last if condition evaluated to false, if (guess > secret) will assess its condition. In the case that guess is greater than secret, the console.log() displays “too high”
    Finally, we see an else sitting by itself. This else means that if all previous if conditions are evaluated to false, the enclosed statement will execute. As we established earlier, if all previous conditions are evaluated to false, it means that the user guessed the number.

Putting it All Together

Our draft can be updated to include the conditions we covered in this task. The previous draft will be expanded to provide the user with feedback on their guesses. The updated program we have constructed so far is listed below and is also available on the system as guess_v2.js in the /home/ubuntu/JavaScript-Demo directory.

import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";

const rl = readline.createInterface({ input, output });

try {
    const secret =
        Math.floor(Math.random() * (20)) + 1; // 1 <= secret <= 20
    let tries = 0;
    let guess = 0; // start with a value that cannot be the secret (since secret is 1..20)

    console.log("I'm thinking of a number between 1 and 20");

    const text = await rl.question("Take a guess: "); // rl.question() returns text (a string)
    guess = parseInt(text, 10); // convert the text to a number

    tries = tries + 1; // add 1 try

    // Give a hint using if / else if / else.
    if (guess < 1 || guess > 20) {
        console.log("That number is out of range. Try again.");
    } else if (guess < secret) {
        console.log("Too low, try again.");
    } else if (guess > secret) {
        console.log("Too high, try again.");
    } else {
        console.log("You got it in", tries, "tries!");
    }
} finally {
    rl.close();
}

Let’s quickly review what this code does:

    It picks a random secret number between 1 and 20
    It keeps track of the user’s guess and number of tries
    Then it asks the user to “Take a guess:”
    The user’s guess is received as text and converted to a number, and saved in guess
    We compare guess with secret and give feedback to the user about their attempt

Make sure that you have a good understanding of the script so far. You are not expected to write it yourself; however, you should be able to explain it by looking at it.
What’s Missing?

This code runs once, giving the user a single chance. This situation is shown in the interaction below.
Terminal

           
ubuntu@tryhackme:~/JavaScript-Demo$ node guess_v2.js
I'm thinking of a number between 1 and 20
Take a guess: 10
Too low, try again.

        

Obviously, that’s not a fun game if the user gets only one chance. We need to give the user more chances until they make the correct guess. In the next task, we will get our script to provide the user with many chances to make the game more fun.


The script we have so far efficiently provides feedback on the user’s guess; however, it does not give them a second chance. In this task, we will make the necessary changes so that it keeps prompting the user for new guesses until they figure it out.

One way to achieve this is to keep prompting the user to make new guesses as long as their guess is wrong, i.e., while their guess is not equal to secret. That’s quite easy to express in JavaScript: while (guess !== secret). The !== means “not equal”. This is called a while loop and is written as shown below:

// Repeat until the user guesses the secret number.
while (guess !== secret) {
    // Loop body: instructions to be repeated
}

The next part to decide is what to include in the body of this while loop. Based on the program logic we have built so far, we should repeat the following:

    Prompt the user to take a guess
    Convert the user’s input to a number and save it in guess
    Increase the number of tries by one
    Check guess with respect to the lower and upper limits
    If it is within the limits, compare it to the secret number
    Display feedback to the user about their choice

And we will repeat if the users didn’t make the correct guess.

The JavaScript code with the while loop filled is shown below.

// Repeat until the user guesses the secret number.
while (guess !== secret) {
    const text = await rl.question("Take a guess: "); // rl.question() returns text (a string)
    guess = parseInt(text, 10); // convert the text to a number

    tries = tries + 1; // add 1 try

    // Give a hint using if / else if / else.
    if (guess < 1 || guess > 20) {
        console.log("That number is out of range. Try again.");
    } else if (guess < secret) {
        console.log("Too low, try again.");
    } else if (guess > secret) {
        console.log("Too high, try again.");
    } else {
        console.log("You got it in", tries, "tries!");
    }
}

Putting it All Together

The program we have constructed so far is listed below and is also available on the system as guess_v3.js.

import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";

const rl = readline.createInterface({ input, output });

try {
    const secret =
        Math.floor(Math.random() * (20)) + 1; // 1 <= secret <= 20
    let tries = 0;
    let guess = 0; // start with a value that cannot be the secret (since secret is 1..20)

    console.log("I'm thinking of a number between 1 and 20");

    // Repeat until the user guesses the secret number.
    while (guess !== secret) {
        const text = await rl.question("Take a guess: "); // rl.question() returns text (a string)
        guess = parseInt(text, 10); // convert the text to a number

        tries = tries + 1; // add 1 try

        // Give a hint using if / else if / else.
        if (guess < 1 || guess > 20) {
            console.log("That number is out of range. Try again.");
        } else if (guess < secret) {
            console.log("Too low, try again.");
        } else if (guess > secret) {
            console.log("Too high, try again.");
        } else {
            console.log("You got it in", tries, "tries!");
        }
    }
} finally {
    rl.close();
}

You can test it on the system by running node guess_v3.js; it can be found in /home/ubuntu/JavaScript-Demo. Every time you rerun the program, it should pick a new secret number for you to guess.
Terminal

           
ubuntu@tryhackme:~/JavaScript-Demo$ node guess_v3.js
I'm thinking of a number between 1 and 20
Take a guess: 10
Too low, try again.
Take a guess: 15
Too high, try again.
Take a guess: 13
Too low, try again.
Take a guess: 14
You got it in 4 tries!

        

It should be noted that the file node guess_v4.js, on the VM and in the zip file attached to Task 3, further improves this program. You are encouraged to take a look; however, it is not critical for this introductory room.


# Database

In this table, each column represents one type of information, such as a name or a price.

Each row represents a complete record, and the table contains all records.

Imagine a small café.

At first, the café owner writes each order in a paper notebook to track orders and payments.

Each order includes:

    The drink name
    The price
    The time of the order

This works fine when the café is small. However, after many days, the notebook becomes full. Finding answers to questions like “How many coffees were sold today?” or “What was the cheapest drink sold this morning?” becomes slow and difficult.

The owner has to read through many pages and count orders manually. This is where computers and databases become useful.
What Is a Database

Think of a database as a place where a computer stores information in an organised way.

You can think of a database as a digital notebook that never runs out of pages. Unlike a paper notebook, a database allows the computer to search, count, and sort information very quickly.

Even if the café has thousands of orders, a database can still answer questions in seconds.

Inside a database, information is stored in tables.
Tables, Columns, and Rows

A table resembles a spreadsheet, where information is organised neatly into rows and columns.

    Columns are the titles at the top of the table. They describe the type of information stored.
    Rows go across the table. Each row contains one complete set of information.

For the café example:

    Columns might be: order number, drink, price, and time
    Each row is one café order

This means:

    One column stores one type of information, such as prices
    One row stores all the information about a single order

If the café sells ten drinks in one day, the table will contain ten rows. If one more customer places an order, one more row is added to the table.

If an order is removed, only that row disappears. The rest of the table stays the same.
Asking Questions With SQL

SQL is a language used to ask questions of a database.

Instead of reading the table row by row, SQL lets the computer do the work for us.

For example, the café owner might ask:

    “Show me all orders.”
    “Show me only coffee orders.”
    “Show me the cheapest drink.”

These questions are called queries.

A query does not change the data. It only displays the requested information from the table.

In the next task, you will learn how to write simple SQL queries to ask these questions yourself.


In this task, you will use a safe browser-based database client. Nothing here can break. If you make a mistake, you can click  Reset Data and try again.

At the top of the page, you can see the two tables and their columns:

    Orders (id,drink,price,time)
    Menu (drink, price)

Your goal is to practise writing queries using four core SQL parts: SELECT, FROM, WHERE, and ORDER BY.
Step 1: View Everything in a Table (Select + From)

We start with the most basic query. When we use SELECT *, the * symbol means all columns. The word FROM tells the database which table to use.

Try this query:

SELECT * FROM Orders;

Click Run Query. You should see every order currently stored in the database.

Café SQL app running SELECT * FROM Orders, returning 50 rows with id, drink, price, and time columns
Step 2: Show Only Specific Columns (Select Drink, Price)

Sometimes we do not need every column. We can choose specific columns by listing them after SELECT.

Try this query:

SELECT drink, price FROM Orders;

This will display only the drink and price columns.

Café SQL app running SELECT drink, price FROM Orders, returning 50 rows showing only the drink and price columns
Step 3: Filter Results (Where)

The WHERE keyword filters rows. It keeps only rows that match a condition.

Try filtering by drink name:

SELECT * FROM Orders WHERE drink = 'Coffee';

If the database contains coffee orders, you will now see only those rows.

Café SQL app running SELECT * FROM Orders WHERE drink = 'Coffee', returning 10 filtered rows of Coffee orders

Hint: If you are not sure which drink names exist, run:

SELECT * FROM Menu;
Step 4: Sort Results (Order By)

The ORDER BY keyword sorts results by a column. By default, results are sorted in ascending order (lowest to highest).

Try sorting orders by price (lowest first):

SELECT * FROM Orders ORDER BY price;

Café SQL app running SELECT * FROM Orders ORDER BY price, returning rows sorted by price from lowest to highest

To sort in reverse order (highest to lowest), add DESC.

Try sorting orders by price (highest first):

SELECT * FROM Orders ORDER BY price DESC;

Café SQL app running SELECT * FROM Orders ORDER BY price DESC, returning rows sorted by price from highest to lowest
Step 5: Combine Filtering + Sorting

Most real queries combine parts together. Here, we filter to keep only one drink type and then sort by price.

Try this query:

SELECT * FROM Orders WHERE drink = 'Coffee' ORDER BY price DESC;

Café SQL app running SELECT * FROM Orders WHERE drink = 'Coffee' ORDER BY price DESC, returning 10 Coffee orders sorted by price descending