This extension allows to change site language.
I was using [this](http://www.yiiframework.com/extension/languagepicker "extension") extension earlier and I decided to make my own.

##Requirements

- Bootstrap (works with newest alpha version) - only if you choose buttons style
- Yii 1.1
- Enabled cookies

##Usage

Just add this code to **init()** method in your main controller class (**protected/components/Controller.php**)

~~~
[php]
public function init()
{
	Yii::import('ext.LangPick.ELangPick');
	ELangPick::setLanguage();
	parent::init();
}
~~~

And in the place where you want to render Language Picker

~~~
[php]
<?php $this->widget('ext.LangPick.ELangPick', array()); ?>
~~~

And don't forget to set source language in (**protected/config/main.php**)
~~~
[php]
return array(
	'basePath'=>dirname(__FILE__).DIRECTORY_SEPARATOR.'..',
	'name'=>'Demo',
	...
    'sourceLanguage'=>'en',
	...
~~~

##Translations

You have to create translations, which should be placed in **messages** folder

~~~
[php]
messages
	de	// folder
		strings.php	// translation file
	pl	// folder
		strings.php	// translation file

~~~

Each translation file should contain translation array

~~~
[php]
<?php

return array (
    'Home' => 'Główna',
    'About' => 'O stronie',
);

?>
~~~


finally, to use translations:


~~~
[php]
Yii::t('strings', 'Home')
~~~

For more info, [please read manual](http://www.yiiframework.com/doc/guide/1.1/en/topics.i18n "manual").

##Additional information

If you want to customize it
~~~
[php]
<?php $this->widget('ext.LangPick.ELangPick', array(
	'excludeFromList' => array('pl', 'en'),	// list of languages to exclude from list
	'pickerType' => 'buttons',          	// buttons, links, dropdown
	//'linksSeparator' => '<b> | </b>',   // if picker type is set to 'links'
	'buttonsSize' => 'mini',            	// mini, small, large
	'buttonsColor' => 'success',        	// primary, info, success, warning, danger, inverse
)); ?>
~~~

##Look

![Look](http://i.imgur.com/QXNiE.png "Look")

##Try out

 * [Demo page](http://lowliet.com/Demo/)
