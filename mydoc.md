# Table of Contents  
[ ](#) 
 * [Create child theme to modify theme without losing code when the theme updated](#create-child-theme-to-modify-theme-without-losing-code-when-the-theme-updated)  
 * [Css stylesheet for mobile ver](#css-stylesheet-for-mobile-ver)  
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
 * [Wordpress error : Request URL / not found on wampserver fix ](#fix-request-url-not-found-on-wampserver)
 * [Display product cat with thumbnail](#display-product-cat-on-widget-with-img)
 * [Css stylesheet for mobile ver](#css-stylesheet-for-mobile-ver)
 * [Add css style for mobile inside the {} + !important after the styling](#add-css-style-for-mobile-inside-the---important-after-the-styling)
 * [Sticky fb box sidebar](#sticky-fb-box-sidebar)
 * [Exit popup when user leave the site](#exit-popup-when-user-leave-the-site)
 * [Set font styling and color for whole site (h1, h2, p….)](#set-font-styling-and-color-for-whole-site-h1-h2-p)
 * [Popup display when scroll down](#popup-display-when-scroll-down)
 * [Increase website speed](#increase-website-speed)



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
1.	Create 2 menu with [woocommerce_my_account[ shortcode. My account and reg/login
2.	Add custom ccs name nav-login and nav-account.
3.	Make a custom link menu with a link of  /my-account/customer-logout  and name log out.
4.	Then add this code to function to display the menu depend on user have login or not.
5.	NOTE : thi code my not work with different theme cause they got different menu css style. eg. menu that use list item for menu then instead of .nav-login { display: none; }  try change it to li.nav-login a { display: none; }
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

  ```bash
  <?php
add_shortcode( 'show_my_search', 'mysearch' );
function mysearch()
{
  	include 'db_connect.php'; 
    $strSQL = "Select term_id From wp_term_taxonomy Where taxonomy='location' AND parent= 0 AND count !=0";
    $query = mysqli_query($conn, $strSQL);
    $string = '';
    $i = 0; 
     while($row=mysqli_fetch_array($query))
     {
       $string .= $row[$i].',';
     }
     $array=array_map('intval', explode(',', $string));
    $array = implode("','",$array);
    $strSQLcity = "Select name,term_id From wp_terms Where term_id IN ('".$array."')";
    $query_city = mysqli_query($conn, $strSQLcity);
// Execute the query.

          $output  ="<label class='searchlable' for='city'>City</label>";
          $output  .="<select class='searchdropdown' id='my_city' onchange='fetch_suburb(this.value);'>";
          $output .= "<option value='0'>All City</option>";
     while($row=mysqli_fetch_array($query_city))
     {
       // echo $row['name'];
       $output .= "<option value='".$row['term_id']."'>".$row['name']."</option>";
     }
      $output .= "</select> ";

	 	 $output  .="<label class='searchlable'  id='lblsuburb' for='suburb'>Suburb</label>";
	 	$output .="<select class='searchdropdown'  id='suburb' onchange='fetch_store(this.value);'>";
	 	$output .= "<option value='0'>All suburb</option>";
	  	$output .="</select>";  
	  $output  .="<label class='searchlable'  id='lblstore' for='store'>Store</label>";
	 $output .="<select class='searchdropdown'  id='store' onchange='fetch_category(this.value);'>";
	 $output .= "<option value='0'>All Store</option>";
	  $output .="</select>"; 
	 $output  .="<label class='searchlable'  id='lblcat'>Category</label>";
	  $output .="<select class='searchdropdown'  id='category' >";
	 $output .= "<option value='0'>All Category</option>";
	 $output .="</select><br>"; 
	  $output .="<button id='btnseach' onclick='search();' type='button'>Search</button> ";

           return $output;

}
add_action( 'wp_enqueue_scripts', 'emmet_script' );
function emmet_script()
{
	wp_enqueue_script( 'myjs',  get_template_directory_uri() . '/js/myjs.js',   array('jquery'),   '1.0', true );
  	wp_enqueue_script( 'jquery.js',  get_template_directory_uri() . '/js/jquery.js',   array('jquery'),   '1.0', true );
}
?>
 ```
 
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

# Woocomerce facebook login
use YITH WooCommerce Social Login

https://wordpress.org/plugins/yith-woocommerce-social-login/

# Get search keywork from Dave's WordPress Live Search save and display
    NOTE : this is a continue from the dropdown search ajax 
    https://github.com/tear123/mydoc/blob/master/mydoc.md#ajax-dropdown-search
    go and create those folder and files first.
1. go to wp-content\plugins\daves-wordpress-live-search/js/dwls-results.tpl and open it
1. add thi javascript to the end of the code out site </ul> and change www.yourdomain.com to your domain 
	```bash
	  <script type="text/javascript">
        $(document).ready(function () {
                            $("#dwls_search_results li").click(function() { 
                        var keyword=$(this).text().trim();
                        var keyword_slug=keyword.replace(" ","-");
                        //send keyword and check to see if need added or increase the count
                        $.ajax({
                        type: 'post',
                        url: myurl()+'fetch_data.php',
                        data: {keyword: keyword},
                        success: function (response) {
                                //alert("added");
                                 window.location.href="www.yourdomain.com/product/"+keyword_slug+"/";
                        }
                       
                });
                        
                });
        });
  </script>
	```

1. add this code to the theme functions.php.
  
  ```bash
   // get keywords from database
function show_keywords()
{
    include 'db_connect.php'; 
    $keyword_sql= "SELECT keyword FROM keyword_search ORDER BY count DESC LIMIT 10";
    $query=mysqli_query($conn,$keyword_sql);
    $output ="";
   while($row=mysqli_fetch_array($query))
   {
      $output .="<a href='".$url."".str_replace(' ', '-', $row['keyword'])."'>".$row['keyword']."</a><br>";
          
   }
    return $output;
}
   ```
 1. pase this function inside functions.php > this function use to retrieve the keywords from db and display it.
 
  ```bash
   // get keywords from database
function show_keywords()
{
    include 'db_connect.php'; 
    $keyword_sql= "SELECT keyword FROM keyword_search ORDER BY count DESC LIMIT 10";
    $query=mysqli_query($conn,$keyword_sql);
    $output ="";
   while($row=mysqli_fetch_array($query))
   {
      $output .="<a href='".$url."".str_replace(' ', '-', $row['keyword'])."'>".$row['keyword']."</a><br>";
          
   }
    return $output;
}
  ```
1. add this code to the fetch-data.php inside the if else loop.
 
  ```bash
else if(isset($_POST['keyword'])){
    $keyword=$_POST['keyword'];
    $keyword_sql= "SELECT * FROM keyword_search WHERE `keyword`='".$keyword."'";
    $query= mysqli_query($conn, $keyword_sql);
    //$keyword_sql="";
    if ($query && mysqli_num_rows($query) > 0){
        //keyword exist > ++count
         //$add_keyword_sql= "INSERT INTO keyword_search(keyword,count) VALUES ('".$keyword."',1)";
        $keyword_sql="UPDATE keyword_search SET count=count+1 WHERE `keyword` ='".$keyword."'";
         //$query= mysqli_query($conn, $add_keyword_sql);
         echo "update";
    }else{
        //keyowrd not exist > add
        $keyword_sql= "INSERT INTO keyword_search(keyword,count) VALUES ('".$keyword."',1)";
        echo "add new";
    }
    $runquery=mysqli_query($conn, $keyword_sql);
    echo "end";
    unset($_POST['keyword']);
}
  ```
1. add this code to the myjs.js file. replace  www.yourdomain.com iwth your domain.

  ```bash
function myurl()
{
  var url="www.yourdomain.com/wp-content/themes/sparkling-child/";
  return url;
}
  ```
# Fix request url not found on wampserver:
Left click on wampserver icon > Apache > Apache modules > tick rewrite_module
# Display product cat on widget with img:
Use pluggin : https://wordpress.org/plugins/xo10-woocommerce-categories-widget/ 
# Css stylesheet for mobile ver
Add this code to css
 ```css
 @media screen and (max-width: 885px) {}
 ```
# Add css style for mobile inside the {} + !important after the styling
 ```css
 .col-md-4{
        margin-top: 5%;
        width: 100% !important;  
    }
 ```
# Sticky fb box sidebar
 ```css
 	Aspexi Facebook Like Box Slider
	https://wordpress.org/plugins/aspexi-facebook-like-box/

 ```
# Exit popup when user leave the site
  ```css
	Yeloni Exit Popup
 ```
# Set font styling and color for whole site (h1, h2, p….)
  ```css
	Plugin: Easy Google fonts
	Link: https://en-nz.wordpress.org/plugins/easy-google-fonts/
 ```
# Popup display when scroll down
  ```css
	Scroll Triggered Boxes
 ```
# Increase website speed
 Install W3 Total Cache pluggin
 
  ```css
	Step 1:

If you’ve already installed W3 Total Cache simply head over to 
WordPress Dashboard » Performance » General Settings and Enable “Browser cache“

Enable browser cache in w3 total cache

Step 2:

Go to performance >> Browser Cache. Apply the following settings.
Browser Cache – General Settings

    Enable “Set Last-Modified header”
    Enable “Set expires header”
    Enable “Set cache control header”
    Disable “Set entity tag (eTag)”
    Enable “Set W3 Total Cache header”
    Enable “HTTP (gzip) compression”
    Disable “Prevent caching of objects after settings change”
    Disable “Do not process 404 errors for static objects“

Browser Cache – CSS & JS

    Enable “Set Last-Modified header”
    Enable “Set expires header”
    Expires header lifetime – 31536000 seconds (1 year)
    Enable “Set cache control header”
    Cache Control Policy: cache with max-age
    Disable “Set entity tag (eTag)”
    Enable “Set W3 Total Cache header”
    Enable “HTTP (gzip) compression”
    Disable “Prevent caching of objects after settings change “
    Disable “Disable cookies for static files “

Browser Cache – HTML and XML

    Enable “Set Last-Modified header”
    Enable “Set expires header”
    Expires header lifetime – 3600 seconds (1 hour)
    Enable “Set cache control header”
    Cache Control Policy: cache with max-age
    Disable “Set entity tag (eTag)”
    Enable “Set W3 Total Cache header”
    Enable “HTTP (gzip) compression”

Browser Cache – Media and other files

    Enable “Set Last-Modified header”
    Enable “Set expires header”
    Expires header lifetime – 31536000 seconds (1 year)
    Enable “Set cache control header”
    Cache Control Policy – cache with max-age
    Disable “Set the entity tag (eTag)”
    Enable “Set W3 Total Cache header”
    Enable “HTTP (gzip) compression”
    Disable “Prevent caching of objects after settings change” 
    Disable “Disable cookies for static files” 
 ```
 Edit .htaccess by adding
   ```css
	## EXPIRES CACHING ##
<IfModule mod_expires.c>
ExpiresActive On
ExpiresByType image/jpg "access 1 year"
ExpiresByType image/jpeg "access 1 year"
ExpiresByType image/gif "access 1 year"
ExpiresByType image/png "access 1 year"
ExpiresByType text/css "access 1 month"
ExpiresByType text/html "access 1 month"
ExpiresByType application/pdf "access 1 month"
ExpiresByType text/x-javascript "access 1 month"
ExpiresByType application/x-shockwave-flash "access 1 month"
ExpiresByType image/x-icon "access 1 year"
ExpiresDefault "access 1 month"
</IfModule>
## EXPIRES CACHING ##

<IfModule mod_gzip.c>
mod_gzip_on Yes
mod_gzip_dechunk Yes
mod_gzip_item_include file \.(html?|txt|css|js|php|pl)$
mod_gzip_item_include handler ^cgi-script$
mod_gzip_item_include mime ^text/.*
mod_gzip_item_include mime ^application/x-javascript.*
mod_gzip_item_exclude mime ^image/.*
mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
</IfModule>
 ```	
