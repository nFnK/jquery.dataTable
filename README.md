jquery.dataTable
-------------
jquery 数据表格

![](https://poppinrubo.github.io/jquery.dataTable/images/125055_CqBH_2939922.png)  

![](https://poppinrubo.github.io/jquery.dataTable/images/125202_2Po2_2939922.png)  

`dataTable配置项` 
<br>
<br>
<table>
    <tr>
        <td colspan="2">配置项</td>
        <td>说明</td>
        <td>选项</td>
    </tr>
    <tr>
        <td colspan="2">debug</td>
        <td>是否开启调试模式，默认关闭</td>
        <td>可选,bool类型，false-true</td>
    </tr>
	<tr>
        <td colspan="2">method</td>
        <td>发送数据请求的方式，默认使用GET方式请求</td>
        <td>可选,string类型，get-post</td>
    </tr>
	<tr>
        <td colspan="2">serial</td>
        <td>表格是否生成序号，默认生成序号</td>
        <td>可选,bool类型，false-true</td>
    </tr>
    <tr>
        <td colspan="2">check</td>
        <td>行是否开启复选框,默认关闭</td>
        <td>可选,bool类型，false-true</td>
    </tr>
    <tr>
        <td colspan="2">pageCapacity</td>
        <td>页码容量，一页显示数据的条数，默认为10行</td>
        <td>可选，int 正整数</td>
    </tr>
    <tr>
        <td colspan="2">loading</td>
        <td>是否显示加载动画，默认加载</td>
        <td>可选,bool类型，false-true</td>
    </tr>
    <tr>
        <td colspan="2">url</td>
        <td>返回数据的URL地址,返回数据为json格式，不填写只能生成表头</td>
        <td>必选,string类型</td>
    </tr>
    <tr>
        <td colspan="2">style</td>
        <td>table样式设置,可自行编写css样式，多项，格式{"font-size": "12px", "width": "800px"}</td>
        <td>可选,object类型</td>
    </tr>
    <tr>
        <td colspan="2">align</td>
        <td>内容停靠方向,默认靠向左</td>
        <td>可选，string类型center , left , right</td>
    </tr>
    <tr>
        <td colspan="2">ButtonStyle</td>
        <td>按钮部件风格，按钮背景色与字体颜色，两项,格式{fontColor:"#ffffff",backgroundColor:"#10AA9C"}，默认黑色</td>
        <td>可选,object类型</td>
    </tr>
    <tr>
        <td colspan="2">oddEven</td>
        <td>奇偶行样式，开启后显示样式区别奇偶行,默认开启</td>
        <td>可选,bool类型，false-true</td>
    </tr>
    <tr>
        <td colspan="2">sign</td>
        <td>行选中标记，开启后点击行选中显示标记,风格与ButtonStyle的backgroundColor一致，默认开启</td>
        <td>可选,bool类型，false-true</td>
    </tr>	
    <tr>	
	<td rowspan="5">columns</td>
	<td>ColumnName</td>
        <td>绑定的字段名，必须与返回数据字段对应，自定义列可不设置该属性</td>
        <td>非按钮列必选，string类型</td>
    </tr>
    <tr>
	<td>title</td>
        <td>显示的表头列名</td>
        <td>必选，string类型</td>
    </tr>
    <tr>
    	<td>width</td>
        <td>列宽</td>
        <td>可选，int 正整数</td>
    </tr>
    <tr>
    	<td>button</td>
        <td>自定义按钮功能列，设置按钮名为此按钮标识，自定义列可必选设置该属性，自定义按钮列不需设置ColumnName</td>
        <td>按钮列必选，string类型,英文(与事件绑定)</td>
    </tr>
    <tr>
    	<td>buttonName</td>
        <td>自定义按钮功能列,显示的按钮名，自定义列可必选设置该属性，自定义按钮列不需设置ColumnName</td>
        <td>按钮列必选，string类型</td>
    </tr>
</table>

`dataTable事件` 
<br>
<br>
<table>
    <tr>
        <td>事件名</td>
        <td>说明</td>
        <td>使用方法</td>
    </tr>
    <tr>
        <td>Click</td>
        <td>行单击事件,返回该行数据</td>
        <td>Click: function (row){alert(row.id);}使用row.返回数据字段可获得数据,列未显示也可获得数据</td>
    </tr>
    <tr>
        <td>doubleClick</td>
        <td>行双击击事件，返回该行数据，该双击事件不触发单击事件</td>
        <td>设置doubleClick: function (row){alert(row.id);}使用row.返回数据字段可获得数据,列未显示也可获得数据</td>
    </tr>
    <tr>
        <td>自定义Click</td>
        <td>点击按钮，返回该行数据,设置的button为del 则事件为delClick</td>
        <td>设置 自定义Click:function (row) {alert(row.id);} 与双击单击事件用法一致</td>
    </tr>
</table>

`使用方法` 
<br><br>
1、引入JQ及dataTable插件
``` html

<script type="text/javascript" src="jquery-3.1.1.min.js"></script>
<script type="text/javascript" src="jquery.dataTable.js"></script>
```
2、创建table

``` html

<table id="table"></table>
```
3、绑定设置

``` JavaScript


        $("#Table").dataTable({
            debug: true,
            check: true,
            pageCapacity:15,
            loading:false,
            oddEven:false,
            url: "data.php",
            style: {"font-size": "12px", "width": "800px"},
            align:"center",
            ButtonStyle:{fontColor:"#ffffff",backgroundColor:"#10AA9C"},
            columns: [
                {ColumnName: "id", title: "ID", width: 30},
                {ColumnName: "name", title: "视频名", width: 500},
                {ColumnName: "img", img:true, title: "图片", width: 40},//img:true,后台数据反回图片url这一列就生成图片显示
                {title: "查看", button: "show", buttonName: "查看", width: 50},//自定义的按钮
                {title: "编辑", button: "edit", buttonName: "编辑", width: 50},//自定义的按钮
                {title: "删除", button: "del", buttonName: "删除", width: 50}//自定义的按钮
            ],
            Click: function (row) {//内置事件行单击
                alert("单击："+row.id);
            },
            doubleClick: function (row) {//内置事件行双击事件
                alert("双击："+row.id);
            }
            ,
            editClick: function (row) {//自定义按钮事件，事件名是上面设置的按钮名+Click
                alert("自定义编辑："+row.id);
            }
            ,
            delClick: function (row) {
                alert("自定义删除："+row.id);
            },
            showClick: function (row) {
                alert("自定义查看："+row.name);
            }
        });
```
`关于后台数据` 
<br>
<br>
返回的json格式(total:为数据总条数，用于分页)
``` JavaScript

{
  "total": 3744,
  "rows": [
    {
      "id": 3832,
      "name": "Haeni Kim- Falling For Someone New - Kuma"
    },
    {
      "id": 3831,
      "name": "Top Moments- A Friday Night vol. 100 (Korea)"
    },
    {
      "id": 3830,
      "name": "WAACKXXY Waacking 2017"
    },
    {
      "id": 3829,
      "name": "TRIX a.k.a. EYE X Krump 2017"
    }
  ]
}
```
后台需配合插件做分页设置，插件默认使用GET方式(可以设置为POST)发送page(页码)和pageCapacity(页码容量，一页显示的条数),后台需要收到这两个参数处理分页。

参照PHP版本可解析到对象,并处理输出

``` php

<?php
    $page = $_GET["page"];
    $Capacity = $_GET["pageCapacity"];
    $List = $DB->order('id desc')->limit($page, $Capacity)->select('video');
    $total = $DB->count('video');
    $rows = array();
    foreach ($List as $ListRow) {
        $rows[] = array(
            'id' => $ListRow['id'],
            'name' => $ListRow['name'],
        );
    }
    $data = array('total' => $total, 'rows' => $rows);
echo json_encode($data);
?>
```
以上示例仅供参考,不建议直接使用在项目。对于分页可自行封装
<br>
<br>

`获取返回数据的使用方法`
<br>
<br>
``` JavaScript

$('#Table').GetJSONArray();//获取Table通过URL获取到的数据，为数组类型的数据集
$('#Table').GetCheckArray();//获取当前复选框选中的值，为数组类型的数据集,未选择获取到null
```
`刷新表格数据`
<br>
<br>
``` JavaScript

$('#Table').TableRefresh();
//通过table绑定调用可以刷新当前表格数据，
//效果相当于点击了一下刷新按钮，
//要说明的是数据无变化并且没有开启loading，看着没变化并不是坏掉了
```
`通过url实现搜索功能`
<br>
<br>
``` JavaScript

//如果绑定的URL为url: "data.php",则可以通过以下方式来设置,然后后台对URL的get请求参数的处理进行表格的搜索查询
$("#Table").dataTable({
    url: "data.php?name=查询"
})
//注意事项:需要考虑到IE浏览器的情况搜索中文需要使用encodeURI进行编码,避免传到后台乱码无法查询，则使用以下方式
$("#Table").dataTable({
    url: "data.php?name="+encodeURI("查询")
})
```
搜索功能拉取数据PHP参考代码
<br>
``` php

<?php
function getList()
{/*拉取列表*/
    include_once('class/DB.php');
    $DB = new DB();
    $page = $_GET["page"];
    $Capacity = $_GET["pageCapacity"];
    $Query = $_GET["search"];
    $List = $DB->order('AmountID asc')->limit($page, $Capacity)->select('statistics');/*常规查询*/
    $total = $DB->count('statistics');
    if ($Query != null && $Query != "") {/*搜索内容不为空则采取模糊查询*/
        $total = $DB->where("material like '%$Query%'")->count('statistics');
        $List = $DB->order('AmountID desc')->where("material like '%$Query%'")->limit($page, $Capacity)->select('statistics');
        if (is_numeric($Query)) {/*实现ID查询判断是否为数字*/
            $total = $DB->where(array("AmountID" => $Query))->count('statistics');
            $List = $DB->order('AmountID asc')->where(array("AmountID" => $Query))->limit($page, $Capacity)->select('statistics');
        }
    }
    $rows = array();
    foreach ($List as $ListRow) {
        $rows[] = array(
            'id' => $ListRow['AmountID'],
            'ip' => $ListRow['ip'],
            'material' => $ListRow['material']==null?"无":$ListRow['material'],
            'time' => $ListRow['PlayData'],
        );
    }
    //返回数据
    echo json_encode(array('total' => $total, 'rows' => $rows));
}
getList();
?>
```
### [查看demo](http://www.showdoing.cn/dataTable/ "查看demo")
