## Gretting Started
1. The basic building blocks of a PDF files are objects
2. There are eight types of objects that are used in PDF files.

### Character:
1. There are 3 types of characters: `white-space`, `delimiter` and `regular characters`.
2. White-space characters:
    + Null, Horizontal tab, Line feed(EOL), Form feed, Carriage return(EOL) and Space.
3. Delimiter characters:
    +  (, ), <, >, [, ], {, }, / and % (4 pairs and 2 unique).
    + These are used in the objects we would look at later
    + They basically act as delimiters (mark the boundary or border) for entities. 
    + Tip: If you need to remember them, imagine these characters ( ) being bent < > and then stretched [ ] and then bent again { } and then eventually made flat / %. 
4. Regular characters:
    + All characters other than White-space and Delimiter characters including those that are not part of the standard ASCII character set
    + An interesting fact to note is that a PDF may consist entirely of just ASCII characters or can consist of ASCII characters and Binary data
    + In simple terms, characters in ASCII files use only 7 out of the 8 bits in a byte while characters in the Binary files use all the 8 bits in the byte
    + This allows a possibility of 128 unique characters for ASCII files and 256 unique characters for Binary files
    + Most PDF files that are encrypted or contain images will have binary data (images are represented in binary)
    + PDF files that contain binary data get corrupted when edited or even opened and saved in normal text editors like Notepad
    + It is critical that we understand the difference between ASCII and Binary files as other areas of the PDF specification touch on them.

    + You may also wonder why you don't see any text (that can be seen when opened using a reader) or its equivalent when opening a PDF file in a text editor or even binary editor. There may be two reasons.
    + The first and most common reason is that the content stream (where the text is stored/kept) is encoded (transformed/changed) to conserve space
    + This is what happens with most files.The second reason could be that the PDF file is encrypted purposely to keep the text secure.

### Objects:
Here are the objects that make use of the characters we looked at above.
Each of these objects have a corresponding class in PDFBox. Have a look at this link https://pdfbox.apache.org/1.8/architecture.html under the section "The COS  Model"

1. Boolean objects: 
    +The keywords true and false. 

2. Numeric objects: 
    + There are two types; integer & real.Integers are numbers without any decimal points and can have a + or – symbol preceding it.  For instance, the number 10. Real numbers must have a decimal point. For instance, 10.5, 0.0, +5.0, -1.0. Real numbers cannot be expressed in exponential format. 

3. String Objects: 
    + Strings contain characters (can be zero characters as well). They can be literal characters within parenthesis or hexadecimal data within angle brackets. Notice that the parenthesis and angle brackets are delimiter characters.  

4. Name Objects
5. Array Objects:
6. Dictionary Objects
7. Stream Objects
    + Length - Mandatory entry
    + Filter
    + DecodeParms
    + F
    + FFilter
    + FDecodeParms
    + DL
8. Null object

## Other components of a PDF file
1. Comments:
    + The comment is represented by the percentage sign i.e. %. This is commonly used to describe the version of PDF specification used in creating the PDF file.
    + `%PDF-1.7`
2. Indirect Objects: 
    + An object (for example, a string) that has been given a unique object identifier, that other objects can use to refer to itself is called an indirect object. This is different from the 'Name' object that we looked at earlier. Looking at any PDF file in its raw form (for instance, by opening it in a text editor) you will notice lots of indirect objects.

    + The identifier has two parts. The first part is the object number that can be any positive integer. The second part is the generation number which is always zero in the first non-updated version of the PDF file. You declare an indirect object within the keywords ‘obj’ and ’endobj’. Be aware that the combination of the object number and generation number has to be unique. 
    ```
    1 0 obj

    (my biography)

    endobj
    ```

### File Structure:
A PDF file will initially have the following structure.
1. A Header (not more than a line) showing the PDF specification this file follows.
    + `%PDF-1.2`
    + If the file has binary data, there will be at least four binary characters, immediately after the header.
2. A File Body that has the objects of the file
    + consists of indirect objects
    + These objects represent text and other details (like font type etc.) used in displaying PDF
    + As of version 1.5, the body can also contain object streams.

3. A Cross-reference table that has info about indirect objects
    + This table is similar to a directory
    + It contains the location of each object within the PDF file.
    + By looking at the entries in this table, the PDF reading application (for example, Adobe Reader), can easily locate an object within the file
    + Each section begins with the word 'xref'.
    ```
    xref

    0 5
    ```
4. A Trailer that shows the location of the cross-reference table and special objects within the body of the file. 
    + The end of a PDF file is read first by the PDF reading application
    + The trailer holds information about the location and details of the Cross-reference table. The trailer has three parts
    + The first part has the keyword trailer followed by a dictionary that holds values for certain fields.  
    + The second part has the keyword startxref, and in the next line, a number. The number denotes how far (in bytes) the keyword xref (of the last section of the cross-reference table) is from the start of the file. 
    + The very next line has the value %%EOF to denote the end of the file.  

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
    + `Size` - Total number of entries in the cross reference table (combination of original & update sections). The value has to be an integer. In the example above there are 62 entries including an entry for object 0.
    + `Root` - Is an indirect reference to the PDF's catalog (which we will learn later). In the example above, I can assume that the indirect object 1 is the catalog.

5. Incremental Updates: 
    + The team that developed the PDF specification was smart enough to include a special feature. When a PDF gets updated, the changes are added to the end of the file rather than updating the original content. This feature saves time (as the whole file need not be modified). However, this also makes me wonder what happens when many changes take place. Does the size of the PDF file increase massively?

6. Document Catalog:
    + The Document Catalog is a dictionary that refers to other objects that define the PDF file. 
    + Basically, the Document Catalog is like the centre from where every information about the PDF file can be found. Being a dictionary it consists of various keys. 
    + We will  for the time being only look at the mandatory keys.
    + `Type` - will always be Catalog (type Name)
    + `Pages` - An indirect reference to the object that is the root of the page tree (will look at this later)

    + A PDF file that I created using a free PDF creating software has this Catalog Dictionary 
    ```
    1 0 obj
    <</Type /Catalog /Pages 3 0 R
    >>
    endobj
    ```