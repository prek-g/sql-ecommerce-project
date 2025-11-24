Table category {
  category_id int [pk]
  category_name varchar(20)
}

Table customers {
  customer_id int [pk]
  first_name varchar(15)
  last_name varchar(15)
  state varchar(20)
  address varchar(5)
}

Table sellers {
  seller_id int [pk]
  seller_name varchar(25)
  origin varchar(10)
}

Table products {
  product_id int [pk]
  product_name varchar(50)
  price numeric
  cogs numeric
  category_id int
}

Table orders {
  order_id int [pk]
  order_date date
  customer_id int
  seller_id int
  order_status varchar(15)
}

Table order_items {
  order_item_id int [pk]
  order_id int
  product_id int
  quantity int
  price_per_unit numeric
  total_sales numeric
}

Table payments {
  payment_id int [pk]
  order_id int
  payment_date date
  payment_status varchar(20)
}

Table shipping {
  shipping_id int [pk]
  order_id int
  shipping_date date
  return_date date
  shipping_providers varchar(25)
  delivery_status varchar(15)
}

Table inventory {
  inventory_id int [pk]
  product_id int
  stock int
  warehouse_id int
  last_stock_date date
}

Ref: products.category_id > category.category_id
Ref: orders.customer_id > customers.customer_id
Ref: orders.seller_id > sellers.seller_id
Ref: order_items.product_id > products.product_id
Ref: order_items.order_id > orders.order_id
Ref: payments.order_id > orders.order_id
Ref: shipping.order_id > orders.order_id
Ref: inventory.product_id > products.product_id
