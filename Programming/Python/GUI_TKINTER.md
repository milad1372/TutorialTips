### installation
Linux
```
sudo apt-get install python-tk
```
Mac
```
brew install tcl-tk
```

### usage
https://realpython.com/python-gui-tkinter/

https://likegeeks.com/python-gui-examples-tkinter-tutorial/

```
from tkinter import *
from tkinter.ttk import *
window = Tk()
window.title("Welcome to LikeGeeks app")
selected = IntVar()
rad1 = Radiobutton(window,text='First', value=1, variable=selected)
rad2 = Radiobutton(window,text='Second', value=2, variable=selected)
rad3 = Radiobutton(window,text='Third', value=3, variable=selected)
def clicked():
   print(selected.get())
btn = Button(window, text="Click Me", command=clicked)
rad1.grid(column=0, row=0)
rad2.grid(column=1, row=0)
rad3.grid(column=2, row=0)
btn.grid(column=3, row=0)
window.mainloop()
```
```
from tkinter import *

from tkinter import messagebox

window = Tk()

window.title("Welcome to LikeGeeks app")

#window.geometry('600x500')

#def clicked():
#    messagebox.showinfo('Message title', 'Message content')
#btn = Button(window,text='Click here', command=clicked)
#btn.grid(column=0,row=0)

window.attributes('-fullscreen',True)
window.configure(bg='black')
window.mainloop()
```
#### CLOCK
```
from tkinter import *
from tkinter import messagebox
import time
import sys

def tick():
    global time1
    # get the current local time from the PC
    time2 = time.strftime('%H:%M:%S')
    # if time string has changed, update it
    if time2 != time1:
        time1 = time2
        clock.config(text=time2)
        # calls itself every 200 milliseconds
        # to update the time display as needed
        # could use >200 ms, but display gets jerky
    clock.after(200, tick)

window = Tk()

time1 = ''

#status = Label(window, text="v1.0", bd=1, relief=SUNKEN, anchor=W)
#status.grid(row=0, column=0)

clock = Label(window, font=('times', 30, 'bold'), fg='white', bg='black')
#clock.grid(row=0, column=1)
clock.config(anchor=CENTER)
clock.pack()

tick()

window.title("Welcome to LikeGeeks app")

#window.geometry('600x500')

#def clicked():
#    messagebox.showinfo('Message title', 'Message content')
#btn = Button(window,text='Click here', command=clicked)
#btn.grid(column=0,row=0)

window.attributes('-fullscreen',True)

window.configure(bg='black')

window.mainloop()
```
### CLock V2
```
pip install persiantools
```
```
from tkinter import *
from tkinter import messagebox
import subprocess
import time
import sys
from persiantools.jdatetime import JalaliDate
import datetime
import urllib.request

def tick():
    global time1
    # get the current local time from the PC
    time2 = time.strftime('%H:%M:%S')
    # if time string has changed, update it
    if time2 != time1:
        time1 = time2
        clock.config(text=time2)
        # calls itself every 200 milliseconds
        # to update the time display as needed
        # could use >200 ms, but display gets jerky
    clock.after(200, tick)

def exit():
    sys.exit()

def webstats():
    try:
        urllib.request.urlopen("http://localhost").getcode()
        test = "SV UP"
        statuslab.config(fg="GREEN")
    except Exception as e:
        test = "SV Down"
        statuslab.config(fg="RED")
    statuslab.config(text=test)

def startweb():
    ps = subprocess.Popen("sudo python3 /home/pi/Downloads/WOL_CCTV/button.py", shell=True, stdout=subprocess.PIPE)
    #stopweb.config(bg="BLUE")
    statuslab.config(fg="GREEN", text="Start")

def stopweb():
    ps = subprocess.Popen("sudo kill -9 $(ps -ef | grep '/usr/bin/python3 /home/pi/Downloads/WOL_CCTV/button.py' | head -n1 | awk '{print $2}')", shell=True, stdout=subprocess.PIPE)
    ps.wait()
    output1, errors1 = ps.communicate()
    #stopweb.config(bg="RED")
    statuslab.config(fg="RED", text="Stop")


def status():
    p1 = subprocess.Popen("/opt/vc/bin/vcgencmd measure_temp", shell=True, stdout=subprocess.PIPE)
    p2 = subprocess.Popen("ifconfig | grep 'inet 192' | awk '{print $2}'", shell=True, stdout=subprocess.PIPE)
    p3 = subprocess.Popen("df -h | grep '/dev/root' | awk '{print $5}'", shell=True, stdout=subprocess.PIPE)

    p1.wait()

    output1, errors1 = p1.communicate()
    output2, errors2 = p2.communicate()
    output3, errors3 = p3.communicate()
    webstats()
    templab.config(text=output1)
    iplab.config(text=output2)
    usagelab.config(text=output3)
    templab.after(3000, status)



window = Tk()
frame = Frame(window)
frame.pack()

pdate = JalaliDate.today()

time1 = ''
#status = Label(window, text="v1.0", bd=1, relief=SUNKEN, anchor=W)
#status.grid(row=0, column=0)

########CLOCK########

clock = Label(window, font=('times', 74, 'bold'), fg='white', bg='black')
#clock.grid(row=0, column=1)
clock.config(anchor=CENTER)
pdatelab = Label(window, font=('times', 14, 'bold'), fg='white', bg='black')
#clock.grid(row=0, column=1)
pdatelab.config(text=pdate,anchor=CENTER)
clock.pack()
pdatelab.pack()
tick()

#######EXIT BTN##########
fm1 = Frame(window)
fm1.config(bg="black")

exitbtn = Button(fm1, text="EXIT APP",bg='#0059b3' , command=exit)
exitbtn.pack( side = TOP)

startweb = Button(fm1, text="Start WB",bg='#0059b3' , command=startweb)
startweb.pack( side = TOP)

stopweb = Button(fm1, text="Stop WB",bg='#0059b3', command=stopweb)
stopweb.pack( side = TOP)

statuslab = Label(fm1,font=('times', 14, 'bold'), background="black", fg="WHITE", anchor=W)
statuslab.pack( side = TOP)
webstats()

fm1.pack(side=RIGHT, expand=YES)
#######STATUS###########
###TEMP
fm2 = Frame(window)
fm2.config(bg="black")

templab = Label(fm2,font=('times', 14, 'bold'), background="black", fg="#3471eb", anchor=W)
templab.pack( side = TOP )
iplab = Label(fm2,font=('times', 14, 'bold'), background="black", fg="#3471eb", anchor=W)
iplab.pack( side = TOP )
usagelab = Label(fm2,font=('times', 14, 'bold'), background="black", fg="#3471eb", anchor=W)
usagelab.pack( side = TOP )

fm2.pack(side=LEFT, expand=YES )

status()
#########################
window.title("Welcome to LikeGeeks app")

#window.geometry('600x500')
#def clicked():
#    messagebox.showinfo('Message title', 'Message content')
#btn = Button(window,text='Click here', command=clicked)
#btn.grid(column=0,row=0)

window.attributes('-fullscreen',True)

window.configure(bg='black')

window.mainloop()

```
