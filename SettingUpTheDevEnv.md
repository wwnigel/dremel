  1. Install Eclipse from www.eclipse.org
  1. Install mercurialeclipse plugin: Eclipse/Help menu/Install new software, put URL http://cbes.javaforge.com/update hit next and etc...
  1. Install AJDT plugin Eclipse/Help menu/Install new software, put URL http://download.eclipse.org/tools/ajdt/36/update hit nextand etc...
  1. Restart Eclispe...
  1. Go Eclipse/File menu/New/Project/Mercurial/Clone, put URL: https://metaxa.dremel.googlecode.com/hg/dremel-metaxa
  1. Open browser, navigate https://code.google.com/hosting/settings
  1. Copy&paste your google code credentials to the appropriate places in eclipse mercurial dialog, IMPORTANT: select correct branch (now "san code") and proceed with code cloning/download
  1. Agree to enabling AJDT weaving and restart eclipse
  1. In PackageExplorer go to test / left mouse click / Run as / Junit. All/Most tests must be passed.
  1. Congrats you have a working environment to start hacking with the project!