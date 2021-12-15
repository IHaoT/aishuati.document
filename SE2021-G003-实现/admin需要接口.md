###  需要：
#### 学生update接口 

 /admin/changeStuInfoById

````json
{
   "stuId":"2",
   "stuName":"chenzizhui",
   "stuNickName":"chenzihui",
   "stuEmail":"chenzihui@qq.com",
   "stuTelephoto":"1234567890123",
   "majorName":"软件工程",
   "stu_level":""
}
````

````json
{
    "code": 200,
    "msg": "更新成功"
}
````



#### 教师update接口  

/admin/changeTeacherInfo

#### 单选题update接口 

/problem/updateSigleProblem

```JSON
{
"problemId":13,
"choice_A":"1",
"choice_B":"2",
"choice_C":"3",
"choice_D":"4",
"Info_text_content":"TESTCBHXZBCZ",
"difficult":1,
"correct":1,
"reference":"WU"
}
```

```JSON
{
    "code": 200,
    "data": 1
}
```





#### 主观题update接口

/problem/updateSubjectiveProblem

```json
{
"problemId":3,

"Info_text_content":"TESTCBHXZBCZ",
"difficult":1,
"reference":"WU"
}
```

```json
{
    "code": 200,
    "data": 1
}
```



试卷update接口
学生条件查询：/student/search/${page}/${size}，请求参数：stuName，stu_level



#### 教师条件查询：

/teacher/search/${page}/${size}，请求参数：adminName



```json
{
   "adminName":"yc"

}
```

```json
{
    "code": 200,
    "data": {
        "total": 1,
        "rows": {
            "introduce": null,
            "state": 999,
            "administrator_name": "yc",
            "administrator_email": "222@qq.com",
            "administrator_telephone": "11241234135233",
            "administrator_createTime": "2021-11-26T15:43:46.000+00:00",
            "administrator_id": 1,
            "administrator_pwd": "9v3/5IyQjesPTDvTbAMucg==",
            "administrator_Account": "admin"
        }
    }
}
```



----------以下两个接口文档好像有但是改成仅学科查询

#### 单选题条件查询：

/problem/choice/adminSearch/{page}/{size}

```json
{
   "subjectName":"ruanjiangongcheng "

}
```

```json
{
    "code": 200,
    "data": {
        "total": 0,
        "rows": []
    }
}
```



#### 主观题条件查询：/problem/subjective/adminSearch/{page}/{size}，请求参数：subjectName

跟上面单选题的一样

bug：/admin/changeTeacherInfo，请求返回500错误
请求方式POST

{
    "adminId":"编号",
    "adminName":"",
    "adminEmail":"",
    "adminTelephone":"",
    "adminAccount":""    //登录账号传过来，但是前端不让修改
}
返回参数

{
    "code": 200,
    "msg": "更新成功"
}

