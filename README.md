# Program to make to-do-list application (in command line form)

class Task:
    def _init_(self, description, due_date, priority):
        self.description = description
        self.due_date = due_date
        self.priority = priority
        self.completed = False

class ToDoList:
    def _init_(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def display_tasks(self):
        if not self.tasks:
            print("No tasks in the to-do list.")
        else:
            print("To-Do List:")
            for i, task in enumerate(self.tasks):
                status = "Completed" if task.completed else "Pending"
                print(f"{i + 1}. Description: {task.description} | Due Date: {task.due_date} | Priority: {task.priority} | Status: {status}")

    def mark_task_completed(self, task_index):
        if 0 <= task_index < len(self.tasks):
            self.tasks[task_index].completed = True
            print("Task marked as completed.")
        else:
            print("Invalid task index.")

    def update_task(self, task_index, new_description, new_due_date, new_priority):
        if 0 <= task_index < len(self.tasks):
            task = self.tasks[task_index]
            task.description = new_description
            task.due_date = new_due_date
            task.priority = new_priority
            print("Task updated.")
        else:
            print("Invalid task index.")

    def remove_task(self, task_index):
        if 0 <= task_index < len(self.tasks):
            del self.tasks[task_index]
            print("Task removed.")
        else:
            print("Invalid task index.")

def main():
    todo_list = ToDoList()

    while True:
        print("\nMenu:")
        print("1. Add Task")
        print("2. Display Tasks")
        print("3. Mark Task as Completed")
        print("4. Update Task")
        print("5. Remove Task")
        print("6. Quit")

        choice = input("Enter your choice: ")

        if choice == "1":
            description = input("Enter task description: ")
            due_date = input("Enter due date (YYYY-MM-DD): ")
            priority = input("Enter priority: ")
            task = Task(description, due_date, priority)
            todo_list.add_task(task)
        elif choice == "2":
            todo_list.display_tasks()
        elif choice == "3":
            task_index = int(input("Enter the task index to mark as completed: "))
            todo_list.mark_task_completed(task_index - 1)
        elif choice == "4":
            task_index = int(input("Enter the task index to update: "))
            new_description = input("Enter new description: ")
            new_due_date = input("Enter new due date (YYYY-MM-DD): ")
            new_priority = input("Enter new priority: ")
            todo_list.update_task(task_index - 1, new_description, new_due_date, new_priority)
        elif choice == "5":
            task_index = int(input("Enter the task index to remove: "))
            todo_list.remove_task(task_index - 1)
        elif choice == "6":
            break
        else:
            print("Invalid choice. Please try again.")

if _name_ == "_main_":
    main()
