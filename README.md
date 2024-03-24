# MAIL-TO-STUDENTS-PROJECT
TO SEND MAIL FOR STUDENTS QUALIFIED AND NOT QUALIFIED FOR THE EXAM
from csv import reader
import smtplib
receiver=[]
names=[]
grade=[]
from_address = "my@gmail.com"
password = input("Type your password and press enter: ")

context = ssl.create_default_context()

with open("emails.csv","r") as file:
  csv_reader=reader(file)
  for line in csv_reader:
      receiver.append(line[0])
      grade.append(line[1])
  for row in receiver:
      str=row
      name=str.split('@')[0].split('+')[1]
      names.append(name)
with smtplib.SMTP_SSL("smtp.gmail.com", 465, context=context) as server:
  server.login()
  for i in range(0,97):
    
    if(grade[i])>"4":
      msg=''' Dear {student_name},
        Congratulations!You have sucessfully completed the STW-Python in oct-2022. You have received <grade> grade. Please keep this spirit of learning.
        With Regards,
        STW Team'''
      msg.format(student_name = loop_var )
      msg=msg.replace("<grade>",grade[i])
    else:
       msg='''Dear <student name>,
          After your evluation we are sorry to inform you that your performance does not matter the expectations for the certification of STW-python Course in oct-2022.
          Wishes for next workshops.
          With Regards, 
          STW Team'''
    msg = msg.replace("<student name>",names[i])
    print(msg)
