# JsonRegObject

RegLab_RESSECT.json --> 未使用

ExamRepor.json --> 未使用, 請勿修改

summary.json --> 未使用, 請勿修改

TpnOrder.json --> 未使用, 請勿修改

IOReg_QDC.json --> 有使用, 請勿修改



--------------------
| Calories.json |
--------------------

	說明 : 
		(1) item : QDC 類別,null是其他
		(2) parser_name : 這個類別要用的參數
		(3) mappings.regex_str:parse的關鍵字
		(4) mappings.valueKey:要用哪個value
		(5) mappings.parameter:係數
	範例 :
	        "item": "進食",
            "parser_name": "lost",
            "mappings": [
                {
                    "regex_str": "配方奶",
                    "regex_flags": "ism",
                    "valueKey": "inp_val2",
                    "parameter": 0.8
                },
                {
                    "regex_str": "母奶",
                    "regex_flags": "ism",
                    "valueKey": "inp_val2",
                    "parameter": 0.7
                }
            ]

--------------------
| Chronic_Lab.json |
--------------------

	說明 : 以 [ ] 包覆要解析的條件, 條件用「" "」包覆, 各條件用「,」區隔  
	範例 :
		{
		    "Biochemical": ["Na,","K,"],  // ["aaa","bbb"] --> 此為符合Biochemical的兩項條件
		    "Blood": ["CBC","DC","HGB"],
		    "Cultivate": ["CULTURE"],
		    "GAS": ["BLOOD GAS"],
		    "Glu": [],
		    "Radiation": ["CHEST KUB"]
		}

--------------
| Class.json |
--------------
	說明 : 
		(1) mappings.key : 顯示於畫面上的類別文字
		(2) mappings.regex_str : 以()包覆整個條件, 中間用 | 區隔多個條件
            ex. (A | B) --> 符合 A or B 的條件
	範例 :
	    {
	        "parser_name": "NonLabExamReport",
	        "apply_condition":  {
	            "name": "NonLabExamReport",
	            "lab": null
	        },
	        "mappings": [
	            {
	                "key": "生化類別",
	                "regex_str": "(CHEST\\s+KUB\\s+\\(FOR\\s+BABY\\)\\s+PORTABLE)|(BRAIN\\s+ECHO\\s+\\(NBD\\))",
	                "regex_flags": "ism",
	                "sample": null
	            },
	    }

------------------
| ExamRepor.json | --> 有在用嗎?
------------------
	說明 : title 以 [ ] 包覆要解析的條件, 條件用「" "」包覆, 各條件用「,」區隔 
	範例 :
	    {
	        "select": "血球記數CBC",
	        "index": 0,
	        "title": [
	            "WBC",
	            "Band",
	            "Seg",
	            "Lym",
	            "Hb",
	            "Hct",
	            "PLT"
	        ]
	    },


----------------
| FlagReg.json |
----------------
	說明 : 
		(1) ParseValueUD 以 [ ] 包覆要解析的條件, 條件用「" "」包覆, 各條件用「,」區隔 
		(2) ParseValueTRT 以 [ ] 包覆要解析的條件, 條件用「" "」包覆, 各條件用「,」區隔 
	範例 :	    
	    {
	        "item": "InvasiveRespirator",
	        "ParseValueUD": [],
	        "ParseValueTRT": ["(?<!非)侵入性氧療設備"]
	    },



----------------
| LabView.json |
----------------
	說明 : mappings.regex_str : 以()包覆整個條件, 中間用 | 區隔多個條件
	範例 :
    {
        "parser_name": "Labview value Mg++",
        "apply_condition": {
            "name": "mg",
            "sample": null,
            "lab": null,
            "start_time": null,
            "end_time": null
        },
        "mappings": [
            {
                "key": "mg",
                "regex_str": "mg\\s*(\\d+(.\\d+)*)\\s*\\(",
                "regex_flags": "im",
                "position": 1
            }
        ]
    },


-------------------
| WhiteBlack.json |
-------------------
	說明 : mappings.regex_str : 以()包覆整個條件, 中間用 | 區隔多個條件
	範例 :
	    {
        "parser_name": "White List",
        "mappings": [
            {
                    "key": "UDGNAME",
                    "regex_str": "(Ampicillin\\s+sod\\s+for\\s+inj\\s+500\\s+mg)",
                    "regex_flags": "ism"
            },
            {
                    "key": "UDRPNAME",
                    "regex_str": "(Ampolin\\s+inj\\s+500\\s+mg\\s+\\\"YF\\\")",
                    "regex_flags": "ism"
            }
        ]
    },
