---
layout: post
title: "Adding custom programs to favourites of Ubuntu Dock"
date:   2023-06-01 05:00:00 -0400
categories: ubuntu
comments: true
---

In this blog post, you will learn how to add custom programs, specifically AppImage applications, to the favorites section of the Ubuntu Dock. This will make it easier to access and launch these applications directly from the dock.

### 1. Create a Desktop Application File

First, youneed to create a desktop application file in the `~/.local/share/applications` directory. This file will contain the necessary information for the application to be recognized by the system.

Create a new file called cursor.desktop with the following content:
```
# /home/remy/share/applications/cursor.desktop

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Cursor
Comment=Cursor
Exec=/home/remy/Cursor.AppImage
Icon=/home/remy/Cursor.ico
Terminal=false
```

### 2. Make the .desktop File Executable

Next, youneed to make the `.desktop` file executable. Run the following command in the terminal:

```bash
chmod a+x ~/.local/share/applications/cursor.desktop
```

### 3. Get the List of Favorite Apps

Now, youneed to get the current list of favorite apps. Run the following command in the terminal:

```bash
dconf read /org/gnome/shell/favorite-apps
```

Take note of the output, as youwill need it in the next step.

### 4. Add the New .desktop File to the List of Favorite Apps

Finally, youwill add the new `.desktop` file to the list of favorite apps. Replace `your-previous-apps` with the output from the previous step, and run the following command in the terminal:

```bash
dconf write /org/gnome/shell/favorite-apps "[your-previous-apps, 'cursor.desktop']"
```

Now, you should be able to search for [Cursor](https://www.cursor.so) by name, and it will appear in your dock. Enjoy your new, easily accessible custom program!
