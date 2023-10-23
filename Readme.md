# 南科大润杨羽毛球场地预定脚本

## 特别声明

- 本项目内所有资源文件，禁止任何公众号、自媒体进行任何形式的转载、发布。
- 编写本项目主要目的为学习和研究Python，无法保证项目内容的合法性、准确性、完整性和有效性。
- 本项目涉及的数据由使用的个人或组织自行填写，本项目不对数据内容负责，包括但不限于数据的真实性、准确性、合法性。使用本项目所造成的一切后果，与本项目的所有贡献者无关，由使用的个人或组织完全承担。
- 本项目中所有内容只供学习和研究使用，不得将本项目中任何内容用于违反国家/地区/组织等的法律法规或相关规定的其他用途。
- 所有基于本项目源代码，进行的任何修改，为其他个人或组织的自发行为，与本项目没有任何直接或间接的关系，所造成的一切后果亦与本项目无关。
- 所有直接或间接使用本项目的个人和组织，应24小时内完成学习和研究，并及时删除本项目中的所有内容。如对本项目的功能有需求，应自行开发相关功能。
- 本项目保留随时对免责声明进行补充或更改的权利，直接或间接使用本项目内容的个人或组织，视为接受本项目的特别声明。
- 若有想法交流，可联系邮箱：eh905@outlook.com

### 2023/10/23更新
移除多线程操作。优化代码逻辑。
手动模式与固定时间模式测试均通过。脚本在一定程度上存在预约权限被封禁的风险，使用前请注意。



## 使用前
在`post.json`文件中需要修改的信息:
customer_name（预约人姓名）, customer_num（预约人数），student_id（学号）, customer_tel（接收预约短信的号码）, start_time（预约场地的起始时间）, end_time（预约场地的离场结束时间）


**注意：**

1. `"ground_id"`为场地参数，无需修改
2. start_time和end_time需要相互符合，脚本没有检查此异常的设置。例如：我想预约2023-10-29 20:30:00-22:00:00的场地，那么start_time就应该设置为2023-10-29 20:30:00，end_time就应该设置为2023-10-29 22:00:00
3. 起始时间和结束时间不一定需要相隔0.5小时，1h、1.5h、2h等均可

## 使用时

固定时间模式：为脚本设定一个运行时间，一般在晚上8点会有空场地放出，故`post.json`中`set_time`一般设置为`20XX-XX-XX 20:00:00`，脚本会在设定时间前开抢

```shell
# 固定时间模式运行
python script.py 0
```

手动回车模式：回车一次，自动在10个场地中寻找空闲位，预约成功一次后，会自动退出

```shell
# 手动回车模式运行
python script.py 1
```
