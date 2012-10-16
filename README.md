Advanced Custom Fields - Pages by Template add-on
=====================
adds a Pages by Template field to Advanced Custom Fields. Select pages by template.

Description
------
This is an add-on for the <a href="http://advancedcustomfields.com/">Advanced Custom Fields WordPress plugin</a> and will not provide any functionality to WordPress unless Advanced Custom Fields is installed and activated.

The Pages by Template field provides a new kind of field which allows you to choose pages based on their assigned templates (custom templates). When creating the field in ACF you may choose one or multiple templates to display pages from. You can also choose the ability to select one page or more in which the type will change between checkboxes and radio buttons. 

The return value is one or more post objects. Display these in the same way you would a <a href="http://www.advancedcustomfields.com/docs/field-types/relationship/">Relationship field</a> or <a href="http://www.advancedcustomfields.com/docs/field-types/post-object/">Post Object field</a>. 

<h4>Source Repository on GitHub</h4>
<a href="https://github.com/jonathan-dejong/ACF-Pages-by-Template">https://github.com/jonathan-dejong/ACF-Pages-by-Template</a>

<h4>Bugs, Questions or Suggestions</h4>
<a href="https://github.com/jonathan-dejong/ACF-Pages-by-Template/issues">https://github.com/jonathan-dejong/ACF-Pages-by-Template/issues</a>

Installation
------
* Download the add-on and copy the folder <i>fields</i> containing the acf_pages-by-template.php file to your theme folder
* Include the <code>acf_pages-by-template.php</code> in your theme's <code>functions.php</code>

<code>if( function_exists( 'register_field' ) )
  {
	   register_field('acf_page_template', dirname(__File__) . '/fields/acf_page_per_template.php');
	}
</code>

Frequently Asked Questions
--------
<h5>I've activated the plugin, but nothing happens!</h5>

Make sure you have Advanced Custom Fields installed and activated. This is not a standalone plugin for WordPress, it only adds additional functionality to Advanced Custom Fields.