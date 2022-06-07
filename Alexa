import datetime
import os
import pyttsx3
import speech_recognition as sr
import wikipedia
import webbrowser
import pywhatkit
import pyjokes


listener = sr.Recognizer()
engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
#print(voices[1].id)
engine.setProperty('voice',voices[1].id)


def speak(audio):
    engine.say(audio)
    engine.runAndWait()


def wishMe():
    hour = int(datetime.datetime.now().hour)
    if hour>=0 and hour<12:
        speak("Good Morning!")

    elif hour>=12 and hour<18:
        speak("Good Afternoon!")

    else:
        speak("Good Evening!")

    speak("I am your Alexa. Please tell me how can I help you")
def takeCommand():
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("listening...")
        r.pause_threshold = 1
        r.energy_threshold = 1000
        audio = r.listen(source)

        try:
            print("Recognizing...")
            query = r.recognize_google(audio, language='en-in')
            speak(f"User said: {query}\n")
            print(f"User said: {query}\n")
        except Exception as e:
            #print(e)
            speak("Sorry Can't hear you")
            print("Say that again...")
            return "None"
        return query
if __name__ == "__main__":
    wishMe()
    while True:
            query = takeCommand().lower()

            if 'wikipedia' in query:
                speak("searching wikipedia...")
                query=query.replace("wikiedia", "")
                results = wikipedia.summary(query, sentences=2)
                speak ("According to Wikipedia")
                print(results)
                speak(results)

            elif 'play' in query:
                query = query.replace('play', '')
                speak('playing' + query)
                pywhatkit.playonyt(query)
            
            elif 'time' in query:
                time = datetime.datetime.now().strftime('%H:%M')
                speak("The time right now is" + time)
                print(time)

            elif 'date' in query:
                date = datetime.date.today()
                speak(date)
                print(date) 

            elif 'joke' in query:
                query = (pyjokes.get_joke())
                print(query)
                speak(query)

            elif 'google' in query:
                query = query.replace('google', '')
                speak("According to google" + query)
                pywhatkit.search(query)
                results = wikipedia.summary(query, sentences=2)
                speak(results)

            elif 'open youtube' in query:
                webbrowser.open("youtube.com")

            elif 'open google' in query:
                webbrowser.open("google.com")

            elif 'how are you' in query:
                speak("I am fine. Thank you for asking.")
                print("I am fine. Thank you for asking")

            elif 'open code' in query:
                codePath = "C:\\Users\\Rhishav\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"
                os.startfile(codePath)

            elif 'quit' or 'bye' in query:
                speak("GoodBye see you again")
                break
            
            
