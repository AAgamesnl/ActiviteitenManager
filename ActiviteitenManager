import tkinter as tk
import datetime as DT
import time
KlaarmakenNa12 = int(900)
KlaarmakenVoor12 = int(1800)



root = tk.Tk()
root.title('ActiviteitenManager')
frame = tk.Frame(root, height=500, width=800, bg="darkgrey")
frame.pack()


#----------------widgets--------------------
StartACL = tk.Label(frame, text="omhoelaat start je activiteit of school?", bg="darkgrey")#
StartACL.place(width=210, height=50, relx=0.001, rely=0.004)#

StartACE = tk.Entry(frame, bg="darkgrey",)#
StartACE.place(relx=0.001, rely=0.08, height=20, width=210)#

TijdOnderwegL = tk.Label(frame, text="hoelang duurt je reis in minuuten?", bg="darkgrey")#
TijdOnderwegL.place(width=190, height=50, relx=0.005, rely=0.15)#

TijdOnderwegE = tk.Entry(frame, bg="darkgrey")#
TijdOnderwegE.place(relx=0.001, rely=0.23, height=20, width=210)#

VroegTijdL = tk.Label(frame, text="hoe vroeg wil je aankomen in minuuten?", bg="darkgrey")#
VroegTijdL.place(width=220, height=50, relx=0.005, rely=0.3)#

VroegTijdE = tk.Entry(frame, bg="darkgrey")#
VroegTijdE.place(relx=0.001, rely=0.38, height=20, width=210)#

BerekenRes = tk.Label()#
BerekenRes.place(height=400, width=400, relx=0.4, rely=0.09)#

def activiteitenmanager():
    try:
        StartAC = StartACE.get()
        TijdOnderweg = int(TijdOnderwegE.get())
        VroegTijd = int(VroegTijdE.get())

        TijdOnderwegSeconds = TijdOnderweg * 60
        VroegTijdSeconds = VroegTijd * 60

        t1 = DT.datetime.strptime(StartAC, '%H:%M')
        t2 = DT.datetime(1900, 1, 1)
    except:
        BerekenRes['bg'] = "red"
        BerekenRes['text'] = "ERROR\n!!geef een juiste tijd in zoals. 8:30. \nof Geef een juiste aantal minuuten op van 0 - 60!!\nA gehandicapten rand mongool"

    StartACnaarSeconden = int(((t1 - t2).total_seconds()))

    TotaalZonderKlaarmaken = StartACnaarSeconden - TijdOnderwegSeconds - VroegTijdSeconds

    if StartACnaarSeconden < 43200:
        TotaalMetKlaarmaken = TotaalZonderKlaarmaken - KlaarmakenVoor12
    else:
        TotaalMetKlaarmaken = TotaalZonderKlaarmaken - KlaarmakenNa12

    def convert(seconds):
        seconds = TotaalMetKlaarmaken
        hour = seconds // 3600
        seconds %= 3600
        minutes = seconds // 60
        seconds %= 60
        return "%d:%02d" % (hour, minutes)

    n = TotaalMetKlaarmaken
    BerekenRes['bg'] = "white"
    BerekenRes['text'] = "je moet om " + convert(n) + " beginnen klaarmaken om optijd op je activiteit te zijn!!!"

BerekenKnop = tk.Button(text="Bereken!", command=activiteitenmanager)#
BerekenKnop.place(relx=0.07, rely=0.5, height=40, width=100)#

#----------------widgets--------------------

root.mainloop()
