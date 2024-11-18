
## Total events - by location

### By region (Pie)
``` sql
select
    region_txt as region,
    count(*) as total
from gtd
where region_txt in (${region:sqlstring})
group by region
order by total desc
```

To discuss:

- Variables
- sqlstring resulting in 'region1, region 2'
- Donut
- Legend placement - not repeating what is already in the chart

### By country (map)

``` sql
select
    country_txt as country,
    count(*) as total
from gtd
where
    region_txt in (${region:sqlstring}) and
    country_txt in (${country:sqlstring})
group by country_txt
```

To discuss:

- Variables
- Linking Variables

### By city

``` sql
select city , count(*) as total from gtd group by city order by city
```

To discuss:

- Lagging result on long lists
- Lagging on filter with long lists
- The efficiency of such a graph

### Top 10 cities

``` sql
select city , count(*) as total from gtd group by city order by total desc limit 10
```

- To discuss the efficiency of the data
- Column alignment choice that make it easy to read

