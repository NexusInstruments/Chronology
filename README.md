TimeUtils
=========
A Wildstar LUA library to format localized date and objects

This can be very helpful when needing to export or save data inside the add-on data storage/settings. Or useful when you want to transport encoded data between add-ons or between clients through the use of in-game comm-channels.

Usage
=====
## Localization
The library currently supports localization of Month and Day of Week names. The following languages are supported:
| Language Code | Description |
|---------------|-------------|
|"en"|English|
|"fr"|Français (French)|
|"de"|Deutsch (German)|
|"es"|Español (Spanish)|

## Formatting
Elements of the formatting strings are used to produce strings that are in a desired format.
| Format Code | Description |
|-------------|-------------|
|"{YYYY}"| 4 Digit Year (e.g "2014") |
|"{YY}"| 2 Digit Year (e.g. "14") |
|"{MMMM}"| Localized Month Name (e.g. "January", "Mayo", "Avril") |
|"{MMM}"| Localized Abbreviated Month Name (e.g. "Jan.", "May", "Avr.") |
|"{MM}"| 2 Digit Month; zero-padded (e.g. "01") |
|"{M}"| Month; not-padded (e.g. "1") |
|"{DDDD}"| Localized Day of Week (e.g. "Miercoles", "Friday", "Sonntag") |
|"{DDD}"| Localized Abbreviated Day of Week (e.g. "Mi", "Fri", "So") |
|"{DD}"| 2 Digit Date; zero-padded (e.g. "04", "30") |
|"{D}"| Date digit; not-padded (e.g. "1") |
|"{HH}"| 2 Digit Hour (24h); zero-padded (e.g. "01", "23") |
|"{H}"| Hour digit (24h); not-padded (e.g. "1", "23") |
|"{hh}"| 2 Digit Hour (12h); zero-padded (e.g. "01", "11") |
|"{h}"|  Hour digit (12h); not-padded (e.g. "1", "11") |
|"{mm}"| 2 Digit Minute; zero-padded (e.g. "01", "43") |
|"{m}"| Minute digit; not-padded (e.g. "9", "14") |
|"{SS}"| 2 Digit Seconds; zero-padded (e.g. "09", "43") |
|"{S}"| Seconds digit; not-padded (e.g. "9", "14") |
|"{TT}"| Full Meridian Designator ("AM"/"PM") |
|"{T}"| Short Meridian Designator ("a"/"p") |

## Including the Library 
```lua
  local TimeUtils
  TimeUtils = Apollo.GetPackage("Time:Utils-1.0").tPackage

  TimeUtils:GetFormattedDate(GameLib.GetLocalTime())
```

Reference
---------
## GetFormattedDate(tDate, strFormat, strLangCode)
|-------|-----------|
| tDate | A Wildstar (GameLib) date table object |
| strFormat | A format string to use to format the data |
| strLangCode | A language code string to use |

**Notes**
* Default format used for date strings if no format is passed is "{YYYY}-{MM}-{DD}"
* Default language user is English ("en") if no language code is passed

**Example**
```lua
  local strDate = TimeUtils:GetFormattedDate(GameLib.GetLocalTime())
```
**Results**
```
Value of strDate:
----> "2014-07-23"
```

## GetFormattedTime(tDate, strFormat, strLangCode)
|-------|-----------|
| tDate | A Wildstar (GameLib) date table object |
| strFormat | A format string to use to format the data |
| strLangCode | A language code string to use |

**Notes**
* Default format used for date strings if no format is passed is "{HH}:{mm}:{SS}"
* Default language user is English ("en") if no language code is passed

**Example**
```lua
  local strTime = TimeUtils:GetFormattedTime(GameLib.GetLocalTime())
  local strTime2 = TimeUtils:GetFormattedTime(GameLib.GetLocalTime(),"{hh}.{mm} {T}")
```
**Results**
```
Value of strTime:
----> "21:32:43"

Value of strTime2:
----> "11:32 p"
```

## GetFormattedDateTime(tDate, strFormat, strLangCode)
|-------|-----------|
| tDate | A Wildstar (GameLib) date table object |
| strFormat | A format string to use to format the data |
| strLangCode | A language code string to use |

**Notes**
* Default format used for date strings if no format is passed is "{HH}:{mm}:{SS}"
* Default language user is English ("en") if no language code is passed

**Example**
```lua
  local strDateTime = TimeUtils:GetFormattedTime(GameLib.GetLocalTime())
  local strDateTime2 = TimeUtils:GetFormattedTime(GameLib.GetLocalTime(),"{DDDD} {D} {MMMM} {YYYY} {HH}:{mm}", "es")
```
**Results**
```
Value of strDateTime:
----> "2014-07-23 21:32:43"

Value of strDateTime2:
----> "Martes 23 Julio 2014 21:32"
```

## GetMonthString(month, bAbbrv, strLangCode)
|-------|-----------|
| month | Integer for the month (1 - 12) |
| bAbbrv | Abbreviated value (true/false) |
| strLangCode | A language code string to use |

**Notes**
* Default language user is English ("en") if no language code is passed

## GetDayOfWeekString(day, bAbbrv, strLangCode)
|-------|-----------|
| day | Integer for the day of the week (1 - 7) |
| bAbbrv | Abbreviated value (true/false) |
| strLangCode | A language code string to use |

**Notes**
* Default language user is English ("en") if no language code is passed
