# Secure-Online-Banking-Application-in-ASP.NET-MVC-Architecture-using-Entity-Framework
Secure Online Banking Application in ASP.NET MVC Architecture using Entity Framework


Readme

This is the OnlineBankning application as implemented by Dinsmore and Sahai, this application 
is designed to execute in an IIS 7.0 environment with a SQL server database.
Set the connection string for the Default Connection in the Web.config file.
Typically, this is set to:
<add name="DefaultConnection" connectionString="Data Source=(LocalDb)\v11.0;Initial Catalog=OnlineBanking;Integrated Security=SSPI" providerName="System.Data.SqlClient" />
This will give you a local database using windows security. Note that depending on your set-up
you may need to manually create the database, but the application will use the Entity Framework
Code First mechanisms to create the required tables and populate them with a set of test data.

The test data includes three customers 123:
Ken@email.com
Sangam@email.com
Jayson@email.com

Each customer has two accounts:
Ken-123C and Ken-123S are Kens checking and savings accounts;
Sangam-123C and Sangam-123S are Sangams checking and savings accounts;
Jayson-123C and Jayson-123S are Jaysons checking and savings accounts;

Each account has one or more transfer transactions that affect it.
Each account has one alert defined.
Each checking account has a check image associated with it, but the requirements did not allow for check transactions, so they are not associated with a real transaction, and that is one of the use cases that was not implemented.

Run the application and register with a user based on the email addresses above. This will create a login that is associated with the customer record. Then run the following script to
add the required roles to the database and associate the new user with the role(s). Note that this will add the user to both the Customer and the Operator role. In a production environment,
this would be an unlikely scenario, but for demonstration it is more convenient.

select * From AspNetRoles
Select * from AspNetUsers
Select * From AspNetUserRoles
Insert Into AspNetRoles (Id, Name) Values ('0BDA489D-8B8D-480F-BD6B-0707B488A811', 'Customer')
Insert Into AspNetRoles (Id, Name) Values ('DAC8057B-17AA-4AD5-84AC-D5CD2FBC94D7', 'Operator')
Declare @UserID NVarchar(50)
Select @UserID = Id From AspNetUsers Where UserName = 'Your user name here'
Insert Into AspNetUserRoles (UserId, RoleId) Values (@userId, '0BDA489D-8B8D-480F-BD6B-0707B488A811')
Insert Into AspNetUserRoles (UserId, RoleId) Values (@userId, 'DAC8057B-17AA-4AD5-84AC-D5CD2FBC94D7')


Once this is complete, you must log out of the application, then log back in to have access to your roles.
Note that not all of the use cases have been implemented due to lack of participation by one of our team members.

For a detailed view of the class documentation, see ClassDocumentation.chm in the root folder.
For a detailed description of the security mechanisms that have been used, see "Security related features of the OnlineBanking web application.docx".

