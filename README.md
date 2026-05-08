# OOP Shop Inventory-management-system-C++


---

## Project Structure

```
shop_inventory/
│
├── include/
│   ├── Product.h          # Abstract base class — encapsulation & abstraction
│   ├── ProductTypes.h     # ElectronicsProduct, FoodProduct, ClothingProduct
│   └── Inventory.h        # Inventory manager — composition & modularity
│
├── src/
│   ├── Product.cpp        # Base class implementation
│   ├── ProductTypes.cpp   # Subclass implementations
│   └── Inventory.cpp      # Inventory logic
│
└── main.cpp               # Full demo simulation — run this
```

---

| Concept | Where |
|---|---|
| **Encapsulation** | Private `_price`, `_quantity` etc., exposed via getters/setters with validation |
| **Abstraction** | `Product` defines the interface; subclasses handle specifics |
| **Inheritance** | `ElectronicsProduct`, `FoodProduct`, `ClothingProduct` extend `Product` |
| **Polymorphism** | `getDiscount()` and `display()` overridden per product type |
| **Composition** | `Inventory` owns a collection of `shared_ptr<Product>` objects |
| **Smart Pointers** | `std::shared_ptr` used throughout — no raw `new`/`delete` |
| **Operator Overloading** | `<<`, `<`, `==` overloaded on `Product` |

---

##  Product Types

### Electronics
- **5% discount** on all electronics
- Stores warranty period in months

### Food
- **15% discount** for perishable items, **5%** for non-perishable
- Tracks expiry date

### Clothing
- **20% discount** when on seasonal sale, otherwise no discount
- Tracks brand and size

---

## Tech Features

- Add, remove, restock, and sell products
- Graceful error handling for over-selling and invalid IDs
- Low stock alert (triggers when quantity < 5)
- Search by name (case-insensitive)
- Filter by category
- Price updates with before/after display
- Full inventory summary report with total stock value

---

##  How to Compile & Run

```bash
#
git clone https://github.com/ianmajango-ux/shop-inventory-manager.git
cd shop-inventory-manager

# Compile
g++ -std=c++17 src/*.cpp main.cpp -Iinclude -o shop

# Run
./shop
```

---

##  Sample Output

```
=======================================================
   C++ OOP SHOP INVENTORY MANAGER
   by Ian Alfred Majango
=======================================================

  ✔ Added: [101] Samsung TV 43" | Electronics | KES 42750.00 | Qty: 8
  ✔ Sold 2x 'Samsung TV 43"' | Revenue: KES 85500.00
  ✘ Cannot sell 5 unit(s) of 'Men's Polo Shirt'. Only 1 in stock.
  ⚠ LOW STOCK ALERT — 2 item(s) need restocking

  INVENTORY SUMMARY
  Total products   : 8
  Total stock value: KES 384,341.00
  Low stock items  : 1
```

---

##  Key Design Decisions

- **Abstract base class** — `Product` cannot be instantiated directly; forces correct subclassing
- **Pure virtual functions** — `getType()` and `getDiscount()` must be implemented by every subclass
- **Smart pointers** — `std::shared_ptr<Product>` enables polymorphism without memory leaks
- **Single Responsibility** — `Inventory` manages the collection; `Product` manages its own data
- **Open/Closed Principle** — new product types can be added by subclassing `Product` with zero changes to `Inventory`

---

##  

**Ian Alfred Majango**  
Dics Information & Cybersecurity — Riara University  
GitHub: [github.com/ianmajango](https://github.com/ianmajango-ux)

