
# Inventory Management System

## Prerequisites

Before you begin, ensure you have met the following requirements:

- **Go**: Make sure you have Go installed on your local machine. You can download and install it from [here](https://golang.org/dl/).

- **Docker**: If you prefer to run the application using Docker, make sure you have Docker installed on your machine. You can download and install Docker Desktop from [here](https://www.docker.com/products/docker-desktop).

## Local Development

To run the application locally, follow these steps:

1. Clone the repository: 

   ```bash
   git clone https://github.com/your_username/your_repo.git

2. CD to repo and download the project dependencies
   ```bash
   go mod tidy && go mod vendor

3. Start the docker container by running the following cmd
   ```bash
   docker-compose up -d

4. Now start the app server by following cmd
   ```bash
   go run main.go
   
## Below is the API Spec
   
### Create Supplier API
```curl
curl --location 'localhost:8080/suppliers' \
--header 'Content-Type: application/json' \
--data '{
    "name": "lucky_1",
    "phoneNumber": "12345678"
}'
```
![Screenshot 2024-05-23 at 5.13.41 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_sXTU4U%2FScreenshot%202024-05-23%20at%205.13.41%E2%80%AFPM.png)

### Update Supplier API
```curl
curl --location --request PUT 'localhost:8080/suppliers/{supplier_id}' \
--header 'Content-Type: application/json' \
--data '{
    "name": "lucky_barkane",
    "phoneNumber": "12345678"
}'
```
![Screenshot 2024-05-23 at 5.15.12 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_mo7PX7%2FScreenshot%202024-05-23%20at%205.15.12%E2%80%AFPM.png)

### Create Product API
```curl
curl --location 'localhost:8080/products' \
--header 'Content-Type: application/json' \
--data '{
    "name": "Product_1",
    "supplier": {
        "id": 14
    },
    "price": 10.99,
    "stockQuantity": 12,
    "images": [
        {
            "name": "Product_Image_1",
            "data": "DAIYFw0="
        },
        {
            "id": 12,
            "name": "Product_Image_2",
            "data": "DAIYFw0="
        }
    ]
}'
```
![Screenshot 2024-05-23 at 5.20.30 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_6vTBM3%2FScreenshot%202024-05-23%20at%205.20.30%E2%80%AFPM.png)

### Update Product API
```curl
curl --location --request PUT 'localhost:8080/products/{product_id}' \
--header 'Content-Type: application/json' \
--data '{
    "name": "New Product Name",
    "supplier": {
        "id": 14
    },
    "images": [
        {
            "id": 13,
            "name": "new product image 1",
            "data": "DAIYFw0="
        },
        {
            "id": 14,
            "name": "new product image 2",
            "data": "DAIYFw0="
        }
    ]
}'
```
![Screenshot 2024-05-23 at 5.29.32 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_nBhjsh%2FScreenshot%202024-05-23%20at%205.29.32%E2%80%AFPM.png)


### Get Product By Product ID API
```curl
curl --location 'localhost:8080/products/{product_id}'
```
![Screenshot 2024-05-23 at 5.31.02 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_U6nnD4%2FScreenshot%202024-05-23%20at%205.31.02%E2%80%AFPM.png)

### Get Product All Products
```curl
curl --location --request POST 'localhost:8080/products/list' \
--data ''
```
![Screenshot 2024-05-23 at 5.25.00 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_5cyLIB%2FScreenshot%202024-05-23%20at%205.25.00%E2%80%AFPM.png)


### Get Product With Supplier Filter
```curl
curl --location --request POST 'localhost:8080/products/list' \
--data ''
```
![Screenshot 2024-05-23 at 6.12.53 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_U0E887%2FScreenshot%202024-05-23%20at%206.12.53%E2%80%AFPM.png)

### Get Product With Price Filter
```curl
curl --location 'localhost:8080/products/list' \
--header 'Content-Type: application/json' \
--data '{
    "price":{
        "min":10,
        "max":11
    }
}'
```
![Screenshot 2024-05-23 at 6.14.00 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_DGSxL1%2FScreenshot%202024-05-23%20at%206.14.00%E2%80%AFPM.png)

### Get Products With Price and Supplier Filter
```curl
curl --location 'localhost:8080/products/list' \
--header 'Content-Type: application/json' \
--data '{
   "supplierId": 5,
    "price":{
        "min":10,
        "max":11
    }
}'
```
![Screenshot 2024-05-23 at 6.14.48 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_u5xwNg%2FScreenshot%202024-05-23%20at%206.14.48%E2%80%AFPM.png)

### Get Product By Product ID API
```curl
curl --location --request PUT 'localhost:8080/products/{product_id}/stocks' \
--header 'Content-Type: application/json' \
--data '{
   "stockQuantity": 121
}'
```
![Screenshot 2024-05-23 at 5.32.12 PM.png](..%2F..%2F..%2F..%2F..%2F..%2F..%2Fvar%2Ffolders%2F7s%2Fp_r2wsbj6cg5wdx1clcxvy9h0000gr%2FT%2FTemporaryItems%2FNSIRD_screencaptureui_XLB3Vb%2FScreenshot%202024-05-23%20at%205.32.12%E2%80%AFPM.png)

