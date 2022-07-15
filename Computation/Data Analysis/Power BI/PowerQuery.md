# Power Query

## Create a date table
= List.Dates(StartDate,Duration.Days(EndDate-StartDate),#duration(1,0,0,0))
