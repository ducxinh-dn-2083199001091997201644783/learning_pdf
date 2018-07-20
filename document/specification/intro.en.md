## Understanding the Portable Document Format (PDF)

**Preface**: I wish to acknowledge that this article was written with full reference to http://www.adobe.com/devnet/acrobat/pdfs/PDF32000_2008.pdf. 

Most of all that I have learned about PDFs are from the above reference. If you are really interested take time to read it. Surprisingly, it is easy and interesting to read! I am writing this tutorial out of my interest in knowing the PDF specification. 

My quest started when I tried hard but failed to extract text from a simple PDF file that contained a single page of text. Please let me know (steve@printmyfolders.com) if you find any errors. 

I have relied on the PDF specification (link on page top) to create this tutorial. This tutorial covers PDF files conforming to the ISO 32000-1 specification (Pages vi to viii in the PDF32000_2008.pdf give more information on this).
 


Imagine you are alone on a island with no internet, no means of communication apart from a phone where you can only make voice calls. 

Apart from this, you have all your needs met - you have a home to stay in, you have enough food to eat and you are comfortable. A plane will arrive in a week's time to take you home. All of a sudden, you remember that an important document, currently with you has to be submitted to a printer in a day's time. It is a simple one page invitation containing only text. How would you communicate this information to your printer?

Here is one way of doing it. You would grab a ruler, measure the width and height of your page and note it down. You will measure the exact location where each line starts. You will note down the font, its size and colour of all of your text. You will then call your printer and give her all these details. Provided you have given her enough details she should be able to replicate your document exactly as it is.

PDF works in a similar way. We give instructions so that, the PDF viewing app such as, Adobe Reader can understand our instructions and display the way we want it to. Of course, there is so much more to PDF than that. Rather than speaking to a person, we are instructing a  software. So we need structure, and follow specific rules.

Keep this imagery in mind and it will help you understand better.


PDF files are interesting. If you were to open a PDF file in a text editor like Notepad, the contents may look like junk and probably not very interesting. But it will make a little more sense once you understand that PDF files follow a set pattern.
 
"At the core of PDF is an advanced imaging model derived from the PostScript® page description language. This PDF Imaging Model enables the description of text and graphics in a device-independent and resolution-independent manner. To improve performance for interactive viewing, PDF defines a more structured format than that used by most PostScript language programs. Unlike Postscript, which is a programming language, PDF is based on a structured binary file format that is optimized for high performance in interactive viewing. PDF also includes objects, such as annotations and hypertext links, that are not part of the page content itself but are useful for interactive viewing and document interchange." (Quoted from Page vii of PDF32000_2008.pdf).
 
The basic building blocks of a PDF files are objects. There are eight types of objects that are used in PDF files. Before we look at them we will briefly look at the character set of PDFs. There are 3 types of characters - white-space, delimiter and regular characters.

### Charater
##### White-space characters:
- Null, Horizontal tab, Line feed, Form feed, Carriage return and Space. 
- Tip: If you need to remember them, imagine seeing them in sequence (except for null of course) being typed on an imaginary typewriter. White-space characters separate names and other objects from each other. Interestingly, PDF treats all white-space characters outside a comment, string or stream the same. Outside a comment, string or stream, PDF considers any sequence of consecutive white-space characters as one character. What this means is that you may have 5 spaces but in reality it is considered as one. Note that this does not apply to white-space characters within strings, streams and comments. The Carriage return and Line feed are considered as end-of-line (EOL) markers. EOL markers play a very important role in showing where a new line starts. Carriage return followed immediately by a Line feed is considered as one EOL marker.
 
##### Delimiter characters: 
- (, ), <, >, [, ], {, }, / and % (4 pairs and 2 unique). These are used in the objects we would look at later. They basically act as delimiters (mark the boundary or border) for entities. Tip: If you need to remember them, imagine these characters ( ) being bent < > and then stretched [ ] and then bent again { } and then eventually made flat / %. 
 
##### Regular characters: 
- All characters other than White-space and Delimiter characters including those that are not part of the standard ASCII character set. Please read the note below as it is critical you understand this.

An interesting fact to note is that a PDF may consist entirely of just ASCII characters or can consist of ASCII characters and Binary data. In simple terms, characters in ASCII files use only 7 out of the 8 bits in a byte while characters in the Binary files use all the 8 bits in the byte. This allows a possibility of 128 unique characters for ASCII files and 256 unique characters for Binary files. Most PDF files that are encrypted or contain images will have binary data (images are represented in binary). PDF files that contain binary data get corrupted when edited or even opened and saved in normal text editors like Notepad. It is critical that we understand the difference between ASCII and Binary files as other areas of the PDF specification touch on them. Here is an interesting link that explains the difference between Binary and ASCII files. http://www.cs.umd.edu/class/spring2003/cmsc311/Notes/BitOp/asciiBin.html 

You may also wonder why you don't see any text (that can be seen when opened using a reader) or its equivalent when opening a PDF file in a text editor or even binary editor. There may be two reasons. The first and most common reason is that the content stream (where the text is stored/kept) is encoded (transformed/changed) to conserve space. This is what happens with most files.The second reason could be that the PDF file is encrypted purposely to keep the text secure.
 
### Objects:

Here are the objects that make use of the characters we looked at above.

Each of these objects have a corresponding class in PDFBox. Have a look at this link https://pdfbox.apache.org/1.8/architecture.html under the section "The COS  Model"
 
##### Boolean objects: 
The keywords true and false. 

##### Numeric objects: 
There are two types; integer & real. Integers are numbers without any decimal points and can have a + or – symbol preceding it. For instance, the number 10. Real numbers must have a decimal point. For instance, 10.5, 0.0, +5.0, -1.0. Real numbers cannot be expressed in exponential format. 

##### String Objects: 
Strings contain characters (can be zero characters as well). They can be literal characters within parenthesis or hexadecimal data within angle brackets. Notice that the parenthesis and angle brackets are delimiter characters. 
```
(I love Java (and PDF))
```

There are escape characters that can be used. Refer to the PDF specification for more details. The sequence \ddd where ddd is an octal character code can be used to represent characters outside the printable ASCII character set. Be aware that, some of the escape characters, especially the ones that cause characters to move, for instance \n (newline), did not have any visual effects when I added them to a string displayed by the PDF. You can replace one of the characters in the string I have used in the sample PDF and notice no difference.

We can also use octal characters (usually to represent character outside the printable ASCII character set) when using parenthesis. An octal character is represented in the format \ddd. In the following example \052 represents * (asterisk), a printable ASCII character.
```
(I love Java (and \052PDF))
```
Here is an example of a String represented with hexadecimal numbers. 

<48454C4C4F>
Each pair is taken as a value. In the above example, the hexadecimal value 48 is decimal 72 which is the ASCII equivalent of H. Likewise 45 is E, 4C is L and 4F is O. The above string is same as the string (HELLO). If the final hexadecimal digit is on its own (without another digit to make a pair) a zero is attached to the end.
```
<4845C>
```
will be considered as
```
<4845C0>
```
##### Name Objects: 
Names consist of a sequence of characters (except null). A forward slash / must be used to introduce the name. In case hash (#) is part of the name, use # followed by its hexadecimal code 23. To represent characters using their hexadecimal value use # followed by the hexadecimal value. All characters that are not regular characters have to be represented by the # followed by their hexadecimal value. Please refer to the PDF specification for more details.
```
/MyName represents MyName

/My#20Name represents My Name

/All#20#23Numbers represents All #Numbers
```

##### Array Objects: 
These are similar to the arrays found in computer languages but differ in that they can contain different object types (including strings, names and even other arrays). Arrays are represented within square brackets. As you can see, the values are separated by spaces.
``` 
[false 170 85.5 (Hello) /My#20Name]
```
Arrays are single dimensional but can include other arrays which can hold arrays themselves.
 
##### Dictionary Objects: 
These are similar to an actual dictionary, where a description follows a word. The description here can be any object (including another dictionary) but the name is always a Name object that we just discussed. The key (Name) is unique (there cannot be two similar Names). A dictionary is represented within << >>.
```
<< /Name (Steve)

/Age 99

/Address << /Number 1234

                /Street (Java Street)

                /Suburb (Java Town)

                /PostCode (4321)

>>

>> 
```

##### Stream Objects: 
Streams are similar to strings except that can be of unlimited length. They are usually used to represent large data that cannot fit into a String. An image, for instance, can be represented as a stream. As you will see later, the contents of each page in PDF is represented as a 'Contents' stream. It consists of a dictionary followed by the keyword ‘stream’, newline, the stream’s data and the keyword ‘endstream’. 
``` 
dictionary
stream

……….

endstream
```

While the stream consists of the data, the dictionary contains information about the stream itself. Here are the keys that are common for most stream dictionaries. Out of these the only mandatory key is Length.

- **Length - Mandatory entry** that contains the length (number of bytes) of the stream. An error occurs if the stream has more bytes of data that the length mentioned in the dictionary.

- **Filter** - The name(s) of the filter(s) used to decode the data on the stream. Can be a name or an array. The filters are used in the order supplied

- **DecodeParms** - Parameter dictionary used by the filters. Can be a dictionary or array. Parameters are values used by the filters. If the filter uses the default parameters, it can be  skipped.

- **F** - From PDF specification version 1.2, the stream contents can be stored in an external file. This shows the file where it is stored. In this case the contents between stream and endstream are ignored.

- **FFilter** - Similar to Filter entry but for the stream's external file.

- **FDecodeParms** - Similar to DecodeParms but for stream's external file's filter

- **DL** - An approximate size of the contents (after decoding) in the stream. This will help determine if there is enough disk space for the stream.


##### Null object
Refers to a non existent object and denoted by the keyword null. 


### Other components of a PDF file. 
##### Comments: 
The comment is represented by the percentage sign i.e. %. This is commonly used to describe the version of PDF specification used in creating the PDF file.
```
%PDF-1.7
```

##### Indirect Objects: 
An object (for example, a string) that has been given a unique object identifier, that other objects can use to refer to itself is called an indirect object. This is different from the 'Name' object that we looked at earlier. Looking at any PDF file in its raw form (for instance, by opening it in a text editor) you will notice lots of indirect objects.
 
The identifier has two parts. The first part is the object number that can be any positive integer. The second part is the generation number which is always zero in the first non-updated version of the PDF file. You declare an indirect object within the keywords ‘obj’ and ’endobj’. Be aware that the combination of the object number and generation number has to be unique. 
```
1 0 obj

(my biography)

endobj
```

The object number is 1 and the generation number is 0. The indirect object is the string object (my biography).  If another object wanted to refer to this object, it would quote the object number, followed by space, generation number, followed by space and then R.
```
1 0 R
```

It is not an error if one was to refer to a non existing indirect object.

### File Structure
A PDF file will initially have the following structure. However, if the file is updated or edited, additional elements may be added to the end of the file.
 
1. **A Header** (not more than a line) showing the PDF specification this file follows.

2. **A File Body** that has the objects of the file

3. **A Cross-reference** table that has info about indirect objects

4. **A Trailer** that shows the location of the cross-reference table and special objects within the body of the file. 



**File Header**: This denotes the PDF specification version of the PDF file. %PDF- followed by version number 1.N, where N is a digit between 0 & 7.
```
%PDF-1.2
```
As mentioned earlier this is actually a comment that is used to specify the PDF version.

 
Beginning with version 1.4 the document's catalog dictionary is used instead of this. If the file has binary data, there will be at least four binary characters, immediately after the header. This is to show PDF reading applications (like Adobe reader) that the PDF has binary data. Again, when opening some PDF files in their raw form (as in a text editor) you may notice the four binary characters just after the first comment.

**File Body**: The File body consists of indirect objects (discussed earlier). These objects represent text and other details (like font type etc.) used in displaying PDF.  As of version 1.5, the body can also contain object streams. 

**Cross-Reference Table**: This table is similar to a directory. It contains the location of each object within the PDF file. By looking at the entries in this table, the PDF reading application (for example, Adobe Reader), can easily locate an object within the file. This saves time as the object is accessed in a random manner (rather than reading every line of the file). The cross-reference table can have one or more sections. Each of these sections can have one or more subsections. 

**Note**: From PDF version 1.5 onward the cross-reference table can be stored as a stream and if so you will not be able to view the table as shown below when opening with a text editor.

Each section begins with the word 'xref'. Following this line are two numbers separated by a single space. The first number is the object number of the first of the series of objects listed below it. The second number refers to the number of entries in that subsection. For a PDF file that has been created for the first time or a PDF file that has not been incrementally updated, there shall be only one subsection and the object numbering starts with 0. Notice that the object numbers have to be consecutive. In the example below, it is safe to assume that entries for objects 1, 2, 3 & 4 will follow. 
```
xref

0 5  
```
Following this are the entries for each object. Each entry shall be exactly 20 bytes long. The entries are of the format
```
nnnnnnnnnn ggggg meol
```
`nnnnnnnnnn` - This is a ten digit value. This reveals how far the object is from the start of the file. For instance, the value 100 denotes that the object is 100 bytes from the start of the file. 

`ggggg` - 5-digit generation number

`m` - can be either 'n' or 'f'. 'n' denotes that the object is still in use and 'f' denotes that the object has been deleted and is free. 

`eol` - end of line. Consists of 2 chars.

The ten digits, followed by space, followed by five digits, followed by space, followed by a single character and the eol make exactly 20 digits. If the first two numbers are not long enough, to be ten and five digits respectively, zeroes are added to the front. 

Let's come back to the 0 5 that we saw in the example earlier.The 0 denotes the object number of the first object in this subsection. The value 5 denotes that there are 5 entries (including the one for 0) and that the remaining four entries are for objects with object numbers 1, 2, 3 and 4. The first entry at the cross-reference table is for object 0. Object 0 will have 0000000000 as its first ten digits (if there are no other free objects) and will always have 65535 as its 5-digit generation number. It also shall have 'f' as the character.  
```
xref

0 2
0000000000 65535 f
...........
```

If there are object(s) that have been deleted and are free then the ten digit number will be changed to denote the nth entry of the next free object. To make it easy to understand let's look at an example.
```
xref
0 4
0000000003 65535 f
0000000015 00000 n
0000000075 00000 n
0000000000 00005 f
```

The 0 4 denotes that there are four entries - Entry for object 0 followed by entries for objects 1, 2 & 3. The first ten digits (0000000003) of the first entry for object 0 points to the next free object, which is, object 3. If there had been another free object, then the 4th entry will have the object number of the next free object. In this case, as there are no other free objects it points back to object 0. Objects 1 & 2 are 15 & 75 bytes (respectively) away from the start of the file. This basically informs lets the PDF application know that object 3 is free and therefore it can be used to refer to another data.
 
Let's look at another example
```  
xref
0 4
0000000003 65535 f
0000000015 00000 n
0000000075 00000 n
0000000000 00005 f
9 2
0000000099 00000 n
0000000150 00000 n
```

In the above case, in addition to objects 0, 1, 2, 3 there are two other objects 9 & 10.
 
An object cannot be entered in more than one subsection within a section.
 
When an indirect object is deleted, its entry is marked as free (by changing the n to f) and linked to the linked list of free objects. It's generation number is increased by 1. The object's generation number gets updated each time the object gets deleted and can go upto a maximum of 65,535. For instance, an indirect object that was referenced as 1 0 will become 1 1 when reused.
 
Trailer: The end of a PDF file is read first by the PDF reading application. The trailer holds information about the location and details of the Cross-reference table. The trailer has three parts. The first part has the keyword trailer followed by a dictionary that holds values for certain fields.  
The second part has the keyword startxref, and in the next line, a number. The number denotes how far (in bytes) the keyword xref (of the last section of the cross-reference table) is from the start of the file. The very next line has the value %%EOF to denote the end of the file.  
A random PDF taken from my computer has this trailer. Looking at this trailer I can assume that the xref of the last section of the cross-reference table is found 361441 bytes from the beginning of the file. 
```
trailer
<< /Size 62 /Root 1 0 R /Info 2 0 R
/ID [(X$X@>66...)(X$X@>66...)]
>>
startxref
361441
%%EOF
```

The following keys are mandatory for the trailer dictionary.
 
**Size** - Total number of entries in the cross reference table (combination of original & update sections). The value has to be an integer. In the example above there are 62 entries including an entry for object 0.
 
**Root** - Is an indirect reference to the PDF's catalog (which we will learn later). In the example above, I can assume that the indirect object 1 is the catalog.
 
Some keys are mandatory when certain capabilities are used. We may look at the Info & ID keys later. 
 
**Incremental Updates**: The team that developed the PDF specification was smart enough to include a special feature. When a PDF gets updated, the changes are added to the end of the file rather than updating the original content. This feature saves time (as the whole file need not be modified). However, this also makes me wonder what happens when many changes take place. Does the size of the PDF file increase massively?
 
When a PDF gets an incremental update, in addition to the data being added, a new cross-reference section is created. This new section contains entries for all the objects that were deleted, replaced or changed. As we learnt earlier deleted objects have the 'f' letter at the end of the cross-reference entry. This means that if say object 5, existed before and was deleted during the update the new cross section will have the same entry but with 'f' as the last character in the entry for object 5.
 
When the PDF file gets updated, along with a new cross-reference section a new trailer is added. This contains all the entries from the previous trailer but will have a different value for the Prev entry in the dictionary. The Prev entry will have the location of the previous cross-reference section.
 
%%EOF will continue to be the last line for the new trailer as well. Hopefully we will discuss this in detail later.
 
**PDF Document Structure:**
The structure of a PDF file is like the different levels of hierarchy found in a typical company. Similar to the CEO, the Document Catalog dictionary sits at the top of the hierarchy. You can actually view the structure of a PDF using the PDFDebugger tool - I have included more details in this webpage http://www.printmyfolders.com/view-structure-of-a-pdf
 
As we saw earlier a PDF reading application will look at the trailer of the PDF first. The trailer will have a Root entry that has the location of the catalog. This is similar to a person (PDF reading application) approaching the CEO (Document Catalog) after finding her contact details via the contact section (Trailer) on the company's website (PDF file).
 
**Document Catalog: **
    + The Document Catalog is a dictionary that refers to other objects that define the PDF file. Basically, the Document Catalog is like the centre from where every information about the PDF file can be found. Being a dictionary it consists of various keys. We will  for the time being only look at the mandatory keys.
 
 
    + **Type** - will always be Catalog (type Name)
    + **Pages** - An indirect reference to the object that is the root of the page tree (will look at this later)
 
A PDF file that I created using a free PDF creating software has this Catalog Dictionary 
```
1 0 obj
<</Type /Catalog /Pages 3 0 R
>>
endobj
```

You will notice that each of these dictionaries always start with a '/Type' entry that descirbes what type of dictionary it is. In this case, it is a 'Catalog' dictionary.
 
An application that reads the above Catolog dictionary will know that it needs to read the 'Pages' dictionary (indirect object 3) to get information about the pages in this PDF file.
 
 
**Page Tree:**  Page Tree is the name of the structure used to describe the pages in a PDF file. It has two type of nodes - page tree nodes and page objects. Each page in a PDF file is represented as a Page object. Each of these objects is called as 'leaf' node in the Page Tree.
 
**Page Tree Nodes:** The mandatory keys are 
 
Type - will always be Pages for a Page Tree node
Parent - the page tree node which is this node's parent. Not allowed in root node.
Kids - an array referring to the children of this node. The children can only be page tree nodes or page objects
Count - the number of page objects that are descendants of this node
 
The PDF that I had created earlier has this page tree (remember that the Catalog Dictionary was pointing to indirect object 3). 
 
3 0 obj
<< /Type /Pages /Kids [
4 0 R
] /Count 1
/Rotate 0>>
endobj
 
This Page tree node has only one kid which is object 4. The Parent key is missing and therefore this is the root node.
 
As the /Count is 1, we can safely assume that there is only 1 page under this Page tree (which based on the /Kids array is indirect object 4.
 
As menioned earlier, you will notice that this dictionary too has an entry '/Type' that reveals what type of dictionary it is.
 
**Page Objects**: This is a dictionary that reveals the page itself characteristics. Some of the keys are 
 
Note: Most of the keys are new to me. I have purposefully left out keys that make no sense to me at this moment. As I learn more about the PDF specification I will hopefully cover them in detail. 
 
- Type - Will always be Page
- Parent - An indirect reference to the parent of this page
- LastModified - Date and time when this page was last modified
- Resources - The resources required by this page. This usually refers to the font used on this page and other info.
- MediaBox - A rectangle that defines the boundary inside which the page has to be displayed.
- Contents - A content stream that describes the contents of this page.
- Rotate - In multiples of 90. Rotates the page by the number of degrees before displaying.
- Thumb - A stream object that gives the thumbnail image for this page.
- Dur - the number of seconds the page will be displayed in presentations before automatically moving on to the next page.
- Trans - A dictionary advising what transition to use when displaying the page during presentation.
- Annots - This is an array of dictionaries containing references to all the annotations for this page
- AA - This is the short form for additional-actions. This dictionary defines the actions that need to be taken when the file is open or closed.
- Metadata - A stream that contains metadata for this page
  
Here is a grab from a sample PDF that I created using a free PDF creating software.
```
 
4 0 obj
<</Type/Page/MediaBox [0 0 595 842]
/Rotate 0/Parent 3 0 R
/Resources<</ProcSet[/PDF /Text]
/ExtGState 10 0 R
/Font 11 0 R
>>
/Contents 5 0 R
>>
endobj
 
3 0 obj
<< /Type /Pages /Kids [
4 0 R
] /Count 1
/Rotate 0>>
endobj
 
1 0 obj
<</Type /Catalog /Pages 3 0 R
>>
endobj
```

As you can see Object 1 is the catalog that directs the PDF reading application to the root of the page tree (Object 3). Object 3, the root node had only one kid (Object 4) and obviously cannot have a parent. Object 4 is 'displayed' within a rectangle (0 0 595 842) and is not rotated (Rotate 0) and has Object 3 as its parent. It's 'resources' as well as its contents (Object 5) are included. Here is Object 5 from my file.
 
As we had discussed earlier, the stream in this object starts with a dictionary that shows the length of the stream (which is stored in Object 6). We will discuss more about Content streams further down. 
``` 
5 0 obj
<</Length 6 0 R/Filter /FlateDecode>>
stream
xMK.1.鶵u*j.czi2& 7KnSK..Z?]."6.3w>^&s@MQ...K.d\>}q...    ).|.ѣ'o1lA.ۥ
S-lE,.C.W.&#xf01d2;YGKM\vjEG.'|F[j.:..2f2Ź^.uujNWǌY::si/.L9,ČGPY1k/.%'f!endstream
endobj
``` 
**Page attributes are inherited**: Here is an interesting fact. Certain attributes in a page can be inherited from its parent or any of its ancestors in the page tree. The eliminates the need to keep repeating similar attributes for every child, grandchild etc. If an ancestor defines a value for an attribute, that value can be replaced or changed by the child.
 
**Name Dictionary:** Rather than referring to the objects by their references, some objects can be referred to by their names. The link between the names and their references is stored in the PDF file's name dictionary. One of the optional keys in the Catalog, Names is used to used to specify the Name Dictionary. Please refer to the PDF specification for more details.
 
**Content Streams:** This is a stream (an object in PDF, if you remember) that has instructions on how to display text & graphics on the corresponding page. In Object 5, of my PDF file, mentioned earlier and repeated below we can see a stream. This stream gives the PDF reader (for instance Adobe Reader) the instructions on how to display.
```
5 0 obj
<</Length 6 0 R/Filter /FlateDecode>>
stream
xMK.1.鶵u*j.czi2& 7KnSK..Z?]."6.3w>^&s@MQ...K.d\>}q...    ).|.ѣ'o1lA.ۥ
S-lE,.C.W.&#xf01d2;YGKM\vjEG.'|F[j.:..2f2Ź^.uujNWǌY::si/.L9,ČGPY1k/.%'f!endstream
endobj
```

The data in the stream makes no sense because the data has been encoded (converted from its original form to another). In the following sections we will look more in detail about the structure of these data and understand how they form instructions for the PDF reading application to display the page.
 
Note that unlike other objects in a PDF file, the instructions in the object stream are read and followed sequentially (one after the other).
 
Before proceeding further we will try to create a simple PDF file from what we have learnt so far.
 
Sample PDF file: Here is a sample PDF file that I created with help from the specification. You can copy this file from here and save it in a text editor like notepad. Save it with a filename but with a file extension "pdf". In notepad, you will have to save as "filename.pdf" (Quotes inclusive). You can then view it with a PDF reader (for instance using Acrobat Reader). Note: Not all PDF files are as simple as this. This PDF file that is very basic and just displays a single line of text.

Article continues at Understanding the Portable Document Format (PDF): Part 2
 
 
I love your feedback and suggestions. Please leave a comment below or contact me at steve@printmyfolders.com.


## Sample pdf
Here is a sample PDF. Copy all the text from the % all the way till the EOF. Place it in a text editor and save it as a file with an extension PDF. With notepad you will have to save as "filename.pdf" (quotes inclusive). Once saved, you can view it with Acrobat reader.

```
%PDF-1.4
1 0 obj
<</Type /Catalog
/Pages 2 0 R
>>
endobj
2 0 obj
<</Type /Pages
/Kids [3 0 R]
/Count 1
>>
endobj
3 0 obj
<</Type /Page
/Parent 2 0 R
/MediaBox [0 0 500 500]
/Contents 5 0 R
/Resources <</ProcSet [/PDF /Text]
/Font <</F1 4 0 R>>
>>
>>
endobj
4 0 obj
<</Type /Font
/Subtype /Type1
/Name /F1
/BaseFont /Helvetica
/Encoding /MacRomanEncoding
>>
endobj
5 0 obj
<</Length 53
>>
stream
BT
/F1 20 Tf
120 120 Td
(Hello from Steve) Tj
ET
endstream
endobj
xref
0 6
0000000000 65535 f
0000000009 00000 n
0000000063 00000 n
0000000124 00000 n
0000000277 00000 n
0000000392 00000 n
trailer
<</Size 6
/Root 1 0 R
>>
startxref
502
%%EOF
```