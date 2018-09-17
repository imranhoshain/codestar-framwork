# codestar-framwork
1. Create a file name like: theme-metabox-and-options.php

2. Include file on function.php

 //Themeoptions and metabox functions.
 
include_once (get_template_directory().'/inc/theme-metabox-and-options.php');

3. Copy bellow code and paste theme-metabox-and-options.php


## Example (Optional)

```php

get_template_part( '/inc/marvel-framework/cs-framework' ) ;

// framework Metabox options filter example
function marvel_cs_metabox_options($options)
{
    
    $options = array(); // remove old options     
  
    //All page option meta    
    $options[] = array(
        'id' => 'theme_page_meta',
        'title' => 'Page Options',
        'post_type' => 'page',
        'context' => 'normal',
        'priority' => 'default',
        'sections' => array(
            array(
                'name' => 'theme_page_metabox',
                'title' => 'Page Options',
                'fields' => array(
                    // begin: a field
                    array(
                        'id' => 'enable_title',
                        'type' => 'switcher',
                        'title' => 'Enable Page Title',
                        'default' => 'false'
                    ),
                    // end: a field  
                    array(
                        'id' => 'custom_title',
                        'type' => 'textarea',
                        'title' => 'Add Page custom Title',
                        'dependency' => array(
                            'enable_title',
                            '==',
                            'true'
                        )
                    ),
                    // end: a field
                    array(
                        'id' => 'text_title_direction',
                        'type' => 'select',
                        'title' => 'Select Text Align',
                        'options' => array(
                            'center' => 'Center',
                            'left' => 'Left',
                            'right' => 'Right'
                        ),
                        'default' => 'left',
                        'dependency' => array(
                            'enable_title',
                            '==',
                            'true'
                        )
                    ),
                    // end: a field         
                    
                )
            )
        )
    );
    
    return $options;
    
}
add_filter('cs_metabox_options', 'marvel_cs_metabox_options');



// framework Theme options filter example
function marvel_theme_options($options)
{
    
    $options = array();    
   //End footer acordian

    $options[] = array(
        'name' => 'script_section',
        'title' => 'Script Section',
        'fields' => array(
            array(
                'id' => 'custom_css',
                'type' => 'textarea',
                'sanitize' => false,
                'title' => 'Custom Css'
            )
        )
    );
    

    return $options;
    
}
add_filter('cs_framework_options', 'marvel_theme_options');



// framework Customize options filter example
function marvel_custom_framework_options($options)
{
    
    $options = array(); // remove old options
    
    return $options;
    
}
add_filter('cs_customize_options', 'marvel_custom_framework_options');

```

---
