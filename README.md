# yingjiaren14520
备忘录
<meta name="viewport" content="width=device-width" />
<style>
.bak{
    border:1px  solid  #aaa;
    border-radius:5px;
     margin:10px;
     padding:10px;
    background:#ccc;
}
</style>
<div id="d1">
      <h3>备忘录</h3>
      <hr/>
      <div onclick="toAdd()" style="font-size:25px;">+</div>
      <div id="bakList"></div>
      </div>
<div id="d2" style="display:none">
      <h3 onclick="toReturn()">返回     新增备忘录</h3>
      <hr/>
      <div id="cnt"  contentEditable style="height:300px;border:1px     
   solid red;"></div>
 </div>
<script>
var baks=[];
if(localStorage.baks){
      baks=JSON.parse(localStorage.baks);
}
function showBak(){
    bakList.innerHTML="";
    for(var i=baks.length-1;i>=0;i--){
           var b=baks[i];
	bakList.innerHTML = bakList.innerHTML + "<div class='bak'>"
	+b.content+"<div>"+b.createDate+"</div>　<span onclick='delBak("+i+")'）>删除</span></div>";
          
}
}
showBak();
function delBak(i){
    if(confirm("确定要删除吗?")){
            baks.splice(i,1);
            showBak();
            localStorage.baks=JSON.stringify(baks);
}
}
function toAdd(){
      d1.style.display="none";
      d2.style.display="block";
}
function toReturn(){
      d1.style.display="block";
      d2.style.display="none";
      baks.push({
             content:cnt.innerText,
              createDate:(new Date()).toLocaleString()
}); 
      localStorage.baks=JSON.stringify(baks);
      cnt.innerHTML="";
      showBak();
}
</script>
