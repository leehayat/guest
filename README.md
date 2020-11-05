<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Test037.html</title>
<link rel="stylesheet" type="text/css" href="css/main.css">

<script type="text/javascript">


   // 배열 구성
   var boardArray = new Array();

   // 사용자 정의 객체 구성 (→ 생성자 함수 정의)
   function Board(uName, uContent)
   {
      // 주요 속성 구성
      this.userName=uName;
      this.content=uContent;
      this.writeDay=new Date();
   }
   
   // 프로토타입 구성을 통해... 사용자 정의 객체의 함수 정의
   //프로토타입 구성을 통해 ... 사용자 정의 객체의 함수 정
   Board.prototype.userLocalString = function()
   {
      return this.writeDay.getFullYear() + "-"
          + (this.writeDay.getMonth()+1) + "-"
          + this.writeDay.getDate() + "-"
          + this.writeDay.getHours() + ":"
          + this.writeDay.getSeconds();
          
          // 시 → getHours()
          // 분 → getMinutes()
          // 초 → getSeconds()          
   }

   function main()
   {
      //alert("함수 호출 확인");
      
      var uName = document.getElementById("uName").value;
      var uContent = document.getElementById("uContent").value;
      
      var len = boardArray.length;
      //alert(len);      //-- 이 시점에서 테스트 시 → 0
      
      boardArray[len] = new Board(uName, uContent);
      //-- 『Board()』 → 사용자 정의 객체(생성자 함수)
      
      //alert(len);// -- 작성이 이루어질 때 마다... 『+1』
      
      print(len);
      
      clear(); //폼 클리어 하도록 호출 
   }
   
   // 내용 출력 함수
   function print(idx)
   {
      //var strTemp = boardArray[idx].content;
      //alert(strTemp);
      
      var tableNode = document.getElementById("bbsTable");
      var trNode = document.createElement("tr");
      
      trNode.appendChild(createTdNode((idx+1).toString()));
      trNode.appendChild(createTdNode(boardArray[idx].userName));
      trNode.appendChild(createTdNode(boardArray[idx].content));
      trNode.appendChild(createTdNode(boardArray[idx].userLocalString()));
      
      tableNode.appendChild(trNode);
   }
   
   function createTdNode(val)
   {
      var textNode = document.createTextNode(val);
      var tdNode = document.createElement("td");
      tdNode.appendChild(textNode);
      return tdNode;
   }
   
   function clear()
   {
	
	   	document.getElementById("uName").value="";
	   	document.getElementById("uContent").value="";
	   	document.getElementById("uName").focus();
	   
   }

</script>

</head>
<body>

<div>
   <h1>자바스크립트 활용</h1>
   <hr>
</div>

<div>
   <p>사용자 정의 객체 및 프로토타입을 활용한 자바스크립트 방명록</p>
   
   <div>
      <form>
         <!-- 입력 폼을 구성하는 레이아웃 테이블 -->
         <table class="tbl">
            <tr>
               <th>작성자</th>
               <td>
                  <input type="text" id="uName" style="width: 150px;">
               </td>
            </tr>
            <tr>
               <th>내용</th>
               <td>
                  <input type="text" id="uContent" style="width: 560px;">
               </td>
            </tr>
         </table>
         
         <br>
         <input type="button" value="글쓰기" class="btn" style="width: 624px; height= 50px; font-size:18pt;" onclick="main()">
         
         <br><br>
         <!-- 방명록의 내용이 리스트 형식으로 보여지는 레이아웃 테이블 -->
         <table class="tbl" id="bbsTable">
            <tr>
               <th>번호</th>
               <th>작성자</th>
               <th>내용</th>
               <th>작성일</th>
            </tr>
         </table>
      </form>
   </div>
</div>


</body>
</html>
