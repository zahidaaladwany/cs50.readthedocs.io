•	My project’s title; project name students in python
•	My name; zahida ahmad shahatha aladwany
•	My GitHub and edX usernames; zahida aladwany
•	My city and country; Mousl,Iraq
    date recorded video : 21/8/2024

 project title : project name students in python
#### Video Demo:  <(https://youtu.be/rg5-VVlVt84)>

#### Description:
In this project I will  depends on lecture 6 and 7 and 8 I make 4 files one file the main  its name project.py which contain the main functions to solve the problem  I start by creating  first file new_students.csv which contain name,characteristic,birthdatefor the students  it is csv file with detailed below
New_students.csv file which contain  name,characteristic,birthdate
name,characteristic,birthdate
Ahmad Ali,adeventure,2007
Ali Fdel,patientce,2008
Alla Fath,courage,2014
Fatema Abd,honesty,2010
Tamer Ayub,wisdom,2009
Mohamad Ali,competitive,2012
Mohsen Adam,creativity,2007
Dawood Adb,perfectionism,2011
Zubyda Ahmad,ambation,2013
Sabah Abdulla,loyalty,2015
Then my aim is to make another file name after.csv containing  name  house grade


My project.py will be with this code

# importing system
import sys
# importing csv file
import csv
# define arguments
def main():
    check_correct_args()
# using dictionray for data
    data = []
 # reading  dictionary data
    try:
        with open(sys.argv[1]) as csvfile:
            reader = csv.DictReader(csvfile)
            for row in reader:
                data.append(row)
    except FileNotFoundError:
        sys.exit("could not  read csv file")
  # output data
    output = []
    for row in data:
        house = select_house(row["characteristic"])
        grade = select_grade(row["birthdate"])
        output.append({ "name": row["name"], "house": house, "grade": grade})
  # writing dictionary
    with open(sys.argv[2], "w") as file:
        writer = csv.DictWriter(file, fieldnames=["name", "house", "grade"])
        writer.writerow({"name": "name", "house": "house", "grade": "grade"})
        for row in output:
            writer.writerow({"name": row["name"], "house": row["house"], "grade": row["grade"]})
# checking arguments and file type
def check_correct_args():
    if len(sys.argv) < 3:
       sys.exit("Too few command-line arguments")
    if len(sys.argv) > 3:
        sys.exit("Too many command-line arguments")
    if ".csv" not in sys.argv[1] or ".csv" not in sys.argv[2]:
        sys.exit("Not a csv file")

# selecting and making relation between charactrsitic and house
def select_house(characteristic):
    if characteristic in ["courage", "loyalty", "adeventure"]:
        return "Alwahda"
    elif characteristic in ["honesty", "patientce", "dedication"]:
        return "Zhoor"
    elif characteristic in ["wisdom", "creativity", "perfectionism"]:
        return "Sukar"
    elif characteristic in ["ambation", "competitive", "leadership"]:
        return "Mothana"
    else:
        return"No house"

# define grade with year
def select_grade(year):
    age = 2024 - int(year)
    grade = age - 5
    return "Grade " + str(grade)

if __name__ == "__main__":
    main()

# making test file by using assert and by  pytest check it work or not name of file test_project.py
# first importing check_correct_args, select_house, select_grade
from project import check_correct_args, select_house, select_grade
# import pytest
import pytest
# checking correct arguments
def test_check_correct_args():
    with pytest.raises(SystemExit):
         check_correct_args()

# define and test select house
def test_select_house():
    assert select_house("courage") == "Alwahda"
    assert select_house("honesty") == "Zhoor"
    assert select_house("ambation") == "Mothana"
    assert select_house("wisdom") == "Sukar"

# define and test select grade
def test_select_grade():
    assert select_grade("2007") == "Grade 12"
    assert select_grade("2015") == "Grade 4"
# every thing ok
# result in file name after.csv
name,house,grade
Ahmad Ali,Alwahda,Grade 12
Ali Fdel,Zhoor,Grade 11
Alla Fath,Alwahda,Grade 5
Fatema Abd,Zhoor,Grade 9
Tamer Ayub,Sukar,Grade 10
Mohamad Ali,Mothana,Grade 7
Mohsen Adam,Sukar,Grade 12
Dawood Adb,Sukar,Grade 8
Zubyda Ahmad,Mothana,Grade 6
Sabah Abdulla,Alwahda,Grade 4


