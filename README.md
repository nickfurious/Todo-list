# Todo-list
this is my todo list, i couldn't get the trash icons to work for new items on the todo list.
css file
h1 {
  background: #2980b9;
  color: white;
  margin: 0;
  padding: 10px 20px;
  text-transform: uppercase;
  font-size: 24px;
  font-weight: normal;
  font-family: 'Roboto', sans-serif;
}

.fa-plus {
  float: right;
}

body {
  background: #009FFF;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right, #ec2F4B, #009FFF);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right, #ec2F4B, #009FFF); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Roboto', sans-serif;
}

li {
  background: #fff;
  height: 40px;
  line-height: 40px;
  color: #666;
}

input {
  font-size: 18px;
  color: #2980b9;
  background-color: #f7f7f7;
  width: 100%;
  padding: 13px 13px 13px 20px;
  box-sizing: border-box;
  border: 3px solid rgba(0, 0, 0, 0);
}

input: :focus{
  background: #fff;
  border: 3px solid #2980b9;
  outline: none;
}

li:nth-child(2n){
  background: #f7f7f7;
}

span {
  background: #e74c3c;
  height: 40px;
  margin-right: 20px;
  text-align: center;
  color: white;
  width: 0;
  display: inline-block;
  transition: 0.2s linear;
  opacity: 0;
}

li:hover span {
  width: 40px;
  opacity: 1.0;
}

#container {
  width: 360px;
  margin: 100px auto;
  background: #f7f7f7 ;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.1);
}

.completed {
  color: gray;
  text-decoration: line-through;
}
html file
<!DOCTYPE html>
<html>
  <head>
    <title>Todo List</title>
   <link rel="stylesheet" type="text/css" href="index.css">
  <link href="https://fonts.googleapis.com/css?family=Roboto&display=swap" rel="stylesheet">
    <link rel="stylesheet" type="text/css"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.4.0/css/font-awesome.css">
    <script src="https://code.jquery.com/jquery-3.4.1.min.js"
      integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo=" crossorigin="anonymous"></script>
  </head>
  <body>
  
  <div id="container">
    <h1>To-Do List <i class="fa fa-plus"></i></h1>
    <input type="text" placeholder="Add New Todo">

    <ul>
      <li><span><i class="fa fa-trash"></i></span> Go To Potions Class</li>
      <li><span><i class="fa fa-trash"></i></span> Buy New Robes</li>
      <li><span><i class="fa fa-trash"></i></span> Visit Hagrid</li>
    </ul>
  </div>

  <script type="text/javascript" src="index.js"></script>
  </body>
</html>
JS file
//Check Off Specific Todos By Clicking
$("ul").on("click","li", function(){
  $(this).toggleClass("completed");
});

//Click on X to delete Todo
$("ul").on("click", "span", function(event){
  $(this).parent().fadeout(500,function(){
    $(this).remove();
  });
  event.stopPropagation();
});

$("input[type='text']").keypress(function(event){
  if(event.which === 13){
    // grabbing new todo text from input 
    var todoText =  $(this).val();
    $(this).val("");
    // create a new li and add to ul
    $("ul").append("<li><span><i class='fa fa - trash'></i></span> " + todoText +"</li>")
  }
});

$(".fa-plus").click(function(){
  $("input[type='text'").fadeToggle();
});
