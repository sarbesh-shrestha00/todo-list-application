FILENAME = "tasks.txt"

# Load tasks from the file into a list
def load_tasks():
    try:
        with open(FILENAME, "r") as file:
            return [line.strip() for line in file.readlines()]
    except FileNotFoundError:
        return []

# Save the list of tasks into the file
def save_tasks(tasks):
    with open(FILENAME, "w") as file:
        for task in tasks:
            file.write(task + "\n")

# Show current tasks
def view_tasks(tasks):
    if not tasks:
        print("No tasks found.")
    else:
        print("\nYour Tasks:")
        for i, task in enumerate(tasks, 1):
            print(f"{i}. {task}")

# Add a new task
def add_task(tasks):
    task = input("Enter new task: ").strip()
    if task:
        tasks.append(task)
        save_tasks(tasks)
        print(" Task added.")
    else:
        print(" Task cannot be empty.")

# Remove a task by number
def remove_task(tasks):
    view_tasks(tasks)
    if not tasks:
        return
    try:
        num = int(input("Enter task number to remove: "))
        if 1 <= num <= len(tasks):
            removed = tasks.pop(num - 1)
            save_tasks(tasks)
            print(f" Removed task: {removed}")
        else:
            print(" Invalid task number.")
    except ValueError:
        print(" Please enter a valid number.")

# Main menu loop
def main():
    tasks = load_tasks()

    while True:
        print("\n--- TO-DO LIST MENU ---")
        print("1. View Tasks")
        print("2. Add Task")
        print("3. Remove Task")
        print("4. Exit")

        choice = input("Choose (1–4): ")

        if choice == "1":
            view_tasks(tasks)
        elif choice == "2":
            add_task(tasks)
        elif choice == "3":
            remove_task(tasks)
        elif choice == "4":
            print(" Goodbye!")
            break
        else:
            print(" Invalid choice. Enter a number from 1 to 4.")

if __name__ == "__main__":
    main()








# 📝 Simple To-Do List (Console App)

This is a beginner-friendly Python command-line app that allows you to:

-  View tasks
-  Add tasks
-  Remove tasks
- Save/load tasks using a text file (`tasks.txt`)

---

##  How It Works

The program uses a `tasks.txt` file to **store your to-do list** even after the program exits.

### Features

- Uses **Python lists** to manage tasks in memory.
- Stores tasks in a plain `.txt` file using the built-in `open()` function.
- Fully **menu-driven**, no external libraries required.

---

## 🧪 Example

```bash
1. View Tasks
2. Add Task
3. Remove Task
4. Exit
Choose (1–4): 2
Enter new task: Finish assignment
Task added.

Choose (1–4): 1
Tasks:
1. Finish assignment
