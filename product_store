class Product {
  String name;
  double basePrice;
  int stockQuantity;
  double discount;

  Product({
    required this.name,
    required this.basePrice,
    this.stockQuantity = 0,
    this.discount = 0.0,
  });

  Product.onSale({
    required this.name,
    required this.basePrice,
    this.stockQuantity = 0,
  }) : discount = 0.10;

  Product.bulk({
    required this.name,
    required this.basePrice,
    required int stockQuantity,
    required int packageSize,
    this.discount = 0.0,
  }) : stockQuantity = stockQuantity * packageSize;

  double get discountedPrice {
    if (discount > 0) {
      return basePrice * (1 - discount);
    }

    return basePrice;
  }

  bool get isLowStock => stockQuantity < 10;

  void printDetails() {
    print('Product: $name');
    print('Price: \$${discountedPrice.toStringAsFixed(2)}');
    print('Stock: $stockQuantity');
    print('Low stock: $isLowStock');
    print('');
  }
}

class Bundle {
  List<Product> products;

  Bundle({required this.products});

  double get totalPrice {
    return products.fold(
      0.0,
      (total, product) => total + product.discountedPrice,
    );
  }
}

void main() {
  Product regularProduct = Product(
    name: 'Headphones',
    basePrice: 50.00,
    stockQuantity: 5,
  );

  Product saleProduct = Product.onSale(
    name: 'Keyboard',
    basePrice: 100.00,
    stockQuantity: 20,
  );

  Product bulkProduct = Product.bulk(
    name: 'Water Bottle',
    basePrice: 10.00,
    stockQuantity: 4,
    packageSize: 6,
  );

  regularProduct.printDetails();
  saleProduct.printDetails();
  bulkProduct.printDetails();

  Bundle bundle = Bundle(
    products: [regularProduct, saleProduct, bulkProduct],
  );

  print('Bundle total: \$${bundle.totalPrice.toStringAsFixed(2)}');
}
