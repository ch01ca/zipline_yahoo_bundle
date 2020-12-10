
# setting

### trading_calendars\trading_calendar.py  
	start_default '1990-01-01' or earlier
	
### ~/.zipline/extension.py 
```python
import pandas as pd
from zipline.data.bundles import register
from zipline.data.bundles.csvdir import csvdir_equities

start_session = pd.Timestamp('1990-1-2', tz='utc') ##  the same as csv data date
end_session = pd.Timestamp(datetime.date.today().isoformat(),tz='utc')
register(
	'custom-csvdir-bundle',
	csvdir_equities(
	  ['daily'],
	  '/path/to/your/csvs',
	),
	calendar_name='NYSE', # US equities
	start_session=start_session,
	end_session=end_session
	)
```python

### Calendar    
Get all registered calendars with get_calendar_names:
	tc.get_calendar_names()[:5]
  ['XPHS', 'FWB', 'CFE', 'CMES', 'XSGO']
Get a calendar with get_calendar:
	xnys = tc.get_calendar("XNYS")
