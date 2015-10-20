---
published: true
title: Background Technology II
---


#The Editor: Sublime-Text 3
Actually this is a decision of each one, but I recommend to use Sublime-Text as your main editor. Is not free, but is not paid. You download an unlimited evaluation (is the full version) copy. So, actually you can pay for it or not.

## Install it

Download it from here [Sublime-Text 3](http://www.sublimetext.com/3) and install it.

### Install Package Control

The best of Sublime-Text are the plugins and the most are installable through the Package Controll. For installin it open the console from *View>Show Console* and paste this commands to it:

	import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + 			'8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)



