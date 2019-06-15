=======================================
Flutter Web Preview Plugins Work Around
=======================================

Intro
-----
Flutter for the web preview does NOT support plugins or the dart dependency management. One reason for this is because flutter web is a seperate repostory from flutter (main) with a seperate name space ("flutter_web"). As a work around I modify the source code of these plugins to be flutter web compatible. Next I add the modified plugins to this repository so that we can still add depdencies in the pubspec.yaml. This solution keeps our depedencies clean without the need to pull each plugin source into our flutter_web projects. The modifications are all cosmetic and 99% of the time it is just replacing "package:flutter/..." with "package:flutter_web" =). The pubspec.yaml also needs modifications. With that said more sophisticated plugins with dependencies can be complicated.

In the future flutter_web will be merged with flutter master. At that time this repository will be obsolete.


Working Plugins
---------------
* provider
  - works as expected
* flutter_progress_button
  - TBD


Not Working Plugins (for your referrence)
-----------------------------------------
These packages are listed for referrence. These packages were an early attempt to get working, but failed for the reasons below:
* firebase_core
  - cannot run on web because it is only a wrapper. this plugin depends on native code for Android/iOS. also developers intentionally added an exception that throws when trying to use this on flutter_web. "this is not compatible with flutter web preview".
* cloud_firestore
  - cannot run on web because it is only a wrapper. this plugin depends on native code for Android/iOS. also developers intentionally added an exception that throws when trying to use this on flutter_web. "this is not compatible with flutter web preview".


Usage
-----

::

	dependencies:
	  provider: any

	dependency_overrides:
	  flutter_web:
	    git:
	      url: https://github.com/j3g/flutter_web_plugins.git
	      path: packages/provider

