<!DOCTYPE html>
<html>
<head>
    <title>AI Virtual Assistant</title>

    <style>

        body{
            font-family: Arial;
            background: linear-gradient(to right, #4facfe, #00f2fe);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container{
            background: white;
            padding: 30px;
            border-radius: 15px;
            width: 400px;
            text-align: center;
            box-shadow: 0px 0px 15px gray;
        }

        h1{
            color: #333;
        }

        button{
            padding: 15px 25px;
            background: blue;
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            cursor: pointer;
            margin-top: 20px;
        }

        button:hover{
            background: darkblue;
        }

        #output{
            margin-top: 20px;
            font-size: 20px;
            color: green;
        }

    </style>
</head>

<body>

<div class="container">

    <h1>AI Virtual Assistant</h1>

    <button onclick="startListening()">
        🎤 Speak
    </button>

    <div id="output">
        Click the button and speak
    </div>

</div>

<script>

const output = document.getElementById("output");

function speak(text){

    let speech = new SpeechSynthesisUtterance();

    speech.text = text;

    speech.volume = 1;
    speech.rate = 1;
    speech.pitch = 1;

    window.speechSynthesis.speak(speech);
}

function startListening(){

    const recognition =
    new webkitSpeechRecognition();

    recognition.lang = "en-US";

    recognition.start();

    recognition.onresult = function(event){

        let command =
        event.results[0][0].transcript.toLowerCase();

        output.innerHTML =
        "You said: " + command;

        if(command.includes("hello")){

            speak("Hello, how can I help you?");
        }

        else if(command.includes("open google")){

            speak("Opening Google");

            window.open(
            "https://www.google.com");
        }

        else if(command.includes("open youtube")){

            speak("Opening YouTube");

            window.open(
            "https://www.youtube.com");
        }

        else if(command.includes("time")){

            let time =
            new Date().toLocaleTimeString();

            speak("Current time is " + time);
        }

        else if(command.includes("your name")){

            speak("I am your AI Assistant");
        }

        else{

            speak("Sorry, I did not understand");
        }
    };
}

</script>

</body>
</html># CodeAlpha_AIvirtualAssistant
This repository is about AI virtual assistant
