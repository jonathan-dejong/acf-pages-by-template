=== Advanced Custom Fields: Pages by template Field ===
Contributors: Jonathan de Jong, Xavier Priour
Tags: ACF, page, template
Requires at least: 3.5
Tested up to: 3.8.1
Stable tag: trunk
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Adds a field to select a page, filtered on pages of a specific template

== description ==

This is an add-on for the <a href="http://advancedcustomfields.com/">Advanced Custom Fields WordPress plugin</a> and will not provide any functionality to WordPress unless Advanced Custom Fields is installed and activated.

The Pages by Template field provides a new kind of field which allows you to choose pages based on their assigned templates (custom templates). When creating the field in ACF you may choose one or multiple templates to display pages from. You can also choose the ability to select one page or more in which the type will change between checkboxes and radio buttons. 

The return value is one or more post objects. Display these in the same way you would a <a href="http://www.advancedcustomfields.com/docs/field-types/relationship/">Relationship field</a> or <a href="http://www.advancedcustomfields.com/docs/field-types/post-object/">Post Object field</a>.

= Compatibility =

This ACF field type is compatible with:
* ACF 5
* ACF 4

== Installation ==

1. Copy the `acf-pages-by-template` folder into your `wp-content/plugins` folder
2. Activate the Pages by template plugin via the plugins admin page
3. Create a new field via ACF and select the Pages by template type
4. Please refer to the description for more info regarding the field type settings

== Changelog ==

= 1.0.0 =
* Initial Release.