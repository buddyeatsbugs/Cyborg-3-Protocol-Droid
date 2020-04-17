# Filters





# Black List
```
if(preg_match("/<!DOCTYPE/i", preg_replace("/\s/", '', $xml_string))) 
{//DOCTYPE found
  die('Invalid XML ...'); //Abort processing
}
```

# White List
```
if (!preg_match('/^[a-z]+$/i', (string) $_GET['xss']))
{ // Something other than letters were provided!
  die("This hacking attempt has been logged .."); //Abort Processing
}
```


# Output Encoding / Language Specific Functions for Filtering
```
<span class="" . htmlentities($_GET['xss'], ENT_QUOTES, "UTF-8") . "\">test</span
echo "<a href=\"http://site.com/?test=" . urlencode($_GET['xss']) . "\"> test </a>";
```

# PHP Language Specific Functions for Input Validation
```
1. 
$sql = "INSERT INTO test_table VALUES (?, ?, ?, ?)"; //No user-input in the SQL query string
$sql_statement = $mysqli->prepare($sql);
$sql_statement->bind_param('dsss', $user_id, $name, $address, $email);//Tell the library which variable goes to which part of the query
$user_id = $_POST['user_id'];
$name = $_POST['name'];
$address = $_POST['address'];
$email = $_POST['email'];
$sql_statement->execute(); //Executes the query in the database

2. 
if (!$mysqli->set_charset("utf8")) {//IMPORTANT: Set the charset to escape properly later!
die('...'); //Connection to DB failing
}
$user_id = $mysqli->real_escape_string($_POST['user_id']);//Escape user input
$name = $mysqli->real_escape_string($_POST['name']); //Escape user input
$address = $mysqli->real_escape_string($_POST['address']);//Escape user input
$email = $mysqli->real_escape_string($_POST['email']); //Escape user
input
//Now user-input is in the string, but it is escaped, and all values
are surrounded in quotes!

```

# Casting
```
$number = (string) $_GET['number']; //Cast to String to avoid "[]" PHP converting it to an array
if ( !preg_match('/^\d+$/', $number)) 
{   //This is not a number
    die('Invalid Number!..'); //This is an attack
}
$number = (int) $number; //Safely cast the number to an int, incase there is a mistake earlier in the process
//Finally output encode the value
echo "<html><head><meta charset="UTF-8"></head>
<span class=\"test" . htmlentities($number, ENT_QUOTES,"UTF-8") . "\"> test </span>
</html>";

```
