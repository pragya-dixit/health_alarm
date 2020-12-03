# health_alarm
#this alarm reminds u to do exercise , refrain to use any screen for specific time in order to relax your eyes , to drink water after every specific time interval. the busy schedules needs alarm like this.  
from pygame import mixer
from time import time
from datetime import datetime


def musicbajega(file, stopper):
    mixer.init()
    mixer.music.load(file)
    mixer.music.play()
    while True:
        user_input = input()
        if user_input == stopper:
            mixer.music.stop()
            break


def log_content(msg):
    with open("tut.txt", "a") as l:
        l.write(f"{msg} at {datetime.now()}   \n")
        print()


water_time = time()
eye_time = time()
exercise_time = time()
secs_OF_water = 45*60
secs_OF_eye = 30*60
secs_OF_exercise = 40*60
while True:
    if (time() - water_time) > secs_OF_water:
        print("water________________time      ")
        musicbajega("drinking.ogg", "drank")
        water_time = time()
        log_content("drank water ")

    if (time() - eye_time) > secs_OF_eye:
        print("eye_______________relaxation________________time      ")
        musicbajega("relaxing.mp3", "done")
        eye_time = time()
        log_content("done with eye relaxation  ")
    if (time() - exercise_time) > secs_OF_exercise:
        print("exercise_______________________________time      ")
        musicbajega("warmup.mp3", "havedone")
        eye_time = time()
        log_content("done exercise  ")


