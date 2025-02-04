# Speech-To-Text
import speech_recognition as sr

def recognize_speech_from_mic():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print(" Listening... Speak now:")
        recognizer.adjust_for_ambient_noise(source, duration=1)  # Reduce background noise
        audio = recognizer.listen(source)
    
    try:
        text = recognizer.recognize_google(audio)
        print(f" Recognized Text: {text}")
        return text
    except sr.UnknownValueError:
        print(" Could not understand the audio")
    except sr.RequestError:
        print("⚠ API request failed, check internet connection")

if __name__ == "__main__":
    recognize_speech_from_mic()
