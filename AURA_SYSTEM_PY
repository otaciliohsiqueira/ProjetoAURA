from tkinter import  *

import tkinter.messagebox as tkMessageBox

import sqlite3

import tkinter.ttk as ttk

import serial


root = Tk()

root.title("SISTEMA AURA")

width = 1000

height = 600

screen_width = root.winfo_screenwidth()

screen_height = root.winfo_screenheight()

x = (screen_width/2) - (width/2)

y = (screen_height/2) - (height/2)

root.geometry("%dx%d+%d+%d" % (width, height, x, y))

root.resizable(0, 0)

root.config(bg="lightSteelBlue3")


# CRIANDO AS VARIAVEIS DO SISTEMA CADASTO DE PESSOAS

USERNAME = StringVar()

PASSWORD = StringVar()

NAME = StringVar()

EMAIL = StringVar()

STARTUP = StringVar()

PLANO = StringVar()

ONLINE_OFFLINE = StringVar()

SENHA_NUMERICA = StringVar()

TAG = StringVar()

TELEFONE = StringVar()

RG = StringVar()

CPF = StringVar()

SEARCH = StringVar()



# CRIANDO CONEXAO COM O BD SQLITE3

def Database():

    global conn, cursor

    conn = sqlite3.connect("pythontut.db")

    cursor = conn.cursor()

    cursor.execute("CREATE TABLE IF NOT EXISTS admin (admin_id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL, username TEXT, password TEXT)")

    cursor.execute("CREATE TABLE IF NOT EXISTS person (id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL, name TEXT, email TEXT, startup TEXT, plano TEXT, online_offline TEXT, senha_numerica TEXT, tag TEXT, telefone TEXT, rg TEXT, cpf TEXT)")

    cursor.execute("SELECT * FROM admin WHERE username = 'admin' AND password = 'admin'")

    if cursor.fetchone() is None:

        cursor.execute("INSERT INTO admin (username, password) VALUES('admin', 'admin')")

        conn.commit()


'''
arduino = serial.Serial('COM7',  9600) 

##########################################################################################
if(arduino.in_waiting):
    leitura_arduino = arduino.read()
    

    
#########################################################################################

'''

def ConectionPython():
    
    ArduinoUnoSerial = serial.Serial('/dev/cu.usbmodem1431', 9600)
    print("entre")
    leitura = ArduinoUnoSerial.read(1)
    print(leitura)
    if leitura == b'1':
        print("entrei agora")
        tkMessageBox.showinfo("Aviso", "A porta do Coworking se encontra aberta")
        
    #root.after(2000,ConectionPython)
'''
    tamanho = 0
    valor_recebido = ""
    senha = ""

    while tamanho < 4:
        if arduino.in_waiting:
            valor_recebido = arduino.read().decode("utf-8")
            tamanho += len(valor_recebido)
            senha += valor_recebido
        #ActiveUser
    #print(senha)
'''

'''
arduino = serial.Serial('COM6', 9600)
if arduino.in_waiting:
    valor_recebido = arduino.read().decode("utf-8")
    ActiveUser(valor_recebido)
    print(valor_recebido)
'''

# CRIANDO METODOS DOS BOTÕES DE SAIR

def Exit():

    result = tkMessageBox.askquestion(':', 'TEM CERTEZA?', icon="warning")

    if result == 'yes':

        root.destroy()

        exit()



def Exit2():

    result = tkMessageBox.askquestion(':', 'TEM CERTEZA?', icon="warning")

    if result == 'yes':

        root.destroy()

        exit()



# CRIANDO O FORMULARIO DE LOGIN

def ShowLoginForm():

    global loginform

    loginform = Toplevel()

    loginform.title("SISTEMA DE CADASTRO DE PESSOAS/SISTEMA DE LOGIN")

    width = 600

    height = 400


    screen_width = root.winfo_screenwidth()

    screen_height = root.winfo_screenheight()

    x = (screen_width / 2) - (width / 2)

    y = (screen_height / 2) - (height / 2)

    loginform.geometry("%dx%d+%d+%d" % (width, height, x, y))

    loginform.resizable(0, 0)

    LoginForm()



# CRIANDO CAMPOS DO FORMULARIO LOGIN

def LoginForm():

    global lbl_result

    TopLoginForm = Frame(loginform, width=50, height=50, bd=1, relief=SOLID)

    TopLoginForm.pack(side=TOP, pady=2)

    lbl_text = Label(TopLoginForm, text="CADASTRO DE PESSOAS COWORKING", fg="white",font=("arial", 10, "bold"), width=100)

    lbl_text.pack(fill=X)

    MidLoginForm = Frame(loginform, width=600)

    MidLoginForm.pack(side=TOP, pady=50)

    lbl_username = Label(MidLoginForm, text="USUARIO:", font=("arial", 15, "bold"), fg="blue", bd=18)

    lbl_username.grid(row=0)

    lbl_password = Label(MidLoginForm, text="PASSWORD:", font=("arial",15, "bold"), fg="blue", bd=18)

    lbl_password.grid(row=1)

    lbl_result = Label(MidLoginForm, text="", font=("arial", 18))

    lbl_result.grid(row=3, columnspan=2)

    username = Entry(MidLoginForm, textvariable=USERNAME, font=("arial ", 15), width=30)

    username.grid(row=0, column=1)

    password = Entry(MidLoginForm, textvariable=PASSWORD, font=("arial ", 15), width=30, show="*")

    password.grid(row=1, column=1)

    btn_login = Button(MidLoginForm, text="Login", font=("arial", 18), width=30, command=Login)

    btn_login.grid(row=2, columnspan=2, pady=20)

    btn_login.bind("<Return>", Login)



# CRIANDO FORMULARIO DE PRODUTOS /  HOME PRINCIPAL


def Home():
 
    global Home

    Home = Tk()

    Home.title("CADASTRO DE PESSOAS")

    width = 1024

    height = 500

    screen_width = Home.winfo_screenwidth()

    screen_height = Home.winfo_screenheight()

    x = (screen_width / 2) - (width / 2)

    y = (screen_height / 2) - (height / 2)

    Home.geometry("%dx%d+%d+%d" % (width, height, x, y))

    Home.resizable(0, 0)

    Title = Frame(Home, bd=1, relief=SOLID)

    Title.pack(pady=10)

    lbl_display = Label(Title, text="CADASTRO DE PESSOAS", bg='gray', font=("Microsoft_Sans_Serif_Regular", 45))

    lbl_display.pack()

    menubar = Menu(Home)

    filemenu = Menu(menubar, tearoff=0)

    filemenu2 = Menu(menubar, tearoff=0)

    filemenu.add_command(label="LOGOUT", command=Logout)

    filemenu.add_command(label="SAIR", command=Exit2)

    filemenu2.add_command(label="NOVO CADASTRO", command=ShowAddNew)

    filemenu2.add_command(label="VISUALIZAR", command=ShowView)

    menubar.add_cascade(label="CONTA", menu=filemenu)

    menubar.add_cascade(label="CADASTROS", menu=filemenu2)

    Home.configure(menu=menubar)

    Home.configure(bg="gray")
    
# CRIANDO O METODO DE ADICIONAR NOVO CADASTRO DE PESSOAS

def ShowAddNew():

    global addnewform

    addnewform = Toplevel()

    addnewform.title("CADASTRO DE PESSOAS/ADICIONANDO PESSOAS")

    width = 1000

    height = 500

    screen_width = Home.winfo_screenwidth()

    screen_height = Home.winfo_screenheight()

    x = (screen_width / 2) - (width / 2)

    y = (screen_height / 2) - (height / 2)

    addnewform.geometry("%dx%d+%d+%d" % (width, height, x, y))

    addnewform.resizable(0, 0)

    AddNewForm()

# CRIANDO OS CAMPOS DO FORMULARIO NOVO CADASTRO DE PESSOAS

def AddNewForm():

    TopAddNew = Frame(addnewform, width=600, height=100, bd=1, relief=SOLID)

    TopAddNew.pack(side=TOP, pady=20)


    lbl_text = Label(TopAddNew, text="CADASTRAR UMA NOVA PESSOA", font=("Microsoft_Sans_Serif_Regular", 18), width=600)

    lbl_text.pack(fill=X)


    MidAddNew = Frame(addnewform, width=600)

    MidAddNew.pack(side=TOP, pady=50)


    lbl_name = Label(MidAddNew, text="NOME:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_name.grid(row=0,column=0, sticky=W)


    lbl_email = Label(MidAddNew, text="E-MAIL:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_email.grid(row=1,column=0, sticky=W)


    lbl_startup = Label(MidAddNew, text="STARTUP:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_startup.grid(row=2,column=0, sticky=W)
    

    lbl_plano = Label(MidAddNew, text="PLANO:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_plano.grid(row=3,column=0, sticky=W)


    lbl_onlineoffline = Label(MidAddNew, text="ONLINE/OFFLINE:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_onlineoffline.grid(row=4,column=0, sticky=W)


    lbl_senhanumerica = Label(MidAddNew, text="SENHA NUMÉRICA:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_senhanumerica.grid(row=0,column=2, sticky=W)


    lbl_senhanumerica = Label(MidAddNew, text="TAG:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_senhanumerica.grid(row=1,column=2, sticky=W)


    lbl_telefone = Label(MidAddNew, text="TELEFONE:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_telefone.grid(row=2,column=2, sticky=W)


    lbl_rg = Label(MidAddNew, text="RG:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_rg.grid(row=3,column=2, sticky=W)


    lbl_cpf = Label(MidAddNew, text="CPF:", font=("Microsoft_Sans_Serif_Regular", 15), bd=10)

    lbl_cpf.grid(row=4,column=2, sticky=W)
    

    name = Entry(MidAddNew, textvariable=NAME, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    name.grid(row=0, column=1)


    email = Entry(MidAddNew, textvariable=EMAIL, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    email.grid(row=1, column=1)


    startup = Entry(MidAddNew, textvariable=STARTUP, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    startup.grid(row=2, column=1)

    plano = Entry(MidAddNew, textvariable=PLANO, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    plano.grid(row=3, column=1)

    online_offline = Entry(MidAddNew, textvariable=ONLINE_OFFLINE, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    online_offline.grid(row=4, column=1)

    senha_numerica = Entry(MidAddNew, textvariable=SENHA_NUMERICA, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    senha_numerica.grid(row=0, column=3)

    tag = Entry(MidAddNew, textvariable=TAG, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    tag.grid(row=1, column=3)

    telefone = Entry(MidAddNew, textvariable=TELEFONE, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    telefone.grid(row=2, column=3)

    rg = Entry(MidAddNew, textvariable=RG, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    rg.grid(row=3, column=3)

    cpf = Entry(MidAddNew, textvariable=CPF, font=("Microsoft_Sans_Serif_Regular", 25), width=15)

    cpf.grid(row=4, column=3)

    btn_add = Button(MidAddNew, text="SALVAR", font=("Microsoft_Sans_Serif_Regular", 18), width=30, bg="gray63",

    command=AddNew)

    btn_add.grid(row=6, columnspan=4, pady=50)



# CRIANDO A CONECÃO DO NOVO CADASTRO AO BANCO DE DADOS


def AddNew():

    Database()

    cursor.execute("INSERT INTO person (name, email, startup, plano, online_offline, senha_numerica, tag, telefone, rg, cpf) VALUES(?, ?, ?, ?, ?, ?, ?, ?, ?, ?)",(str(NAME.get()), str(EMAIL.get()), str(STARTUP.get()), str(PLANO.get()),str(ONLINE_OFFLINE.get()),str(SENHA_NUMERICA.get().upper()),str(TAG.get()), str(TELEFONE.get()), str(RG.get()), str(CPF.get())))

    conn.commit()
    
    NAME.set("")

    EMAIL.set("")    

    STARTUP.set("")

    PLANO.set("")

    ONLINE_OFFLINE.set("")

    SENHA_NUMERICA.set("")

    TAG.set("")

    TELEFONE.set("")

    RG.set("")

    CPF.set("")

    cursor.close()

    conn.close()

    tkMessageBox.showinfo("Cadastro", "O Usuario foi cadastrado")
#################################################################################################
def ActivateUser(tagOrKey):

    Database()

    cursor.execute("SELECT online_offline FROM person WHERE tag = \'"+tagOrKey+"\' OR senha_numerica = \'"+tagOrKey+"\'")

    retorno = cursor.fetchall()
        #ativo = retorno[0][0]
    ativo = retorno

    if ativo == "Online":
        cursor.execute("UPDATE person SET online_offline = \'Offline\' WHERE tag = \'"+tagOrKey+"\' OR senha_numerica = \'"+tagOrKey+"\'")
    elif ativo == "Offline":
        cursor.execute("UPDATE person SET online_offline = \'Online\' WHERE tag = \'"+tagOrKey+"\' OR senha_numerica = \'"+tagOrKey+"\'")
            
    conn.commit()

    ONLINE_OFFLINE.set("")

########################################################################################
# CRIANDO OS CAMPOS DO FORMULARIO CADASTRO DE PESSOAS/LISTVIER

def ViewForm():

    global tree

    TopViewForm = Frame(viewform, width=400, bd=1, relief=SOLID)

    TopViewForm.pack(side=TOP, fill=X)

    LeftViewForm = Frame(viewform, width=600)

    LeftViewForm.pack(side=LEFT, fill=Y)

    MidViewForm = Frame(viewform, width=400)

    MidViewForm.pack(side=RIGHT)

    lbl_text = Label(TopViewForm, text="Pessoas", font=('Microsoft_Sans_Serif_Regular', 18), width=600)

    lbl_text.pack(fill=X)

    lbl_txtsearch = Label(LeftViewForm, text="Pesquisar", font=('Microsoft_Sans_Serif_Regular', 15))

    lbl_txtsearch.pack(side=TOP, anchor=W)

    search = Entry(LeftViewForm, textvariable=SEARCH, font=('Microsoft_Sans_Serif_Regular', 15), width=10)

    search.pack(side=TOP, padx=10, fill=X)

    btn_search = Button(LeftViewForm, text="Pesquisar", command=Search)

    btn_search.pack(side=TOP, padx=10, pady=10, fill=X)

    btn_reset = Button(LeftViewForm, text="Atualizar", command=Reset)

    btn_reset.pack(side=TOP, padx=10, pady=10, fill=X)

    btn_delete = Button(LeftViewForm, text="Deletar", command=Delete)

    btn_delete.pack(side=TOP, padx=10, pady=10, fill=X)

    scrollbarx = Scrollbar(MidViewForm, orient=HORIZONTAL)

    scrollbary = Scrollbar(MidViewForm, orient=VERTICAL)

    tree = ttk.Treeview(MidViewForm, columns=("ID","Nome Pessoa", "Email", "Startup", "Plano","Online_Offline","Senha_numerica","Tag", "Telefone", "Rg", "Cpf"), selectmode="extended", height=100, yscrollcommand=scrollbary.set, xscrollcommand=scrollbarx.set)

    scrollbary.config(command=tree.yview)

    scrollbary.pack(side=RIGHT, fill=Y)

    scrollbarx.config(command=tree.xview)

    scrollbarx.pack(side=BOTTOM, fill=X)

    tree.heading('ID', text="ID", anchor=W)

    tree.heading('Nome Pessoa', text="Nome da Pessoa", anchor=W)

    tree.heading('Email', text="E-mail", anchor=W)

    tree.heading('Startup', text = "Startup", anchor=W)

    tree.heading('Plano', text = "Plano", anchor=W)

    tree.heading('Online_Offline', text = "Online/Offline", anchor=W)

    tree.heading('Senha_numerica', text = "Senha Numerica", anchor=W)

    tree.heading('Tag', text = "Tag", anchor=W)

    tree.heading('Telefone', text = "Telefone", anchor=W)

    tree.heading('Rg', text = "RG", anchor=W)

    tree.heading('Cpf', text = "CPF", anchor=W)

    tree.column('#0', stretch=NO, minwidth=0, width=0)

    tree.column('#1', stretch=NO, minwidth=0, width=120)

    tree.column('#2', stretch=NO, minwidth=0, width=200)

    tree.column('#3', stretch=NO, minwidth=0, width=120)

    tree.column('#4', stretch=NO, minwidth=0, width=120)

    tree.pack()

    DisplayData()



def DisplayData():

    Database()

    cursor.execute("SELECT * FROM person ")

    fetch = cursor.fetchall()

    for data in fetch:

        tree.insert('', 'end', values=(data))

    cursor.close()

    conn.close()



# CRIANDO METODO DE ATUALIZAR CADASTRO DE PESSOAS

def Search():

    if SEARCH.get() != "":

        tree.delete(*tree.get_children())

        Database()

        cursor.execute("SELECT * FROM person WHERE name LIKE ?", ('%' + str(SEARCH.get()) + '%',))

        fetch = cursor.fetchall()

        for data in fetch:

            tree.insert('', 'end', values=(data))

        cursor.close()

        conn.close()



# CRIANDO METODO PARA ATUALIZAR CADASTRO

def Reset():

    tree.delete(*tree.get_children())

    DisplayData()

    SEARCH.set("")



# CRIANDO METODO PARA DELETAR

def Delete():

    if not tree.selection():

        print("ERROR")

    else:

        result = tkMessageBox.askquestion(' CADASTRO DE PESSOAS', 'TEM CERTEZA? DELETANDO CADASTRO', icon="warning")

        if result == 'yes':

            curItem = tree.focus()

            contents = (tree.item(curItem))

            selecteditem = contents['values']

            tree.delete(curItem)

            Database()

            cursor.execute("DELETE FROM person WHERE id = %d" % selecteditem[0])

            conn.commit()

            cursor.close()

            conn.close()



# DEFININDO O NOVO FORMULARIO CADASTRO NOVO PESSOAS

def ShowView():

    global viewform

    viewform = Toplevel()

    viewform.title(" CADASTRO DE PESSOAS/ VISUALIZAR PESSOAS")

    width = 600

    height = 400

    screen_width = Home.winfo_screenwidth()

    screen_height = Home.winfo_screenheight()

    x = (screen_width / 2) - (width / 2)

    y = (screen_height / 2) - (height / 2)

    viewform.geometry("%dx%d+%d+%d" % (width, height, x, y))

    viewform.resizable(0, 0)

    ViewForm()



# METODO DO FORMULARIO SAIR


def Logout():

    result = tkMessageBox.askquestion('CADASTRO DE PESSOAS', 'TEM CERTEZA? LOGOUT', icon="warning")

    if result == 'yes':

        admin_id = ""

        root.deiconify()

        Home.destroy()



# METODO DO FORMULARIO DE LOGIN

def Login(event=None):
    global admin_id
    Database()
    if USERNAME.get == "" or PASSWORD.get() == "":
        lbl_result.config(text="FAVOR ENTRAR COM OS CAMPOS VALIDOS, TENTE NOVAMENTE!", fg="red", font=('arial', 10))
    else:
        cursor.execute("SELECT * FROM admin WHERE username = ? AND password = ?",(USERNAME.get(), PASSWORD.get()))
        if cursor.fetchone() is not None:
            cursor.execute("SELECT * FROM admin WHERE username = ? AND password = ?", (USERNAME.get(), PASSWORD.get()))
            data = cursor.fetchone()
            admin_id = data[0]
            USERNAME.set("")
            PASSWORD.set("")
            lbl_result.config(text="")
            ShowHome()
        else:
            lbl_result.config(text = "USUARIO OU SENHA INVALIDAS", fg="red")
            USERNAME.set("")
            PASSWORD.set("")
    cursor.close()
    conn.close()
def ShowHome():
    root.withdraw()
    Home()
    loginform.destroy()

# CRIANDO O METODO SAIR BOTÃO

def Exit():

    result = tkMessageBox.askquestion('CADASTRO DE PESSOAS', 'TEM CERTEZA? SAINDO DO SISTEMA', icon="warning")

    if result == 'yes':

        root.destroy()

        exit()



# CRIANDO O MENU DROPDOWN

menubar = Menu(root)

filemenu = Menu(menubar, tearoff=0)

filemenu.add_command(label="ENTRAR", command=ShowLoginForm)

filemenu.add_command(label="SAIR", command=Exit)

menubar.add_cascade(label="ARQUIVOS", menu=filemenu)

root.configure(menu=menubar)


# CRIANDO O FRAME SEJA BEM VINDO AO SISTEMA CADASTRO DE PESSOAS

Title = Frame(root, bd=1, relief=SOLID)

Title.pack(pady=10)


# CRIANDO LABEL CADASTRO DE PRODUTOS

lbl_display = Label(Title, text="CADASTRO DE PESSOAS", bg="red", font=('Microsoft_Sans_Serif_Regular', 45))

lbl_display.pack()

root.after(2000,ConectionPython)
# FECHANDO O ROOT DO SISTEMA

if __name__ == '_main_':

    root.mainloop() 
