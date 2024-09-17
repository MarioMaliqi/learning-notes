# GTK

## Basic Overview
- Each GTK App consists of smaller widgets
- Widgets are organized in a hierarchy (the window widget being the main container)
- GTK exposes a object oriented interface for c via the `GObject`
- GTK is a event driven toolkit
---

## GTK App Flow
- `gtk/gtk.h` contain all the definitions needed for writing a gtk app
- GTK code can only be included with the `gtk/gtk.h` header (main header basically)
- A GTK app starts by creating the `GtkApplication` Object. The Object gets instantiated with the `gtk_apllication_new()` function
- `gtk_apllication_new()` takes in flags as arguments for special behaviour.
- activate signal gets connected on the apps startup (kinda like an event)
- `g_application_run()` binds that signal to a function and also gets the cmd-line parameters. (for handling cmd-line args)
- inside the `actiavte()` function is where the window setup happens. 
- `gtk_application_window_new()` creates a new `GtkApplicationWindow` Object and stores it inside the `*window` pointer.
- When creating a window. It's type is `GtkWidget*`. Instead of typecasting it to `(GtkWindow*)`, you can use the `GTK_WINDOW()` macro. It does some typechecking before casting and if the widget pointer is not a viable window, it fails.
- The Windows title, size, and showabillity are set via `gtk_window_set_title()`, `gtk_window_set_default_size` and `gtk_widget_show()`
- When quitting the app, the status code gets returned to the `status` variable from `g_application_run()`
- Then the `GtkApplication` object is freed from memory via `g_object_unref()`. The `status` integer ie being returned at the end of the program.
---

## GTK App Flow in a nutshell
-> Signal (user input, desktop env, linux -> handler for that signal -> ui change (thats it!)


## Source
[gtk docs guid](https://docs.gtk.org/gtk4/getting_started.html#hello-world)
