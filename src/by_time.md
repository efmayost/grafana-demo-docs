
## Total events - by time

### By year (bar)
``` sql
select iyear as year, count(*) as total from gtd group by iyear
```

Options to discuss:

- X Axis label rotation
- Tooltip
- Legend
- Overrides

### By month (bar)
``` sql
select cast(imonth as decimal) as month, count(*) as total from gtd where imonth!=0 group by month
```

Or:

``` sql
select
  case imonth
    when 1 then 'Jan'
    when 2 then 'Feb'
    when 3 then 'Mar'
    when 4 then 'Apr'
    when 5 then 'May'
    when 6 then 'Jun'
    when 7 then 'Jul'
    when 8 then 'Aug'
    when 9 then 'Sep'
    when 10 then 'Oct'
    when 11 then 'Nov'
    when 12 then 'Dec'
  end as month,
  count(*) as total
from gtd
where imonth!=0
group by month
order by cast(imonth as decimal)
```

To discuss:

- The difference between filtering in the query and Transform Data (transform happening BEFORE visualisation)
- Value mappings as an easier way than case/then in sql query
- The difference between the types of imonth and month and the need for casting for ordering correctly.

### By weekday (table)

``` sql
select case strftime('%w', printf('%04d-%02d-%02d', iyear, imonth, iday))
           when '1' then 1
           when '2' then 2
           when '3' then 3
           when '4' then 4
           when '5' then 5
           when '6' then 6
           when '0' then 7
       end as weekday_name, count(*) as total
from gtd
where imonth!=0 and iday!=0
group by weekday_name
order by weekday_name
```

To discuss:

- Explain why we are using case/then here
- Cell options gauge - Retro LCD

