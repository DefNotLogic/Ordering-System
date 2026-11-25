# Ordering-System
POs Ordering sytem

# ==========================================
# MINI STORE - POS ORDERING SYSTEM
# ==========================================

products = {
    1: {"name": "Burger", "price": 50.00},
    2: {"name": "Fries", "price": 35.00},
    3: {"name": "Soft Drink", "price": 25.00}
}

store_name = "MINI STORE"
orders = []

print("=" * 45)
print(" WELCOME TO", store_name)
print(" POS ORDERING SYSTEM")
print("=" * 45)

# PRODUCT MENU
print("\nPRODUCT MENU")
print("-" * 45)

for number, product in products.items():
    print(f"[{number}] {product['name']:<15} PHP {product['price']:.2f}")

print("-" * 45)

# CUSTOMER ORDER
while True:
    try:
        choice = int(input("\nEnter product number (1-3): "))

        if choice not in products:
            print("Invalid product number. Try again.")
            continue

        quantity = int(input("Enter quantity: "))

        if quantity <= 0:
            print("Quantity must be greater than zero.")
            continue

        selected_product = products[choice]

        name = selected_product["name"]
        price = selected_product["price"]
        subtotal = price * quantity

        # STORE ORDER INFORMATION
        orders.append({
            "name": name,
            "quantity": quantity,
            "price": price,
            "subtotal": subtotal
        })

        print(f"\nAdded: {name} x {quantity}")
        print(f"Subtotal: PHP {subtotal:.2f}")

    except ValueError:
        print("Invalid input. Please enter a number.")
        continue

    # ASK FOR ANOTHER ORDER
    another = input("\nOrder another product? (yes/no): ").lower()

    if another not in ["yes", "y"]:
        break

# ==========================================
# RECEIPT GENERATION
# ==========================================

print("\n")
print("=" * 55)
print(" RECEIPT")
print(f" {store_name}")
print("=" * 55)

print(f"{'Product':<15}{'Qty':<7}{'Price':<12}{'Subtotal':<12}")
print("-" * 55)

total = 0

for order in orders:
    print(
        f"{order['name']:<15}"
        f"{order['quantity']:<7}"
        f"{order['price']:<12.2f}"
        f"{order['subtotal']:<12.2f}"
    )

    total += order["subtotal"]

print("-" * 55)
print(f"{'TOTAL AMOUNT:':<34} PHP {total:.2f}")
print("=" * 55)
print(" THANK YOU FOR YOUR ORDER!")
print("=" * 55)
