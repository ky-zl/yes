# KY is our GUY
# Program source reference URL 
https://static1.squarespace.com/static/533a5f1be4b00bb34469c085/t/5ae6f3c00e2e72dfd92a15dd/1525085122048/Tamagotchi.pdf 
https://make.techwillsaveus.com/microbit/activities/micro-pet-advanced
https://microbit-micropython.readthedocs.io/en/latest/tutorials/buttons.html 

![alt text](https://raw.githubusercontent.com/ky-zl/yes/master/Screenshot%202019-09-06%20at%2022.24.40.png "Ky sleeping")

# Program description
Our Program’s name is Ky. The microbit acts like a pet that interacts with the user, with a use of buttons and motion sensors. It’s a friendly companion that can make you laugh and will perform for you, but can get upset if you are mean to it. When still, a sleeping face is displayed but when motion is detected, Ky will show a sad face and scream until he is calmed down (by pushing button A). Then Ky will ask the user if he can perform a song for the user, by scrolling text. If button A is held, he will perform “Prelude” and display a fabulous face but if button B is pressed, he will show an angry face and play “Funk”. After that, Ky spontaneously dies. This was implemented to shock/confuse the user. A skull is displayed with Ky screaming “Noooooo”, followed by a funeral song and a “X”. The user will then be confused as the “X” does not disappear for a while and no buttons have any effect, but after a certain amount of time a silly face will appear and it turns out Ky was just joking, which he communicates by displayed “JK!”. The program ends with Ky thanking you and showing a heart. He then powers down with a final goodbye, returning to the sleeping state, until he is woken up again.

![alt text](https://raw.githubusercontent.com/ky-zl/yes/master/Screenshot%202019-09-06%20at%2022.23.25.png "Ky when he is angry")

# Python Code listing
```
from microbit import

import speech
import music

while True:
    display.show(Image.ASLEEP)
    sleep(2000)
    readingx = accelerometer.get_x()
    readingy = accelerometer.get_y()
    readingz = accelerometer.get_z()
    while readingx > 300 or readingy > 300 or readingz > 300:
        display.show(Image.SAD)
        speech.say("reeeeeeeee", pitch=255, mouth=255, throat=0, speed=255)
        if button_a.get_presses() == 1:
            readingx = 0
            readingy = 0
            readingz = 0 
            display.show(Image.HAPPY)
            sleep(2000)
            display.scroll("Can I perform?")
            sleep(2000)
            if button_a.is_pressed():
                display.show(Image.FABULOUS)
                music.play(music.PRELUDE)
            elif button_b.is_pressed():
                display.show(Image.ANGRY)
                music.play(music.FUNK)
            sleep(1000)
            display.show(Image.SKULL)
            speech.say("Nooooooooooooooooooooooooo", pitch=0)
            image = Image("90009:" "09090:" "00900:" "09090:" "90009")
            display.show(image)
            music.play(music.FUNERAL)
            sleep(10000)
            display.show(Image.SILLY)
            sleep(3000)
            display.scroll("JK!")
            display.show(Image.HEART)
            sleep(2000)
            display.scroll("Thx for playing!")
            display.show(Image.HAPPY)
            sleep(2000)
            music.play(music.POWER_DOWN)
            display.scroll("I'm tired...BYE!")

```

# BBC Microbit sensors or characteristics used / showcased
We made use of the accelerometer function and the buttons for our microbit. The accelerometer was used when it displayed a sad face if moved a certain amount. The buttons were used as input from the users, in the beginning of the program to calm Ky down by pressing button A and when Ky asks if he can perform. The features used in the program are images, music and speech. Ky showcases different images and expressions throughout the program. We also imported the music and speech functions, and used them during the program multiple times.

![alt text](https://raw.githubusercontent.com/ky-zl/yes/master/Screenshot%202019-09-06%20at%2022.24.14.png "Ky playing dead")

# Testing information
We used MU editor to test our code. The “check” function was very useful for proof-reading our code and making sure it was fine before exporting the code to the microbit. Also the “flash” function played an extremely important role for checking our code, it essentially allowed us to quickly export code to the microbit with just a simple click of a button.
A big error we faced was effectively allowing the user to input choices via the buttons. The input/output section of the BBC microbit micropython helped with this as it gave us several options of how to make use of the buttons. We struggled with using “if button_a.is_pressed():” as the microbit wouldn’t respond to button A being pressed and would constantly repeat the same code. We couldn’t get it out of the loop. So we changed it to “if button_a.get_presses() == 1:” that worked much better with how we wanted our code to play out. We were a little confused in the beginning but it wasn’t actually a problem with our code, we just had a misunderstanding of it. Everything else went very smoothly, sometimes we thought button A or B didn’t work button but you just needed to hold it for a certain amount of time. 

![alt text](https://raw.githubusercontent.com/ky-zl/yes/master/Screenshot%202019-09-06%20at%2022.23.50.png "Ky being fabulous")

# List ideas to extend the project
Add more activities:
-Experiment and implement the “ticklish” function via the pins and program Ky to display a happy face when “tickled”.
-Have Ky “paint you a picture” by displaying certain animals that the user can decide on based on button A or B.
-Have Ky make poetry by using the random module.
-Experience random emotions that the user may have to deal with, by achieving a certain speed with the accelerometer or pressing button A or B.
Then add spontaneity to the program, so the multiple events aren’t always in the same order and you may get different activities every time.
