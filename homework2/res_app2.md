# Research on Application 2 - The CSV protocol (definition and rules)

A file with Comma Separated Values, also called CSV file, is an easy way to represent data in a tabular way within a simple text file. In fact, the file basically consists in a sequence of lines, each of them corresponding to a certain unit. In each line there is a list of values, the attributes of the unit, separated by a comma (hence Comma Separated Values). Because of its simplicity and immediacy, it's still today widely used to store and exchange data of any kind.

A problem that the CSV file format has is that it lacks a real standard that formalizes it in all its charateristics. Hence, we can find different ways to write data in the CSV format. To solve this, the RFC 4180 was written: it is a document that, although recognising the existence of many implementations, summarizes those charateristics that seem to be followed by most of those implementations. The features that the document reports are the following[1]:

1. Each record is located on a separate line, delimited by a line break (CRLF). For example:

       aaa,bbb,ccc CRLF
       zzz,yyy,xxx CRLF

2. The last record in the file may or may not have an ending line break. For example:

       aaa,bbb,ccc CRLF
       zzz,yyy,xxx

3. There maybe an optional header line appearing as the first line of the file with the same format as normal record lines. This header will contain names corresponding to the fields in the file and should contain the same number of fields as the records in the rest of the file. For example:

       field_name,field_name,field_name CRLF
       aaa,bbb,ccc CRLF
       zzz,yyy,xxx CRLF

4. Within the header and each record, there may be one or more fields, separated by commas. Each line should contain the same number of fields throughout the file. Spaces are considered part of a field and should not be ignored. The last field in the record must not be followed by a comma. For example:

       aaa,bbb,ccc

5. Each field may or may not be enclosed in double quotes (however some programs, such as Microsoft Excel, do not use double quotes at all). If fields are not enclosed with double quotes, then double quotes may not appear inside the fields. For example:

       "aaa","bbb","ccc" CRLF
       zzz,yyy,xxx

6. Fields containing line breaks (CRLF), double quotes, and commas should be enclosed in double-quotes. For example:

       "aaa","b CRLF bb","ccc" CRLF
        zzz,yyy,xxx

7. If double-quotes are used to enclose fields, then a double-quote appearing inside a field must be escaped by preceding it with another double quote. For example:

       "aaa","b""bb","ccc"

Although the RFC 4180 lists those features for the CSV format, it also states (as previously mentioned) that this list of features isn't meant to define a precise standard, but just wants to point out the common points amongst various implementations. Thus the CSV format remains widely used but not precisely defined.

For instance it happens very often that, although the name himself of the file mentiones commas, the values in the lines are separated by a different separator: a common alternative to the comma (",") is the semicolon (";"), but we can also find CSV files with values separated by a simple space (" "). This of course can create problems of various kinds when parsing the file. Because of that the softwares or the libraries that parse CSV files often ask, as parameters, info on the file they are going to parse in order to avoid errors of any kind.

**References** \
[1] [https://www.rfc-editor.org/rfc/rfc4180](https://www.rfc-editor.org/rfc/rfc4180) \
[2] [https://www.html.it/articoli/file-csv-cosa-sono-come-si-aprono-e-come-crearli/](https://www.html.it/articoli/file-csv-cosa-sono-come-si-aprono-e-come-crearli/)