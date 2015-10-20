---
published: true
title: Background Technology II
---


#The Editor: Sublime-Text 3
Actually this is a decision of each one, but I recommend to use Sublime-Text as your main editor. Is not free, but is not paid. You download an unlimited evaluation (is the full version) copy. So, actually you can pay for it or not.

## Install it
Download it from here [Sublime-Text 3](http://www.sublimetext.com/3) and install it.

## Install Package Control

The best of Sublime-Text are the plugins and the most are installable through the Package Controll. For installin it open the console from *View>Show Console* and paste this commands to it:

	import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + 			'8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)


Wait for the installation to finish and restart Sublime-Text. Now we have installed and we can start installing some plugins. But first lets know some useful Keyboard Shortcuts.

## Keyboard Shortcuts

#### Command Palette
	ctrl + shift + p
One of the most used commands. You can access everything from here: Installing plugins, using plugins, settings, changing syntax, snippets, etc.
#### Fast file switching
	ctrl + p    
#### Multi select and edit
	ctrl + d
#### Toggle Comment
	ctrl + /
#### Toggle sidebar
	ctrl + k + b
#### Duplicate line
	ctrl + shift + d
    

## Installing a new theme

This is another time a decision of each one, but I like to use a different theme on the editor. I use this: [SpaceGray](https://github.com/kkga/spacegray).

For installing it we are going to use the Package Control, so open the command palette *ctrl + shift + p* and type **Package Control: Install Package**. *Tip: You don't need to write the full sentence: just write some letters in it as 'packin'*. 

Now find the theme **Theme - Spacegray** and hit Enter. Wait for the installation. For activating it go to **Preferences>Settings - User** and add this to the settings file:

	"theme": "Spacegray.sublime-theme",
  	"color_scheme": "Packages/Theme - Spacegray/base16-ocean.dark.tmTheme"

This is a JSON file so remember to correctly add the commas at the end of each sentence (less the last one) or it won't work. Restart Sublime and you have it.


## Installing some plugins

Here is a list of the plugins I use. All of them are installed through the Package Control, so for installing open the command palette and type: **Package Control: Install Package** and type the name of the package.

#### SideBarEnhancements
Add some functions to the sidebar as Open / Run, Open in browser, Open With, etc.
#### BracketHighlighter
Add hightlight to bracket in the code for viewing it easily.
#### Emmet
Powerful improvement for CSS and HTML. It permits you to have short codes for writting. 

For example writting: **.class#id** and tab key it will result in:
	<div class="class id"></div>
For a full guide I recommend the guide from Scotch.io [Scotch.io Emmet](https://scotch.io/tutorials/write-html-crazy-fast-with-emmet-an-interactive-guide)

This is basically what you need to start, but you can search for more plugins in internet or in the [Package Control website](https://packagecontrol.io/).

	

