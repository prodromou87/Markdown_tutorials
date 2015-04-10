#Git Flavored Markdown Guide

##Beginner's guides

For my documentations, I'm using the Git-Flavored-Markdown (GFM) which is an extended version of Markdown language. You can use the following links for learning Markdown and/or GFM

- [Markdown Tutorial](http://markdowntutorial.com/)
- [GFM](https://help.github.com/articles/github-flavored-markdown/)
- Some extra GFM features can be found [here](https://help.github.com/articles/writing-on-github/)
- [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

##Examples

[This file](gfm_cheat_sheet.md) contains several examples of all the things you can do with GFM.

##Sublime Editor Markdown Configuration

I use Sublime Text 2 as my editor for Markdown documentations. Some packages need to be installed to support a smooth and easy markdown workflow:

1. **Install Package Control (For fresh Sublime installation):** 
Pull up the *Python Console* by pressing `` control + ` `` or click ` View > Show Console`. Paste the following python script (for SL2) and then Enter:
```Python
import urllib2,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
```
You might need to restart SL for the installation to complete.

2. **Install MarkdownEditing:**
We need to manually install this. For some reason, package control does not include it anymore (?). 
	1. **Mac:** `git clone https://github.com/SublimeText-Markdown/MarkdownEditing.git ~/Library/Application\ Support/Sublime\ Text\ 2/Packages/MarkdownEditing`
	2. **Windows:** `git clone https://github.com/SublimeText-Markdown/MarkdownEditing.git %APPDATA%\Sublime/ Text/ 2/\MarkdownEditing`
	3. **Linux:** `git clone https://github.com/SublimeText-Markdown/MarkdownEditing.git ~/.Sublime\ Text\ 2/Packages/MarkdownEditing`

3. **Install Markdown Preview:**:
Press `control + shift + p` to open the Command Pallette. Start typing "install" and select "Package Control: Install Package". Start typing "Markdown HTML Preview". Select and install. 
Add the following line in `Preferences > Key Bindings - User` to configure `alt + m` to preview in your browser.
```
{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} }
```