# < !DOCTYPE html > < html > < head > < meta name = "viewport"
content = "width=device-width, initial-scale=1.0" / > < style >
    canvas {
    border: 1px solid #000000;
    background-color: # 00FFFF;
} < /style>
</head > < body onload = "startGame()" > < script >
<script>
  window.fbAsyncInit = function() {
    FB.init({
      appId      : '657143474492922',
      xfbml      : true,
      version    : 'v2.8'
    });

    // widowsNOTES
  };

  (function(d, s, id){
     var js, fjs = d.getElementsByTagName(s)[0];
     if (d.getElementById(id)) {return;}
     js = d.createElement(s); js.id = id;
     js.src = "//connect.facebook.net/en_US/sdk.js";
     fjs.parentNode.insertBefore(js, fjs);
var myGamePiece;

function startGame() {
    myGamePiece = new component(30, 30, "smiley.gif", 10, 120, "image");
    myGameArea.start();
}

var myGameArea = {
    canvas: document.createElement("canvas"),
    start: function () {
        this.canvas.width = 480;
        this.canvas.height = 270;
        this.context = this.canvas.getContext("2d");
        document.body.insertBefore(this.canvas, document.body.childNodes[0]);
        this.frameNo = 0;
        this.interval = setInterval(updateGameArea, 20);
    },
    clear: function () {
        this.context.clearRect(0, 0, this.canvas.width, this.canvas.height);
    },
    stop: function () {
        clearInterval(this.interval);
    }
}

    function component(width, height, color, x, y, type) {
        this.type = type;
        if (type == "image") {
            this.image = new Image();
            this.image.src = color;
        }
        this.width = width;
        this.height = height;
        this.speedX = 0;
        this.speedY = 0;
        this.x = x;
        this.y = y;
        this.update = function () {
            ctx = myGameArea.context;
            if (type == "image") {
                ctx.drawImage(this.image,
                    this.x,
                    this.y,
                    this.width, this.height);
            } else {
                ctx.fillStyle = color;
                ctx.fillRect(this.x, this.y, this.width, this.height);
            }
        }
        this.newPos = function () {
            this.x += this.speedX;
            this.y += this.speedY;
        }
    }

    function updateGameArea() {
        myGameArea.clear();
        myGamePiece.newPos();
        myGamePiece.update();
    }

    function move(dir) {
        myGamePiece.image.src = "angry.gif";
        if (dir == "up") {
            myGamePiece.speedY = -1;
        }
        if (dir == "down") {
            myGamePiece.speedY = 1;
        }
        if (dir == "left") {
            myGamePiece.speedX = -1;
        }
        if (dir == "right") {
            myGamePiece.speedX = 1;
        }
    }

    function clearmove() {
        myGamePiece.image.src = "smiley.gif";
        myGamePiece.speedX = 0;
        myGamePiece.speedY = 0;
    } < /script>
<div style="text-align:center;width:480px;">
  <button onmousedown="move('up')" onmouseup="clearmove()" ontouchstart="move('up')">UP</button > < br > < br > < button onmousedown = "move('left')"
onmouseup = "clearmove()"
ontouchstart = "move('left')" > LEFT < /button>
  <button onmousedown="move('right')" onmouseup="clearmove()" ontouchstart="move('right')">RIGHT</button > < br > < br > < button onmousedown = "move('down')"
onmouseup = "clearmove()"
ontouchstart = "move('down')" > DOWN < /button>
</div >

< p > & copy widowskenya 2016 & trade; < /p>
   }(document, 'script', 'facebook-jssdk'));
</script>
</body> </html>
