# XML-Editor
XML (Extensible Markup Language) is one of the most famous formats for storing and sharing information among different devices. Some text editors such as Sublime Text are able to parse such files and do some basic operations. 
In this project, the GUI (Graphical User Interface) based program is able to parse and visualize an XML file and also perform different operations on the XML file like:
- Detecting Errors
- Fixing the Errors that were detected
- Formating ( or Prettifying )
- Converting the XML to JSON (JavaScript Object Notation )
- Minifying
- Compressing the file  


YOUTUBE LINK DEMONSTRATING THE GUI:  
https://youtu.be/NnOtau86Bkg
  
The program can view, edit and save XML files.
In addition, it has the ability to detect many errors in the XML file including missing tag terminator or in correct terminator and fix them.
Another functionality is minifying and prettifying the XML file in which spaces before each tag is either removed to decrease file size or add to restore format respectively. 
Also it has the functionality of compressing the XML file to nearly 50% of its size.
And it has the functionality of converting the XML file to a JSON file.



# Documentation

# Background

XML is a markup language created by the World Wide Web Consortium (W3C) to define a syntax for encoding documents that both humans and machines could read. It does this through the use of tags that define the structure of the document, as well as how the document should be stored and transported.

It&#39;s probably easiest to compare it to another markup language with which you might be familiar—the Hypertext Markup Language (HTML) used to encode web pages. HTML uses a pre-defined set of markup symbols (short codes) that describe the format of content on a web page.

Like XML, JSON is one of the ways of formatting the data. Such format of data is used by web applications to communicate with each other.

Although, it is light weight text based data interchange format which means, it is simpler to read and write when compared to XML.

The JSON format is syntactically identical to the code for creating JavaScript objects therefor a JavaScript program can easily convert JSON data into native JavaScript objects.

# Program Functionalities

The program is known as XML-Editor, where it can view, edit and save XML files.

In addition, it has the ability to detect many errors in the XML file including missing tag terminator or in correct terminator and fix them.

Another functionality is minifying and prettifying the XML file in which spaces before each tag is either removed to decrease file size or add to restore format respectively.

Also it has the functionality of compressing the XML file to nearly 50% of its size.

And it has the functionality of converting the XML file to a JSON file.

# Program development tools and languages

The XML-Editor is designed and implemented using QtCreator v5.15.1 and C++11 language.

Different IDEs where using during development including Eclipse, VScode &amp; VS studio.

# Implementation and Function descriptions

## Reading file

QtCreator is used to read the XML file and convert it to a Qstring in which it is converted to a normal string.

_XML\_Parser function:_

The normal string is then passed to XML\_Parser function which extracts the information from the string into a vector of strings.

Each string in the vector represents one line in the text where that line will either be an opening tag, body or a tag terminator.

Error Checking and Error Fixing_XML\_fixError function:_

The Read vector will be passed to the XML\_fixError Function which is responsible of detecting different types of error including missing terminal tags and incorrect terminal tags.

The XML\_fixError function will return two vectors, the first one is XML\_Original which has the same lines of the Read vector but with a string flag pointed to the lines which have errors.

The other vector is XML\_fixed vector, this vector has all the error fixed.

## Prettifying

_XML\_Indent function:_

All lines of both vectors include no indents and here comes the XML\_Indent function.

This function is responsible of production correct indentation for the XML\_file, it takes the desired vector (Original or Fixed) and outputs a vector of spaces that can be combined with the desired vector to produce an XML file with perfect format.

This sequence results in Auto Indentation Fix when viewing an XML file which increases file readability without overwriting the Original XML file permanently.

The user can save the new fixed indentations by using the save button.

## Minifying

_XML\_Minify function:_

Responsible of the production of an XML file with no indentations which decreases the total file size.

The current way of separating the indentations from its lines into different vectors facilitates the minifying process very much.

The XML\_Minify function just takes the desired vector (Original or Fixed) and outputs its content in a file directly without using the space vector which results in an XML file with no indentations or extra spaces.

## Compression

_PrintCompressedTree Function:_

The function takes the fixed vector and turns it back to a string where Huffman coding Algorithm is used on it.

Huffman coding is a lossless data compression algorithm. The idea is to assign variable-length codes to input characters, lengths of the assigned codes are based on the frequencies of corresponding characters. The most frequent character gets the smallest code and the least frequent character gets the largest code.

The variable-length codes assigned to input characters are Prefix Codes, means the codes (bit sequences) are assigned in such a way that the code assigned to one character is not the prefix of code assigned to any other character. This is how Huffman Coding makes sure that there is no ambiguity when decoding the generated bitstream.

_Steps to build Huffman Tree_

1-Input is an array of unique characters along with their frequency of occurrences and output is Huffman Tree.

2-Create a leaf node for each unique character and build a min heap of all leaf nodes (Min Heap is used as a priority queue. The value of frequency field is used to compare two nodes in min heap. Initially, the least frequent character is at root)

Extract two nodes with the minimum frequency from the min heap.

3-Create a new internal node with a frequency equal to the sum of the two nodes frequencies. Make the first extracted node as its left child and the other extracted node as its right child. Add this node to the min heap.

4-Repeat steps#2 and #3 until the heap contains only one node. The remaining node is the root node and the tree is complete.

Some of the binary assigned to each character of file after encoding and compression:

m =\&gt; 111111 E =\&gt; 001000011010 7 =\&gt; 11111011 j =\&gt; 1000001100

9 =\&gt; 11111010 H =\&gt; 001000010

\_ =\&gt; 1111100 , =\&gt; 00100000111

= =\&gt; 111001 8 =\&gt; 0010001 / =\&gt; 111000 v =\&gt; 1000111 i =\&gt; 11011 &#39; =\&gt; 001000001101 \&gt; =\&gt; 11010 ` =\&gt; 0010000011001 \&lt; =\&gt; 11001 S =\&gt; 0010000000 a =\&gt; 11000 ) =\&gt; 10111101010 2 =\&gt; 1011111 x =\&gt; 100001

D =\&gt; 101111011 C =\&gt; 00100001100

I =\&gt; 10111101001 h =\&gt; 0101110

O =\&gt; 10111101000 e =\&gt; 000

- =\&gt; 101111001 k =\&gt; 100000111

. =\&gt; 1011110001 P =\&gt; 0010000111

N =\&gt; 10111100001111 u =\&gt; 100010

G =\&gt; 10111100001110 ? =\&gt; 00100000011

V =\&gt; 10111100001101 M =\&gt; 0010000011000

U =\&gt; 10111100001100 r =\&gt; 0110

F =\&gt; 1011110000101 A =\&gt; 0010000010

B =\&gt; 1011110000100 f =\&gt; 01010

: =\&gt; 101111000001 ! =\&gt; 00100000010

R =\&gt; 1011110000001 p =\&gt; 00101

&quot; =\&gt; 11101 t =\&gt; 0011 q =\&gt; 1011110000000 n =\&gt; 0100 y =\&gt; 101110 c =\&gt; 010110 s =\&gt; 10110 5 =\&gt; 0101111 l =\&gt; 10101 1 =\&gt; 011100 d =\&gt; 10100 4 =\&gt; 0111010 o =\&gt; 11110 6 =\&gt; 0111011 =\&gt; 1001 0 =\&gt; 01111

3 =\&gt; 1000110 z =\&gt; 10000011010 ( =\&gt; 10111101011 g =\&gt; 1000000 w =\&gt; 001001 b =\&gt; 10000010

W =\&gt; 001000011011 T =\&gt; 10000011011

This will result in a file compression of around 50% of its original size.

## Converting XML to JSON

XML\_JSON function:

JSON (Javascript Object Notation) is another format that is used to represent data. It&#39;s helpful to convert the XML into JSON, especially when using javascript as there&#39;s tons of libraries and tools that use json notation.

The function takes the fixed vector of strings and each string represents a line in xml file and returns a vector of strings where each string represents one line of the JSON file.

Each opening tag is written and its contents are written after that between braces, if the tags are repeated they aren&#39;t written again instead braces of first tag is closed and then comma and open new braces for the content of the new repeated tag, closing tags aren&#39;t written instead braces are closed.

# Program Screenshots

- Starting the program.

![image](https://user-images.githubusercontent.com/68311964/161386105-8ac2174a-eb0b-4309-aeae-b33e5779c67c.png)


- Opening an existing XML.

![image](https://user-images.githubusercontent.com/68311964/161386113-d65f7498-94d2-4ab2-85f6-c039769c1455.png)


- Using (Filter by Extension) option.

![image](https://user-images.githubusercontent.com/68311964/161386118-f2eb6611-6797-48e7-81d0-222db0ee08cd.png)


- Open an XML file that has some format errors.

![image](https://user-images.githubusercontent.com/68311964/161386128-52106aa8-322e-41ea-ad9e-71b1ae78f9b2.png)


- Push &quot;Check For Errors&quot; button

![image](https://user-images.githubusercontent.com/68311964/161386147-f5204b15-cb30-4a58-9bd3-f5c9360e1cba.png)


_A dialog appear where errors are pointed to by &quot;\&lt; ------error here&quot; with the option to Fix the errors or Cancel and keep the file as it is._

-Selecting &quot;Fix&quot; button.

![image](https://user-images.githubusercontent.com/68311964/161386157-dd312702-9fb9-4e11-b88e-611e32c6017c.png)

## _All errors are fixed and the file indents are corrected automatically_

-Selecting &quot;Minify&quot; button.

![image](https://user-images.githubusercontent.com/68311964/161386173-e2bc76dc-064e-4001-8280-0ebcb3c2c67e.png)

## _All indents and extra spaces are removed_

-Using &quot;Format (Prettify)&quot; button to add correct indents again.

![image](https://user-images.githubusercontent.com/68311964/161386182-4a8db5c9-411f-45c5-8168-9a4dab3cb661.png)

## _Correct indents added again_

-Using &quot;Compress&quot; Button.

![image](https://user-images.githubusercontent.com/68311964/161386186-6dc04e08-9da5-4cf1-a595-663c745a7935.png)

## _The compressed file size is around 50% of the original file size_

-Using &quot;Convert To JSON&quot; button.

![image](https://user-images.githubusercontent.com/68311964/161386190-7e0a7d78-e13c-4cf7-9495-bc63d11df1c5.png)

_XML converted to JSON_

# Complexity of Operations

XML\_Parser (Reading XML): O(n)

XML\_fixError (Checking errors and fixing them): O(n)

XML\_Indent (Adding indentations): O(n)

XML\_Minify (Removing indentations and extra spaces): O(n)

XML\_to\_JSON (Converting XML to JSON): O(n)

PrintCompressedTree (Compressing XML): O(nlogn)
