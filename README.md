# JWT Extension Request Edition
A plugin to request the response for authentication

## INSTALLATION

Add widget to the end of the /library/widgets.php file
```php
/*********************
Weather & Search
*********************/

class fb_sidebar_weather_search extends WP_Widget {

    /** constructor -- name this the same as the class above */
    function __construct() {
        $widget_ops = array( 'classname' => 'sidebar-weather-search', 'description' => __( "Use this Widget to place the Weather & Search" ) );
        $this->WP_Widget( 'sidebar_weather_search', __('Sidebar Weather Search'), $widget_ops);
    }

    /** @see WP_Widget::widget -- do not rename this */
    function widget($args, $instance) {

      extract( $args );
        

      // Check if checkbox is checked
      if( $checkbox AND $checkbox == '1' ) { $hide_on_phone = " show-above-768"; } else { $hide_on_phone = ""; }

        ?>
              <?php echo $before_widget; ?>
				<div class="weather-search pull-right">
					<a href="<?php echo trim(get_field('weather_link', 'option')); ?>" target="_blank">
						<?php get_template_part( 'partials/snippet', 'weather' ); ?>
					</a>
					<form method="get" class="navbar-search pull-right" action="/search-results/">
						<div class="input-append">
								<input type="text" name="q" class="q" id="q-d" placeholder="Search" value="<?php echo $_GET['q']; ?>" />
								<button class="btn" type="submit"><i class="fa fa-search"></i></button>
						</div>
					</form>
				</div>
				<div style="clear:both"></div>
              <?php echo $after_widget; ?>
        <?php
    }

    /** @see WP_Widget::update -- do not rename this */
    function update($new_instance, $old_instance) {
    $instance = $old_instance;

        return $instance;
    }

    /** @see WP_Widget::form -- do not rename this */
    function form($instance) {

    }

} // end class example_widget
add_action('widgets_init', create_function('', 'return register_widget("fb_sidebar_weather_search");'));
```

Replace lines 253 to 263 on header.php
```php
<div class="weather-search pull-right">
	<a href="<?php echo trim(get_field('weather_link', 'option')); ?>" target="_blank">
		<?php get_template_part( 'partials/snippet', 'weather' ); ?>
	</a>
	<form method="get" class="navbar-search pull-right" action="/search-results/">
		<div class="input-append">
				<input type="text" name="q" class="q" id="q-d" placeholder="Search" value="<?php echo $_GET['q']; ?>">
				<button class="btn" type="submit"><i class="fa fa-search"></i></button>
		</div>
	</form>
</div>
```
... with the following:
```php
<?php if (function_exists("editorsClubHeaderSignIn")){
	editorsClubHeaderSignIn();
} ?>
```
