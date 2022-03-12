## Data Structures Project

GitHub page that documents Data Structures project, using code snippets for key learnings, and links to  GitHub for code and Replit for runtime.

### Python Menu

You can see the [code used](https://github.com/zachye111/zach_individual_tri3/blob/main/menu.py) in the python menu.

Creating a Python menu with data structures and try/except statements - the lazy programmer way.

```markdown
`main_menu = [
    ["Swaps", "swaps.py"],
    ["Matrix", "matrix.py"],
    ["Fibonacci", "fibonacci.py"],
    ["Health", "health.py"],
    ["MNMS", "mnms.py"]
]

sub_menu = [
    ["Swaps", "swaps.py"],
    ["Matrix", "matrix.py"],
]

patterns_sub_menu = [
    ["Health", "health.py"],
]
` 
```
```markdown

- Main list of [Prompts, Actions] 
- Two styles are supported to execute abstracted logic 
- File names will be run by exec(open("filename.py").read()) 
- Function references will be executed directly file.function()

```markdown
`def menu():
    title = "Function Menu" + banner
    menu_list = main_menu.copy()
    menu_list.append(["Swaps and Matrix", submenu])
    menu_list.append(["Create Task", patterns_submenu])
    buildMenu(title, menu_list)

def submenu():
    title = "Function Submenu" + banner
    buildMenu(title, sub_menu)
def patterns_submenu():
    title = "Function Submenu" + banner
    buildMenu(title, patterns_sub_menu)

def buildMenu(banner, options):
    print(banner)
    prompts = {0: ["Exit", None]}
    for op in options:
        index = len(prompts)
        prompts[index] = op

    for key, value in prompts.items():
        print(key, '->', value[0])

    choice = input("Type your choice> ")
` 
```
```markdown

- def menu
- using main_menu list:
- main menu and submenu reference are created [Prompts, Actions]
- menu_list is sent as parameter to menuy.menu function that has logic for menu control
- def submenu
- using sub menu list above:
- sub_menu works similarly to menu()
- header for menu
- build dictionary
- get user choice

```markdown
` try:
        choice = int(choice)
        if choice == 0:
            # stop
            return
        try:
            # try as function
            action = prompts.get(choice)[1]
            action()
        except TypeError:
            try:  # try as playground style
                exec(open(action).read())
            except FileNotFoundError:
                print(f"File not found!: {action}")
            # end function try
        # end prompts try
    except ValueError:
        # not a number error
        print(f"Not a number: {choice}")
    except UnboundLocalError:
        # traps all other errors
        print(f"Invalid choice: {choice}")
    except TypeError:
        print(f"Not callable {action}")
` 
```
```markdown

- validate choice and run
- execute selection
- convert to number

```markdown
`  buildMenu(banner, options)
` 
```
```markdown

- recursion, start menu over again
