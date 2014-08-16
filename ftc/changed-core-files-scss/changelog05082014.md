	templates/be_main.html5 
	

##update in c3.3.3 TL_ASSETS

scssphp-compass
Handle .scss and .less files in the Combiner. This also allows to add SCSS or LESS files as external style sheets to the page layout.


# files taken from c3.3.3
	  root / system / modules / core / library / Contao / Combiner.php 

	  root / system / config / default.php #taken from c3.3.3
	  root / system / modules / core / languages / de / tl_layout.xlf  #taken from c3.3.3
	  root / system / modules / core / languages / en / tl_layout.xlf
	  root / system / modules / core / library / Contao / File.php
	  root / system / modules / core / dca / tl_layout.php
	  root / system / modules / core / classes / Backend.php
 


 ##require
  TL_ROOT . '/vendor/leafo/scssphp-compass/stylesheets'


----
Ergänzung der  core / system / modules / core / drivers / DC_Folder.php

ca L1700  // Update the database
				if ($this->blnIsDbAssisted)
				{
					$objMeta->hash = $objFile->hash;
					$objMeta->save();

					$objVersions->create();
				}

				// Purge the script cache (see #7005)
				if ($objFile->extension == 'css' || $objFile->extension == 'scss' || $objFile->extension == 'less')
				{
					$this->import('Automator');
					$this->Automator->purgeScriptCache();
				}


				---


				// Restore a version
			if (\Input::post('FORM_SUBMIT') == 'tl_version' && \Input::post('version') != '')
			{
				$objVersions->restore(\Input::post('version'));

				// Purge the script cache (see #7005)
				if ($objFile->extension == 'css' || $objFile->extension == 'scss' || $objFile->extension == 'less')
				{
					$this->import('Automator');
					$this->Automator->purgeScriptCache();
				}

-------
#
L337  # Ergänzung core / system / modules / core / library / Contao / Combiner.php 

require_once(TL_ROOT . '/vendor/leafo/scssphp/scss.inc.php');
require_once(TL_ROOT . '/vendor/leafo/scssphp-compass/compass.inc.php');




