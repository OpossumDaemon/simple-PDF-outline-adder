# simple-PDF-outline-adder

A simple tool for adding an outline to PDF files that do not contain one using a rather simple and convenient input file
where you put a table of contents with their page numbers and section depth (i.e. whether an outline entry is a chapter,
section, subsection, etc). This tool can also modify the page offset so that the PDF numbers match those of the book. 

Useful for huge digital books (frequently legally scanned books) where
you would get easily tired of finding a page from the table of contents pages and the books' page number does
not match that of the PDF reader.

## Why does this tool exist?

Being a physics's student, it's pretty usual for me to find books that don't contain an outline in the PDF file,
which was a pet peeve whenever I want to access a certain chapter or subsection of the book,
and I didn't like the Ghostscript's way to add them, so I decided to create this simple tool for myself and then
release it for anyone that finds it useful.

## Requisites

Your computer must have the Ghostscript interpreter (gs for UNIX/Linux, gswin32c for Windows) and Python 2.7 installed. At 
least this is how I tested it.

## How do I use it?

First you need to create an outline file with your favourite text editor. The format looks kinda like this:

```
base b

p1 Put text here for chapter 1
 p2 Put text here for section 1.1
 p3 Put text here for section 1.2
  p4 Put text here for subsection 1.2.1
 p5 Put text here for section 1.3
p6 Put text here for chapter 2
 p7 Put text here for section 2.1
```

p1, p2, p3, etc (which are integer numbers) are the page numbers that you would see in the book's table of contents and
you want to go when you click in the outline entry of the PDF reader. As you may have noticed, the section levels are
created by separating them with spaces (or tab characters if you want).

The "base" statement (also an integer number) tells the program which PDF page to point at when adding the outline entries
below it. By default the base starts as 0.

After you're done creating the outline, you must call the tool from the command line:

```
python create_outline_pdf.py input_pdf_file outline_file output_pdf_file 
```

After this, you can see the output PDF file containing the outline.

You can refer to the example files example.pdf and example_outline. In this case you must enter this in the command line

```
python create_outline_pdf.py example.pdf example_outline example_output.pdf
```

## Limitations

This tool doesn't seem to support Unicode characters, only ASCII

## License

This tool is public domain so do whatever you want with it. I'd appreciate you giving me credit though.
