### Digital-Media-Store-Analysis-with-SQL 

This is an analysis of a digital media store's data using SQL.

**Data**

![chinook_schema](https://user-images.githubusercontent.com/97487571/217852297-ed2eb123-01e7-476c-a9a5-3eb76dc35c1a.png)


The Chinook data model represents a digital media store, and it contains 11 tables;

* album
* artist
* customer
* employee
* genre
* invoice
* invoice_line
* media_type
* playlist
* playlist_track
* track

 **Sample Data**
 
Media related data was created using real data from an iTunes Library. Sales information was auto generated using random data over a four year period. Customer and employee information were manually created using fictitious names, addresses that can be located on Google maps, as well as postal_code,email, phone, fax.

**Background**
The name chinook is based on the Northwind database. Chinooks are winds in the interior West of North America, where the Canadian Prairies and Great Plains meet various mountain ranges. Chinooks are most prevalent over southern Alberta in Canada. The chinook database was created as an alternative to the Northwind data.

**Analysis**
The chinook db provides information on a music digital store. I analyzed the data with SQL in order to get some insight into how the business is doing.

The jupyter notebook; chinook.ipynb contains the queries and visualizations, while the chinook.sql file contains the queries. You can run either of these on your local machine.
