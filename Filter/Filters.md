# Filters





# Black List
```

```

# White List
```
if (!preg_match('/^[a-z]+$/i', (string) $_GET['xss']))
{ // Something other than letters were provided!
  die("This hacking attempt has been logged .."); //Abort Processing
}
```


# Output Encoding
```
<span class="" . htmlentities($_GET['xss'], ENT_QUOTES, "UTF-8") . "\">test</span
echo "<a href=\"http://site.com/?test=" . urlencode($_GET['xss']) . "\"> test </a>";
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
