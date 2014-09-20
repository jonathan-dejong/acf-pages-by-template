<?php

class acf_page_template extends acf_Field
{
	
	/*--------------------------------------------------------------------------------------
	*
	*	Constructor
	*
	*	@author Jonathan de Jong, based on file by Elliot Condon
	*	@since 3.5.0
	* 
	*-------------------------------------------------------------------------------------*/
	
	function __construct($parent)
	{
    	parent::__construct($parent);
    	
    	$this->name = 'page_template';
		$this->title = __("Pages by template",'acf');
		
   	}
   	
   	
   	/*--------------------------------------------------------------------------------------
	*
	*	create_field
	*
	*	@author Jonathan de Jong, based on file by Elliot Condon
	*	@since 3.5.0
	* 
	*-------------------------------------------------------------------------------------*/
	
	function create_field($field)
	{
		// vars
		$args = array(
			'numberposts' => -1,
			'post_type' => 'page',
			'orderby' => 'title',
			'order' => 'ASC',
			'post_status' => array('publish', 'private', 'draft', 'inherit', 'future'),
			'suppress_filters' => false,
			'meta_key' => '_wp_page_template',
	    	'meta_value' => ''
		);
		
		$defaults = array(
			'multiple'		=>	'0',
			'post_type' 	=>	false,
		);
		

		$field = array_merge($defaults, $field);
		
		
		// load all page templates by default
		if( !$field['meta_value'] || !is_array($field['meta_value']) || $field['meta_value'][0] == "" )
		{
			global $wpdb;
			$field['meta_value'] = get_page_templates();
		}

		
		// Change Field into a checkbox or radio buttons depending on if the user should be able to choose multiple pages or not
		if($field['multiple'] == 1){
			$field['type'] = 'checkbox';
			$field['choices'] = array();
			$field['optgroup'] = false;
		}else{
			$field['type'] = 'radio';
			$field['choices'] = array();
			$field['optgroup'] = true;
		}
		
		
		if($field['page_template']){
			foreach( $field['page_template'] as $page_template )
			{
				// set page_templates
				$args['meta_value'] = $page_template;
				
				//set order
				$args['sort_column'] = 'menu_order, post_title';
				$args['sort_order'] = 'ASC';
				//get the pages
				$posts = get_pages( $args );
			
				
				if($posts)
				{
					foreach( $posts as $post )
					{
						// find title. Could use get_the_title, but that uses get_post(), so I think this uses less Memory
						$title = '';
						$ancestors = get_ancestors( $post->ID, $post->post_type );
						if($ancestors)
						{
							foreach($ancestors as $a)
							{
								$title .= '–';
							}
						}
						$title .= ' ' . apply_filters( 'the_title', $post->post_title, $post->ID );
						
						
						// status
						if($post->post_status != "publish")
						{
							$title .= " ($post->post_status)";
						}
						
						// WPML
						if( defined('ICL_LANGUAGE_CODE') )
						{
							$title .= ' (' . ICL_LANGUAGE_CODE . ')';
						}
						
						// add to choices
						$field['choices'][ $post->ID ] = $title;
						
					}
					// foreach( $posts as $post )
				}
				// if($posts)
			}
			// foreach( $field['page_template'] as $page_template )
		}
		//if page_template
		
		
		// create field
		$this->parent->create_field( $field );
		
		
	}
	
	
	/*--------------------------------------------------------------------------------------
	*
	*	create_options
	*
	*	@author Jonathan de Jong, based on file by Elliot Condon
	*	@since 3.5.0
	* 
	*-------------------------------------------------------------------------------------*/
	
	function create_options($key, $field)
	{	
		// defaults
		$defaults = array(
			'page_template' 	=>	'',
			'multiple'		=>	'0',
		);
		$field = array_merge($defaults, $field);
		?>
		<tr class="field_option field_option_<?php echo $this->name; ?>">
			<td class="label">
				<label for=""><?php _e("Page template",'acf'); ?></label><p class="description">Choose for which templates you want to get pages</p>
			</td>
			<td>
				<?php 
				
				global $wpdb;
				$page_templates = get_page_templates();
				foreach( $page_templates as $page_template_name => $page_template )
				{
					$choices[$page_template] = $page_template_name;
				}
				
				$this->parent->create_field(array(
					'type'	=>	'select',
					'name'	=>	'fields['.$key.'][page_template]',
					'value'	=>	$field['page_template'],
					'choices'	=>	$choices,
					'multiple'	=>	'1',
				));
				
				?>
			</td>
		</tr>
		
		<!-- Depending on the choice of this we will display the pages as checkboxes (multiple) or radio (single) -->
		<tr class="field_option field_option_<?php echo $this->name; ?>">
			<td class="label">
				<label><?php _e("Select multiple values?",'acf'); ?></label><p class="description">Multiple values creates checkboxes, else it will display as radiobuttons</p>
			</td>
			<td>
				<?php 
				$this->parent->create_field(array(
					'type'	=>	'radio',
					'name'	=>	'fields['.$key.'][multiple]',
					'value'	=>	$field['multiple'],
					'choices'	=>	array(
						'1'	=>	__("Yes",'acf'),
						'0'	=>	__("No",'acf'),
					),
					'layout'	=>	'horizontal',
				));
				?>
			</td>
		</tr>
		<?php
	}
	
	
	/*--------------------------------------------------------------------------------------
	*
	*	get_value_for_api
	*
	*	@author Jonathan de Jong, Based on file by Elliot Condon
	*	@since 3.5.0
	* 
	*-------------------------------------------------------------------------------------*/
	
	function get_value_for_api($post_id, $field)
	{
		// get value
		$value = parent::get_value($post_id, $field);
		
		
		// no value?
		if( !$value )
		{
			return false;
		}
		
		
		// null?
		if( $value == 'null' )
		{
			return false;
		}
		
		
		// multiple / single
		if( is_array($value) )
		{
			// find posts (DISTINCT POSTS)
			print_r($value);
			$posts = get_posts(array(
				'numberposts' => -1,
				'post__in' => $value,
				'post_type'	=>	'page',
				'post_status' => array('publish', 'private', 'draft', 'inherit', 'future'),
			));
	
			
			$ordered_posts = array();
			foreach( $posts as $post )
			{
				// create array to hold value data
				$ordered_posts[ $post->ID ] = $post;
			}
			
			
			// override value array with attachments
			foreach( $value as $k => $v)
			{
				// check that post exists (my have been trashed)
				if( isset($ordered_posts[ $v ]) )
				{
					$value[ $k ] = $ordered_posts[ $v ];
				}
			}
			
		}
		else
		{
			$value = get_post($value);
		}
		
		
		// return the value
		return $value;
	}
		
}

?>