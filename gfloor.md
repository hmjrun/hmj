```html
----------------------------------------------------------
api:
----------------------------------------------------------
-给定区域id。查询商家列表
-url: /api/v1/org/role_profile/region_sellers/?region_id=01
-method: GET
-return data : 
	[
	  {
	    "invite_code": "0101000000054",
	    "seller_id": 82,
	    "seller_name": "我是商家 "
	  },
	  ...
	]
---------------------------------------------------------
给定开始时间，结束时间，区域region_id,或者细化到商家。查询历史订单列表信息
区域:/api/v1/takeout/order/history_data/?start_time=2016-08-01&end_time=2016-9-30&region_id=01
商家:/api/v1/takeout/order/history_data/?start_time=2016-08-01&end_time=2016-9-30&seller_id=89
状态:/api/v1/takeout/order/history_data/?start_time=2016-08-01&end_time=2016-9-30&region_id=01&state=delivered
method: GET
return data:
	[
	  {
	    "order_info": "美团外卖002",
	    "out_trade_no": "0102000000530",
	    "seller": "商家小辣椒6",
	    "state": "receive",
	    "time": "Mon, 12 Sep 2016 16:35:31 +0800"
	  },
	  ...
	]	
---------------------------------------------------------
给定订单out_trade_no。查询目标订单运转轨迹信息
url: /api/v1/takeout/order_tracks/detail_track/?out_trade_no=010100000002D
method: GET
return data:
	[
	  {
	    "staff_name": "15800020001 ",
	    "staff_role": "tally_staff",
	    "state": "receive",
	    "time": "Tue, 16 Aug 2016 15:17:14 +0800"
	  },
	  {
	    "staff_name": "15800002002 ",
	    "staff_role": "driver_staff",
	    "state": "loaded",
	    "time": "Tue, 16 Aug 2016 15:17:14 +0800"
	  },
	  {
	    "staff_name": "No user ",
	    "staff_role": "sorting_staff",
	    "state": "sorting",
	    "time": "Tue, 16 Aug 2016 15:17:14 +0800"
	  },
	  {
	    "staff_name": "宋江 ",
	    "staff_role": "delivery_staff",
	    "state": "delivered",
	    "time": "Tue, 16 Aug 2016 15:17:14 +0800"
	  }
	]
------------------------------------------------------------
```
