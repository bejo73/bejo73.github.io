Hur skapar man en connection sträng i BizTalk?
Data Link Properties

My question is, is there any way to test the connection to a remote SQL server 2005 database from biztalk?

Go to any file folder but preferably the one containing your mapping project/files.
Create a text file and name it "DBConnection.udl". (The important part is the extension .udl)
Double click the file.
On the Provider Tab, select SQL Native Client (this assumes it is installed), then Next
For Data Source, enter yours: HPSQL05T
Initial Catalog, TESTDB
Either use integrated security or click allow saving password
Test Connection...OK
In your map, either drop a String Concatenate functoid or add the following to the Database Lookup functoid as the second paramter.
File Name=
example: File Name=C:\Project\Database\DBConnection.udl
Configure the rest of the Database functoid(s) input(s), but at least a Value Extractor, and connect it to output so you can see the results.
Test your map.
