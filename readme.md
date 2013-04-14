# iPad Theme for Fever
### Version .01 | By [Chris Johnson](http://chrisltd.com) | https://github.com/ChrisLTD/fever_ipad_theme

This iPad theme for Fever takes the iPhone theme, stretches the width for the iPad screen (portrait and landscape), bumps up the article font size, and removes the animations to make it feel snappier.

![Screenshot](https://github.com/chrisltd/fever_ipad_theme/raw/master/screenshot.png)

## Requirements
* Working installation of [Fever](http://feedafever.com/) 1.28+ by Shaun Inman.
* Willingness to possibly break your Fever installation by installing this theme.

## Installation
1. Backup your Fever installation.
2. Copy the `ipad` directory into `firewall/app/views/` so that you have a `firewall/app/views/ipad` directory.
3. Go into your `firewall/app/libs/fever.php` and replace the view_file() function on approximately line 800 with this:

``` php
/**************************************************************************
 view_file()
 **************************************************************************/
function view_file($base_file_name)
{
	$dir	= 'default';
	if ($this->is_mobile)
	{
		$dir = 'mobile';
	}
	// New code
	if ($this->is_ipad)
	{
		$dir = 'ipad';
	}
	// End new code
	$file = FIREWALL_ROOT.'app/views/'.$dir.'/'.$base_file_name.'.php';
	if (!file_exists($file))
	{
		$file = FIREWALL_ROOT.'app/views/default/'.$base_file_name.'.php';
	}
	return $file;
}
```

## Known Issues
* After a Fever update, the theme files are overwritten and you will have to reinstall them.
* You may run into file permission issues that will keep you from modifying anything in your `firewall` folder. Changing the `fever.php` file `views` folder so your user owns them should be enough.
* The icons aren’t retina.
* This theme won’t work on tablets besides the iPad and iPad mini.