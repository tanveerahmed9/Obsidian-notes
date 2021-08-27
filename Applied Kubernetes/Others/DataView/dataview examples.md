

```dataview
list from #Go 
```

//lets check where 
```dataview
list from #datatyype  
where file.size > 200
```


// use table

```dataview
table file.path
from #Go  
```

// contains 
```dataview
list 
where contains(file.name, "Data")
```

// contains with tags metadata (Authored by Tanveer Ahmed)


```dataview
list 
where contains(authors,"Tanveer Ahmed")
```


//regex 

```dataview
list 
where regexmatch("some regular expression",authors)
```


//length function


```dataview
list
where length(file.tags) = 2
```


// sum function 

```dataview
 table sum(Studied) as TotalReadTimeinMinutes
```



