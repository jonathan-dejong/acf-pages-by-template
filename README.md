* `AUTHOR_URL`: URL to author's website

### step 2.

Edit the `acf_pages_by_template-v5.php` and `acf_pages_by_template-v4.php` files (now renamed using your field name) and include your custom code in the appropriate functions. 
Please note that v4 and v5 field classes have slightly different functions. For more information, please read:
* http://www.advancedcustomfields.com/resources/tutorials/creating-a-new-field-type/

### step 3.

Edit this `README.md` file with the appropriate information and delete all content above and including the following line.

-----------------------

# ACF Pages by template Field

Adds a field to select a page, filtered on pages of a specific template

-----------------------

### Description

This is an add-on for the <a href="http://advancedcustomfields.com/">Advanced Custom Fields WordPress plugin</a> and will not provide any functionality to WordPress unless Advanced Custom Fields is installed and activated.

The Pages by Template field provides a new kind of field which allows you to choose pages based on their assigned templates (custom templates). When creating the field in ACF you may choose one or multiple templates to display pages from. You can also choose the ability to select one page or more in which the type will change between checkboxes and radio buttons. 

The return value is one or more post objects. Display these in the same way you would a <a href="http://www.advancedcustomfields.com/docs/field-types/relationship/">Relationship field</a> or <a href="http://www.advancedcustomfields.com/docs/field-types/post-object/">Post Object field</a>.

### Compatibility

This ACF field type is compatible with:
* ACF 4

### Installation

1. Copy the `acf-pages-by-template` folder into your `wp-content/plugins` folder
2. Activate the Pages by template plugin via the plugins admin page
3. Create a new field via ACF and select the Pages by template type
4. Please refer to the description for more info regarding the field type settings

### Changelog
Please see `readme.txt` for changelog
