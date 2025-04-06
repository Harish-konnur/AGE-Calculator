# AGE-Calculator

HTML//

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <div class="calci">
            <h1> JavaScript<br> Age<span>Calculator</span></h1>
            <div class="box">
                <input type="date" id="date">
             <button onclick="calculateAge()">Calculate</button>
            </div>
            <p id="result"></p>
        </div>
    </div>
    <script>

        let userInput = document.getElementById("date");
        userInput.max = new Date().toISOString().split("T")[0];

        let result = document.getElementById("result");

        function calculateAge(){
            
            let birthdate = new Date(userInput.value)

            let d1 =birthdate.getDate();
            let m1 =birthdate.getMonth() + 1;
            let y1 =birthdate.getFullYear();

            let today = new Date();

            let d2 =today.getDate();
            let m2 =today.getMonth() + 1;
            let y2 =today.getFullYear();

            let d3,m3,y3;

            y3 = y2 - y1;

            if(m2>=m1) {
                m3 =m2-m1;
            }
            else{
                y3--;
                m3 = 12 + m2 - m1;
            }

            if(d2>=d1){
                d3 = d2 - d1;
            }
            else{
                m3--;
                d3 = getDaysInMonth(y1  , m1)  + d2  - d1;
            }

            if(m3<0)
            {
                m3 =11;
                y3--;
            }
            result.innerHTML =you are <span>${y3}</span> years,<span> ${m3}</span> months, and <span>${d3} </span> days old;
        

        }

        function getDaysInMonth(year,month){
            return new Date(year, month, 0).getDate();
        }

    </script>
</body>
</html>


CSS///
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: sans-serif;
}
.container{
    width: 100%;
    min-height: 100vh;
    background: linear-gradient(135deg, #4203a9, #90bafc);
    color: #fff;
    padding: 10px;
}

.calci{
    width: 100%;
    max-width: 400px;
    margin-left: 10%;
    margin-top: 10%;
}
.calci h1{
    font-size: 60px;
}

.calci h1 span{
    color: #ffff76;

}
.box{
    margin: 40px 0;
    padding: 35px;
    border-radius: 10px;
    background: rgba(255,255,255,0.3);
    display: flex;
    align-items: center;
}

.box input{
    flex: 1;
    margin-right: 20px;
    padding: 14px 20px;
    border: 0;
    outline: 0;
    font-size: 18px;
    border-radius: 5px;
    position: relative;

}

.box button{
    background: #ffff76;
    border: 0;
    outline:0;
    padding: 15px 30px;
    border-radius: 4px;
    font-weight: 500;
    color: #333;
    cursor: pointer;
}
.box input::-webkit-calendar-picker-indicator{
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: auto;
    position: absolute;
    background-position: calc(100% - 10px);
    background-size: 30px;
    cursor: pointer;
    height: auto;


}

#result{
    font-size: 20px;
}

#result span{
    color: #ffff76;
}
