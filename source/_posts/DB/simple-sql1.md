---
title: 简单sql练习50句之一
date: 2018-10-07 12:17:17
thumbnail: /gallery/img_3/dog.jpg
categories: mysql # 分类
---
-- ----------------------------
#### <font color=pink> 笑一笑，十年少 </font>
#### <font color=pink>xixixixi~xixixixi~xixixixi~xixixixi~xixixixi </font>
闲来无事刷了点sql
简简单单的50句查询语句，修身养性~不错不错
自己写的时候发现网上很多都是sqlite、oracle的
所以，就记录一下下mysql咯，方便以后自己用
如果能为其他sql道友带来帮助那就再好不过啦
同时如果哪里有不对的或者写的不好的地方欢迎指正，Olily在此谢过啦
在此声明~50句并非原创，问题是凑的emmmm但是代码是撸的
道友可直接百度“sql练习”，便可以搜到更多啦
-- ----------------------------

#### <font color=pink>创建表</font>
-- ----------------------------
###### Table structure for student
-- ----------------------------
```sql
    DROP TABLE IF EXISTS `student`;
    CREATE TABLE `student`  (
      `sno` varchar(10) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
      `sname` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
      `sage` int(2) NULL DEFAULT NULL,
      `ssex` varchar(5) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
      PRIMARY KEY (`sno`) USING BTREE
    ) ENGINE = MyISAM CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
```
-- ----------------------------
###### Table structure for teacher
-- ----------------------------
```sql
    DROP TABLE IF EXISTS `teacher`;
    CREATE TABLE `teacher`  (
      `tno` varchar(10) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
      `tname` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
      PRIMARY KEY (`tno`) USING BTREE
    ) ENGINE = MyISAM CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
```
-- ----------------------------
###### Table structure for course
-- ----------------------------
```sql
    DROP TABLE IF EXISTS `course`;
    CREATE TABLE `course`  (
      `cno` varchar(10) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL DEFAULT '',
      `cname` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
      `tno` varchar(20) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL DEFAULT '',
      PRIMARY KEY (`cno`, `tno`) USING BTREE
    ) ENGINE = MyISAM CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
```
-- ----------------------------
###### Table structure for sc
-- ----------------------------
```sql
    DROP TABLE IF EXISTS `sc`;
    CREATE TABLE `sc`  (
      `sno` varchar(10) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL DEFAULT '',
      `cno` varchar(10) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL DEFAULT '',
      `score` decimal(10, 2) NULL DEFAULT NULL,
      PRIMARY KEY (`sno`, `cno`) USING BTREE
    ) ENGINE = MyISAM CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
    SET FOREIGN_KEY_CHECKS = 1;
```
##### <font color = pink>向表中插入数据</font>
-- ----------------------------
###### Records of student
-- ----------------------------
```sql
    INSERT INTO `student` VALUES ('s001', '张三', 23, '男');
    INSERT INTO `student` VALUES ('s002', '李四', 23, '男');
    INSERT INTO `student` VALUES ('s003', '吴鹏', 25, '男');
    INSERT INTO `student` VALUES ('s004', '琴沁', 20, '女');
    INSERT INTO `student` VALUES ('s005', '王丽', 20, '女');
    INSERT INTO `student` VALUES ('s006', '李波', 21, '男');
    INSERT INTO `student` VALUES ('s007', '刘玉', 21, '男');
    INSERT INTO `student` VALUES ('s008', '萧蓉', 21, '女');
    INSERT INTO `student` VALUES ('s009', '陈萧晓', 23, '女');
    INSERT INTO `student` VALUES ('s010', '陈美', 22, '女');
```
-- ----------------------------
###### Records of teacher
-- ----------------------------
```sql
    INSERT INTO `teacher` VALUES ('t001', '刘阳');
    INSERT INTO `teacher` VALUES ('t002', '谌燕');
    INSERT INTO `teacher` VALUES ('t003', '胡明星');
```
-- ----------------------------
###### Records of course
-- ----------------------------
```sql
    INSERT INTO `course` VALUES ('c001', 'J2SE', 't002');
    INSERT INTO `course` VALUES ('c002', 'Java Web', 't002');
    INSERT INTO `course` VALUES ('c003', 'SSH', 't001');
    INSERT INTO `course` VALUES ('c004', 'Oracle', 't001');
    INSERT INTO `course` VALUES ('c005', 'SQL SERVER 2005', 't003');
    INSERT INTO `course` VALUES ('c006', 'C#', 't003');
    INSERT INTO `course` VALUES ('c007', 'JavaScript', 't002');
    INSERT INTO `course` VALUES ('c008', 'DIV+CSS', 't001');
    INSERT INTO `course` VALUES ('c009', 'PHP', 't003');
    INSERT INTO `course` VALUES ('c010', 'EJB3.0', 't002');
```
-- ----------------------------
###### Records of sc
-- ----------------------------
```sql
    INSERT INTO `sc` VALUES ('s004', 'c002', 67.90);
    INSERT INTO `sc` VALUES ('s003', 'c003', 92.00);
    INSERT INTO `sc` VALUES ('s003', 'c001', 89.00);
    INSERT INTO `sc` VALUES ('s002', 'c002', 78.70);
    INSERT INTO `sc` VALUES ('s002', 'c001', 56.00);
    INSERT INTO `sc` VALUES ('s001', 'c002', 67.80);
    INSERT INTO `sc` VALUES ('s001', 'c001', 92.00);
    INSERT INTO `sc` VALUES ('s001', 'c003', 59.00);
    INSERT INTO `sc` VALUES ('s002', 'c004', 92.00);
    INSERT INTO `sc` VALUES ('s002', 'c005', 91.00);
    INSERT INTO `sc` VALUES ('s003', 'c004', 97.00);
    INSERT INTO `sc` VALUES ('s005', 'c004', 23.00);
    INSERT INTO `sc` VALUES ('s004', 'c004', 56.03);
    INSERT INTO `sc` VALUES ('s003', 'c005', 54.90);
```
#### <font color = pink>查询语句</font>
###### 1.查询学生表的前10条数据;
```sql
    select * from student limit 0,10;
```

###### 2.查询成绩表中的最低分,平均分,总分;
```sql
    select min(score),avg(score) avg,sum(score) sum
    from sc;
```
###### 3.查询老师 "谌燕" 所带的课程设数量;
```sql
    -- 方案一：
    select count(cno)
    from teacher t,course c  
    where t.tno = c.tno and t.tname = '谌燕';
    -- 方案二：
    select count(*)
    from teacher t inner join course c on t.tno = c.tno
    where t.tname = '谌燕';
    -- 方案三：
    select count(*)
    from course
    where course.tno = 't002';
```
###### 4.查询所有老师所带的课程数量;
```sql
    select t.tno,count(*)
    from teacher t left join course c on t.tno=c.tno
    group by t.tno;
```
###### 5.查询姓张同学的信息;
```sql
    select *
    from student
    where sname like '张%';  
```
###### 6.查询课程名称为"数据库",且分数低于60 的学生姓名和分数;
```sql
    select s.sname,sc.score
    from course c inner join sc on c.cno = sc.cno inner join student s on sc.sno=s.sno
    where sc.score<60 and cname = '数据库';
```
###### 7.查询所有学生的选课情况;
```sql
    select s.sno,GROUP_CONCAT(sc.cno)
    from student s inner join sc on s.sno = sc.sno
    group by s.sno;
```
###### 8.查询任何一门课程成绩在70 分以上的姓名.课程名称和分数;
```sql
    select sname,cname,score
    from student s inner join sc on s.sno = sc.sno inner join course c on sc.cno=sc.cno
    where sc.score >70;
```
###### 9.查询不及格的课程,并按课程号从大到小排列;

```sql
    select sc.cno,cname,sc.score
    from course c inner join sc on c.cno = sc.cno
    where sc.score <60 
    order by cno desc;
```
###### 10.查询没学过"谌燕"老师讲授的任一门课程的学生姓名;
```sql
    -- 方案1 
    select sname
    from student s
    where s.sno not in  
    (select sc.sno 
    from student stu inner join sc on stu.sno = sc.sno 
    inner join course c on sc.cno = c.cno 
    inner join teacher t on c.tno = t.tno 
    where tname = '谌燕');
    -- 方案2    
    select sc.sno,stu.sname 
    from student stu inner join sc on stu.sno = sc.sno 
    inner join course c on sc.cno = c.cno 
    inner join teacher t on c.tno = t.tno 
    where tname = '谌燕';
```
###### 11.查询两门以上不及格课程的同学的学号及其平均成绩;
```sql
    select sno,avg(score)
    from (select s.sno,score from student s inner join sc on s.sno = sc.sno ) as A
    where A.sno in 
    (select A.sno from (select s.sno,score from student s inner join sc on s.sno = sc.sno ) as A 
    where score<60 group by A.sno having count(*)>2);
```
###### 12.课程号为c004,成绩小于90分的学生学号,通过成绩降序排列;
```sql
    select s.sno,sc.score
    from student s inner join sc on s.sno = sc.sno
    where score<90 and cno = 'c004'
    order by score;
```
###### 13.删除"s002"同学的"c001"课程的成绩;
```sql
    delete from sc 
    where sno = 's002' and cno='c001';
```
###### 14、把“SC”表中“谌燕”老师教的课的成绩都更改为此课程的平均成绩;
```sql
    update sc set score = (select avg(sc.score) 
    from course c,teacher t where c.tno = t.tno and tname = '谌燕' and sc.cno = c.cno group by sc.cno) 
    where cno in (
    select cno from course c,teacher t
    where c.tno = t.tno
    and tname = '谌燕');
```
###### 15.查询平均成绩大于60 分的同学的学号和平均成绩;
```sql
    select sno,avg(score)
    from sc
    group by sno
    having avg(score)>60;
```
###### 16.删除学习“谌燕”老师课的SC 表记录;
```sql
    delete from sc
    where cno in (select sc.cno from course c,teacher t 
    where c.tno = t.tno and sc.cno = c.cno and tname = '谌燕') ;
```
###### 17.查询姓"刘"的老师的个数;
```sql
    select count(*)
    from teacher
    where tname like '刘%';
```
###### 18.查询不同老师所教不同课程平均分从高到低显示;
```sql
    -- 方案1
    select tno,c.cno,avg(score) avg
    from sc inner join course c on sc.cno = c.cno
    group by tno,c.cno
    order by avg desc;
    -- 方案2
    select max(t.tno),max(t.tname),max(c.cno),max(c.cname),c.cno,avg(score) from sc , course c,teacher t
    where sc.cno=c.cno and c.tno=t.tno
    group by c.cno
    order by avg(score) desc;
```
###### 19.统计各科成绩,各分数段人数:课程ID,课程名称,[100-85],[85-70],[70-60],[ <60];
```sql
    select sc.cno,c.cname,
    sum(case when score between 85 and 100 then 1 else 0 end ) as '[100-85]',
    sum(case when score between 70 and 85 then 1 else 0 end ) as '[85-70]',
    sum(case when score between 60 and 70 then 1 else 0 end ) as '[70-60]',
    sum(case when score<60 then 1 else 0 end ) as '[<60]'
    from sc inner join course c on sc.cno = c.cno
    group by sc.cno;
```
###### 20.查询学过"谌燕"老师所教的所有课的同学的学号:姓名;
```sql
    select sc.sno,s.sname
    from sc inner join student s on sc.sno = s.sno
    where sc.sno in (select sc.sno 
    from sc inner join course c on sc.cno = c.cno inner join teacher t on c.tno = t.tno 
    where tname = '谌燕');
```
###### 21.查询课程编号"c002"的成绩比课程编号"c001"课程低的所有同学的学号.姓名;
```sql
    select sc1.sno,sc1.sname 
    from 
    (select s1.sno,s1.sname,sc.score 
    from sc inner join student s1 on sc.sno = s1.sno 
    where sc.cno = 'c001') sc1,
    (select s2.sno,s2.sname,sc.score from sc inner join student s2 on sc.sno = s2.sno where sc.cno = 'c002') sc2 
    where sc1.sno = sc2.sno and sc1.score < sc2.score;
```
###### 22.查询所有课程成绩小于60 分的同学的学号.姓名;
```sql
    select s1.sno,sname
    from student s1
    where sno not in (select sc.sno from student,sc where student.sno = sc.sno and score>60);
```
###### 23.查询没有学全所有课的同学的学号.姓名;
```sql
    select s1.sno,s1.sname
    from student s1 inner join sc on sc.sno = s1.sno
    group by s1.sno
    having count(*) < (select count(*) from course);
```
###### 24.查询至少有一门课与学号为"s001"的同学所学相同的同学的学号和姓名;
```sql
    select distinct s1.sno,s1.sname
    from student s1 inner join sc on s1.sno = sc.sno
    where s1.sno<>'s001' and sc.cno in (select cno from sc where sno = 's001');
```
###### 25.查询至少学过学号为"s001"同学所有课的其他同学学号和姓名;
```sql
    select distinct s1.sno,s1.sname
    from sc inner join student s1 on sc.sno  = s1.sno
    where sc.cno in (select distinct sc.cno from sc where sc.sno = 's001' )
    group by sc.sno,s1.sname
    having count(sc.cno) = (select count(*) from sc where sno = 's001'）
    and s1.sno<>'s001';
```
###### 26.查询各科成绩前三名的记录:(不考虑成绩并列情况);
```sql
    select cno,substring_index(group_concat(score order by score desc ),',',3)
    from sc
    group by sc.cno;
```
###### 27.查询和"s001"号的同学学习的课程完全相同的其他同学学号和姓名;
```sql
    select distinct s1.sno,s1.sname
    from sc inner join student s1 on sc.sno  = s1.sno
    where sc.cno in (select distinct sc.cno from sc where sc.sno = 's001' )
    group by sc.sno,s1.sname
    having count(sc.cno) = (select count(*) from sc where sno = 's001')
    and s1.sno<>'s001';
```
###### 28.查询男生、女生人数;
```sql
    select ssex,count(*)
    from student s
    group by ssex;
```
###### 29.向SC表中插入一些记录,这些记录要求符合以下条件:没有上过编号"c002"课程的同学学号."c002"号课的平均成绩; 
```sql
    insert into sc(sno,cno,score)
    select distinct s.sno,sc.cno,(select avg(score) from sc where cno = 'c002')
    from student s inner join sc on s.sno = sc.sno
    where not exists
    (select sc.sno from sc where sc.cno = 'c002') and sc.cno = 'c002';
```
###### 30.查询所有学生的选课情况;
```sql
    select s.sno,s.sname,group_concat(cname)
    from sc inner join student s on sc.sno = s.sno inner join course c on c.cno = sc.cno
    group by s.sno;
```
###### 31.按各科平均成绩从低到高和及格率的百分数从高到低顺序;
```sql
    select sc.cno,avg(score) avg,pass/count(*) percent
    from sc,(select cno,count(*) pass from sc where score>=60 group by cno) sc2
    where sc.cno = sc2.cno
    group by sc.cno
    order by avg asc,percent desc;查询同名同性学生名单，并统计同名人数
    select cno,avg(score) avg,sum( case when score >=60 then 1 else 0 end)/count(*) as rate
    from sc 
    group by cno
    order by avg,rate desc;
```
###### 32.查询课程编号为c001 且课程成绩在80 分以上的学生的学号和姓名;
```sql
    select distinct s.sno,sname,score
    from sc inner join student s
    where cno = 'c001' and score >80;
```
###### 33.求选了课程的学生人数
```sql
    select count(distinct sno)
    from sc;
```
###### 34.查询各个课程及相应的选修人数
```sql
    select sc.cno,cname,count(distinct sno)
    from sc inner join course c on sc.cno = c.cno
    group by sc.cno;
```
###### 35.查询每门课程被选修的学生数
```sql
    select cno,count(*)
    from sc
    group by cno;
```
###### 36.查询每门功课成绩最好的前两名
```sql
    select sc.cno,substring_index(group_concat(sname order by score),',',2)
    from sc inner join student s on s.sno = sc.sno
    group by sc.cno;
```
###### 37.统计每门课程的学生选修人数（超过10 人的课程才统计）。要求输出课程号和选修人数，查询结果按人数降序排列，若人数相同，按课程号升序排列
```sql
    select cno,count(distinct sno) num
    from sc
    group by cno
    having num>10;
```
###### 39.1996年出生的学生名单(注:Student 表中Sage列的类型是number)
```sql
    select sno
    from student
    where sage = (2018-1996);
```
###### 40.查询同名同姓学生名单，并统计同名人数
```sql
    select distinct sname,count(*)
    from student s
    group by sname;
```
###### 41.查询平均成绩大于85 的所有学生的学号.姓名和平均成绩
```sql
    select s.sno,s.sname,avg(score) avg
    from sc inner join student s on s.sno = sc.sno
    group by sno
    having avg>85;
```
###### 42.查询没学过“谌燕”老师讲授的任一门课程的学生姓名
```sql
    select sc.sno,sname
    from sc inner join student s on sc.sno = s.sno
    where cno not in 
    (select sc.cno 
    from sc inner join  course c on sc.cno = c.cno inner join teacher t on c.tno = t.tno 
    where tname = '谌燕');
```
###### 43.查询两门及以上不及格课程的同学的学号及其平均成绩
```sql
    select nsno.sno,avg(score) avg
    from sc,(select sno from sc where score<60 group by sno having count(*)>=2) nsno
    where sc.sno = nsno.sno
    group by nsno.sno;
```
###### 44.查询选修"谌燕"老师所授课程的学生中,成绩最高的学生姓名及其成绩
```sql
    select sc.sno,sname,max(score)
    from sc inner join student s on sc.sno = s.sno 
    inner join course c on sc.cno = c.cno 
    inner join teacher t on c.tno = c.tno
    where tname = '谌燕';
```
###### 45.检索“c004”课程分数小于60，按分数降序排列的同学学号
```sql
    select sno
    from sc
    where cno = 'c004' and score<60
    order by score desc;
```
###### 46.查询不同课程成绩相同的学生的学号.课程号.学生成绩

```sql
    select sc1.sno,sc1.cno,sc2.sno,sc2.cno,sc1.score
    from sc sc1 inner join sc sc2 on sc1.score = sc2.score and sc1.sno<>sc2.sno;
```
###### 47.查询全部学生都选修的课程的课程号和课程名
```sql
    select sc.cno,cname
    from sc inner join course c on sc.cno = c.cno
    group by cno
    having count(distinct sno) = (select count(*) from student);
```
###### 48.查询各科成绩最高和最低的分：以如下形式显示：课程ID，最高分，最低分
```sql
    select cno,max(score) max_score,min(score) min_score
    from sc
    group by cno;
```
###### 49.检索至少选修两门课程的学生学号
```sql
    select sno,count(*)
    from sc
    group by sno
    having count(*)>=2;
```
###### 50.删除“s002”同学的“c001”课程的成绩
```sql
    delete from sc where sno = 's002' and cno = 'c001'; 
```

<font color=pink>xixixixixixi~</font>
<font color=pink>望各位道友能原谅这突兀的粉色，满足我的少女心</font>
<font color=pink>笔芯ღ( ´･ᴗ･` )</font>





