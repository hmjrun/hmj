

##  数据总览

时间：2019-10-01 ~ 2019-11-01
业务：圈存

| 指标   | 总数  | 成功数 | 成功率 | 失败数 | 失败率 | 存疑数 | 初始化数 |
| :----- | :---- | ------ | ------ | ------ | ------ | ------ | -------- |
| 哈尔滨 | 44582 | 44328  | 0.9943 | 122    | 0.0027 | 7      | 125      |
| 郑州   | 32469 | 32087  | 0.9882 | 114    | 0.0035 | 27     | 241      |
| 河北   | 1226  | 1214   | 0.9902 | 10     | 0.0082 | 0      | 2        |



时间：2019-10-01 ~ 2019-11-01
业务：开卡

| 指标 | 总数 | 成功数 | 成功率 | 失败数 | 失败率 | 存疑数 | 初始化数 |
| :--- | :--- | ------ | ------ | ------ | ------ | ------ | -------- |
| 深圳 | 7019 | 6445   | 0.9182 | 548    | 0.0781 | 1      | 25       |
| 河北 | 522  | 518    | 0.9923 | 0      | 0      | 0      | 4        |
|      |      |        |        |        |        |        |          |



## 具体分析

### 郑州

失败数：114，存疑确认为失败：60笔，剩下的54笔为失败订单。





## 附SQL脚本

### 河北、哈尔

```sql
SELECT
	'2019-10-01 ~ 2019-11-01' as `时间段`,
	r.allNum AS `总数`,
	r.successNum AS `成功数`,
	r.successNum / r.allNum AS `成功率`,
	r.failNum AS `失败数`,
	r.failNum / r.allNum AS `失败率`,
	r.doubtNum,
	r.initNum 
FROM
	(
SELECT
	count( 1 ) AS `allNum`,
	sum( CASE WHEN bstatus = '1' THEN 1 ELSE 0 END ) AS `successNum`,
	sum( CASE WHEN bstatus = '-1' THEN 1 ELSE 0 END ) AS `failNum`,
	sum( CASE WHEN bstatus = '2' THEN 1 ELSE 0 END ) AS `doubtNum`,
	sum( CASE WHEN bstatus = '0' THEN 1 ELSE 0 END ) AS `initNum` 
FROM
	recharge 
WHERE
	invalid = 0 
     AND FROM_UNIXTIME( create_time / 1000, '%Y-%m-%d' ) BETWEEN '2019-10-01' AND '2019-11-01' 
	) r;
```



### 郑州

```sql
SELECT
	'2019-10-01 ~ 2019-11-01' AS `时间段`,
	r.allNum AS `总数`,
	r.successNum AS `成功数`,
	r.successNum / r.allNum AS `成功率`,
	r.failNum AS `失败数`,
	r.failNum / r.allNum AS `失败率`,
	r.doubtNum,
	r.initNum 
FROM
	(
SELECT
	count( 1 ) AS `allNum`,
	sum( CASE WHEN bstatus = '1' THEN 1 ELSE 0 END ) AS `successNum`,
	sum( CASE WHEN bstatus = '-1' THEN 1 ELSE 0 END ) AS `failNum`,
	sum( CASE WHEN bstatus = '2' THEN 1 ELSE 0 END ) AS `doubtNum`,
	sum( CASE WHEN bstatus = '0' THEN 1 ELSE 0 END ) AS `initNum` 
FROM
	`cb_recharge` 
WHERE
	invalid = 0 
	AND `app_code` = '0371' 
	AND `create_time` BETWEEN '2019-10-01' AND '2019-11-01' 
	) r;
```



