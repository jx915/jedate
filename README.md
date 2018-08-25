原控件bug:初始化日期不是当前时间日期直接点击确认按钮会变为当前时间的日期

重写了一下初始化selectValue
```
var getCurrValue = function () {
	var mats = jet.reMatch(that.format), isEmpty = that.getValue() != "",curVal = [],
	    parmat = that.dlen == 7 ? "hh:mm:ss" : "YYYY-MM"+ (that.dlen <= 2 ? "":"-DD");

	//修改
	var result = that.valCell.value;
	result = result.substr(0,11);
	var nowTime = [jet.parse(jet.getDateTime({}), parmat)];
	nowTime = nowTime[0];
	var time1 = new Date(result).setHours('0');
	var time2 = new Date(nowTime).setHours('0');
	var nDays = (parseInt((time1 - time2) / 1000 / 3600 / 24));
	var redate = {
		DD: nDays
	};
	that.selectValue = [jet.parse(jet.getDateTime(redate), parmat)];
```
jeDate.js
=======
jeDate V6.5.0 是一款原生JS开发的 不依赖任何第三方库 大众化的日期控件，她身兼多职，虽不是万能的，但是她却是功能强大多样的美少女，她除了包含 单双面板、区域选择、 多语言、日历固定、有效无效日期、日期时间戳转换、日期加减、限制时分秒、初始化日期加减N、日期标注点、设定年月（YYYY-MM）、日期范围限制、开始日期设定、自定义日期格式、当天的前后若干天返回、时分秒选择、智能响应、自动纠错、节日识别，操作等常规功能外，根据不同的日期格式，显示不同内容，还拥有更多趋近完美的解决方案。更多的是需要你与她的亲密接触与呵护！ QQ群：516754269 

**使用方法**

* [点击查看详细日期API（http://www.jemui.com/uidoc/jedate.html）](http://www.jemui.com/uidoc/jedate.html) 


# 快速上手

**使用NPM安装**

    npm install jquery.jedate
    
**使用Git安装**

    git clone git://github.com/singod/jeDate.git
    
**使用对象**

    <input class="datainp" id="indate" type="text" placeholder="请选择"  readonly>
    <input class="datainp" id="dateinfo" type="text" placeholder="请选择"  readonly>
      

**查看演示**

* [查看演示](http://singod.github.io/jeDate/)   


## License

[MIT License](https://github.com/singod/jeDate/blob/gh-pages/LICENSE)
