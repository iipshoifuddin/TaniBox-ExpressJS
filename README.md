# Tani Box ( BackEnd )

TaniBox is an Android application that (movement) in the Argocultural, that allows farmers to sell fresh fruits and vegetables directly.


## pre-Instalation

before installing this application, first install Node JS

_https://nodejs.org/en/download/



second create tables in your database like this :
```PHP

CREATE TABLE `buyer` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `user_id` int(11) NOT NULL,
  `province` varchar(5) DEFAULT '',
  `province_name` varchar(45) DEFAULT '',
  `city` varchar(5) DEFAULT '',
  `city_name` varchar(45) DEFAULT '',
  `kecamatan` varchar(45) DEFAULT '',
  `address` varchar(50) DEFAULT '',
  `postal_code` varchar(6) DEFAULT '',
  `phone` varchar(15) DEFAULT '',
  `photo` varchar(50) DEFAULT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `date_updated` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=24 DEFAULT CHARSET=latin1;


CREATE TABLE `cart` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `unit_price` int(11) NOT NULL,
  `qty` int(11) NOT NULL,
  `total` int(11) NOT NULL,
  `product_id` int(11) NOT NULL,
  `user_id` int(11) NOT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `date_updated` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4;


CREATE TABLE `category` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `date_updated` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4;


CREATE TABLE `notifications` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `receive_id` int(11) DEFAULT NULL,
  `sender_id` int(11) DEFAULT NULL,
  `message` text,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;


CREATE TABLE `payment` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `id_transaction` varchar(255) NOT NULL,
  `va_number` varchar(255) DEFAULT NULL,
  `bank` varchar(255) DEFAULT NULL,
  `transaction_time` varchar(255) DEFAULT NULL,
  `transaction_status` varchar(255) DEFAULT NULL,
  `transaction_id` varchar(255) DEFAULT NULL,
  `status_message` varchar(255) DEFAULT NULL,
  `status_code` varchar(255) DEFAULT NULL,
  `signature_key` text,
  `settlement_time` varchar(255) DEFAULT NULL,
  `payment_type` varchar(255) DEFAULT NULL,
  `merchant_id` varchar(255) DEFAULT NULL,
  `gross_amount` varchar(255) DEFAULT NULL,
  `fraud_status` varchar(255) DEFAULT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `date_updated` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=13 DEFAULT CHARSET=latin1;


CREATE TABLE `photo_product` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `photo` varchar(255) NOT NULL,
  `product_id` int(11) NOT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `date_updated` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=25 DEFAULT CHARSET=utf8mb4;


CREATE TABLE `products` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `unit` int(11) DEFAULT NULL,
  `price` int(11) DEFAULT NULL,
  `stock` int(11) DEFAULT NULL,
  `description` text,
  `category_id` int(11) DEFAULT NULL,
  `user_id` int(11) DEFAULT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `date_updated` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=30 DEFAULT CHARSET=utf8mb4;


CREATE TABLE `seller` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `user_id` int(11) NOT NULL,
  `name_of_store` varchar(45) DEFAULT '',
  `address1` varchar(50) DEFAULT '',
  `province1` varchar(45) DEFAULT '',
  `province1_name` varchar(45) DEFAULT '',
  `city1` varchar(45) DEFAULT '',
  `city1_name` varchar(45) DEFAULT '',
  `kecamatan1` varchar(45) DEFAULT '',
  `postal_code1` varchar(6) DEFAULT '',
  `address2` varchar(50) DEFAULT '',
  `province2` varchar(45) DEFAULT '',
  `province2_name` varchar(45) DEFAULT '',
  `city2` varchar(45) DEFAULT '',
  `city2_name` varchar(45) DEFAULT '',
  `kecamatan2` varchar(45) DEFAULT '',
  `postal_code2` varchar(6) DEFAULT '',
  `phone` varchar(12) DEFAULT '',
  `photo_profile` varchar(50) DEFAULT '',
  `photo_store` varchar(50) DEFAULT '',
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `date_updated` timestamp NULL DEFAULT NULL,
  `description` text,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=latin1;


CREATE TABLE `transaction` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `seller_user_id` int(11) NOT NULL,
  `buyer_user_id` int(11) DEFAULT NULL,
  `invoice` varchar(200) NOT NULL,
  `shipment_amount` int(11) NOT NULL,
  `transaction_amount` int(11) NOT NULL,
  `total_amount` int(11) NOT NULL,
  `status` varchar(10) DEFAULT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `date_updated` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;


CREATE TABLE `transaction_detail` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `id_transaction` int(11) NOT NULL,
  `id_product` int(11) NOT NULL,
  `qty` int(11) NOT NULL,
  `price` int(11) NOT NULL,
  `total_price` int(11) NOT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `date_updated` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;


CREATE TABLE `transaction_shipment` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `id_transaction` int(11) DEFAULT NULL,
  `seller_address` varchar(45) DEFAULT NULL,
  `seller_kecamatan` varchar(45) DEFAULT NULL,
  `seller_postal_code` varchar(6) DEFAULT NULL,
  `seller_province` varchar(5) DEFAULT NULL,
  `seller_province_name` varchar(45) DEFAULT NULL,
  `seller_city` varchar(5) DEFAULT NULL,
  `seller_city_name` varchar(45) DEFAULT NULL,
  `buyer_address` varchar(45) DEFAULT NULL,
  `buyer_kecamatan` varchar(45) DEFAULT NULL,
  `buyer_postal_code` varchar(6) DEFAULT NULL,
  `buyer_province` varchar(5) DEFAULT NULL,
  `buyer_province_name` varchar(45) DEFAULT NULL,
  `buyer_city` varchar(5) DEFAULT NULL,
  `buyer_city_name` varchar(45) DEFAULT NULL,
  `courier` varchar(5) DEFAULT NULL,
  `courier_service` varchar(5) DEFAULT NULL,
  `weight` int(11) DEFAULT NULL,
  `shipment_amount` int(11) NOT NULL,
  `date_created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `date_updated` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;


CREATE TABLE `user` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(100) DEFAULT NULL,
  `email` varchar(100) DEFAULT NULL,
  `password` varchar(100) DEFAULT NULL,
  `role` varchar(100) DEFAULT NULL,
  `OTP` int(11) DEFAULT NULL,
  `date_created` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `date_updated` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=51 DEFAULT CHARSET=latin1;


CREATE TABLE `wishlist` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `product_id` int(11) NOT NULL,
  `user_id` int(11) NOT NULL,
  `date_created` timestamp NULL DEFAULT CURRENT_TIMESTAMP,
  `date_updated` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=12 DEFAULT CHARSET=utf8mb4;


```


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
