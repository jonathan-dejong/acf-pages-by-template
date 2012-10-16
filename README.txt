{\rtf1\ansi\ansicpg1252\cocoartf1138\cocoasubrtf470
{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\listtable{\list\listtemplateid1\listhybrid{\listlevel\levelnfc23\levelnfcn23\leveljc0\leveljcn0\levelfollow0\levelstartat1\levelspace360\levelindent0{\*\levelmarker \{disc\}}{\leveltext\leveltemplateid1\'01\uc0\u8226 ;}{\levelnumbers;}\fi-360\li720\lin720 }{\listname ;}\listid1}}
{\*\listoverridetable{\listoverride\listid1\listoverridecount0\ls1}}
\paperw11900\paperh16840\margl1440\margr1440\vieww15060\viewh8700\viewkind0
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural

\f0\b\fs56 \cf0 Advanced Custom Fields - Pages by Template add-on
\fs48 \

\b0\fs28 adds a Pages by Template field to Advanced Custom Fields. Select pages by template. \
\

\b\fs48 Description
\fs36 \

\b0\fs28 This is an add-on for the Advanced Custom Fields WordPress plugin and will not provide any functionality to WordPress unless Advanced Custom Fields is installed and activated.\
\
The Pages by Template field provides a new kind of field which allows you to choose pages based on their assigned templates (custom templates). When creating the field in ACF you may choose one or multiple templates to display pages from. You can also choose the ability to select one page or more in which the type will change between checkboxes and radio buttons. \
\
The return value is one or more post objects. Display these in the same way you would a Relationship field or Post Object field. 
\fs48 \
\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural

\b\fs36 \cf0 Source Repository on GitHub\

\b0\fs28 https://github.com/jonathan-dejong/ACF-Pages-by-Template
\b\fs36 \
\
Bugs, Questions or Suggestions\

\b0\fs28 https://github.com/jonathan-dejong/ACF-Pages-by-Template/issues
\b\fs36 \
\

\fs56 Installation\
\pard\tx220\tx720\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\li720\fi-720\pardirnatural
\ls1\ilvl0
\fs36 \cf0 {\listtext	\'95	}
\b0\fs28 Download the add-on and place the and copy the folder "fields" containing the acf_pages-by-template.php file to your theme folder\
\ls1\ilvl0
\b\fs36 {\listtext	\'95	}
\b0\fs28 Include the acf_pages-by-template-php in you theme' functions.php\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural

\i \cf0 if( function_exists( 'register_field' ) )\
\{\
	register_field('acf_page_template', dirname(__File__) . '/fields/acf_page_per_template.php');\
\}
\i0\b\fs36 \
}