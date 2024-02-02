# COS-project.repo
Using python to create a simple notepad for a project 
import tkinter as tk
from tkinter import filedialog
class Notepad:
    def __init__(self, root):
        self.root = root
        self.root.title("Notepad")
        self.root.geometry("600x400")

        self.text_widget = tk.Text(self.root, wrap="word")
        self.text_widget.pack(expand=True, fill="both")

        # Menu Bar
        menu_bar = tk.Menu(self.root)

        # File Menu
        file_menu = tk.Menu(menu_bar, tearoff=0)
        file_menu.add_command(label="New", command=self.new_file)
        file_menu.add_command(label="Open", command=self.open_file)
        file_menu.add_command(label="Save", command=self.save_file)
        file_menu.add_command(label="Save As", command=self.save_as_file)
        file_menu.add_separator()
        file_menu.add_command(label="Exit", command=self.root.destroy)
        menu_bar.add_cascade(label="File", menu=file_menu)

        # edit menu
        edit_menu = tk.Menu(menu-bar, tearoff=0)
        edit_menu.add_command(label="Cut", command=self.cut_text)
        edit_menu.add_command(label="Copy", command=self.copy_text)
        edit_menu.add_command(label="Paste", command=self.paste_text)
        menu_bar.add_cascade(label="Edit", menu=edit_menu)

        # Help Menu
        help_menu = tk.Menu(menu_bar, tearoff=0)
        help_menu.add_command(label="About", command=self.show_about)
        menu_bar.add_cascade(label="Help", menu=help_menu)

        self.root.config(menu=menu_bar)

        def new_file(self):
            self.text_widget.delete("1.0", tk.END)

        def open_file(self):
            file_path = filedialog.askopenfilename(defaultextension=".txt", filetypes=[("Text files", "*.txt"), ("All files", "*.*")])
            if file_path:
                with open(file_path, 'r') as file:
                    content = file.read()
                    self.text_widget.delete("1.0", tk.END)
                    self.text_widget.insert(tk.END, content)

def save_file(self):
    if not hasattr(self, "current_file_path") or not self.current_file_path:
        self.save_as_file()
    else:
        content = self.text_widget.get("1.0", tk.END)
        with open(self.current_file_path, "w") as file:
            file.write(content)
            
 def save_as_file(self):
        file_path = filedialog.asksaveasfilename(defaultextension=".txt", filetypes=[("Text.files", "*.txt"), ("All files", "*.*)")])
        if file_path:
            content = self.text_widget.get("1.0", tk.END)
            with open(file_path, "w") as file:
                file.write(content)
                self.current_file_path = file_path
