# Jarvis
Jarvis Code

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jarvis</title>
    <style>
        body {
    background: #f3f3f3;
    margin: 0;
}
h1 { color: crimson;}
.wrapper{
    display: flex;
    flex-direction: column;
    justify-content: center;
    max-width: 768px;
    margin: 0 auto;
    padding: 25px;
    }
    p{
        color: firebrick;
    }
    body{
        background-color:red;
      }
    #start {
        background-color:crimson;
    }
    #end {
        background-color: cyan;
        color: darkblue;
    }
    </style>
</head>
<body onload="greeting()">
    <h1>HELLO I AM J.A.R.V.I.S , ________'s In Built Assistant - I was programmed by ______</h1>
    <div class="wrapper">
        <div class="actions">
            <button id="start">Talk</button>
            <button id="end" disabled>End</button>
        </div>
        <div id="transcript">
        </div>
    </div>
    <script>
    window.SpeechRecognition = window.SpeechRecognition ||
window.webkitSpeechRecognition;

const recognition = new SpeechRecognition();
recognition.interimResults = true;
const transcript_element = document.getElementById("transcript");
const talk_button = document.getElementById("start");
const end_button = document.getElementById("end");

let p = document.createElement("p");
transcript_element.appendChild(p);

recognition.addEventListener("result", (e) => {
    const transcript = Array.from(e.results)
    .map(result => result [0])
    .map(result => result.transcript)   
    .join("");
    p.textContent = transcript;;
    if(e.results[0].isFinal){
        p = document.createElement("p")
        p.textContent = transcript;
        transcript_element.appendChild(p);
        p.textContent = "";

 

        }
        if (transcript.includes("YouTube")){
            window.open('https://www.youtube.com/')
            alert(" Sir , Just a Friendly Reminder To Drink Some Water - Drinking plenty of water can help you lose weight. This is because water can increase satiety and boost your metabolic rate. Some evidence suggests that increasing water intake can promote weight loss by slightly increasing your metabolism, which can increase the number of calories you burn on a daily basis")

        }
        if (transcript.includes("WhatsApp")){
            window.open('https://web.whatsapp.com/')
            alert(" Sir , Just a Friendly Reminder To Drink Some Water - Drinking plenty of water can help you lose weight. This is because water can increase satiety and boost your metabolic rate. Some evidence suggests that increasing water intake can promote weight loss by slightly increasing your metabolism, which can increase the number of calories you burn on a daily basis")

        }
       

    }

);

function greeting(){
    alert("Good Day Sir, How Are You ?")
}

recognition.addEventListener("end", () =>{
    end_button.disabled = false;
    talk_button.disabled =  true;
 });
talk_button.addEventListener("click", () => {   
    end_button.disabled = false;
    talk_button.disabled =  true;
    recognition.start();
});
end_button.addEventListener("click", () => {
    end_button.disabled = true;
    talk_button.disabled =  false;
    recognition.stop()
});
    </script>
// JARVIS IS AMAZING
</body>
</html>
