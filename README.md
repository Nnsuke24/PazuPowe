PazuPowe
========
<html>
<head>
	<meta charset = "utf-8">
	<title>パズドラ攻撃力カルキュレーター</title>
	<script type = "text/JavaScript" src="http://jquery.com/jquery-1.9.0..js"></script><!--このコードが大切！jQueryを使うために必要-->	
	<script language="JavaScript">
	function get(){ 
		var _val_lea = "";
		var _val_fri = "";
		var _val_enh = "";
		var _val_dro = "";
		var _val_lin = "";
		var _val_num = "";
		var _val_com = "";
//1-radio(leader)の取得
		var l_Power = document.getElementsByName("leader");
		for (i = 0; i < l_Power.length; i++) {
  			if (l_Power[i].checked) {
    			_val_lea = l_Power[i].value;
  			}
		}
//2-radio(friend)の取得
		var f_Power = document.getElementsByName("friend");
		for (i = 0; i < f_Power.length; i++) {
  			if (f_Power[i].checked) {
    			_val_fri = f_Power[i].value;
  			}
		}
//3-radio(enhance)の取得
		var enhance = document.getElementsByName("enhance");
		for (i = 0; i < enhance.length; i++) {
  			if (enhance[i].checked) {
    			_val_enh = enhance[i].value;
  			}
		}
//4-radio(列強化)の取得
		var arousal = document.getElementById("arousal").value;
		var drop_line = document.getElementsByName("line");
		for (i = 0; i < drop_line.length; i++) {
  			if (drop_line[i].checked) {
    			var drop_real = drop_line[i].value;
  			}
  		}
		_val_lin = 1 + 0.1 * arousal * drop_real;
//5-コンボ数(テキスト)の取得
		var c =document.getElementById("combo_all").value;
		_val_com = 1 + ((c - 1) * 0.25);

//6-攻撃力の取得
		attack1 = document.getElementById("attack").value;
//7-ドロップ数(テキスト)の取得
		var a = document.getElementById("num_drop").value;
		var b =document.getElementById("combo_own").value;
		if(b > c){
			document.getElementById("result").innerHTML = "全コンボ数に対して単色コンボ数が多いです。";
		}
		if (parseInt(a) < parseInt(b) * 3){
			document.getElementById("result").innerHTML = "ドロップ数に対してコンボ数が多いです。";
		}else{
			_val_num =  parseInt(b) + ( parseInt(a) - 3 *  parseInt(b) ) * 0.25;
		//8-radio(ドロップ強化)の取得
			var drop_str = document.getElementsByName("drop");
			if (drop_str[1].checked){
				_val_dro = 1 + (0.06 * a);
			}else{
				_val_dro = 1;
			}
		//9-最終ダメージ計算
			var damage = attack1 * _val_lea * _val_fri * _val_enh *  _val_lin * _val_com * _val_num * _val_dro;
			document.getElementById("result").innerHTML = "攻撃力："+damage;
		}

		
	}
	</script>
<!--	<style type="text/css">   
      	.l        { float : left; clear: both; width: 20%; line-height: 50px; } 
      	.l input  { float : left; width : 50%; margin-left: 20px; vertical-align: bottom;} 
      	.r        { float: right;             width : 77%;  line-height: 50px ;  } 
      	h3        { margin: 10px; } 
      	legend    {  height: 50px ; } 
      	.ui-btn-inner{ padding: 10px 15px !important}
      	.ui-controlgroup-label   { width: 13% !important; }
      	.ui-controlgroup-controls{ width: 85% !important; text-align:left}
      	input[type=number]  { width: 90px !important} 
  -->  
	</style>
</head>

<!--================================================================-->

<body>
	
	<div data-role="fieldcontain" style="text-align:center"> 
		パズドラ攻撃力計算<br><br>
		<h2>攻撃力
		<form name="form1" action="">
			<input type="text" id="attack" size="15" value="1000" style="width:12%;padding:4px;font-size:20px;text-align:center;">
			<!--input type="range" name="attack" value="1000" min="10" max="18000"  /-->
		</form>
		</h2>
		<br>
	
		<fieldset data-role="controlgroup" data-type="horizontal" > 
        	<legend>リーダースキル</legend>
			<label><input type="radio" name="leader" value="1"  checked/>なし</label> 
        	<label><input type="radio" name="leader" value="1.5"/>1.5倍</label> 
        	<label><input type="radio" name="leader" value="2"  />2倍</label> 
        	<label><input type="radio" name="leader" value="2.5"/>2.5倍</label>
        	<label><input type="radio" name="leader" value="3"  />3倍</label> 
        	<label><input type="radio" name="leader" value="3.5"/>3.5倍</label> 
        	<label><input type="radio" name="leader" value="4"  />4倍</label>
        	<label><input type="radio" name="leader" value="4.5"/>4.5倍</label> 
        	<label><input type="radio" name="leader" value="5"  />5倍</label> 
        	<label><input type="radio" name="leader" value="6"  />6倍</label>
        	<label><input type="radio" name="leader" value="7"  />7倍</label>
	    </fieldset>
	    <br>
		<fieldset data-role="controlgroup" data-type="horizontal" > 
        	<legend>フレンドスキル</legend>
			<label><input type="radio" name="friend" value="1"  checked/>なし</label> 
        	<label><input type="radio" name="friend" value="1.5"/>1.5倍</label> 
        	<label><input type="radio" name="friend" value="2"  />2倍</label> 
        	<label><input type="radio" name="friend" value="2.5"/>2.5倍</label>
        	<label><input type="radio" name="friend" value="3"  />3倍</label> 
        	<label><input type="radio" name="friend" value="3.5"/>3.5倍</label> 
        	<label><input type="radio" name="friend" value="4"  />4倍</label>
        	<label><input type="radio" name="friend" value="4.5"/>4.5倍</label> 
        	<label><input type="radio" name="friend" value="5"  />5倍</label> 
        	<label><input type="radio" name="friend" value="6"  />6倍</label>
        	<label><input type="radio" name="friend" value="7"  />7倍</label>
	    </fieldset>
	    <br>	
		<fieldset data-role="controlgroup" data-type="horizontal" > 
        	<legend>エンハンス</legend>
			<label><input type="radio" name="enhance" value="1"  checked/>なし</label>
        	<label><input type="radio" name="enhance" value="1.5"/>1.5倍</label> 
        	<label><input type="radio" name="enhance" value="2"  />2倍</label> 
        	<label><input type="radio" name="enhance" value="2.5"/>2.5倍</label> 
        	<label><input type="radio" name="enhance" value="3"  />3倍</label> 
	    </fieldset>
	    <br>
	    <fieldset data-role="controlgroup" data-type="horizontal" > 
        	<legend>列強化</legend>
        	覚醒数・・・<h><input type="number" id="arousal" value="0" size="5" style="width:5% ;text-align: center; "></h>個&emsp;&emsp;/&emsp;&emsp;
        	列数・・・
        	<label><input type="radio" name="line" value="0"  checked/>0列</label> 
        	<label><input type="radio" name="line" value="1"/>1列</label> 
        	<label><input type="radio" name="line" value="2"  />2列</label> 
        	<label><input type="radio" name="line" value="3"/>3列</label>
	    </fieldset>
	    <br>
	   	<fieldset data-role="controlgroup" data-type="horizontal" > 
        	<legend>ドロップ強化</legend>
			<label><input type="radio" name="drop" checked/>なし</label> 
        	<label><input type="radio" name="drop" />あり</label> 
	    </fieldset>
	    <br>
	    <fieldset >
    		<legend>ドロップ数・コンボ数</legend>
    		<label>単色 合計<input type="number" id="num_drop" value="3" size="3" style=" width:5% ; text-align:center;"/>個 </label>		
    		<input type="number" id="combo_own" value="1" style="width:5% ;text-align: center; "/>コンボ&emsp;&emsp;/&emsp;&emsp;
    		全<input type="number" id="combo_all" value="1" size="3" style="width:5% ;text-align: center; "/>コンボ
    	</fieldset>
		<br>

		<input type="submit" style="width:30%;padding:10px;font-size:30px;" value="攻撃力を計算" onclick = get();>
		<hr>
		<h1><div id="result">攻撃力：1000</div></h1>
	</div>
</body>
</html>
