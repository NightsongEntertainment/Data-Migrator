About
=====
Processes the official data dump from CCP in to a format which is a little nicer for rails to consume.

Source Trees
============
Since the ruby version runs cleanly on *some* tables, but not others (this is related to TinyTDS and my 
local server version). I have started an implementation in C# using a native MySQL driver to perform the 
inserts. The ruby logic may be found in /ruby and C# in /C#.

C# Requirements
===============
* [MySQL](http://dev.mysql.com/downloads/mysql/) Instance (v5 or newer)
* MSSQL Server Instance (2005 or newer)
* Pre-defined mysql database with the appropriate rails schema
* Pre-defined mssql server database with the CCP data loaded
* (C# Express 2010)[http://www.microsoft.com/visualstudio/en-us/products/2010-editions/visual-csharp-express]
* MySQL (.NET Connector)[http://dev.mysql.com/downloads/connector/net/]

C# Setup
========
1. Open the sln
2. Done.

C# Execution
============
1. Uncomment the appropriate processors in Program.cs
2. Build / Execute

**DEPRECATED**
==============
The ruby code is old and will _not_ work. All of the models are finished here, but cannot be executed 
(limitation of Ruby / tinytds gem).

Ruby Requirements
-----------------
* Local MySQL Instance (v5.0.3 or newer)
* Remote MSSQL Server Instance
* Pre-defined mysql database with the appropriate rails schema
* Pre-defined mssql server database with the CCP data loaded
* Ruby 1.9.2
* RVM

Ruby Setup
----------
```bash
brew install freetds
rvm 1.9.2@eve_migrator --create
bundle install
```

Ruby Execution
--------------
**WARNING: Any tables that are being loaded will remove all current data before loading the new data. Consider commenting out classes that are "good"**

```bash
be ./process.rb
```
