<div align="center">

## Fill Date Boxes and Check Date


</div>

### Description

The first function fills three select boxes with month, day and year to select a date. The finction also checks for leap years and similiar things.

The second function checks if the date is a date in the future!
 
### More Info
 
Select Boxes are first filled by using VBScript (ASP). So you have to do rewrite this to javascript, but the main functions are JavaScript-only!


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Sven Moderow](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/sven-moderow.md)
**Level**          |Intermediate
**User Rating**    |4.8 (19 globes from 4 users)
**Compatibility**  |
**Category**       |[Forms Validation Processing](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/forms-validation-processing__2-76.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/sven-moderow-fill-date-boxes-and-check-date__2-2193/archive/master.zip)





### Source Code

```
	<body>
	<head>
	<script language="JavaScript">
		function CalculateDays() {
			var intMonth = document.dates.expireMonth.value;
			var intYear = document.dates.expireYear.value;
			var intMaxDay = 31;
			var intDay = 1;
			var dayHTML = "";
			var arrDays = new Array();
			if (intMonth != 0 && intYear != 0) {
				switch (intMonth) {
				 case "1":
				 case "3":
				 case "5":
				 case "7":
				 case "8":
				 case "10":
				 case "12":
				  {
						intMaxDay = 31;
				  }
				  break;
				 case "4":
				 case "6":
				 case "9":
				 case "11":
				  {
						intMaxDay = 30;
				  }
				  break;
				 case "2":
				  {
						if (intYear % 4 == 0 && (intYear % 1000 == 0 || intYear % 100 != 0)) {
							intMaxDay = 29;
						} else {
							intMaxDay = 28;
						}
				  }
				  break;
				 default:
					 {
						intMaxDay = 31;
					 }
				}
				while (document.dates.expireDay.length > 1) {
					document.dates.expireDay.options[document.dates.expireDay.length-1] = null;
				}
				for (intDay=1; intDay<=intMaxDay; intDay++) {
					var Eintrag = new Option(intDay);
					document.dates.expireDay.options[document.dates.expireDay.length] = Eintrag;
					document.dates.expireDay.selectedIndex = intDay;
					document.dates.expireDay.options[document.dates.expireDay.selectedIndex].value = intDay;
				}
				document.dates.expireDay.selectedIndex = 0;
			}
		}
		function IsFutureDate() {
			var intMonth = document.dates.expireMonth.value;
			var intDay = document.dates.expireDay.value;
			var intYear = document.dates.expireYear.value;
			var currentDate = new Date();
			var currentDay = currentDate.getDate();
			var currentMonth = currentDate.getMonth() + 1;
			var currentYear = currentDate.getYear();
			if (intMonth == 0 || intMonth == null) {
				alert("Please select month!");
			} else {
				if (intDay == 0 || intDay == null) {
					alert("Please select day!");
				} else {
					if (intYear == 0 || intYear == null) {
						alert("Please select Year!");
					} else {
						if (intYear <= currentYear) {
							if (intMonth <= currentMonth) {
								if (intDay < currentDay) {
									alert("Select date in future not in past!");
								}
							}
						}
					}
				}
			}
		}
 </script>
	</head>
	<html>
	<body>
	<form name=dates method=post action="">
	<select name="expireMonth" onChange="javascript: CalculateDays();">
	 <option value="0">Month</option>
	 <% For intMonth = 1 To 12 %>
		<option value="<% = intMonth %>"><% = MonthName(intMonth) %></option>
	 <% Next %>
	</select>
	<select name="expireDay">
	 <option value="0">Day</option>
	 <% For intDay = 1 To 31 %>
		<option value="<% = intDay %>"><% = intDay %></option>
	 <% Next %>
	</select>
	<select name="expireYear" onChange="javascript: CalculateDays();">
	 <option value="0">Year</option>
	 <% For intYear = Year(Now()) - 1 To Year(Now()) + 9 %>
		<option value="<% = intYear %>"><% = intYear %></option>
	 <% Next %>
	</select>
	<input type="button" value="Test" onClick="javascript: IsFutureDate();">
	</form>
	</body>
	</html>
```

