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
