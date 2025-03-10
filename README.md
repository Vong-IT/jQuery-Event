<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>jQuery Events Example</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="script.js"></script>
</head>
<body>
    <button id="btnClick">Click Me</button>
    <button id="btnDblClick">Double Click Me</button>
    <button id="removeEvent">Remove Click Me</button>
    <div id="box" style="width:200px; height:100px; border:1px solid black; margin-top:10px;">Move Mouse Here</div>
    <p id="coords"></p>
    <input type="text" id="textInput" placeholder="Type something...">
    <p id="status"></p>
    <form id="form">
        <select id="selectBox">
            <option value="A">A</option>
            <option value="B">B</option>
            <option value="C">C</option>
        </select>
        <button type="submit">Submit</button>
    </form>
    <p id="winSize"></p>
    <p id="scrollMsg"></p>
    <button id="addBtn">Add New Button</button>
    <div id="container"></div>
    <a href="https://www.google.com">Google</a>
    <div id="outerDiv" style="width:200px; height:200px; background-color:lightgray;">
        <div id="innerDiv" style="width:100px; height:100px; background-color:gray; margin:50px auto;">Click Me</div>
    </div>
</body>
</html>
<script>
$(document).ready(function(){
    $("#btnClick").click(function(){
        alert("Clicked!");
    });
   $("#btnDblClick").dblclick(function(){
        alert("Double Clicked!");
    });

    $("#box").mouseenter(function(){
        $(this).css("background-color", "yellow");
    }).mouseleave(function(){
        $(this).css("background-color", "white");
    });

    $("#box").mousedown(function(){
        $(this).css("border", "2px solid red");
    }).mouseup(function(){
        $(this).css("border", "none");
    });

    $("#box").mousemove(function(event){
        $("#coords").text("Mouse X: " + event.pageX + ", Y: " + event.pageY);
    });
});
$(document).ready(function(){
    $("#textInput").keydown(function(){
        $("#status").text("Key is down!");
    });

    $("#textInput").keyup(function(){
        $("#status").text("Key is up!");
    });

    $("#textInput").keypress(function(){
        $("#status").text("Key is pressed!");
    });
});
$(document).ready(function(){
    $("#textInput").focus(function(){
        $(this).css("background-color", "lightblue");
    }).blur(function(){
        $(this).css("background-color", "white");
    });

    $("#selectBox").change(function(){
        alert("Selection changed to: " + $(this).val());
    });

    $("#form").submit(function(event){
        event.preventDefault(); // បញ្ឈប់ការបញ្ជូនទម្រង់
        alert("Form Submitted!");
    });
});
$(document).ready(function(){
    $(window).resize(function(){
        $("#winSize").text("Width: " + $(window).width() + " | Height: " + $(window).height());
    });

    $(window).scroll(function(){
        $("#scrollMsg").text("Scrolling...");
    });
});
$(document).ready(function(){
    $(document).on("click", ".dynamicBtn", function(){
        alert("Dynamic Button Clicked!");
    });
    $("#addBtn").click(function(){
        $("#container").append('<button class="dynamicBtn">New Button</button>');
    });
});
$(document).ready(function(){
    $("a").click(function(event){
        event.preventDefault(); // បញ្ឈប់ការបើក Link
        alert("This link won't work!");
    });

    $("#innerDiv").click(function(event){
        event.stopPropagation(); // បញ្ឈប់ Event Propagation
        alert("Inner div clicked!");
    });

    $("#outerDiv").click(function(){
        alert("Outer div clicked!");
    });
});
$(document).ready(function(){
    $("#btnClick").on("click", function(){
        alert("Clicked!");
    });

    $("#removeEvent").click(function(){
        $("#btnClick").off("click");
    });
});
</script>

