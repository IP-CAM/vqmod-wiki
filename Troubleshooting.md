#Troubleshooting

##Understanding vQmod Errors

It is important to note that vQmod itself is _very_ rarely going to have any actual bugs in the vQmod engine. This is because it only does what it is functionally programmed to do and the rest of it is just file system operations that are built into the server. This leaves little room for error. So when you see a vQmod error on your site, there is a 99.9% chance that it is related to one of the xml scripts you are using, and not to the vQmod engine itself.


###Here are some common errors and solutions

*vQmod scripts don't seem to be working.*

Check the following:
  * Is the vQmod engine installed? Did you run the installer?
  * Do you have the latest version from the [vqmod.com](http://vqmod.com) website?
  * If you recently upgraded opencart, you will need to re-run the vQmod installer. You must always re-run the vQmod installer after upgrading opencart as the index.php files are overwritten and must be re-modified with the vQmod code.
  * If you recently upgraded vQmod, you may need to re-run the vQmod installer again as sometimes it will update it's own code in the index.php.
  * Does the vqmod/vqcache folder have any files in it? If not then be sure you installed vQmod and check the vqcache folder permissions are 755 or 775 or 777. Try each one until it works.
  * Check the vqmod/logs folder for any files and see where the script errors are, then track down the author of the individual script and ask them for assistance.


*I see an error on my site referring to ".../vqmod/vqcache/xxx.php"*

This is an error being caused by one of your scripts. These are generally due to bugs in the script files or conflicting mods that break each other. These can be difficult to trace because the actual vQmod script worked correctly, but its resulting output is causing an error on the store itself. 

So you have to try to isolate the error by first identifying which xml file causes it. Hopefully depending on what you were trying to do (view an order, checkout, view a product) you can narrow down which xml files adjust this particular area. For example, if you are seeing an error on the product page in the front, then you'll likely be able to rule out any vQmod scripts named "admin_sales_report.xml" since you aren't on the admin side. But not all scripts are so aptly named.

The best way to trace an issue like this is to create a subfolder in the vQmod/xml folder called "disabled" or anything you like. And start moving xml files into that folder one-by-one. Each time you move an xml file into that folder, refresh the page on your site and see if the error is gone. Once it is, then you know which file caused the issue and you can restore the other files you disabled up to that point.