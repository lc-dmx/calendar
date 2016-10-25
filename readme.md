虽然借鉴了网上的经验，不过大部分自己手写出来，感觉还是挺不错的...

PS：有些地方还需要改改样式,先展示一下：
![10月份](https://github.com/lc-dmx/calendar/blob/master/16-10.jpg)
![11月份](https://github.com/lc-dmx/calendar/blob/master/16-11.jpg)
![1月份](https://github.com/lc-dmx/calendar/blob/master/17-1.jpg)

主要代码如下：
```
//css实现月份调节按钮
#pre {
			position: absolute;
			top: 12px;
			left: 0;
			border-top: 6px solid transparent;
			border-right: 8px solid #999;
			border-bottom: 6px solid transparent;
			cursor: pointer;
		}
```
```
//判断是否闰年
//闰年能被4整除且不能被100整除，或能被400整除
		return (year % 4 == 0) && (year % 100 != 0 || year % 400 == 0);
```
```
//判断当月第一天星期几，0代表星期天，1代表星期一
		firstday = new Date(year, month-1, 1);	//获取当月的第一天
		dayOfWeek = firstday.getDay();

//创建月份数组,便于分别每个月有几天
		daysPerMonth = new Array(31, 28 + isLeapYear(year), 31, 30, 31, 30, 31, 31, 30, 31, 30, 31);
```
```
//循环输出
for (var i = 0; i < 6; i ++) {
			for (var k = 0; k < 7; k++) {
				//为每个表格创建索引,从0开始
				var index = 7 * i + k;
				//将当月的1号与星期进行匹配      
				var date = index - dayOfWeek + 1;
				//console.log(date);
				//索引小于等于0或者大于当月最大天数值就用空表格代替    
				(date <= 0 || date > daysPerMonth[month-1]) ? date = ' ': date = index - dayOfWeek + 1;
				$("#calendarTable tbody tr").eq(i).find("td").eq(k).html(date);
			}
		}
```
