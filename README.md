# Tani Box ( BackEnd )

TaniBox is an Android application that (movement) in the Argocultural, that allows farmers to sell fresh fruits and vegetables directly.


## pre-Instalation

before installing this application, first install Node JS

_https://nodejs.org/en/download/

## Installation

OS X & Linux & Windows:

```sh
npm init
```

```sh
npm install
```


## Development setup

Before using this application, first enter the project folder _your_project and create a dotEnv file:

Linux :
```sh
cp example.ENV .ENV
```

Windows :
```sh
copy example.ENV .ENV /a
```

then edit the file as follows :
```sh
DB_HOST = YOUR_HOSTNAME
DB_USER = YOUR_USER
DB_PASSWORD = YOUR_PASSWORD
DB_NAME = YOUR_DB_NAME

PORT = 4000
JWT_KEY = secretkey
SHIPMENT_KEY = {cek di api key eksternal}

```


## RUNNING

To run this application, you must run the following command :

```sh
npm start
```

## USE ENDPOINT

To use json from a database, use the endpoints as follows :

```sh
( User Register )
METHOD POST : http://YOUR_SERVER:4000/api/v1/auth/register
REQUEST :
          - name from body
          - email from body 
          - role from body (dengan value pembeli atau penjual)

( User Login ) 
METHOD POST : http://YOUR_SERVER:4000/api/v1/auth/login
REQUEST : 
      - email from body 
	  - password from body

( Forgot Password ) 
METHOD POST : http://YOUR_SERVER:4000/api/v1/auth/forgot-password
REQUEST : 
        - email from body
        - OTP from body


( Update Password ) 
METHOD PATCH : http://YOUR_SERVER:4000/api/v1/auth/update-password
REQUEST :
      - email from body
	  - password from body 
      - password_confirmation from body

list API Products : 

( Get Product )
METHOD GET  : http://YOUR_SERVER:4000/api/v1/products?search=''&limit=''&sort=''&sortBy=''
REQUEST PARAMS :  
         - search
	     - limit
	     - sort
		 - sortBy

( Get Single Product ) 
METHOD GET : http://YOUR_SERVER:4000/api/v1/products/single-product
REQUEST : - product_id from body

( Tambah Product )
METHOD POST : http://YOUR_SERVER:4000/api/v1/products
REQUEST : 
          - name from body
          - description from body 
          - stock from body 
	      - unit from body
	      - category_id from body 
          - user_id from body 
	      - photo from input file 
          - price from input file 



( Update Product )
METHOD PATCH : http://YOUR_SERVER:4000/api/v1/products/update-product
REQUEST : 
      - product_id from body
	  - name from body
      - description from body 
      - stock from body 
	  - unit from body
	  - category_id from body 
      - user_id from body 
	  - photo from input file
      - price from body

( Hapus Product )
METHOD DELETE : http://YOUR_SERVER:4000/api/v1/products/delete-product
REQUEST : - product_id from body

( Notifications )
METHOD POST : http://YOUR_SERVER:4000
REQUEST : 
       - receiver_id from body 



( Keranjang ) 

( Get Cart )
METHOD GET : http://YOUR_SERVER:4000/api/v1/products/cart

( Get Cart By User ID )
METHOD GET : http://YOUR_SERVER:4000/api/v1/products/cart-by-user-id
REQUEST : - user_id from body

( Tambah ) 
METHOD POST : http://YOUR_SERVER:4000/api/v1/products/add-cart
REQUEST : 
      - product_id from body 
	  - user_id from body
	  - qty from body

( Hapus ) 
METHOD DELETE : http://YOUR_SERVER:4000/api/v1/products/delete-cart
REQUEST : - cart_id from body

( Update ) 
METHOD PATCH : http://YOUR_SERVER:4000/api/v1/products/update-cart
REQUEST : 
      - cart_id from body 
	  - qty from body
      - unit_price from body
	  - product_id
	  - user_id

( Wishlist )

( Get Data ) 
METHOD GET : http://YOUR_SERVER:4000/api/v1/products/wishlist
 
( Tambah ) 
METHOD POST : http://YOUR_SERVER:4000/api/v1/products/wishlist
REQUEST : 
          - product_id from body
          - user_id from body

( Hapus )
METHOD DELETE : http://YOUR_SERVER:4000/api/v1/products/delete-wishlist
REQUEST : 
      - product_id from body 
	  - user_id from body


========={{ profile penjual & pembeli }}

( Get Profile By User ID - Buyer and Seller )
METHOD GET : http://YOUR_SERVER:4000/api/v1/profile
REQUEST : - user_id from body

( Delete Profile By User ID - Buyer and Seller )
METHOD DELETE : http://YOUR_SERVER:4000/api/v1/profile
REQUEST : - user_id from body

( Add Profile By User ID - Buyer )
METHOD POST : http://YOUR_SERVER:4000/api/v1/profile
( Update Profile By User ID - Buyer )
METHOD PUT : http://YOUR_SERVER:4000/api/v1/profile
REQUEST : 
    user_id: from body
    name: from body
    province: from body 
    city: from body
    kecamatan: from body
    address: from body
    postal_code: from body
    phone: from body
    province_name: from body
    city_name: from body

( Add Profile By User ID - Seller )
METHOD POST : http://YOUR_SERVER:4000/api/v1/profile
( Update Profile By User ID - Seller )
METHOD PUT : http://YOUR_SERVER:4000/api/v1/profile --- 404 http://YOUR_SERVER:4000/api/v1/profile
REQUEST : 
    user_id: from body
    name_of_seller: from body
    name_of_store: from body
    address1: from body
    province1: from body
    province1_name: from body
    city1: from body
    city1_name: from body
    kecamatan1: from body
    postal_code1: from body
    address2: from body
    province2: from body
    province2_name: from body
    city2: from body
    city2_name: from body
    kecamatan2: from body
    postal_code2: from body
    phone: from body

========={{ shipment - include province & city }}

( Get all Province - shipment )
METHOD GET : http://YOUR_SERVER:4000/api/v1/shipment/province

( Get single Province - shipment )
METHOD GET : http://YOUR_SERVER:4000/api/v1/shipment/province
REQUEST : - province_id from body

( Get all City - shipment )
METHOD GET : http://YOUR_SERVER:4000/api/v1/shipment/city

( Get City by province - shipment )
METHOD GET : http://YOUR_SERVER:4000/api/v1/shipment/city
REQUEST : - province_id from body

( Get single City - shipment )
METHOD GET : http://YOUR_SERVER:4000/api/v1/shipment/city
REQUEST : - city_id from body

( Get all courier - shipment )
METHOD GET : http://YOUR_SERVER:4000/api/v1/shipment/courier

( Get Cost - shipment )
METHOD POST : http://YOUR_SERVER:4000/api/v1/shipment/cost
REQUEST : 
    origin_city: from body
    destination_city: from body
    weight: from body (1700)
    courier: from body
```
