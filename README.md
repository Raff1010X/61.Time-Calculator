# [freeCodeCamp Scientific Computing with Python](https://www.freecodecamp.org/learn/scientific-computing-with-python)

## [Time-Calculator](https://www.freecodecamp.org/learn/scientific-computing-with-python/scientific-computing-with-python-projects/time-calculator)

My git repo: https://github.com/Raff1010X/01.Roadmap

```python
# main function
def add_time(start, duration, day_of_week = 'none'):
    minutes = elpased_minutes(start, duration, day_of_week)
    time = time_from_minutes(minutes)
    day = end_day_name(minutes, day_of_week)
    duration_string = duration_to_string(start, duration)
    return f'{time}{day}{duration_string}'

# calculate elpased time in minutes from monday 00:00
def elpased_minutes(time, duration, day_of_week):
    return start_time_in_minutes(time, day_of_week) + duration_in_minutes(duration) + add_PM_minutes(time)

# returns time string based on elpased minutes since monday 00:00
def time_from_minutes(minutes):
    last_day_minutes = minutes - (minutes // (60 * 24) * (60 * 24))
    hour = last_day_minutes // 60
    minute = format_minutes(last_day_minutes - (last_day_minutes // 60 * 60))
    time = f'{format_hour(hour)}:{minute} {find_AM_PM(hour)}'
    return time

# format time less then 10 minut
def format_minutes(time):
    if int(time) < 10:
        return f'0{time}'
    return time

# return AM/PM
def find_AM_PM(hour):
    if int(hour) >= 12:
        return f'PM'
    return f'AM'

# format 24 to 12 time 
def format_hour(hour):
    if int(hour) > 12:
        return hour - 12
    elif int(hour) == 0:
        return 12
    return hour

# calculate duration in minutes
def duration_in_minutes(duration):
    return int(duration[:-3]) * 60 + int(duration[-2:])

# calculate start time in minutes
def start_time_in_minutes(time, day_of_week):
    return int(time[:-6]) * 60 + int(time[-5:-3]) + days_of_week[day_of_week.lower()] * 60 * 24

# return 60 * 12 minutes if time is PM
def add_PM_minutes(time):
    if time[-2:] == 'PM':
        return 60 * 12
    return 0

# change duration to response string
def duration_to_string(start, duration):
    days = elpased_minutes(start, duration, 'none') // (60 * 24)
    if days > 1: 
        return f' ({days} days later)'
    elif days == 1:
        return ' (next day)'
    return ''

# find end day name
def end_day_name(minutes, day_of_week):
    if day_of_week == 'none':
        return ''
    day = minutes // (24 * 60)
    if day > 7:
        day_name = list(days_of_week)[day - (day // 7) * 7]
    else:
        day_name = list(days_of_week)[day]
    if day_name == 'none':
        day_name = day_of_week
    return f', {day_name.capitalize()}'

# days of week dictionary
days_of_week = {
  "none": 0,
  "monday": 1,
  "tuesday": 2,
  "wednesday": 3,
  "thursday": 4,
  "friday": 5,
  "saturday": 6,
  "sunday": 7
}
```
