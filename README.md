# employe-projict
#program tsjile mwadf
from fileinput import filename
from tkinter import *
from tkinter import ttk
from  tkinter import messagebox

frm = Tk()
# hdo l3fayse li ndi mn3ndhom lalwan o lhjm ta3 l5et o bzaf 3fayse
fnt       = 'none 30 bold'
bg        = 'light blue' # lonse ta3 lforma
bgtxt     = 'white'
fg        = 'black'
fw        = 700 #####################################################
fh        = 500                                                     #
x         = (frm.winfo_screenwidth()  - fw ) / 2                    # hdi lhjme ta3 lforma
y         = (frm.winfo_screenheight() - fh ) / 2                    #
pad       = 10 ######################################################
                                                                    #
                                                                    #
frm.geometry('%dx%d+%d+%d' %(fw , fh , x , y))                      # tab3a lhjme lforma
frm.title('employee file data')                                     #
frm.config(bg = bg)                                                 #
#####################################################################
Label(frm,text = 'employee data',bg = 'navy',fg = 'light blue',font = fnt).pack(pady = pad)  # hdi text li ybane mlfo9 chro kima welcom
fram = Frame(frm,bg = bg)                                                   # hdi background ta3o
fram.pack(pady = pad)                                                       #
#############################################################################
Label(fram,text = 'code',bg = bg , fg = fg , font = fnt).grid(row = 0 , column = 0)   #
Label(fram,text = 'name',bg = bg , fg = fg , font = fnt).grid(row = 1 , column = 0)   # text li y5rojli 9dam mourba3at ta3 nese
Label(fram,text = 'address ',bg = bg , fg = fg , font = fnt).grid(row = 2 , column = 0)#
########################################################################################
svcode     = StringVar()                                                                #
svname     = StringVar()                                                                #
svaddress  = StringVar()                                                                # lmoud5alat ta3 code and name and address
txtcode    = Entry(fram ,bg = bgtxt , fg = fg , font = fnt , textvariable  = svcode)    #
txtname    = Entry(fram ,bg = bgtxt , fg = fg , font = fnt , textvariable  = svname)    #
txtaddress = Entry(fram ,bg = bgtxt , fg = fg , font = fnt , textvariable  = svaddress) #
#########################################################################################
txtcode.grid(row = 0 , column = 1 , pady = pad)
txtname.grid(row = 1 , column = 1 , pady = pad)
txtaddress.grid(row = 2 , column = 1 , pady = pad)

def creat():
    if svcode.get().strip() == '':
        messagebox.showinfo('' , 'code is emptyee !')
        txtcode.focus()
    elif svname.get().strip() == '':
        messagebox.showinfo('' , 'name is emptyee !')
        txtname.focus()
    elif svaddress.get().strip() == '' :
        messagebox.showinfo('' , 'address is emptyee !')
        txtaddress.focus()
    else:
        filename =  'file_employee.txt'
        f = open(filename , 'w+')
        f.write('code   : ' + svcode.get()    + '\n')
        f.write('name   : ' + svname.get()    + '\n')
        f.write('addres : ' + svaddress.get() + '\n')
        f.close()
        svcode.set('')
        svname.set('')
        svaddress.set('')
        txtcode.focus()
        messagebox.showinfo('','employee file is crieite .......')

btnstyle = ttk.Style() ##################################################################
btnstyle.configure('TButton',font = fnt , pady = pad , padding = pad)                   #
ttk.Button(frm , text = 'creat employee file now', command = creat).pack(pady = pad)                                  # hdo lbouton li y5dmli file jdide o li y5roj mlbrnamje
ttk.Button(frm , text = 'exit now',command = frm.destroy).pack(pady = pad) #####################################################

frm.mainloop()
