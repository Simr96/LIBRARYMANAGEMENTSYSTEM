# LIBRARYMANAGEMENTSYSTEM
Library management system built with python and using library Tkinter. Backend data stored with the help of SQL workbench.
from tkinter import*
from tkinter import ttk
import mysql.connector
import sqlite3
import datetime
from tkinter import messagebox
import _tkinter
import tkinter


class LibraryManagementSystem:
    def __init__(self, root):
        self.root=root
        self.root.title = "Library Management System"
        self.root.geometry("1920x1080+0+0")
     
        #=========variables=========

        self.member_var = StringVar()
        self.prnno_var = StringVar()
        self.title_var = StringVar()
        self.firstname_var = StringVar()
        self.lastname_var = StringVar()
        self.address1_var = StringVar()
        self.address2_var = StringVar()
        self.postcode_var = StringVar()
        self.mobile_var = StringVar()
        self.booktitle_var = StringVar()
        self.bookid_var = StringVar()
        self.author_var = StringVar()
        self.dateborrowed_var = StringVar()
        

        lbltitle = Label(self.root, text = "Library Management System", bg = 'pink', fg = "black", bd=20,relief = RIDGE, font =("times new roman", 50, "bold"),padx = 2, pady = 6)
        lbltitle.pack(side = TOP, fill = X)
        
        frame =  Frame(self.root,bd = 12, relief = RIDGE , padx = 20, bg = 'powder blue')
        frame.place(x=0,y=130,width = 1900, height = 510)


        #========df left=========

        DataFrameLeft=LabelFrame(frame,  text = "Library Membership Information", bg = 'powder blue', fg = "green", bd=20,relief = RIDGE, font =("times new roman", 30, "bold" ))
        DataFrameLeft.place(x =0, y =5, width = 910, height= 460 )
        
        lblMember = Label(DataFrameLeft, text = "Member", font = ("times new roman", 14, "bold"),padx= 2, pady = 6, bg ="powder blue")
        lblMember.grid(row = 0, column =0, sticky=W)
        
        comMember = ttk.Combobox(DataFrameLeft,textvariable=self.member_var, font = ("times new roman", 14 ,"bold"), width = 27, state = "readonly")
        comMember["value"] = ("Admin Staff", "Student", "Lecturer")
        comMember.current(0)
        comMember.grid(row=0,column = 1)

        lblPRN_No = Label(DataFrameLeft,font = ("arial", 14, "bold"), text = "PRN No:", padx= 2, bg = "powder blue")
        lblPRN_No.grid(row =1, column =0, sticky=W)
        txtPRN_No=Entry(DataFrameLeft, font= ("times new roman", 20, "bold"),textvariable = self.prnno_var,width = 20)
        txtPRN_No.grid(row =1, column =1)
 
        lblTitle = Label(DataFrameLeft, font = ("arial", 14, "bold"),  text = "Title", padx= 2,pady = 6, bg = "powder blue")
        lblTitle.grid(row =2, column =0, sticky=W)
        txtTitle=Entry(DataFrameLeft, font= ("times new roman", 20, "bold"),textvariable = self.title_var,width = 20)
        txtTitle.grid(row =2, column =1)
         
        lblFirstName = Label(DataFrameLeft,font = ("arial", 14, "bold"), text = "Firstname:", padx= 2, pady = 6, bg = "powder blue")
        lblFirstName.grid(row =3, column =0, sticky=W)
        txtFirstName=Entry(DataFrameLeft, font= ("times new roman", 20, "bold"),textvariable = self.firstname_var,width = 20)
        txtFirstName.grid(row =3, column =1)

        lblLastName = Label(DataFrameLeft, font = ("arial", 14, "bold"),  text = "LastName", padx= 2,pady = 6, bg = "powder blue")
        lblLastName.grid(row =4, column =0, sticky=W)
        txtLastName=Entry(DataFrameLeft, font= ("times new roman", 20, "bold"),textvariable = self.lastname_var,width = 20)
        txtLastName.grid(row =4, column =1)

        lblAddress1 = Label(DataFrameLeft, font = ("arial", 14, "bold"), text = "address1", padx= 2,pady = 6, bg = "powder blue")
        lblAddress1.grid(row =5, column =0, sticky=W)
        txtAddress1=Entry(DataFrameLeft, font= ("times new roman", 20, "bold"),textvariable = self.address1_var,width = 20)
        txtAddress1.grid(row =5, column =1)

        lblAddress2 = Label(DataFrameLeft, font = ("arial", 14, "bold"),  text = "address2", padx= 2,pady = 6, bg = "powder blue")
        lblAddress2.grid(row =6, column =0, sticky=W)
        txtAddress2=Entry(DataFrameLeft, font= ("times new roman", 20, "bold"),textvariable = self.address2_var,width = 20)
        txtAddress2.grid(row =6, column =1)
        
        lblpc = Label(DataFrameLeft, font = ("arial", 14, "bold"), text = "postcode", padx= 2,pady = 6, bg = "powder blue")
        lblpc.grid(row =7, column =0, sticky=W)
        txtpc=Entry(DataFrameLeft, font= ("times new roman", 20, "bold"),textvariable = self.postcode_var,width = 20)
        txtpc.grid(row =7, column =1)

        lblmobile= Label(DataFrameLeft, font = ("arial", 14, "bold"), text = "mobile", padx= 2,pady = 6, bg = "powder blue")
        lblmobile.grid(row =8, column =0, sticky=W)
        txtmobile=Entry(DataFrameLeft, font= ("times new roman", 20, "bold"),textvariable = self.mobile_var,width = 20)
        txtmobile.grid(row =8, column =1)

        lblBookid = Label(DataFrameLeft, font = ("arial", 14, "bold"), text = "Bookid", padx= 2, bg = "powder blue")
        lblBookid.grid(row =1, column =2, sticky=W)
        txtBookid=Entry(DataFrameLeft, font= ("arial", 20, "bold"),textvariable = self.bookid_var,width = 12)
        txtBookid.grid(row =1, column =3)

        lblBooktitle = Label(DataFrameLeft, font = ("arial", 14, "bold"), text = "Booktitle", padx= 2, bg = "powder blue")
        lblBooktitle.grid(row =2, column =2, sticky=W)
        txtBooktitle=Entry(DataFrameLeft, font= ("arial", 20, "bold"),textvariable = self.booktitle_var,width = 12)
        txtBooktitle.grid(row =2, column =3)

        lblBookau = Label(DataFrameLeft, font = ("arial", 14, "bold"), text = "Author", padx= 2, bg = "powder blue")
        lblBookau.grid(row =3, column =2, sticky=W)
        txtBookau=Entry(DataFrameLeft, font= ("arial", 20, "bold"),textvariable = self.author_var,width = 12)
        txtBookau.grid(row =3, column =3)


        lblBookdb = Label(DataFrameLeft, font = ("arial", 14, "bold"), text = "dateborrowed", padx= 2, bg = "powder blue")
        lblBookdb.grid(row =4, column =2, sticky=W)
        txtBookdb=Entry(DataFrameLeft, font= ("arial", 20, "bold"), textvariable = self.dateborrowed_var, width = 12)
        txtBookdb.grid(row =4, column =3)

         
        #=======================df right=======

        DataFrameRight=LabelFrame(frame,  text = "Book Details", bg = 'powder blue', fg = "green", bd=20,relief = RIDGE, font =("times new roman", 30, "bold" ))
        DataFrameRight.place(x =920, y =5, width = 900, height= 460 )

        self.txtBox=Text(DataFrameRight, font = ("arial", 12, "bold"), width = 48, height = 18, padx=2, pady =6)
        self.txtBox.grid(row=0,column =2)
        
        listScrollbar = Scrollbar(DataFrameRight)
        listScrollbar.grid(row=0, column =1, sticky = "ns")
        listBooks = ['row', 'grow', 'thesecret','think and grow', 'why', 'kyu',    'excellent', 'good', 'nice','harry potter']

        def SelectBook(event=""):
            value = str(listBox.get(listBox.curselection()))
            x = value
            if (x == "row"):
                self.bookid_var.set("93u")
                self.booktitle_var.set("hello hfg")
                self.author_var.set("simran")               
                d1 = datetime.datetime.today()
                d2 = datetime.timedelta(days =15)
                d3 = d1 + d2
                self.dateborrowed_var.set(d1)

            elif (x == "grow" ):

                self.bookid_var.set("4553u")

                self.booktitle_var.set("the hfg")
                

                self.author_var.set("dennis")
                

                d1 = datetime.datetime.today()

                d2 = datetime.timedelta(days =15)

                d3 = d1 + d2

                self.dateborrowed_var.set(d1)

            elif (x == "think and grow" ):

                self.bookid_var.set("9799u")

                self.booktitle_var.set("helloyrr")
                

                self.author_var.set("hasns h")
                

                d1 = datetime.datetime.today()

                d2 = datetime.timedelta(days =15)

                d3 = d1 + d2

                self.dateborrowed_var.set(d1)

            elif (x == "the secret" ):

                self.bookid_var.set("93u")

                self.booktitle_var.set("hello hfg")
                

                self.author_var.set("simran")
                

                d1 = datetime.datetime.today()

                d2 = datetime.timedelta(days =15)

                d3 = d1 + d2

                self.dateborrowed_var.set(d1)


            elif (x == "why" ):

                self.bookid_var.set("93u")

                self.booktitle_var.set("hello hfg")
                

                self.author_var.set("simran")
                

                d1 = datetime.datetime.today()

                d2 = datetime.timedelta(days =15)

                d3 = d1 + d2

                self.dateborrowed_var.set(d1)

            elif (x == "kyu" ):

                self.bookid_var.set("93u")

                self.booktitle_var.set("hello hfg")
                

                self.author_var.set("simran")
                

                d1 = datetime.datetime.today()

                d2 = datetime.timedelta(days =15)

                d3 = d1 + d2

                self.dateborrowed_var.set(d1)

            elif (x == "good" ):

                self.bookid_var.set("93u")

                self.booktitle_var.set("hello hfg")
                

                self.author_var.set("simran")
                

                d1 = datetime.datetime.today()

                d2 = datetime.timedelta(days =15)

                d3 = d1 + d2

                self.dateborrowed_var.set(d1)

            elif (x == "harry potter" ):

                self.bookid_var.set("93u")

                self.booktitle_var.set("hello hfg")
                

                self.author_var.set("roslign")
                d1 = datetime.datetime.today()
                d2 = datetime.timedelta(days =15)
                d3 = d1 + d2
                self.dateborrowed_var.set(d1)
 


        listBox = Listbox(DataFrameRight, font = ("arial", 12, "bold"), width = 24, height = 18, exportselection=False, selectmode=MULTIPLE)
        listBox.bind("<ButtonRelease-1>", SelectBook)
        listBox.grid(row = 0, column = 0, padx =4)
        listScrollbar.config(command = listBox.yview)

        for item in listBooks:
            listBox.insert(END, item)



        #==================button frame======

        Framebutton =  Frame(self.root,bd = 12, relief = RIDGE , padx = 20, bg = 'powder blue')
        Framebutton.place(x=0,y=600,width = 1900, height = 80)
       
        btnAddData = Button(Framebutton, command = self.adda_data,text= "Add Data",font = ("arial", 12, "bold"), width = 23, bg ="blue", fg = "white")
        btnAddData.grid(row = 0, column = 0)
        
        btnAddData = Button(Framebutton,command = self.showData, text= "Show Data",font = ("arial", 12, "bold"), width = 23, bg ="blue", fg = "white")
        btnAddData.grid(row = 0, column = 1)

        btnAddData = Button(Framebutton, command = self.update,text= "Update",font = ("arial", 12, "bold"), width = 23, bg ="blue", fg = "white")
        btnAddData.grid(row = 0, column = 2)

        btnAddData = Button(Framebutton,command = self.delete,text= "Delete",font = ("arial", 12, "bold"), width = 23, bg ="blue", fg = "white")
        btnAddData.grid(row = 0, column = 3)

        btnAddData = Button(Framebutton,command = self.reset, text= "Reset",font = ("arial", 12, "bold"), width = 23, bg ="blue", fg = "white")
        btnAddData.grid(row = 0, column = 4)

        btnAddData = Button(Framebutton, command = self.iExit, text= "Exit",font = ("arial", 12, "bold"), width = 23, bg ="blue", fg = "white")
        btnAddData.grid(row = 0, column = 5)
       
        #=======================information frame=====

        framedetails =  Frame(self.root,bd = 12, relief = RIDGE , padx = 20, bg = 'powder blue')
        framedetails.place(x=0,y=680,width = 1900, height = 310)

        Table_frame = Frame(framedetails, bd = 6, relief = RIDGE , bg = 'powder blue')
        Table_frame.place(x=0,y=2,width = 1840, height = 260)

        xscroll = ttk.Scrollbar(Table_frame, orient= HORIZONTAL)
        yscroll = ttk.Scrollbar(Table_frame, orient= VERTICAL)

        self.mydataa_table=ttk.Treeview(Table_frame, column = ("membertype", "prnno","title","firstname","lastname",
        "address1","address2", "postcode","mobile","dateborrowed", "bookid", "booktitle","author"),xscrollcommand=xscroll.set,yscrollcommand=yscroll.set)


        xscroll.pack(side = BOTTOM,fill=X)
        yscroll.pack(side = RIGHT,fill=Y)

        xscroll.config(command = self.mydataa_table.xview)
        yscroll.config(command = self.mydataa_table.yview)

        self.mydataa_table.heading("membertype", text ="member")
        self.mydataa_table.heading("prnno", text ="PRN No.")
        self.mydataa_table.heading("title", text ="Title")
        self.mydataa_table.heading("firstname", text ="First Name")
        self.mydataa_table.heading("lastname", text ="Last Name")
        self.mydataa_table.heading("address1", text ="Address1")
        self.mydataa_table.heading("address2", text ="Address2")
        self.mydataa_table.heading("postcode", text ="Postcode")
        self.mydataa_table.heading("mobile", text ="Mobile")
        self.mydataa_table.heading("bookid", text = "Bookid")
        self.mydataa_table.heading("booktitle", text ="booktitle")
        self.mydataa_table.heading("author", text ="author")
        self.mydataa_table.heading("dateborrowed", text ="dateborrowed")

        self.mydataa_table["show"] = "headings"
        self.mydataa_table.pack(fill=BOTH, expand =1)

        self.mydataa_table.column("membertype", width =100)
        self.mydataa_table.column("prnno", width =100)
        self.mydataa_table.column("title", width =100)
        self.mydataa_table.column("firstname", width =100)
        self.mydataa_table.column("lastname", width =100)
        self.mydataa_table.column("address1", width =100)
        self.mydataa_table.column("address2", width =100)
        self.mydataa_table.column("postcode", width =100)
        self.mydataa_table.column("mobile", width =100)
        self.mydataa_table.column("bookid", width =100)
        self.mydataa_table.column("booktitle", width =100)
        self.mydataa_table.column("author", width =100)
        self.mydataa_table.column("dateborrowed", width =100)

        self.fetch_data()
        self.mydataa_table.bind("<ButtonRelease-1>", self.get_cursor)

    def adda_data(self):
        conn = mysql.connector.connect(host="localhost", username = "simran",password = "Mysql03", database="mydata")
        cursor = conn.cursor()
        cursor.execute("insert into mydataa values(%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s)",(
                                                                                                self.member_var.get(),
                                                                                                self.prnno_var.get(),
                                                                                                self.title_var.get(),
                                                                                                self.firstname_var.get(),
                                                                                                self.lastname_var.get(),
                                                                                                self.address1_var.get(),
                                                                                                self.address2_var.get(),
                                                                                                self.bookid_var.get(),
                                                                                                self.booktitle_var.get(),
                                                                                                self.mobile_var.get(),
                                                                                                self.author_var.get(),
                                                                                                self.postcode_var.get(),
                                                                                                self.dateborrowed_var.get()
                                                                                                
                                                                                             ))

        conn.commit()
        self.fetch_data()
        conn.close()

        messagebox.showinfo("successbox","successfully added")

    def fetch_data(self):
        conn = mysql.connector.connect(host="localhost", username = "simran",password = "Mysql03", database="mydata")
        cursor = conn.cursor()
        cursor.execute("select * from mydataa")
        rows = cursor.fetchall()

        if len(rows)!=0:
            self.mydataa_table.delete(*self.mydataa_table.get_children())
            for i in rows:
                self.mydataa_table.insert("", END, values = i)
            conn.commit()
        conn.close()

    def get_cursor(self,  event = "" ):
        cursor_row = self.mydataa_table.focus()
        content = self.mydataa_table.item(cursor_row)
        row = content['values']

        self.member_var.set(row[0]),
        self.prnno_var.set(row[1]),
        self.title_var.set(row[2]),
        self.firstname_var.set(row[3]),
        self.lastname_var.set(row[4]),
        self.address1_var.set(row[5]),
        self.address2_var.set(row[6]),
        self.postcode_var.set(row[7]),
        self.mobile_var.set(row[8]),
        self.bookid_var.set(row[9]),
        self.booktitle_var.set(row[10]),
        self.author_var.set(row[11]),
        self.dateborrowed_var.set(row[12])

    def showData(self):
        self.txtBox.insert(END, "Member Type\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "PRN No\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Title\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Firstname\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Lastname\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Address1\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Address2\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Postcode\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Mobile\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Bookid\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Booktitle\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "Author\t\t" + self.member_var.get() + "\n")
        self.txtBox.insert(END, "DateBorrowed\t\t" + self.member_var.get() + "\n")
    

    def reset(self):
        self.member_var.set(""),
        self.prnno_var.set(""),
        self.title_var.set(""),
        self.firstname_var.set(""),
        self.lastname_var.set(""),
        self.address1_var.set(""),
        self.address2_var.set(""),
        self.postcode_var.set(""),
        self.mobile_var.set(""),
        self.bookid_var.set(""),
        self.booktitle_var.set(""),
        self.author_var.set(""),
        self.dateborrowed_var.set("")
        self.txtBox.delete("1.0",END)
    
    def iExit(self):
        iExit = tkinter.messagebox.askyesno("Library Management system", "Do you want to exit")
        if iExit>0:
            self.root.destroy()
            return

    def update(self):

        conn = mysql.connector.connect(host="localhost", username = "simran",password = "Mysql03", database="mydata")

        cursor = conn.cursor()
        cursor.execute("update mydataa set member=%s,firstname = %s, lastname =%s, title =%s, address1 =%s, address2=%s,postcode=%s,mobile=%s,bookid=%s,booktitle=%s,author=%s, dateborrowed=%s where prnno = %s",(
                                                          self.member_var.get(),
                                                          self.title_var.get(),
                                                          self.firstname_var.get(),
                                                          self.lastname_var.get(),
                                                          self.address1_var.get(),
                                                          self.address2_var.get(),
                                                          self.postcode_var.get(),
                                                          self.mobile_var.get(),
                                                          self.bookid_var.get(),
                                                          self.booktitle_var.get(),
                                                          self.author_var.get(),
                                                          self.dateborrowed_var.get(),
                                                          self.prnno_var.get()
                                                         ))
        conn.commit()
        self.fetch_data()
        self.reset()
        conn.close()
        messagebox.showinfo("lms", "data updated succesfully")


    
    def delete(self):
        if self.prnno_var.get() == "" or self.title_var.get()=="":
            messagebox.showerror("error", "first select member")
        else:
            conn = mysql.connector.connect(host="localhost", username = "simran",password = "Mysql03", database="mydata")
            cursor = conn.cursor()
            query = "delete from mydataa where prnno = %s"
            value = (self.prnno_var.get(),)
            cursor.execute(query,value)

            conn.commit()
            self.fetch_data()
            self.reset()
            conn.close()

            messagebox.showinfo("success","member has been deleted")
    

    
if __name__ == "__main__":
    root = Tk()
    obj = LibraryManagementSystem(root)
    root.mainloop()

