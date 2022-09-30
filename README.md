# Convert a  price in JS in WooCommerce

A simple JavaScript function making it easy to convert a number into WooCommerce price.

It's based on the code shared by [HelgaTheViking](https://github.com/helgatheviking) in the [WooCommerce Slack Community](https://woocommercecommunity.slack.com/join/shared_invite/zt-1gbkltk7m-mYW~QNTY~GcBCHmngJnK2g)

# How to use it ?  
-- PHP Code
```php 
// enqueue the file into the wp website.
wp_enqueue_script( 'wc-price-js', plugin_dir_url( __FILE__ ) . 'js/wc_price.js', array( 'jquery' ), '1.0', false );

// add inline script to pass currency informations from php to the js.
$wc_store_object = array(
  'html' => true,
  'currency_symbol' => get_woocommerce_currency_symbol( get_woocommerce_currency() ),
  'currency_position' => get_option( 'woocommerce_currency_pos', true ),
  'decimal_separator' => wc_get_price_decimal_separator(),
  'currency_format_trim_zeros' => wc_get_price_thousand_separator(),
  'currency_format_num_decimals' => wc_get_price_decimals(),
  'price_format' => get_woocommerce_price_format(),
);
wp_add_inline_script( 'wc-price-js', ' var wc_settings_args=' . wp_json_encode( $wc_store_object ) . ';' );

```

-- JS Code
```js
console.log( wc_price( 900, wc_settings_args ) ); 
// he will display $ 900 ( based on the currency, the price displayed will be different ).

console.log( wc_price( 10, wc_settings_args ) ); 
// he will display 10$ ( based on the currency, the price displayed will be different ).

```

# Credits  
[Helga The Viking](https://github.com/helgatheviking)  
[Manu The Blacker](https://github.com/manutheblacker)  
