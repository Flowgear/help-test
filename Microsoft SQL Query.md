Microsoft SQL Query
Executes SQL queries against an MS SQL database and returns the result set as an XML document.

 

Revision History
1.0.0.0 Initial Release
3.0.0.6 Minor updates & bugfixes. Also properly supported assigning null values on simple types (Guid, DateTime, numeric, etc)

3.0.0.14 Added support for custom connection string fragments

 

 

Properties
Connection
Type: Connection Input

Server
Type: String
The name or IP address of the server hosting the Microsoft SQL Server instance. Specify a DropPoint if you need to access a SQL instance that is not Internet-exposed.

Database
Type: String
The name of the database to connect to.

UserId
Type: String
The SQL username to be used for the connection. Not required when UseWinAuth is True.

Password
Type: Password
The SQL password to be used for the connection. Not required when UseWinAuth is True.

UseWinAuth
Type: Boolean
When True, indicates that the security context of the caller should be used to authenticate. In Flowgear, UseWinAuth can only be used when the Connection is routed through a DropPoint. In such instances, the security context is the service account used for the DropPoint Windows Service.
Provides an endpoint and credentials for the SQL instance to be queried

ConnectionStringFragments
Type: String

Provide a list of extra connection string fragments that are not part of the standard connection properties. The fragments must be in the format key=value and different fragments should be listed underneath each other. 

 

Query
Type: Multiline Text Input
The SQL query text


 

XmlQuery
Type: Boolean Input
When True, indicates that the query provided in the Query property is an XML Query (ie. a query containing the FOR XML statement - refer to http://msdn.microsoft.com/en-us/library/ms178107.aspx for more information on XML queries).


 

ResultXml
Type: Xml Output
The ResultXml Property


 

RowsAffected
Type:Int32 Output
This return the number of rows returned by SQL. Note that for Xml Query, this is not accurate because the xml string gets split into rows in the result, which is consolidated in the node.


 

Remarks
Use this Connector to execute SQL queries against a Microsoft SQL Server instance. 

 

SQL Parameters via Custom Properties

Flowgear Custom Properties can be added to this Node to make SQL parameters available in the Query Property. Use of a Custom Property is shown in the linked example workflow (see Examples below).

 

XML Mode

In XML Query mode, the Connector will automatically build a single XML document from the multiple result-set rows that may be returned.

 

Other Nodes for SQL databases

If you are updating values in a table based on keys, consider using SQL Table Update instead of crafting update statements.

 

If you need to integrate with a non-Microsoft SQL database, refer to Integrating with SQL Databases for additional information and connection strings.

 

 

 

Examples
See https://flowgear.me/s/td7DRDb for an example.
See https://flowgear.me/s/jUHzlOP for an example of how to safely use an IN-clause.
See https://flowgear.me/s/zDCFM3N and https://flowgear.me/s/PuUSi5c for an example to request and emit a single page of data respectively.

 

See Also
MySQL Query
ODBC Query
OLEDB Query