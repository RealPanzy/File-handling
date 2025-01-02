# Program to write, append, or read files depending on format (normal txt or csv)

```python
import csv

def read_as_txt(file_path):
    """Read and print the content of a text file."""
    with open(file_path, "r") as file:
        file.seek(0)
        reader = file.read()
        print(reader)

def write_as_txt(file_path, content):
    """Write content to a text file."""
    with open(file_path, "w") as file:
        file.write(content)
    print("It has been printed inside here: ")

def append_as_txt(file_path, content):
    """Append content to a text file."""
    with open(file_path, "a") as file:
        file.write(content)
    print("It has been printed inside here: ")

def write_as_csv(file_path, data):
    """Write data to a CSV file."""
    with open(file_path, "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(data)
    print("It has been written.")

def read_as_csv(file_path):
    """Read and print the content of a CSV file."""
    with open(file_path, "r") as file:
        reader = csv.reader(file)
        for row in reader:
            print(row)

def append_as_csv(file_path, data):
    """Append data to a CSV file."""
    with open(file_path, "a", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(data)
    print("It has been written.")

print("First- select if you want a txt file or csv file-\n1.txt \n2.csv\n")
file_format = input("Enter the format you want with 'txt' or 'csv': ").lower()
file_name = input("Enter the name of the file: ")
file_path = file_name + "." + file_format
response = True

while response:
    if file_format == "txt":
        operation = input("Choose operation - read, write, append: ").lower()
        if operation == "write":
            content = input("Enter the content: \n")
            write_as_txt(file_path, content)
        elif operation == "append":
            content = input("Enter the content: \n")
            append_as_txt(file_path, content)
        elif operation == "read":
            read_as_txt(file_path)
    elif file_format == "csv":
        operation = input("Choose operation - read, write, append: ").lower()
        if operation == "write":
            content = input("Enter the data: \n").split()
            write_as_csv(file_path, content)
        elif operation == "append":
            content = input("Enter the content: \n").split()
            append_as_csv(file_path, content)
        elif operation == "read":
            read_as_csv(file_path)
    response = input("continue or exit?: ").lower()
    if response == "exit":
        response = False

print("Thank you for your time.")
