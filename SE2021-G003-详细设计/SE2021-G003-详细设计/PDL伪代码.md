# PDL伪代码

## student登录

```PDL
begin 学生登录
前端传给后端登录账号stu_Account、登录密码Pwd
    if <账号不存在> then 
        提示错误
    else if <密码错误> then
        提式错误
    else 
    	保存用户信息到session
    	后台自动生成登录日志
        登录成功
    end if
end 学生登录
```

## student 登出

```PDL
begin 学生登出
	从session获取用户的StuId，查询到当前用户
	后台自动生成登出日志
	将用户信息从session中移除
end 学生登出
```



## student注册

```PDL
begin 学生注册
前端传给后端后端登录账号stu_Account、登录密码Pwd11，登录密码pwd2，学生邮箱stu_email、学生电话、学生专业、年级
	if<账号stuAccount字段已存在> then
		提式错误
	else if<pwd1!=pwd2> then
		提示错误
	else then
		系统根据subject表筛选符合学生专业年级的课程，供学生选择
		学生选择课程传给后端，possess表中添加数据
	end if
end 学生注册
```

## 学生密码修改

```PLD
begin 修改密码
用户输入旧密码OddPwd，新密码pwd1，重复密码pwd2
	if<旧密码输入错误> then
		提示密码错误
	else if<pwd1！=pwd2> then
		提示重新输入
	else then
		修改成功 
	end if
end 修改密码
```

## 获得个人信息

```Json
begin 查询个人信息
	if<点击界面右上方>
		前端发送请求给服务器，后台从session中获取当前登录的stuId
		根据stuId查询当前用户的stuName、StuNickeName、stuEmail等信息
	end if
end begin
```



## 在线刷题

```PDL
begin 在线刷题
学生选择需要刷题的科目subject_Name
后端根据需求展示题面信息
	if<学生选择查看选择题> then
		显示选项
		if<点击提交> then
			submit表中添加提交记录
			if<答案错误> then
				state状态置为0，表示答案错误
			end if
		end if
	else if<学生选择查看主观题> then
		if<学生点击查看参考答案> then
			显示参考答案
		end if
	end if
end 在线刷题
```

## 查看错题集

```PLD
begin 查看错题
提供根据submit表中state为0的状态和problem连表查询出错题展示给前端，当前用户从session中获得
end 查看错题
```

## 查看历年试卷

```PLD
begin 查看往年试卷
学生选择需要查看的科目，系统展示试卷的基本信息
	if<学生点击‘查看详情’> then
		试卷内容以pfd的形式展现
	end if
end 查看往年试卷
```

## 查看未读公告

```PLD
begin 查看未读公告
系统根据当前登录的学生用户，在news表中查询未读的消息
	if<点击查看详情> then
		该消息标为已读，弹出冒泡框展示公告详细内容
	else if<点击‘全部已回’> then
		未读消息均为已读
	else if<点击反馈> then
		用户对消息进行反馈
	end if
end 查看未读公告
```

### 管理员登录

```PLD
begin 管理员登录
前端传给后端登录账号Account、登录密码Pwd
    if <账号不存在> then 
        提示错误
    else if <密码错误> then
        提式错误
    else 
    	保存用户信息到session
        登录成功
    end if
end 管理员登录
```

## 教师添加

```PDL
begin 添加教师用户
	前端传入adminAccount，adminName，adminEmail，adminTelephoto
	从session中获取当前用户权限，判断权限
	if<权限为管理员> then
		后台自动生成默认密码，并与adminAccount合并产生md5加密码作为用户密码存储在数据库中
	else then
		返回访问受限
	end if
end begin
```



## 题目编创

```PLLD
begin 题目编创
用户选择出题类型
	if <用户选择 编创选择题> then
		前端拼接显示题面信息
		显示A、B、C、D选项内容的编创信息，计划用markdown格式，可以导入数学公式，并给出正确答案
	else if<主观题编创> then
		编辑参考答案
	end if
problem表中新建一条记录，内容为用户所填信息
end 题目编创
```

## 试卷上传

```PLD
begin 试卷上传
用户填写试卷来源、试卷名称等基本信息
用户从本地选择上传的文件，存储到服务器中，并产生相应地址存储在exampaper表中
end 试卷上传
```

## 题面信息修改

```PLD
begin 题面修改
用户选择修改的题面编号
	if<点击修改> then
		跳转到修改页面，修改题面信息
			if<点击保存> then
				确认修改，update problem表中信息
			end  if
	end if
end 题面修i该
```

## 修改密码

```PLD
begin 修改密码
用户输入旧密码OddPwd，新密码pwd1，重复密码pwd2
	if<旧密码输入错误> then
		提示密码错误
	else if<pwd1！=pwd2> then
		提示重新输入
	else then
		修改成功 
	end if
end 修改密码
```

## 系统日志查询

```PLD
begin 日志查询
系统从user_event_log表中查询用户登录记录
	if<根据stu_id查询> then
		用户输入学生编号
			if<查询到结果>  then
				返回结果
			else then
				返回‘暂无信息’
			end if
	else if<清空日志> then
		选择的日志被delete清空
	end if
end 日志查询
```

## 公告系统

```PLD
begin 发布公告
用户选择发送的对象，编辑公告内容
	if<点击确认发送> then
		news表中新增一条state为0的记录
	end if
end 发送公告
```


