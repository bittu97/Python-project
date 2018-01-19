
from Tkinter import *
import sqlite3
conn = sqlite3.connect('list.db')

c = conn.cursor()

c.execute("""CREATE TABLE IF NOT EXISTS lists1 (
            name varchar,
            p11 varchar,
            v11 varchar,
            p21 varchar,
            v21 varchar,
            p31 varchar,
            v31 varchar,
            p41 varchar,
            v41 varchar,
            p51 varchar,
            v51 varchar,
            p61 varchar,
            v61 varchar,
            ip11 varchar,
            iv11 varchar,
            ip21 varchar,
            iv21 varchar,
            ip31 varchar,
            iv31 varchar)""")

conn.commit()


root=Tk()
def placeod(op):
    global p1,v1,p2,v2,p3,v3,p4,v4,p5,v5,p6,v6,ip1,iv1,ip2,iv2,ip3,iv3
    li=[(op,p1,v1,p2,v2,p3,v3,p4,v4,p5,v5,p6,v6,ip1,iv1,ip2,iv2,ip3,iv3)]
    #print odperson
    #print op
    c = conn.cursor()
    c.executemany("INSERT INTO lists1 VALUES(?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?)",li)
    conn.commit()
    c.execute('select * from lists1')
    q=c.fetchall()
    print q
    #billa.destroy()
    #Menu()
    
    p1=0
    v1=0
    p2=0
    v2=0
    p3=0
    v3=0
    p4=0
    v4=0
    p5=0
    v5=0
    p6=0
    v6=0
    ip1=0
    iv1=0
    ip2=0
    iv2=0
    ip3=0
    iv3=0
pi=9
spo=0
root.title('Front Page')
root.geometry('1000x600')
                   #===================================================== BILL PAGE====================================================

                   #===============================================ORDER VARIABLES======================================
#odperson=""
p1=0
v1=0
p2=0
v2=0
p3=0
v3=0
p4=0
v4=0
p5=0
v5=0
p6=0
v6=0
ip1=0
iv1=0
ip2=0
iv2=0
ip3=0
iv3=0
a=PhotoImage(file = "front.gif")
Label(root, image=a).pack()
def front():
    root.destroy()
    Menu()
root.after(3000,front)
def Menu():
    roo=Tk()
    roo.title('Menu')
    roo.geometry('1000x600')
    scrollbar = Scrollbar(roo)
    scrollbar.pack(side=RIGHT, fill=Y)
    b=PhotoImage(file = "wood.gif")
    Label(roo,image=b,bd=0).place(x=0,y=0)
    c=PhotoImage(file = "ground.gif")
    Label(roo,image=c,bd=0).place(x=22,y=20)
    def desol():
        roo.destroy()
    button = Button(roo, text="Click me!")
    quito = PhotoImage(file="quit.gif")
    button.config(image=quito,bd=0,command=desol)
    button.place(x=337,y=440)
    #Label(roo,image=d,bd=0).place(x=180,y=775)
    #e=PhotoImage(file ="bot2.gif")
    #Label(roo,image=e,bd=0).place(x=1000,y=775)
    f=PhotoImage(file = "ground2.gif")
    Label(roo,image=f,bd=0).place(x=450,y=20)
    #======================================================================== ITALIAN SECTION=====================================
    def specialo():
        if(spo==1):
            roo.destroy()
        global spo
        spo=0
        rto=Tk()
        rto.title('Italian')
        rto.geometry('1000x600')
        dro=PhotoImage(file = "italian.gif")
        Label(rto,image=dro,bd=0).place(x=0,y=0)
        def desol():
            rto.destroy()
            Menu()
        Button(rto,text="BACK",relief=GROOVE,bg="red",command=desol).place(x=920,y=570)
        #==================================================================PIZZA ORDER=============================================
        def counter1():
            global pi
            pi=0
            #print pi
            order()
        def counter2():
            global pi
            pi=1
            order()
        def counter3():
            global pi
            pi=2
            order()
        def order():
            rto.destroy()
            rtto=Tk()
            def deso():
                rtto.destroy()
                global pi
                pi=9
            rtto.title('Order Window')
            rtto.geometry('400x400')
            obg=PhotoImage(file = "ordbg.gif")
            Label(rtto,image=obg,bd=0).place(x=0,y=0)
            if(pi==0):
                im=PhotoImage(file = "mexio.gif")
                Label(rtto,image=im,bd=0).place(x=0,y=0)
                qty=PhotoImage(file = "qty.gif")
                Label(rtto,image=qty,bd=0).place(x=20,y=100)
                en=Entry(rtto)
                en.place(x=200,y=104)
                #burst=PhotoImage(file = "burst.gif")
                #Label(ro,image=burst,bd=0)
                b1=IntVar()
                b2=IntVar()
                b3=IntVar()
                Checkbuttn = Checkbutton(rtto, text="Click me!")
                imgb = PhotoImage(file="burst.gif")
                Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
                Checkbuttn.place(x=5,y=200)
                Checkbuttn = Checkbutton(rtto, text="Click me!",variable=b2,onvalue=2)
                imgt = PhotoImage(file="thin.gif")
                Checkbuttn.config(image=imgt,bg="brown",variable=b3,onvalue=4)
                Checkbuttn.place(x=140,y=200)
                Checkbuttn = Checkbutton(rtto, text="Click me!")
                imgs = PhotoImage(file="stuff.gif")
                Checkbuttn.config(image=imgs,bg="brown")
                Checkbuttn.place(x=275,y=200)
                Button(rtto,text="BACK",command=lambda:[deso(),specialo()],relief=GROOVE,bg="red").place(x=260,y=370)
                def odadder():
                    global ip1
                    ip1=float(en.get())
                    if(ip1==0):
                        global iv1
                        iv1=0
                    else:
                        global iv1
                        iv1=b1.get()+b2.get()+b3.get()
                    rtto.destroy()
                    specialo()
                Button(rtto,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
            if(pi==1):
                im=PhotoImage(file = "peperoni.gif")
                Label(rtto,image=im,bd=0).place(x=0,y=0)
                qty=PhotoImage(file = "qty.gif")
                Label(rtto,image=qty,bd=0).place(x=20,y=100)
                en=Entry(rtto)
                en.place(x=200,y=104)
                #burst=PhotoImage(file = "burst.gif")
                #Label(ro,image=burst,bd=0)
                b1=IntVar()
                b2=IntVar()
                b3=IntVar()
                Checkbuttn = Checkbutton(rtto, text="Click me!")
                imgb = PhotoImage(file="burst.gif")
                Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
                Checkbuttn.place(x=5,y=200)
                Checkbuttn = Checkbutton(rtto, text="Click me!")
                imgt = PhotoImage(file="thin.gif")
                Checkbuttn.config(image=imgt,bg="brown",variable=b2,onvalue=2)
                Checkbuttn.place(x=140,y=200)
                Checkbuttn = Checkbutton(rtto, text="Click me!")
                imgs = PhotoImage(file="stuff.gif")
                Checkbuttn.config(image=imgs,bg="brown",variable=b3,onvalue=4)
                Checkbuttn.place(x=275,y=200)
                Button(rtto,text="BACK",command=lambda:[deso(),specialo()],relief=GROOVE,bg="red").place(x=260,y=370)
                def odadder():
                    global ip2
                    ip2=float(en.get())
                    if(ip1==0):
                        global iv2
                        iv1=0
                    else:
                        global iv2
                        iv2=b1.get()+b2.get()+b3.get()
                    rtto.destroy()
                    specialo()
                Button(rtto,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
            if(pi==2):
                im=PhotoImage(file = "seafood.gif")
                Label(rtto,image=im,bd=0).place(x=0,y=0)
                qty=PhotoImage(file = "qty.gif")
                Label(rtto,image=qty,bd=0).place(x=20,y=100)
                en=Entry(rtto)
                en.place(x=200,y=104)
                #burst=PhotoImage(file = "burst.gif")
                #Label(ro,image=burst,bd=0)
                b1=IntVar()
                b2=IntVar()
                b3=IntVar()
                Checkbuttn = Checkbutton(rtto, text="Click me!")
                imgb = PhotoImage(file="burst.gif")
                Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
                Checkbuttn.place(x=5,y=200)
                Checkbuttn = Checkbutton(rtto, text="Click me!")
                imgt = PhotoImage(file="thin.gif")
                Checkbuttn.config(image=imgt,bg="brown",variable=b2,onvalue=2)
                Checkbuttn.place(x=140,y=200)
                Checkbuttn = Checkbutton(rtto, text="Click me!")
                imgs = PhotoImage(file="stuff.gif")
                Checkbuttn.config(image=imgs,bg="brown",variable=b3,onvalue=4)
                Checkbuttn.place(x=275,y=200)
                Button(rtto,text="BACK",command=lambda:[deso(),specialo()],relief=GROOVE,bg="red").place(x=260,y=370)
                def odadder():
                    global ip3
                    ip3=float(en.get())
                    if(ip3==0):
                        global iv3
                        iv3=0
                    else:
                        global iv3
                        iv3=b1.get()+b2.get()+b3.get()
                    rtto.destroy()
                    specialo()
                Button(rtto,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
            rtto.mainloop()
        #===================================================================PIZZA BUTTON=============================================
        button = Button(rto, text="Click me!")
        mexi = PhotoImage(file="mexican.gif")
        button.config(image=mexi,bd=0,command=counter1)
        button.place(x=633,y=30)
        button = Button(rto, text="Click me!")
        pep = PhotoImage(file="peper.gif")
        button.config(image=pep,bd=0,command=counter2)
        button.place(x=633,y=475)
        button = Button(rto, text="Click me!")
        see = PhotoImage(file="seefood.gif")
        button.config(image=see,bd=0,command=counter3)
        button.place(x=580,y=250)
        rto.mainloop()
    button = Button(roo, text="Click me!")
    dro = PhotoImage(file="bot2.gif")
    def spoo():
        global spo
        spo=1
    button.config(image=dro,bd=-1,command=lambda:[spoo(),specialo()])
    button.place(x=550,y=440)
    #g=PhotoImage(file = "opizza.gif")
    #Label(roo,image=g,bd=0).place(x=980,y=495)
                                                                                             #=============================ORDER WINDOW=====================
    def counter1():
        global pi
        pi=0
        #print pi
        order()
    def counter2():
        global pi
        pi=1
        order()
    def counter3():
        global pi
        pi=2
        order()
    def counter4():
        global pi
        pi=3
        order()
    def counter5():
        global pi
        pi=4
        order()
    def counter6():
        global pi
        pi=5
        order()
    def order():
        roo.destroy()
        ro=Tk()
        def deso():
            ro.destroy()
            global pi
            pi=9
        ro.title('Order Window')
        ro.geometry('400x400')
        obg=PhotoImage(file = "ordbg.gif")
        Label(ro,image=obg,bd=0).place(x=0,y=0)
        if(pi==0):
            im=PhotoImage(file = "orrange.gif")
            Label(ro,image=im,bd=0).place(x=0,y=0)
            qty=PhotoImage(file = "qty.gif")
            Label(ro,image=qty,bd=0).place(x=20,y=100)
            en=Entry(ro)
            en.place(x=200,y=104)
            #burst=PhotoImage(file = "burst.gif")
            #Label(ro,image=burst,bd=0)
            b1=IntVar()
            b2=IntVar()
            b3=IntVar()
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgb = PhotoImage(file="burst.gif")
            Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
            Checkbuttn.place(x=5,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgt = PhotoImage(file="thin.gif")
            Checkbuttn.config(image=imgt,bg="brown",variable=b2,onvalue=2)
            Checkbuttn.place(x=140,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgs = PhotoImage(file="stuff.gif")
            Checkbuttn.config(image=imgs,bg="brown",variable=b3,onvalue=4)
            Checkbuttn.place(x=275,y=200)
            Button(ro,text="BACK",command=lambda:[deso(),Menu()],relief=GROOVE,bg="red").place(x=260,y=370)
            def odadder():
                global p1
                p1=float(en.get())
                global v1
                v1=b1.get()+b2.get()+b3.get()
                ro.destroy()
                Menu()
            Button(ro,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
        if(pi==1):
            im=PhotoImage(file = "mus.gif")
            Label(ro,image=im,bd=0).place(x=0,y=0)
            qty=PhotoImage(file = "qty.gif")
            Label(ro,image=qty,bd=0).place(x=20,y=100)
            en=Entry(ro)
            en.place(x=200,y=104)
            #burst=PhotoImage(file = "burst.gif")
            #Label(ro,image=burst,bd=0)
            b1=IntVar()
            b2=IntVar()
            b3=IntVar()
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgb = PhotoImage(file="burst.gif")
            Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
            Checkbuttn.place(x=5,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgt = PhotoImage(file="thin.gif")
            Checkbuttn.config(image=imgt,bg="brown",variable=b2,onvalue=2)
            Checkbuttn.place(x=140,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgs = PhotoImage(file="stuff.gif")
            Checkbuttn.config(image=imgs,bg="brown",variable=b3,onvalue=4)
            Checkbuttn.place(x=275,y=200)
            Button(ro,text="BACK",command=lambda:[deso(),Menu()],relief=GROOVE,bg="red").place(x=260,y=370)
            def odadder():
                global p2
                p2=float(en.get())
                global v2
                v2=b1.get()+b2.get()+b3.get()
                ro.destroy()
                Menu()
               # print p2,v2
            Button(ro,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
        if(pi==2):
            im=PhotoImage(file = "maghi.gif")
            Label(ro,image=im,bd=0).place(x=0,y=0)
            qty=PhotoImage(file = "qty.gif")
            Label(ro,image=qty,bd=0).place(x=20,y=100)
            en=Entry(ro)
            en.place(x=200,y=104)
            #burst=PhotoImage(file = "burst.gif")
            #Label(ro,image=burst,bd=0)
            b1=IntVar()
            b2=IntVar()
            b3=IntVar()
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgb = PhotoImage(file="burst.gif")
            Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
            Checkbuttn.place(x=5,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgt = PhotoImage(file="thin.gif")
            Checkbuttn.config(image=imgt,bg="brown",variable=b2,onvalue=2)
            Checkbuttn.place(x=140,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgs = PhotoImage(file="stuff.gif")
            Checkbuttn.config(image=imgs,bg="brown",variable=b3,onvalue=4)
            Checkbuttn.place(x=275,y=200)
            Button(ro,text="BACK",command=lambda:[deso(),Menu()],relief=GROOVE,bg="red").place(x=260,y=370)
            def odadder():
                global p3
                p3=float(en.get())
                global v3
                v3=b1.get()+b2.get()+b3.get()
                ro.destroy()
                Menu()
            Button(ro,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
        if(pi==3):
            im=PhotoImage(file = "egg.gif")
            Label(ro,image=im,bd=0).place(x=0,y=0)
            qty=PhotoImage(file = "qty.gif")
            Label(ro,image=qty,bd=0).place(x=20,y=100)
            en=Entry(ro)
            en.place(x=200,y=104)
            #burst=PhotoImage(file = "burst.gif")
            #Label(ro,image=burst,bd=0)
            b1=IntVar()
            b2=IntVar()
            b3=IntVar()
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgb = PhotoImage(file="burst.gif")
            Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
            Checkbuttn.place(x=5,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgt = PhotoImage(file="thin.gif")
            Checkbuttn.config(image=imgt,bg="brown",variable=b2,onvalue=2)
            Checkbuttn.place(x=140,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgs = PhotoImage(file="stuff.gif")
            Checkbuttn.config(image=imgs,bg="brown",variable=b3,onvalue=4)
            Checkbuttn.place(x=275,y=200)
            Button(ro,text="BACK",command=lambda:[deso(),Menu()],relief=GROOVE,bg="red").place(x=260,y=370)
            def odadder():
                global p4
                p4=float(en.get())
                global v4
                v4=b1.get()+b2.get()+b3.get()
                ro.destroy()
                Menu()
            Button(ro,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
        if(pi==4):
            im=PhotoImage(file = "chicken.gif")
            Label(ro,image=im,bd=0).place(x=0,y=0)
            qty=PhotoImage(file = "qty.gif")
            Label(ro,image=qty,bd=0).place(x=20,y=100)
            en=Entry(ro)
            en.place(x=200,y=104)
            #burst=PhotoImage(file = "burst.gif")
            #Label(ro,image=burst,bd=0)
            b1=IntVar()
            b2=IntVar()
            b3=IntVar()
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgb = PhotoImage(file="burst.gif")
            Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
            Checkbuttn.place(x=5,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgt = PhotoImage(file="thin.gif")
            Checkbuttn.config(image=imgt,bg="brown",variable=b2,onvalue=2)
            Checkbuttn.place(x=140,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgs = PhotoImage(file="stuff.gif")
            Checkbuttn.config(image=imgs,bg="brown",variable=b3,onvalue=4)
            Checkbuttn.place(x=275,y=200)
            Button(ro,text="BACK",command=lambda:[deso(),Menu()],relief=GROOVE,bg="red").place(x=260,y=370)
            def odadder():
                global p5
                p5=float(en.get())
                global v5
                v5=b1.get()+b2.get()+b3.get()
                ro.destroy()
                Menu()
            Button(ro,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
        if(pi==5):
            im=PhotoImage(file = "hawai.gif")
            Label(ro,image=im,bd=0).place(x=0,y=0)
            qty=PhotoImage(file = "qty.gif")
            Label(ro,image=qty,bd=0).place(x=20,y=100)
            en=Entry(ro)
            en.place(x=200,y=104)
            #burst=PhotoImage(file = "burst.gif")
            #Label(ro,image=burst,bd=0)
            b1=IntVar()
            b2=IntVar()
            b3=IntVar()
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgb = PhotoImage(file="burst.gif")
            Checkbuttn.config(image=imgb,bg="brown",variable=b1,onvalue=1)
            Checkbuttn.place(x=5,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgt = PhotoImage(file="thin.gif")
            Checkbuttn.config(image=imgt,bg="brown",variable=b2,onvalue=2)
            Checkbuttn.place(x=140,y=200)
            Checkbuttn = Checkbutton(ro, text="Click me!")
            imgs = PhotoImage(file="stuff.gif")
            Checkbuttn.config(image=imgs,bg="brown",variable=b3,onvalue=4)
            Checkbuttn.place(x=275,y=200)
            Button(ro,text="BACK",command=lambda:[deso(),Menu()],relief=GROOVE,bg="red").place(x=260,y=370)
            def odadder():
                global p6
                p6=float(en.get())
                global v6
                v6=b1.get()+b2.get()+b3.get()
                ro.destroy()
                Menu()
            Button(ro,text="ADD",relief=GROOVE,bg="blue",command=odadder).place(x=350,y=370)
        #Button(ro,text="Back",command=lambda:[deso(),Menu()]).place(x=50,y=50)
        ro.mainloop()
    #def pizza():


        
                                                                                               #=======================PIZZA BUTTONS=============================
    button = Button(roo, text="Click me!")
    img = PhotoImage(file="opizza.gif")
    button.config(image=img,bd=-1,command=lambda:[counter1()])
    button.place(x=515,y=270)
    button = Button(roo, text="Click me!")
    imgm = PhotoImage(file="muspizza.gif")
    button.config(image=imgm,bd=-1,command=lambda:[counter2()])
    button.place(x=515,y=150)
    button = Button(roo, text="Click me!")
    imgmo = PhotoImage(file="maipizza.gif")
    button.config(image=imgmo,bd=-1,command=lambda:[counter3()])
    button.place(x=515,y=40)
    button = Button(roo, text="Click me!")
    imge = PhotoImage(file="epizza.gif")
    button.config(image=imge,bd=-1,command=lambda:[counter4()])
    button.place(x=770,y=150)
    button = Button(roo, text="Click me!")
    imgcd = PhotoImage(file="cdpizza.gif")
    button.config(image=imgcd,bd=-1,command=lambda:[counter5()])
    button.place(x=770,y=40)
    button = Button(roo, text="Click me!")
    imgha = PhotoImage(file="hapizza.gif")
    button.config(image=imgha,bd=-1,command=lambda:[counter6()])
    button.place(x=770,y=270)
                                                                                         #======================================================SPECIAL OFFERS============================================
    def special():
        roo.destroy()
        rt=Tk()
        rt.title("Special Offer")
        rt.geometry("650x350")
        obgs=PhotoImage(file = "special.gif")
        Label(rt,image=obgs,bd=0).place(x=0,y=0)
        def desol():
            rt.destroy()
            Menu()
        Button(rt,text="BACK",relief=GROOVE,bg="red",command=desol).place(x=390,y=320)
        rt.mainloop()
    button = Button(roo, text="Click me!")
    dr = PhotoImage(file="bot1.gif")
    button.config(image=dr,bd=-1,command=lambda:[special()])
    button.place(x=22,y=440)
                                          #========================================================================BILLING PAGE===============================================================================
    def billo():
        
        roo.destroy()
        billa=Tk()
        billa.title('Billing Section')
        billa.geometry('1000x600')
        obgs=PhotoImage(file = "billsec.gif")
        Label(billa,image=obgs,bd=0).place(x=0,y=0)
        gtotal=0
        xx=160
        gr=PhotoImage(file ="green.gif")
        if(p1!=0):
            pio=PhotoImage(file = "bilor.gif")
            Label(billa,image=pio,bd=0).place(x=390,y=xx)
            global p1
            rad=p1
            if(v1==0):
                net=rad*28
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(v1!=0):
                if(v1==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(28+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(v1==2):
                    net=(28+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v1==4):
                    net=(28+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v1==3):
                    net=(28+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v1==5):
                    net=(28+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(v1==6):
                    net=(28+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v1==7):
                    net=(28+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        if(p2!=0):
            musi=PhotoImage(file = "bilmus.gif")
            Label(billa,image=musi,bd=0).place(x=390,y=xx)
            global p2
            rad=p2
            if(v2==0):
                net=rad*30
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(v2!=0):
                if(v2==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(30+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(v2==2):
                    net=(30+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v2==4):
                    net=(30+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v2==3):
                    net=(30+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v2==5):
                    net=(30+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(v2==6):
                    net=(30+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v2==7):
                    net=(30+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        if(p3!=0):
            mari=PhotoImage(file = "bilmar.gif")
            Label(billa,image=mari,bd=0).place(x=390,y=xx)
            global p3
            rad=p3
            if(v3==0):
                net=rad*35
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(v3!=0):
                if(v3==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(35+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(v3==2):
                    net=(35+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v3==4):
                    net=(35+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v3==3):
                    net=(35+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v3==5):
                    net=(35+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(v3==6):
                    net=(35+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v3==7):
                    net=(35+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        if(p4!=0):
            eggi=PhotoImage(file = "bilegg.gif")
            Label(billa,image=eggi,bd=0).place(x=390,y=xx)
            global p4
            rad=p4
            if(v4==0):
                net=rad*30
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(v4!=0):
                if(v4==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(rad+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(v4==2):
                    net=(28+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v4==4):
                    net=(28+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v4==3):
                    net=(28+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v4==5):
                    net=(28+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(v4==6):
                    net=(28+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v4==7):
                    net=(28+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        if(p5!=0):
            chii=PhotoImage(file = "bilchi.gif")
            Label(billa,image=chii,bd=0).place(x=390,y=xx)
            global p5
            rad=p5
            if(v5==0):
                net=rad*40
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(v5!=0):
                if(v5==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(40+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(v5==2):
                    net=(40+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v5==4):
                    net=(40+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v5==3):
                    net=(40+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v5==5):
                    net=(40+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(v5==6):
                    net=(40+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v5==7):
                    net=(40+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        if(p6!=0):
            hawi=PhotoImage(file = "bilhaw.gif")
            Label(billa,image=hawi,bd=0).place(x=390,y=xx)
            global p6
            rad=p6
            if(v6==0):
                net=rad*35
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(v6!=0):
                if(v6==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(35+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(v6==2):
                    net=(35+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v6==4):
                    net=(35+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v6==3):
                    net=(35+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(v6==5):
                    net=(35+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(v6==6):
                    net=(35+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(v6==7):
                    net=(35+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        if(ip1!=0):
            mexii=PhotoImage(file = "bilmexi.gif")
            Label(billa,image=mexii,bd=0).place(x=390,y=xx)
            global ip1
            rad=ip1
            if(iv1==0):
                net=rad*45
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(iv1!=0):
                if(iv1==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(45+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(iv1==2):
                    net=(45+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(iv1==4):
                    net=(45+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(iv1==3):
                    net=(45+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(iv1==5):
                    net=(45+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(iv1==6):
                    net=(45+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(iv1==7):
                    net=(45+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        if(ip2!=0):
            pepi=PhotoImage(file = "bilpep.gif")
            Label(billa,image=pepi,bd=0).place(x=390,y=xx)
            global ip2
            rad=ip2
            if(iv2==0):
                net=rad*32
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(iv2!=0):
                if(iv2==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(32+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(iv2==2):
                    net=(32+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(iv2==4):
                    net=(32+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(iv2==3):
                    net=(32+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(iv2==5):
                    net=(32+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(iv2==6):
                    net=(32+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(iv2==7):
                    net=(32+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        if(ip3!=0):
            seai=PhotoImage(file = "bilsea.gif")
            Label(billa,image=seai,bd=0).place(x=390,y=xx)
            global ip3
            rad=ip3
            if(iv3==0):
                net=rad*34
                Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
            Label(billa,text=rad,bg="brown",fg="yellow").place(x=540,y=xx+4)
            if(iv3!=0):
                if(iv3==1):
                    #gr=PhotoImage(file ="green.gif")
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    net=(34+8)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                if(iv3==2):
                    net=(34+6)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(iv3==4):
                    net=(34+4)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(iv3==3):
                    net=(34+14)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                if(iv3==5):
                    net=(34+12)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
                if(iv3==6):
                    net=(34+10)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                if(iv3==7):
                    net=(34+18)*rad
                    Label(billa,text=net,bg="brown",fg="yellow").place(x=865,y=xx+4)
                    Label(billa,image=gr,bd=0).place(x=625,y=xx)
                    Label(billa,image=gr,bd=0).place(x=705,y=xx)
                    Label(billa,image=gr,bd=0).place(x=785,y=xx)
            gtotal=gtotal+net
            xx=xx+35
        
        Label(billa,text=gtotal,bd=0,bg="brown",fg="yellow").place(x=875,y=560)
        ent=Entry(billa)
        ent.place(x=560,y=73)
        #global odperson
        #odperson=ent.get()
        def desi():
            billa.destroy()
            Menu()
        Button(billa,text="Place Order",command=lambda:[placeod(ent.get()),desi()],bg="blue").place(x=120,y=520)
        
        #Button(billa,text="Place Order",command=pyar,bg="blue").place(x=120,y=420)
        billa.mainloop()
    Button(roo,text="Order",command=billo,bg="blue").place(x=900,y=500)
    roo.mainloop()
root.mainloop()
