
## Raw data

``` sql
select *
from gtd
where
  region_txt in (${region:sqlstring}) and
  country_txt in (${country:sqlstring}) and
  attacktype1_txt in (${attack_type:sqlstring}) and
  weaptype1_txt in (${weapon:sqlstring})
order by iyear, imonth
```

To discuss:

- Organize/Hide/Rename fields (boolean with ?)
- Value mapping for booleans
- Overrides created automatically by resizing column width
