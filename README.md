admin = Admin.new()
admin.first_name = <First Name>
admin.last_name = <Last Name>
admin.email = <Email Address>
admin.username = <no less than 8 characters>
admin.password = <your password>
admin.save

staff = Staff.new()
staff.first_name = <First Name>
staff.last_name = <Last Name>
staff.email = <Email Address>
staff.username = <no less than 8 charachters>
staff.password = <your password>
staff.save
```

6. Run Server:
```
rails server --port:4200
```

7. Open your browser, navigate to:
* 'localhost:4200' for public access
* 'localhost:4200/admin' for admin access & login using admin account created above
* 'localhost:4200/staff' for staff access & login using staff account created above


## Project Architecture
Rails-Crud project is a sample online rental store, which makes use of sample database [sakila](https://dev.mysql.com/doc/sakila/en/) with a few table additions.

#### Project uses following tables from sakila database:
* Table Name
* Actor
* Address
* Category
* City
* Country
* Customer
* Film
* Film Actor
* Film Category
* Inventory
* Rental


#### Added tables:
* Admin
* Customer Payment Info
* Rental Pending
* Staff


#### Tables are inter-connected through foreign keys or through other tables, and those connections are defined in project's app/models:

| customer              	| order 				| products	                | address                                	
|-------------------------------|---------------------------------------|-------------------------------|---------
| varshini			| order no:567			        | SKU:	                        |					  	
| 8765439879 			| date of order:10/09/23		| MRP:$56	                |						
| amruthavaesh123@gmail.com 	| order status:completed	        | quality:5			| 				
| rajajinagar,blore-10 		| billing and shipping address:blore-10	| discount and net price:0-$56	| 						


#### The project has 3 category of participants with their functions:

* Public: reads `film, actor` tables, creates account in `customer` table, places order by creating row in `rental_pending` table (before checkout, application requires to create an account)
* Staff: reads `rental_pending` table, processes order by locating item from `inventory` table, ships item to customer's address & creates record to `rental` table
* Admin: creates, reads, updates, deletes `actor, film, customer, staff` tables

