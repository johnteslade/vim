Changes by JTES

Changes to make vim multiple windows so it can be used on a multi-monitor setup.

# Design is as follows.

* Using GTK as start
* Create a new top level window
* Use the tab notebook to allow drag and drop between the two windows

https://developer.gnome.org/gtk3/3.9/GtkNotebook.html#gtk-notebook-set-tab-detachable

Posisble issue with the Gtk socket being used
http://gtk.10911.n7.nabble.com/GtkSocket-in-GtkNotebook-with-drag-and-drop-tabs-td80388.html

Example notebooks
https://github.com/jerryd/gtk-fortran/blob/master/examples/notebooks.f90
https://developer.gnome.org/gtk-tutorial/2.90/x1450.html

Notes:
* Currently the drawwindow is not attached to the draw window - this means it does not drag and drop with it
* Need to allow reording of tabs
* Look at how tabs in GTK are mapped to the actual vim tab number


# Build as follows

Prerequisits on ubunutu from https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source

    sudo apt-get install libncurses5-dev libgnome2-dev libgnomeui-dev \
        libgtk2.0-dev libatk1.0-dev libbonoboui2-dev \
        libcairo2-dev libx11-dev libxpm-dev libxt-dev python-dev ruby-dev mercurial

For Fedora

    yum install ncurses-devel libgnome-devel libgnomeui-devel \
        gtk2-devel atk-devel libbonoboui-devel \
        cairo-devel libX11-devel libXpm-devel libXt-devel python-devel ruby-devel mercurial

From http://stackoverflow.com/questions/18488403/building-gvim-7-4-on-centos-6-4

    ./configure --prefix=/usr --with-compiledby="jtes"   \
        --with-features=huge --enable-rubyinterp    \
        --enable-pythoninterp --enable-python3interp    \
        --disable-tclinterp --with-x=yes \
        --enable-xim --enable-multibyte \
        --enable-gui=gtk2 \
        --enable-luainterp --enable-perlinterp \
        --enable-cscope \
        --enable-netbeans 2>&1

Build:

    make -j20 VIMRUNTIMEDIR=`pwd`/runtime/ 



