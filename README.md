# Agregar los campos de ACF a la tabla del Admin

<img src="https://raw.githack.com/ecr007/Agregar-los-campos-de-ACF-a-la-tabla-del-Admin/master/2016-01-05_1516.png" />

```php
/*
 * Add columns to exhibition post list
 */
 public function add_acf_columns ( $columns ) {
   return array_merge ( $columns, array ( 
     'start_date' => __ ( 'Starts' ),
     'end_date'   => __ ( 'Ends' ) 
   ) );
 }
 add_filter ( 'manage_exhibition_posts_columns', 'add_acf_columns' );
 
 ```
 
 ## 2
 
 ```php
 /*
  * Add columns to exhibition post list
  */
 public function exhibition_custom_column ( $column, $post_id ) {
   switch ( $column ) {
     case 'start_date':
       echo get_post_meta ( $post_id, 'start_date', true );
       break;
     case 'end_date':
       echo get_post_meta ( $post_id, 'end_date', true );
       break;
   }
 }
 add_action ( 'manage_exhibition_posts_custom_column', 'exhibition_custom_column', 10, 2 );
 ```
