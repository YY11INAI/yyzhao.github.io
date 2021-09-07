Dota2微信小程序项目

项目简述：

使用海量的高端路人数据，通过神经网络训练出胜率模型，通过Dota2-OB观战系统，获取实时数据，传入模型，输出胜率曲线。

项目目前不能开源，该文档只是记录接口功能，为以后开源做准备！



1.赛程查询接口

URL:		 	 /matchinfo

Method: 	  GET

Data: 			match_id（可选）

Return: 

​					  {

​    						"4050777": {

​        							"match_id": "4050777",

​        							"match_name": "测试联赛",

​        							"match_title": "测试淘汰赛 BO3 第二局",

​       					 		"teamA": "Ehome",

​        							"teamB": "IG",

​        							"match_status": "waiting",

​        							"match_date": "2021-07-28 10:00"

   						 	}

​						}



2.赛程操作接口

URL:		 	 /matchinfo

Method: 	  POST

Data:			 {
    						"match_id": "4050888",
    						"match_name": "测试联赛",
    						"match_title": "测试淘汰赛 BO3 第三局",
    						"teamA":"Ehome",
    						"teamB":"IG",
    						"match_status": "waiting",
    						"match_date": "2021-07-28 10:00",
    						"operate": 0
						}

Return:

​			{

​    			"suc": 1

​			}



3.比赛实时数据获取

URL：			/winrate

Method:		POST

Data：

​		

​				

```json
{		
		"match_id": "4050888",
		"gametime": 140,
    	"status": Live,						#BanPick、PreGame、Live、Over、Wait
		"winrate": 0.5,
		"radiantheros": [2, 53, 88, 77, 39],
		"direheros": [16, 126, 31, 74, 114],
		"lasthits": [108, 137, 17, 181, 191, 147, 47, 16, 162, 181],
		"denies": [3, 5, 1, 6, 22, 3, 3, 8, 16, 14],
		"xpos": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
		"ypos": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
		"level": [18, 18, 15, 19, 22, 17, 15, 13, 18, 19],
		"respawntime": [0, 0, 0, 0, 0, 2, 0, 7, 60, 10],
		"networth": [10089, 11842, 5978, 13816, 15758, 11510, 5418, 3222, 11256, 12009],
		"exp": [15103, 15303, 11357, 16500, 23470, 14912, 11470, 9598, 15664, 17018],
		"kills": [9, 6, 2, 7, 10, 9, 1, 5, 7, 7],
		"assists": [7, 11, 16, 10, 10, 11, 15, 16, 4, 7],
		"deaths": [8, 12, 7, 3, 0, 4, 6, 12, 6, 7],
		"gold": [11814, 12532, 7015, 14151, 16263, 12639, 6509, 6721, 12931, 13118],
		"unusedgold": [11814, 12532, 7015, 14151, 16263, 12639, 6509, 6721, 12931, 13118, 1014],
		"reliablegold": [11814, 12532, 7015, 14151, 16263, 12639, 6509, 6721, 12931, 13118, 363],
		"buybackcooldown": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
		"buff_a": [false, false, false, false, false, false, false, false, false, false],
		"buff_moon": [false, false, false, false, false, false, false, false, false, false],
		"items": {
			"player0": [50, 131, 127, 1, 36, 11, 94, 0, 0, 0],
			"player1": [229, 63, 240, 42, 81, 188, 0, 0, 0, 16],
			"player2": [100, 0, 36, 180, 92, 0, 0, 0, 0, 0],
			"player3": [29, 0, 194, 112, 0, 0, 0, 0, 0, 0],
			"player4": [77, 36, 63, 116, 141, 534, 41, 0, 0, 0],
			"player5": [73, 190, 1, 100, 180, 9, 118, 39, 0, 0],
			"player6": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
			"player7": [73, 218, 0, 244, 0, 214, 0, 0, 0, 0],
			"player8": [34, 98, 65, 77, 29, 116, 0, 0, 0, 0],
			"player9": [50, 21, 108, 166, 569, 36, 11, 0, 0, 0]
		},
		"radiantbarrack": 63,
		"direbarrack": 63,
		"radianttowers": 2047,
		"diretowers": 1956,
		"roshandeathtimer": 486,
		"roshandeathcount": 1,
		"radiantkill": 35,
		"direkill": 30,
		"is_level_max": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
}
```
​		