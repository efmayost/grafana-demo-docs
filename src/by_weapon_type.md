
## Total events - by weapon type

``` UQL
parse-csv
| where "weaptype1_txt" in (${weapon:singlequote})
| project "iyear", "weaptype1_txt"
| summarize count() by "iyear"
```

To discuss:

- The repeat option
- Thresholds
- Filtering with the filter hides all other repeated panels
- Can only edit the first panel as the rest are dependant on it
