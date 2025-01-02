# File-handling
A program to use txt and csv file 


import csv

#function for reading as a txt file.
def read_as_txt(x):
    with open(x,"r")as file:
      file.seek(0)
      reader=file.read()
      print(reader)

#function for writing as a txt file.
def write_as_txt(x,content):
   with open(x,"w")as file:
      file.write(content)
      print("It has been printed inside here: ")

#function for appending as a txt file.
def append_as_txt(x,content):
   with open(x,"a")as file:
        file.write(content)
        print("It has been printed inside here: ")

 #function for writing as a csv file.
def write_as_csv(x,data):
   with open(x,"w",newline="")as file:
      writer=csv.writer(file)
      writer.writerow(data)
      print("It has been written.")
 # function for reading as a csv file.
def read_as_csv(x):
   with open(x,"r")as file:
      reader=csv.reader(file)  
      for row in reader:
        print(row)
 # function for appending as a csv file. 
def append_as_csv(x,data):
   with open(x,"a",newline="")as file:
      writer=csv.writer(file)
      writer.writerow(data)
      print("It has been written.") 

print("First- select if you want a txt file or csv file-\n1.txt \n2.csv\n")
a=input("Enter the format you want with 'txt' or 'csv': ").lower()
b=input("Enter the name of the file: ")
c=b+"."+ a
response=True
while response:
    if a =="txt":
       operation = input("Choose operation - read, write, append: ").lower()
       if operation=="write":
          content=input("Enter the content: \n")
          write_as_txt(c,content)
       if operation=="append":
          content=input("Enter the content: \n")
          append_as_txt(c,content)
       if operation=="read":
          read_as_txt(c)
    elif a=="csv":
        operation = input("Choose operation - read, write, append: ").lower()
        if operation=="write":
           content=input("Enter the data: \n").split()
           write_as_csv(c,content)
        if operation=="append":
           content=input("Enter the content: \n").split()
           append_as_csv(c,content)
        if operation=="read":
           read_as_csv(c)
    response=input("continue or exit?: ")
    if response=="exit":
      response=False
print("Thank you for your time.")
       
