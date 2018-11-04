This is a collection of various keyboard shortcuts that can make your life easier
when using the atom editor with the hydrogen connection to a jupyter kernel.

These have been tested on my machine with Atom `1.32.1` and Ubuntu.
If there are differences across operating systems, or they require specific packages, please point it out.

## General Atom commands

* <kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>p</kbd>

    open the command shell. From here one can access all the more advanced functions.
    it will also show the current keyboard shortcut for the chosen command, if present.
    can do partial search, so it will find commands based on keyword in the middle
    of the commands themselves (for example, the `Hydrogen: Add Watch` can be found just with `watch`)

* <kbd>Ctrl</kbd> + <kbd>, comma</kbd>

    open the `Settings` tab

* <kbd>Ctrl</kbd> + <kbd>/ slash</kbd> (on an italian keyboad is <kbd>Ctrl</kbd> + <kbd>shift</kbd> + <kbd>7</kbd> )

    toggle comment of the code

* <kbd>Ctrl</kbd> + <kbd>shift</kbd> + <kbd>m</kbd>

    toggle the preview for markdown files. (requires the `markdown-preview` extension)

* <kbd>Alt</kbd> + <kbd>shift</kbd> + <kbd>T</kbd>

    toggle the todo list as a side panel (requires the `todo-show` extension)

### bookmark management (<kbd>F2</kbd>)

bookmarks allow you to quickly explore your code and go back and forth between different sections

* <kbd>Ctrl</kbd> + <kbd>shift</kbd> + <kbd>F2</kbd>

    add or remove a bookmark to a line

* <kbd>F2</kbd> and <kbd>Shift</kbd> + <kbd>F2</kbd>

    move to the next (or previous) bookmark in the current file

* <kbd>Ctrl</kbd> + <kbd>F2</kbd>

    list the current bookmarks and allow to jump to the chosen one.
    Can see the bookmarks in all the files you have opened.

### Find and Replace (with multiple selections)

it will select multiple copies of the same string.
It is great for a mass rename of a variable or a function in a file.

if you move the cursor after the selection, you will get multiple cursors.
This is very useful to change the arguments for all the calls of a given function.

* <kbd>Ctrl</kbd> + <kbd>d</kbd>

    select the current object, if selected find the next

* <kbd>Alt</kbd> + <kbd>F3</kbd>

    finds and select all

* <kbd>Ctrl</kbd> + <kbd>k</kbd> and then <kbd>Ctrl</kbd> + <kbd>d</kbd>

    skip the selection to the next one

* <kbd>Ctrl</kbd> + <kbd>u</kbd>

    undo the last selection

* <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>&uarr; up arrow</kbd> and <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>&darr; down arrow</kbd>

    create multiple cursors above and below the current one.
    this is very useful to modify several consecutive lines

## selection management

* <kbd>Alt</kbd> + <kbd>&uarr; up arrow</kbd> and <kbd>Alt</kbd> + <kbd>&darr; down arrow</kbd>

    select (or deselect) the higher level of syntax block from the current selection.
    for example, from the cursor it will select the variable name it is placed on, then the function call list of arguments,
    then the whole function, and so on

* <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>, comma</kbd>

    select all the content inside the current function call.

* <kbd>Ctrl</kbd> + <kbd>r</kbd>

    finds all the symbols defined in the current files (functions, variables, etc...)

* <kbd>Ctrl</kbd> + <kbd>&uarr; up arrow</kbd> and <kbd>Ctrl</kbd> + <kbd>&darr; down arrow</kbd>

    move the current line above or below

* <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>&uarr; up arrow</kbd> and <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>&darr; down arrow</kbd>

    put multiple cursors above or below the current one.
    one can return to a single cursor pressing <kbd>Esc</kbd>

* <kbd>Ctrl</kbd> + <kbd>g</kbd>

    goes to a specific line

* <kbd>Ctrl</kbd> + <kbd>l</kbd>

    select the whole line the cursor is currently on

* <kbd>Ctrl</kbd> + <kbd>left arrow</kbd> or <kbd>right arrow</kbd>

    skip to the previous or next word.
    using <kbd>Alt</kbd> instead of <kbd>Ctrl</kbd> allows a more fine-grained control.
    combined with <kbd>Shift</kbd> can be used to select text.

* <kbd>Ctrl</kbd> + <kbd>Del</kbd> or <kbd>Backspace</kbd>

    delete to the end (or the beginning) of the current word.

* <kbd>Shift</kbd> + <kbd>Home</kbd> or <kbd>End</kbd>

    Select the text to the start of the line or the the end of it

* <kbd>Ctrl</kbd> + <kbd>Home</kbd> or <kbd>End</kbd>

    go the the beginning or the end of the file

## Execution of code on hydrogen

* <kbd>Shift</kbd> + <kbd>Enter</kbd>

    execute a selection or the current line in hydrogen, go to the next one

* <kbd>Ctrl</kbd> + <kbd>Enter</kbd>

    execute a selection or the current line in hydrogen, stays on the current one

* <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>Enter</kbd>

    Execute the current block and go to the next one (blocks are delimited by `# %%`)

* <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Enter</kbd>

    Execute the current block and remains in it (blocks are delimited by `# %%`)

* <kbd>Alt</kbd> + <kbd>i</kbd>

    open the inline help of hydrogen with the help of the function or object that the cursor is corrently residing on

### Watches and Explorative work

*   from the command shell: search for `Hydrogen: Add Watch`

    create a new watch. Watches allow for small snippets of code to be execute
    whenever you launch a new command.
    They can be useful to check the results of a plot when you modify the way data
    are processed.

* from the command shell: search for `Hydrogen Python: toggle variable explorer`

    show as a side tab a simple variable explorer similar to those of spyder and matlab (but less powerful)

* from the command shell: search for `Hydrogen: toggle output area`

    show a new area on the side that display the results of the executed commands
    instead of showing them inline.
    this is very useful to select text from the output, as the inline version
    does not allow text selection.

for this kind of explorative work, there are few useful snippets to be used

* library `pdir2`

    is a drop-in replacement for the default dir function, with some more goodies.
    import it with `import pdir as dir` and then put a watch with

        dir().public

    to have a list of all the functions and modules and a short help

* IPython JSON display

    useful to display dictionaries and lists of simple objects in an interactive way.
    import it with `from IPython.display import JSON` and then use it with

        data = [1, 2, {'a':1}]
        JSON(data, expanded=True)

* pandas styles

    these are useful when doing data exploration.
    instead of just displaing the basic dataframe, with this one
    can have a rich display.
    one can access a dataframe style with `.style`, and then create a rich
    display using pre-defined functions or extending them as you need

        d = pd.DataFrame(plt.randn(5, 3))
        d[0] = plt.nan
        d.style
        d.style.highlight_null()
        d.style.highlight_null().highlight_max()
        d.style.highlight_max(color='darkorange', axis=1)
        d.style.background_gradient()

    you can have the whole list with `dir(d.style).public.methods`

* pandas_profiling

    generates reports on a dataframe, including statistics, correlations, etc...
    Can be installed with `conda install pandas_profiling`.

        import pandas_profiling
        df = pd.DataFrame(plt.randn(500, 3))
        pandas_profiling.ProfileReport(df)

    a similar library is `pivottablejs`, but only works in jupyter notebooks, so I haven't tested it.

* search stackoverflow for code snippets

    requires the package `ask-stack`.
    typing `ask stack` in the command prompt will open a search box
    that will then return a series of replies from stackoverflow that can
    be explored directly in the sidebar.

* special character variables

    ipython allow to replace special letters name with the proper representation
    with a <kbd>⇥ Tab</kbd>. For example, it can replace `\alpha` with `α`.
    Atom is able to do it by itself, but I don't remember from which version.
    This is useful to write expressive formulas, but should be used sparingly
    as it makes it hard to edit for someone that does not have a similar tool.
    it is possible to insert letter modifiers as well, such as hat, dot and so on.
    to make it acceptable to python, first should be the letter, than the modifier,
    such as `a\hat` for `â`.
    This can make the code difficult to read with smaller fonts, so beware.
    Only the unicode letters can be used, so you can't have a cat face `😺` for a
    variable, but you can have it as dictionary key if you want the world to burn.

* display online math

        from IPython.display import Math
        formula = r'i\hbar \frac{dA}{dt}~=~[A(t),H(t)]+i\hbar \frac{\partial A}{\partial t}.'
        Math(formula)

* code block descriptions

    dividing the script in code blocks is useful to keep the code nicely sorted.
    It is even better to put a docstring for each block to make clear what the
    block is about. one simple way is to put a multiline string at the beginning of it.
    To avoid repeating the docstring when you execute the script line by line, just put a semicolon after it.

        """
        docstring
        """;

    one more fancy way to do it is to import the markdown display of ipython and wrapping the docstring with it.
    it will display it, and if you fold the code of the markdown, you just get the nice visualization without the raw string.

        from IPython.display import Markdown

        Markdown("""# test

        * riga 1
        * riga 2
        """)

* artificial code blocks

    sometimes it is useful to collect a bunch of code in a block to be executed
    all together, or disables all together.
    One way of doing it that works reasonably well without relying on the
    code block convetion is to use an if statement with a short descriptive string.

        if "print something to screen":
            a = 3
            print(a)

    if you want to skip the whole block all together you can just interpose a `not`
    between the if and the description string.

        if not "execute my awesome code that is useless now":
            pass

### useful extensions for ipython
* `ipython-sql` to exectute SQL calls inside your script

    load it with

        %load_ext sql

    then you can run SQL commands as a block

        %%sql sqlite://
        CREATE TABLE writer (first_name, last_name, year_of_death);
        INSERT INTO writer VALUES ('William', 'Shakespeare', 1616);
        INSERT INTO writer VALUES ('Bertold', 'Brecht', 1956);

    or as a single instruction

        a = %sql select * from writer
        a.DataFrame() # to get it as a pandas data frame

    it can also do dinamic binding to existing variables:

        state='FINISHED'
        %sql SELECT :state as "bind_variable"

* `cython` (included in the cython package)

    allow to magically compile and import cython functions for extra performance

        %load_ext cython

    then declare and execute a cython block

        %%cython
        cpdef myfunction(int a, int b):
            return a+b

    if it runs successfully, it will import the function in the current namespace

        >>> myfunction(4, 5)
        9

## configurations and packages

* `file-icons` for pretty icons on the file browser to help navigating
* `highlight-selected` show all the locations of the string that is highlighted
* `minimap` and  to have a side bar with a bird-eye view of the source code.

    it does have several plugins that can be installed (and activated and deactivated
    at will from the config icon that appears if you hover the mouse over the minimap)

    * `minimap-bookmarks` and `minimap-highlight-selected`

        display in the minimap the selected text and the bookmarks

    * `minimap-titles`

        use the command <kbd>Ctrl</kbd> + <kbd>shift</kbd> + <kbd>⌫  Del</kbd> to replace the selected text with ASCII graphics.
        this allow to generate titles readable in the minimap.
        if you apply to the word `text`, you obtain:

            ████████ ███████ ██   ██ ████████
               ██    ██       ██ ██     ██
               ██    █████     ███      ██
               ██    ██       ██ ██     ██
               ██    ███████ ██   ██    ██

    * `minimap-codeglance`

        codeglance helps preview the code from the minimap and is very useful,
        but the default graphics can be improved. I would suggest the following style.
        in the file `~/.atom/styles.less`, adding:

            minimap-codeglance {
              box-shadow: 0 0 40px rgba(127, 127, 127, 1);
            }

* `todo-show` to have a side bar with the TODOs and NOTEs for the current code
* `teletype` to collaboatively write code
* `simple-drag-drop-text` to move around selected text with the mouse
* `platformio-ide-terminal` include a simple terminal in the shell. might need to set `source ~/.bashrc` in the config to see the path properly
* `color-picker` use <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>C</kbd> to open up a color explorer and generate the string with the appropriate color. Very useful when plotting stuff.
* `tablr` allows to visualize and edit csv-like files in the editor

    the repository linked in atom is not working anymore, but a working fork can be installed using:

        apm install https://github.com/mfripp/atom-tablr.git

* `project-manager` allows to switch easily between different projects. it relies completely on the command prompt.

* NOT WORKING (in `hydrogen-python` set `extend executable code`)

    this makes sure that when you select a block to run such a an `if`
    statement, it runs the corresponding else as well

* NOT WORKING (`data-explorer`)

    this should allow interactive plotting of a dataframe

# External articles about Atom and shortcuts

* [automate repetitive tasks with composed commands](http://blog.atom.io/2018/10/09/automate-repetitive-tasks-with-composed-commands.html)
* [Atom manual](https://flight-manual.atom.io/)
* https://github.com/nwinkler/atom-keyboard-shortcuts
* https://sweetme.at/2014/03/10/atom-editor-cheat-sheet/
* https://github.com/mehcode/awesome-atom
