# Agregar los campos de ACF a la tabla del Admin

<img src="https://raw.githack.com/ecr007/Agregar-los-campos-de-ACF-a-la-tabla-del-Admin/master/2016-01-05_1516.png" />

```php
function my_page_columns($columns) {
 $columns = array(
  'cb' => '< input type="checkbox" />',
  'title' => 'Title',
  'the-custom-field' => 'Custom Field'
 );
 return $columns;
}
function my_custom_columns($column) {
 global $post;
 if($column == 'seminar-date') {
  echo get_field('the-custom-field', $post->ID);
 } else {
  echo '';
 }
}
add_action("manage_CPTNAME_posts_custom_column", "my_custom_columns");
add_filter("manage_edit-CPTNAME_columns", "my_page_columns");
 ```
