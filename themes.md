# Themes

If you want to change Ubuntu's theme a little bit, let's install Flat-Remix:
- https://www.osradar.com/install-flat-remix-theme-ubuntu/

First, let's create a directory to sotre the repositories that we will download. 
You can use this directory for other projects. The idea here is to organize your folders.

```
mkdir Projects
```

Then open the dir:
```
cd Projects
```

Now, let's download flat-remix repository:
```
git clone https://github.com/daniruiz/flat-remix
```

Second, clone the other repository (GTK theme).
```
git clone https://github.com/daniruiz/flat-remix-gtk
```

The only thing left to do is to create the local folder where the theme will be.
```
mkdir -p ~/.icons && mkdir -p ~/.themes
```

Then, copy the contents of the cloned folder into the new one.
```
cp -r flat-remix/Flat-Remix* ~/.icons/ && cp -r flat-remix-gtk/Flat-Remix-GTK* ~/.themes/
```

Install Gnome Tweak Tool:
```
sudo apt install gnome-tweak-tool
```

Now, open your tweak tool and choose your preferred theme and icons.

Other themes suggestions: https://github.com/nana-4/materia-theme