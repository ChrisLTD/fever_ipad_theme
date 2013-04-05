# iPad Theme for Fever

## Installation
1. Backup your fever installation.
2. Copy the ipad directory into `firewall/app/views/` so that you have a `firewall/app/views/ipad` directory.
3. Go into your firewall/app/libs/fever.php and replace the view_file() function on approximately line 800 with this:
```
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