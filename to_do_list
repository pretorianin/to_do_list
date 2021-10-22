import sqlite3


connection = sqlite3.connect("todo.db")


def create_table(connection):
    try:
        cur = connection.cursor()
        cur.execute("""CREATE TABLE task(task text)""")
    except:
        pass


tasks = []


def show_tasks(connection):
    cur = connection.cursor()
    cur.execute("""SELECT task FROM task""")
    result = cur.fetchall()

    for row in result:
        print([row(0)])


def add_task(connection):
    task = input("wpisz tresc zadania")
    if task == "0":
        print("powrót do menu")
    else:
        cur = connection.cursor()
        cur.execute("""INSERT INTO task(task) VALUES(?)""", (task,))
        connection.commit()
        print("dodano zdanie")


def show_tasks(connection):
    cur = connection.cursor()
    cur.execute("""SELECT rowid, task FROM task""")
    result = cur.fetchall()

    for row in result:
        print(str(row[0]) + " - " + row[1])


def delete_task(connection):
    task_index = int(input("Specify the index of the job to be deleted: "))

    cur = connection.cursor()
    rows_deleted = cur.execute("""DELETE FROM task WHERE rowid=?""", (task_index, )).rowcount
    connection.commit()

    if rows_deleted == 0:
        print("There is no such task")
    else:
        print("Job deleted")




create_table(connection)

while True:
    print("1. Show tasks")
    print("2. Add task")
    print("3. Delete task")
    print("4. Exit")

    user_choice = int(input("choose number: "))
    if user_choice == 1:
        show_tasks(connection)

    if user_choice == 2:
        add_task(connection)

    if user_choice == 3:
        delete_task(connection)

    if user_choice == 4:
        break

connection.close()


