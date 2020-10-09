```flow
获取垃圾分类信息
s=>start: 开始
o=>operation: 打开主页
c=>operation: 选择垃圾种类
j=>operation: 跳转到垃圾信息页
end=>end: 结束
s->o
o->c
c->j
j->end
```
获取垃圾分类信息

```flow
搜索属于哪类垃圾
s=>start: 开始
o=>operation: 输入搜索内容
c=>operation: 点击搜索按钮
j=>operation: 显示搜索结果
end=>end: 结束
s->o
o->c
c->j
j->end
```
搜索属于哪类垃圾


```flow
拍照识别属于哪类垃圾
s=>start: 开始
o=>operation: 点击图片搜索按钮
c=>operation: 拍摄图片
j=>operation: 显示图片相应的搜索结果
end=>end: 结束
s->o
o->c
c->j
j->end
```
拍照识别属于哪类垃圾

```sequence
participant 页面
participant 后台业务
participant 数据库

页面->后台业务: 提交搜索请求(json)
后台业务->后台业务: 验证搜索内容
后台业务-->页面: 搜索内容错误
后台业务->数据库: SQL查询
数据库-->后台业务: 返回查询结果
后台业务-->页面: Success 返回数据(json)
```

搜索查询时序图

```sequence
participant 页面
participant 后台业务
participant 分类模型

页面->后台业务: 提交图片搜索请求
后台业务->后台业务: 验证图片内容
后台业务-->页面: 图片内容存在危险
后台业务->分类模型: 提交给模型
分类模型-->后台业务: 返回模型识别结果
后台业务-->页面: Success 返回数据(json)
```
图片查询时序图
