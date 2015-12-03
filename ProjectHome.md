this page is under construction

## Introduction ##

Cog is a PHP based, minimalistic web framework, targeted for rapid website development.

## Modules ##

### config ###

Contains the configuration file for:

  * modules
  * sql connection
  * e-mail alert for site failure
  * path, and domain of running code

### cog\_database ###
Database interface. Basic utility is to clone a .NET-like, SQL-safe interface, where one might issue commands like:

<i>update mytable set name=@name, var1 = @var1 where id = @id</i>

with a parameter array containing name, var1, id; and have the rest of the operations (string escaping, query resolving) issued automatically.

Public functions:

**void initsql(void)**

Initalizes the database connection based on the configuration object ($g\_cfg).

**array gettable(string $query, array $vals = null)**

Resolves the query using vals, and returns the result of the select in an array.

Example:

**gettable("select _from payments where amount > @minamount",
> array("minamount" => 10) );_**


**bool dbcommit(string $query, array $vals = null)**


**bool dbinsert(string $table, array $fields, array $funcs = null)**


### cog\_scriptor ###

Scriptor takes an array of data from the PHP back-end, and a template file, and generates the HTML output for display. Other than substituding each < %data% > with it's respective value, Scriptor also features the following special tags:

**< cog: if name="varname" value="varvalue" >**

The content will be rendered, if <i>varname</i> exists in the datalist, and it's value equals to <i>varvalue</i>.

**< cog: iterator datasource="source" >**

Iterates through an array given as <i>source</i>, and for each element, renders the content, substituding variables within the array.

**< cog: form name="myform" action="" method="post" >**

Generates a cross-site scripting (<a href='http://en.wikipedia.org/wiki/Cross-site_scripting'>XSS</a>) safe, validatable form.

**< cog: validator func="func" target="name" >**

Validates <i>name</i> posted parameter by passing it into validator<i>func</i>, and checking return value; content of the tag is rendered, if validation fails.

## How does it all fit together ##

## Sites, that use cog ##

## Support ##

## License ##
Cog is licensed as **Public Domain**. You can do whatever you want to do with it, including using it for commercial websites.

## Samples ##

## Downloads ##