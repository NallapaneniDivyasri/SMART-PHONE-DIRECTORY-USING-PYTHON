# SMART-PHONE-DIRECTORY-USING-PYTHON

import sys
def initial_phone_book():
    vertical, horizontal = int(input("Please enter initial number of contacts: ")),5
    phonebook = []
    print(phonebook)
    for i in range(vertical):
        print("\nEnter contact %d details in the following order :" % (i+1))
        print("NOTE:( * ) indicates mandatory fields")
        print("....................................................................")
        temp = []
        for j in range(horizontal):
            if j == 0:
                temp.append(str(input("Enter the name * : ")))
                
                if temp[j] == '' or temp[j] == ' ':
                    sys.exit(
                        "Name is a mandatory field. Process exiting due to blank field...")
            if j == 1:
                temp.append(int(input("Enter number * : ")))
               
            if j == 2:
                temp.append(str(input("Enter mail address : ")))
                
                if temp[j] == '' or temp[j] == ' ':
                    temp[j] = None
                     
            if j == 3:
                temp.append(str(input("Enter date of birth (dd/mm/yy) : ")))

                if temp[j] == '' or temp[j] == ' ':
                                     
                    temp[j] = None
            if j == 4:
                temp.append(
                    str(input("Enter category (Family/Friends/Work/Others) : ")))
                if temp[j] == "" or temp[j] == ' ':
                    temp[j] = None
                     
        phonebook.append(temp)
     
    print(phonebook)
    return phonebook
 
def menu():
    print("************************")
    print("\t\t\tSMARTPHONE DIRECTORY", flush=False)
    print("************************")
    print("\tYou can now perform the following operations on this phonebook\n")
    print("1. Add a new contact")
    print("2. Remove existing contact")
    print("3. Delete all contacts")
    print("4. Search for a contact")
    print("5. Display all contacts")
    print("6. Exit phonebook")
 
    optional = int(input("Please enter your choice: "))
     
    return optional
 
def add_contact(phbk):
    array = []
    for i in range(len(phbk[0])):
        if i == 0:
            array.append(str(input("Enter the name : ")))
        if i == 1:
            array.append(int(input("Enter number : ")))
        if i == 2:
            array.append(str(input("Enter mail address : ")))
        if i == 3:
            array.append(str(input("Enter date of birth (dd/mm/yy) : ")))
        if i == 4:
            array.append(
                str(input("Enter category (Family/Friends/Work/Others) : ")))
    phbk.append(array)
    return phbk
    
def remove_existing(phbk):
    query = str(input("Enter the name of the contact you wish to remove : "))
    temp = 0
    for i in range(len(phbk)):
        if query == phbk[i][0]:
            temp += 1
            print(phbk.pop(i))
            
            print(" This query has now been removed")
            return phbk
    if temp == 0:
        print("Sorry, you have entered an invalid query.\
    Please recheck and try again later.")
         
        return phbk
 
def deleteall(phbk):
    return phbk.clear()
 
def search_existing(phbk):
    optional = int(input("Enter search criteria\n\n\
    1. Name\n2. Number\n3. Email-id\n4. DOB\n5. Category(Family/Friends/Work/Others)\
    \nPlease enter: "))
   
    temp = []
    check = -1
     
    if optional == 1:
        query = str(
            input("Please enter the name of the contact you wish to search: "))
        for i in range(len(phbk)):
            if query == phbk[i][0]:
                check = i
                temp.append(phbk[i])
                 
    elif optional == 2:
        query = int(
            input("Please enter the number of the contact you wish to search: "))
        for i in range(len(phbk)):
            if query == phbk[i][1]:
                check = i
                temp.append(phbk[i])
                 
    elif optional == 3:
        query = str(input("Please enter the mail ID\
        of the contact you wish to search: "))
        for i in range(len(phbk)):
            if query == phbk[i][2]:
                check = i
                temp.append(phbk[i])
                 
    elif optional == 4:
        query = str(input("Please enter the DOB (in dd/mm/yyyy format ONLY)\
            of the contact you wish to search: "))
        for i in range(len(phbk)):
            if query == phbk[i][3]:
                check = i
                temp.append(phbk[i])
                 
    elif optional == 5:
        query = str(
            input("Please enter the category of the contact you wish to search: "))
        for i in range(len(phbk)):
            if query == phbk[i][4]:
                check = i
                temp.append(phbk[i])
    else:
        print("Invalid search criteria")
        return -1
 
    if check == -1:
        return -1
    else:
        displayall(temp)
        return check
        
def displayall(phbk):
    if not phbk:
        print("Directory is empty: []")
    else:
        for i in range(len(phbk)):
            print(phbk[i])
 
def thanks():
    print("************************")
    print("Thanks for using our Smartphone directory system.")
    print("Please visit again!")
    print("************************")

print("....................................................................")
print("Hello dear user, welcome to our smartphone directory system")
print("You may now proceed to explore this directory")
print("....................................................................")

ch = 1
phbk = initial_phone_book()
while ch in (1, 2, 3, 4, 5):
    ch = menu()
    if ch == 1:
        phbk = add_contact(phbk)
    elif ch == 2:
        phbk = remove_existing(phbk)
    elif ch == 3:
        phbk = deleteall(phbk)
    elif ch == 4:
        d = search_existing(phbk)
        if d == -1:
            print("The contact does not exist. Please try again")
    elif ch == 5:
        displayall(phbk)
    else:
        thanks()
