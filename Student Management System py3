#!/usr/bin/env python
import csv as c

#Display option for the user to choose
def display_menu():
    print(" Welcome to Student Management System")
    print("1. Add a new student to the class")
    print("2. Display students in the class")
    print("3. Search a student")
    print("4. Delete a student")
    print("5. Update a student")
    print("6. Save file and quit")


studentfield = ['Full Name', 'Student ID', 'Address', 'Class', 'Grades of subjects']
studentdatabase = 'students.csv'


#Add student information function
def Accept():
    print("Add Student Information: ")
    global studentfield
    global studentdatabase

    student_data = []
    for i in studentfield:
        value = input("Enter " + i + ": ")
        student_data.append(value)
    #Declare a file if the file does not exist
    with open(studentdatabase, "a", encoding="utf-8") as f:
        writer = c.writer(f)
        writer.writerows([student_data])

    print("Student information saved ")
    input("Press any key to continue")
    return

#Show the database of students function
#Including Full Name, Student ID, Address, Class and Grades of subjects
def Display():
    global studentfield
    global studentdatabase

    print("Full student information")
    #open student database to read information
    with open(studentdatabase, "r", encoding="utf-8") as f:
        reader = c.reader(f)
        # Print a field header
        for i in studentfield:
            print(("%26s") % (i), end='  ')
            # print(format(x, "%"), end=' |')
        print("\n")
    #Arrange the columns in straight line
        for i in reader:
            for item in i:
                # print(format(item, "9"), end=" |")
                print(("%26s") % (item), end='  ')

            print("\n")

    input("Press any key to continue")

#Look up for a specific student function
def Search():
    global studentfield
    global studentdatabase

    print("Search student")
    number = input("Enter first name, full name or Student ID: ")

    #Reading the global database to check if student information is exist
    with open(studentdatabase, "r", encoding="utf-8") as f:
        reader = c.reader(f)
        for i in reader:
            if len(i) > 0:
                if number in i[0] or number == i[1]:
                    print("Student Found")
                    print("Full Name: ", i[0])
                    print("Student ID: ", i[1])
                    print("Address ", i[2])
                    print("Class ", i[3])
                    print("Grades of subjects ", i[4])
                    break
        else:
            print("Student information not found or information invalid")
    input("Press any key to continue")

#Delete a specific student function
def Delete():
    global studentfield
    global studentdatabase

    print("Delete Student")
    number = input("Enter first name, full name or Student ID: ")
    student_found = False
    updated_data = []
    # Reading the global database to check if student information is exist
    with open(studentdatabase, "r", encoding="utf-8") as f:
        reader = c.reader(f)
        counter = 0
        for i in reader:
            if len(i) > 0:
                if number != i[0]:
                    updated_data.append(i)
                    counter += 1
                else:
                    student_found = True

    if student_found is True:
        #Open the existed file for writing
        with open(studentdatabase, "w", encoding="utf-8") as f:
            writer = c.writer(f)
            writer.writerows(updated_data)
        print("Student information has been deleted successfully")
    else:
        print("Student information is not found in our database")

    input("Press any key to continue")

#adjust a specific student information

def Update():
    global studentfield
    global studentdatabase

    print("Update Student:")
    number = input("Enter first name, full name or Student ID: ")
    index_student = None
    updated_data = []
    # Reading the global database to check if student information is exist
    with open(studentdatabase, "r", encoding="utf-8") as f:
        reader = c.reader(f)
        counter = 0
        for i in reader:
            if len(i) > 0:
                #if else func to declare the information is included in the database
                if number in i[0] or number == i[1]:
                    index_student = counter
                    print("Student Found: at number", index_student)
                    student_data = []
                    for field in studentfield:
                        value = input("Enter " + field + ": ")
                        student_data.append(value)
                    updated_data.append(student_data)
                else:
                    updated_data.append(i)
                counter += 1

    if index_student is not None:
        #Create a new file if it does not existed or truncates the file if it exists
        with open(studentdatabase, "w", encoding="utf-8") as f:
            writer = c.writer(f)
            writer.writerows(updated_data)
    else:
        print("Number is not found in our database")

    input("Press any key to continue")

#Create a while loop to re-run the program
#Ask the user to input '6' break the program
while True:
    display_menu()
    choice = input("Enter choice: ")
    if choice == '1':
        Accept()
    elif choice == '2':
        Display()
    elif choice == '3':
        Search()
    elif choice == '4':
        Delete()
    elif choice == '5':
        Update()
    else:
        break
