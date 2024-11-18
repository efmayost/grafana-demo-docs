
## Quick glance


### Total events (stat)

``` sql
select count(*) as total from gtd
```

Options to discuss:

- Title
- Value options
- Stat styles
- Standard options

### Total killed

``` sql
select sum(nkill) as total from gtd
```

Options to discuss:

- Colour to emphasize a point

### Year with maximum killed

``` sql
select
  cast(iyear as decimal),
  sum(nkill) as total_killed
from gtd
group by iyear
order by total_killed desc
limit 1;
```

Options to discuss:

- Value options (one field or all fields)
- Stat styles orientation

### Total regions (stat)

``` sql
select count(distinct region_txt) as total from gtd
```

Or:

``` sql
select region_txt as region, count(region_txt) as total from gtd group by region
```

Options to discuss:

- The difference between the two in Value options with Distinct Count on region field
as opposed to First/Last in the first query.

### Total countries (stat)

``` sql
select count(distinct country_txt) as total from gtd
```

### Total groups (stat)

``` sql
select count(distinct(gname)) as total from gtd
```

### Total weapon types (stat)

``` sql
select count(distinct(weaptype1_txt)) as total from gtd
```

### Total attack types (stat)

``` sql
select count(distinct(attacktype1_txt)) as total from gtd
```

### Success rate (stat)

``` sql
with success as (
  select cast(count(*) as float) as total from gtd where success=1
)

select 100 * success.total / count(*) as rate from success, gtd
```

To discuss:

- Cast on rate to get a more accurate result with decimal.
- Standard options unit - only adds the percent sign (i.e needs to be multiplied by 100 in query)

### Suicide rate (stat)
``` sql
with suicide as (
  select cast(count(*) as float) as total from gtd where suicide=1
)

select 100 * suicide.total / count(*) as rate from suicide, gtd
```

### Individual rate (stat)

``` sql
with individual as (
  select cast(count(*) as float) as total from gtd where individual=1
)

select 100 * individual.total / count(*) as rate from individual, gtd
```

To discuss adding a row for grouping multiple panels

