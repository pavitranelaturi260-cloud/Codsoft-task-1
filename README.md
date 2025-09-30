# Codsoft-task-1
#todo_cli.py

tasks = []

def show_menu():
    print("\n==== TO-DO LIST ====")
    print("1. View Tasks")
    print("2. Add Task")
    print("3. Update Task")
    print("4. Delete Task")
    print("5. Exit")

def view_tasks():
    if not tasks:
        print("No tasks found.")
    else:
        for i, task in enumerate(tasks, 1):
            status = "✔️" if task['done'] else "❌"
            print(f"{i}. [{status}] {task['title']}")

def add_task():
    title = input("Enter task: ")
    tasks.append({"title": title, "done": False})
    print("Task added successfully!")

def update_task():
    view_tasks()
    try:
        index = int(input("Enter task number to mark as done: ")) - 1
        tasks[index]['done'] = True
        print("Task marked as done!")
    except (ValueError, IndexError):
        print("Invalid task number.")

def delete_task():
    view_tasks()
    try:
        index = int(input("Enter task number to delete: ")) - 1
        tasks.pop(index)
        print("Task deleted!")
    except (ValueError, IndexError):
        print("Invalid task number.")

# Main Loop
while True:
    show_menu()
    choice = input("Choose an option: ")
    if choice == '1':
        view_tasks()
    elif choice == '2':
        add_task()
    elif choice == '3':
        update_task()
    elif choice == '4':
        delete_task()
    elif choice == '5':
        print("Goodbye!")
        break
    else:
        print("Invalid choice, please try again.")
