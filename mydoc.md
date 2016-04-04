# Table of Contents  
[ ](#) 
 * [Create child theme to modify theme without losing code when the theme updated)as default](#create-child-theme-to-modify-theme-without-losing-code-when-the-theme-updated)  
 * [Woocommerce send invoice and order ](#woocommerce-send-invoice-and-order) 
 * [PayPal setup that display Credit card pay option ](#paypal-setup-that-display-credit-card-pay-option) 
 * [Change the product image size display in the shop page ](#change-the-product-image-size-display-in-the-shop-page) 
 * [To change the product display in shop page to 4 per row (default is 3 per row) ](#change-the-product-image-size-display-in-the-shop-page) 
 * [Align the Add to cart button on shop page ](#align-the-add-to-cart-button-on-shop-page) 
 * [Change the default sorting product in Shop page (to popular or price..ect)as default](#change-the-default-sorting-product-in-shop-page-to-popular-or-priceectas-default)  
 * [Add extra taxonomies install this pluggin “Toolset Types” ](#add-extra-taxonomies-install-this-pluggin-toolset-types) 
 * [Separate the account and reg/login page and add logout](#separate-the-account-and-reglogin-page-and-add--logout) 
 * [Dropdown search as user typing the product name](#dropdown-search-as-user-typing-the-product-name) 
 * [Pop up tab at bottom](#pop-up-tab-at-bottom) 
 * [Slideshow with best rated product and best sell ](#slideshow-with-best-rated-product-and-best-sell)
 * [Ajax dropdown search ](#ajax-dropdown-search)



# Create child theme to modify theme without losing code when the theme updated
1. Create a folder named [your_current_theme_name]-child.
2. Create 2 files functions.php and style.css.
3. Paste this code on style.css file and change the Template name to the same as your theme name.
  ```bash
    /**
    * Theme Name: [your_current_theme_name] Child
    * Theme URI: http://www.getmotopress.com/themes/emmet
    * Author URI: http://www.getmotopress.com/
    * Version: 1.4.1
    * Template: [your_current_theme_name]
    * Domain Path: /languages/
    */
```

1. Any new style and php codes will go to style.css and functions.php in child theme folder from now.
1. More info https://codex.wordpress.org/Child_Themes .

# Woocommerce send invoice and order
For Woocommerce to send invoice to customer and order to owner, needed to change the email under Woocommerce Setting > Email > Email Sender Options - "From" Address to wordpress@yourdomain.com (yourdomain is whatever your domain is).
# PayPal setup that display Credit card pay option 
Just need add the paypal email with bank verified/confirmed> DONE
# Change the product image size display in the shop page 
Woocommerce setting> Product tab > Display tab and change the size accordingly. 
# To change the product display in shop page to 4 per row (default is 3 per row)
Paste this code into the style.css.
```
    .woocommerce ul.products li.product { 
	width: 21% !important;
	margin: 2% !important;
	clear: none !important;
    }
    .woocommerce ul.products li.product:nth-child(4n+1) {
	clear: both !important;
    }
@media screen and (min-width: 768px) and (max-width: 980px) {
.woocommerce ul.products li.product.first, .woocommerce ul.products li.product.last {
  clear: right !important;
}
```
# Align the Add to cart button on shop page
The add to cart button on product may not align with other add to cart button on other product because if the product name is too long, it's push the button down. paste this code in style.css to fix. increase the min-height if needed.
```
    .archive #main ul li a h3 {
    min-height: 50px;
}
```
# Change the default sorting product in Shop page (to popular or price..ect)as default.
Woocommerce setting> product > display tab > change Default Product Sorting.
# Add extra taxonomies install this pluggin “Toolset Types”
To add extra taxomony to the product (city,store...) https://wordpress.org/plugins/types/ . after installed, click Types> taxnomy on the menu on the left to add new taxnomy. 
# Separate the account and reg/login page and add  logout
1.	Create 2 menu with woocommerce_my_acount shortcode. My account and reg/login
2.	Add custom ccs name nav-login and nav-account.
3.	Make a custom link menu with a link of  /my-account/customer-logout  and name log out.
4.	Then add this code to function to display the menu depend on user have login or not.
```
    add_action('wp_head','jg_user_nav_visibility');
    function jg_user_nav_visibility() {
	if ( is_user_logged_in() ) {
    	$output="<style> .nav-login { display: none; } </style>";
	} else {
    	$output="<style> .nav-account { display: none; }.nav-logout { display: none; } </style>";
       	}
	echo $output;
}
```
# Dropdown search as user typing the product name
Use Dave's WordPress Live Search for dropdown as user typing. This pluggin added to the default search.This one search way smarter eg. if searching for noodle egg but type egg noodle still came with same result. https://wordpress.org/plugins/daves-wordpress-live-search/ .
The search dropdown-box sometime overlay the search-textbox. Add the x-value in the setting to push the dropdown-box down. This plugin will added to the wordpress default search.
# Pop up tab at bottom:
Use Sticky Popup plugin. https://wordpress.org/plugins/sticky-popup/ 
# Slideshow with best rated product and best sell 
* FREE : Woo Shop Slider Lite
https://wordpress.org/plugins/woo-shop-slider-lite/ 
* PAY
WooCommerce Product Slider
(pro ver) $29.00
https://wordpress.org/plugins/woocommerce-product-slider/ 

    https://wordpress.org/plugins/woocommerce-products-slider/ 
    
# Ajax dropdown search
1. create 2 files name db_connect.php and fetch_data.php inside child theme folder.
1. install this plugin https://wordpress.org/plugins/woocommerce-products-filter/ to use for the seach url.
1. create a folder name js inside child theme folder and create a file name myjs.js inside js folder just created child-theme/js/. download the jquery file from https://jquery.com/download/ and rename it to jquery.js and put it inside child-theme/js/ folder.
1. paste this code into the functions.php inside child-theme folder. these 2 functions use to create a search form and load the 2 js files myjs.js and jquery.js .
1. open the db_connect.php file and paste this code. this code is use to connect to the databse. change variable value to match the database auth.

 ```bash
<?php 
  $servername = "localhost";
  $username = "root";
  $password = "";
  $dbname="wordpress_city_suburb_store";
  $conn = new mysqli($servername, $username, $password,$dbname);
  ?>
```
1. open the fetch_data.php file and paste this code. this file will populate the next dropdown according to what is selected on the upper level. 

 ```bash
<?php
 include 'db_connect.php'; 
     $string = '';
      $i = 0;
if(isset($_POST['cityid']))
{
    $cityid = $_POST['cityid'];
    if($cityid==0){
       echo "<option value='0'>All Suburb</option>";
    }else{
       $strSQL = "Select term_id From wp_term_taxonomy Where count !=0 AND parent=".$cityid;
    $query = mysqli_query($conn, $strSQL);
     while($row=mysqli_fetch_array($query))
     {
       $string .= $row[$i].',';
     }
    $array=array_map('intval', explode(',', $string));
    $array = implode("','",$array);
    $strSQLsuburb = "Select name,slug From wp_terms Where term_id IN ('".$array."')";
 
// Execute the query.
 
  $querysuburb = mysqli_query($conn, $strSQLsuburb);
   echo "<option value='0'>All Suburb</option>";
     while($row=mysqli_fetch_array($querysuburb))
     {
       echo "<option value='".$row['slug']."'>".$row['name']."</option>";
     }
         
    }
    unset($_POST['cityid']);
   
}
else if(isset($_POST['suburbslug']))
{
   $suburbslug=$_POST['suburbslug'];
   $strgetsuburbid = "Select term_id From wp_terms Where slug='".$suburbslug."'";
   $querygetsuburbid = mysqli_query($conn, $strgetsuburbid);

    while($row=mysqli_fetch_array($querygetsuburbid))
     {
      $suburbid=$row['term_id'];
     }
    $strSQL = "Select term_id From wp_term_taxonomy Where  count !=0 AND parent=".$suburbid;
    $query = mysqli_query($conn, $strSQL);
     
     while($row=mysqli_fetch_array($query))
     {
       $string .= $row[$i].',';
     }
    $array=array_map('intval', explode(',', $string));
    $array = implode("','",$array);
    $strSQLstore= "Select name,slug From wp_terms Where term_id IN ('".$array."')";
    $querystore = mysqli_query($conn, $strSQLstore);
    echo "<option value='0'>All Store</option>";
     while($row=mysqli_fetch_array($querystore))
     {
       echo "<option value='".$row['slug']."'>".$row['name']."</option>";
     }
     unset($_POST['suburbslug']);
}else{
    $storeslug=$_POST['storeslug'];
    if(is_numeric($storeslug)) {
       echo "<option value='0'>All Category</option>";
    }else{
       $strgetstoreid = "Select term_id From wp_terms Where slug='".$storeslug."'";
    $querygetstoreid = mysqli_query($conn, $strgetstoreid);
    while($row=mysqli_fetch_array($querygetstoreid))
     {
      $storeid=$row['term_id'];
     }
    $strSQL = "Select term_id From wp_term_taxonomy Where parent='".$storeid."'AND count !=0";
    $query = mysqli_query($conn, $strSQL);
    while($row=mysqli_fetch_array($query))
     {
       $string .= $row[$i].',';
     }
    $array=array_map('intval', explode(',', $string));
    $array = implode("','",$array);
    $strSQLcat= "Select name,slug From wp_terms Where term_id IN ('".$array."')";
    $querycat = mysqli_query($conn, $strSQLcat);
    echo "<option value='0'>All Category</option>";
     while($row=mysqli_fetch_array($querycat))
     {
       echo "<option value='".$row['slug']."'>".$row['name']."</option>";
     }
    }
        unset($_POST['storeslug']);
}
?>
```
1. open myjs.js file and paste this code. this code handle search function and send the value selected from dropdown to fetch-data.php to display the data on next dropdown.

 ```bash
 var city = document.getElementById("my_city");
 var cityoption;
 var suburb = document.getElementById("suburb");
 //var suburboption;
 var store = document.getElementById("store");
 //var storeoption;
 var category=document.getElementById("category");
 //var categoryoption;
 var btnseach= document.getElementById("btnseach");


function keep_dropdown_data()
{
  //alert("aaaaaa");
  fetch_suburb(city.value);
  // fetch_store(suburb.value);
  // fetch_category(store.value);
}
function fetch_suburb(val)
{
  cityoption=city.options[city.selectedIndex].innerHTML;
   $.ajax({
     type: 'post',
     url: '../wp-content/themes/emmet-lite-child/fetch_data.php',
     data: {cityid: val},
     success: function (response) {
       suburb.innerHTML=response; 
     }
   });
    
}
function fetch_store(val)
{
  suburboption=suburb.options[suburb.selectedIndex].text;
   $.ajax({
     type: 'post',
     url: '../wp-content/themes/emmet-lite-child/fetch_data.php',
     data: {suburbslug: val},
     success: function (response) {
       store.innerHTML=response; 

     }
   });
    
}
function fetch_category(val){
  //storeoption=store.options[store.selectedIndex].text;
   $.ajax({
     type: 'post',
     url: '../wp-content/themes/emmet-lite-child/fetch_data.php',
     data: {storeslug: val},
     success: function (response) {
       category.innerHTML=response; 

     }
   });
}

function search()
{
  if(city.value==0 && suburb.value==0&&store.value==0 && category.value==0){
    alert(cityoption);
    window.location.href = '../shop';
  }else if(category.value!=0){
    alert(category.value);
    window.location.href = '../shop/?swoof=1&location='+category.value;
  }else if(store.value!=0){
    alert(store.value);
    window.location.href = '../shop/?swoof=1&location='+store.value;
  }else if(suburb.value!=0){
    alert(suburb.value);
    window.location.href = '../shop/?swoof=1&location='+suburb.value;
  }else{
      alert(cityoption);
    window.location.href = '../shop/?swoof=1&location='+cityoption;  
  }
}
```
1. Usage > paste this shortcode [show_my_search] to a post or page to display the search form.

    



