Understanding the Portable Document Format (PDF): Part 2

 

We covered a bit of the PDF specification in the previous article Understanding the Portable Document Format (PDF). One of the areas that I had purposely failed to cover was Filters. Filters are an interesting topic altogether. My technical knowledge about filters again is very minimal but I will try to explain what they do with whatever info I have. 


What are Filters?

Filters in simple terms are algorithms that convert encoded data back to their original form. 

For instance, when creating a new PDF file that contains some text, I might have encoded (changed) my data to a bunch of characters that make no sense but save a lot of space and overall reduce the size of my PDF file. When I send this file to a friend and he/she tries to open it using say PDFBox, the program will have to use a specific filter to decode (change back to the original form) my data to its original form - with no loss whatsoever - In fact, there are some algorithms that result in data loss but these algorithms are for images and not for text. These filters are called Decompression filters.

There are other algorithms that convert data to ASCII text. This is primarily for environments that accept ASCII text only - we discussed in Part 1 about the need to convert binary data to ASCII data for some environments. These algorithms result in ASCII text that are larger in size than the original data. There are filters that convert these ASCII text back to their original format. These filters are called ASCII filters. 

Note that there is no use of ASCII filters if the file in encrypted.

Filters used in PDFs:

These are the filters used in PDFs. The first two are ASCII filters.

ASCIIHexDecode
ASCII85Decode
LZWDecode
FlateDecode
RunLengthDecode
CCITTFaxDecode
JBIG2Decode
DCTDecode
JPXDecode
Crypt

Linking Filters:

Note that filters can be linked together. Assuming that some data was encoded using the LZW method and then encoded again in ASCII base-85, the encoded data will have to decoded first by the ASCII85Decode filter and then by the LZWDecode filter.


I will keep updating as I learn. Meanwhile, refer to this link http://www.adobe.com/devnet/acrobat/pdfs/PDF32000_2008.pdf for more details (Page 22 onwards).

I love your feedback and suggestions. Please leave a comment below or contact me at steve@printmyfolders.com.
