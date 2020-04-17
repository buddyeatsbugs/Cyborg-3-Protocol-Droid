# Filters





# Black List
```

```

# White List
```

```


# Output Encoding
```
<span class="" . htmlentities($_GET['xss'], ENT_QUOTES, "UTF-8") . "\">test</span
echo "<a href=\"http://site.com/?test=" . urlencode($_GET['xss']) . "\"> test </a>";
```
