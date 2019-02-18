##　记录一些常用的json遍历到DOM的方法

---

### demo1
```js
	$("input[type=button]").click(function(){
		$(".load").load('test.txt?date='+Math.random());  //解决缓存
	})
```
### demo2
```js
    $('#name').on('click',function(){
        $.ajax({
            url:'demo2.php?'+Math.random(),
            type:'GET',
            dataType:'json',
            success:function(data){
            $(".load").html(data)
            }
        });
    });
```
### demo3
```js
$("input[type=button]").click(function(){
			var ul = $(".load>ul");
			$.ajax({
				url:"demo3.php?"+Math.random(),
				type:"GET",
				dataType:"json",
				success:function(data){
					// alert(data[0].title);
					var res = eval(data);
					for(i in res){
						console.log(res[i].title)
						ul.append('<li>'+res[i].title+'<em>'+res[i].content+'</em></li>');
					}
				}
			})
		});
		//加载事件
		$(document).ajaxStart(function(){$("#img").show()}).ajaxStop(function(){$("#img").hide()});
```
### demo4
```js
$("input[type=button]").click(function(){
			var ul = $(".load>ul");
			$.ajax({
				url:'demo4.php?'+Math.random(),
				type:'GET',
				dataType:'xml',
				success:function(data){
					$(data).find('title').each(function(){
						ul.append("<li>"+$(this).text()+"</li>");
					});
				}
			});
		})
```
### demo5
```js
var div = $("#div");
	div.hover(function(){
		$.lcf.juzhong(div).css({"background":"red"});
	});
```