

# Restaurant Management Simulation

A console-based restaurant management system that tracks orders, calculates waiter commissions, and provides comprehensive sales analytics. This project simulates real-world restaurant operations with a focus on order processing and financial reporting.

## Features

### Order Management
- **Dual Order Types:** Support for both **Take-out** and **Dine-in** orders
- **Order Tracking:** Each order is timestamped and assigned to a specific waiter
- **Menu System:** Flexible menu structure with configurable items and prices
- **Order Modification:** Add, remove, or modify items within orders

### Commission System
- **Individual Waiter Tracking:** Each waiter maintains their own sales ledger
- **Configurable Commission Rates:** Set different commission percentages per waiter or order type
- **Real-time Commission Calculation:** Automatic commission calculation as orders are processed
- **Performance Metrics:** Track each waiter's total sales and earned commissions

### Sales Analytics
- **Real-time Dashboard:** Live updating sales totals across all metrics
- **Comprehensive Reporting:**
  - Total restaurant revenue
  - Breakdown by order type (Take-out vs Dine-in)
  - Individual waiter performance reports
  - Hourly/daily sales summaries
- **Financial Overview:** Track gross sales, total commissions paid, and net revenue

## System Architecture

### Core Classes
- **`Restaurant`**: Main controller class that orchestrates all operations
- **`Order`**: Base order class with derived classes:
  - `DineInOrder`: Tracks table numbers, waiter assignments
  - `TakeOutOrder`: Manages pickup times and customer information
- **`Waiter`**: Tracks individual waiter sales, commissions, and performance
- **`Menu`**: Manages available items, categories, and pricing
- **`MenuItem`**: Represents individual food/drink items with prices
- **`SalesReport`**: Generates comprehensive sales analytics

### Key Relationships
```
Restaurant → manages → Multiple Waiters
Waiter → processes → Multiple Orders
Order → contains → Multiple MenuItems
SalesReport → aggregates → All Order Data
```

## Commission Calculation

The system supports flexible commission structures:

```cpp
// Example Commission Calculation
double calculateCommission(Order order, Waiter waiter) {
    return order.getTotal() * waiter.getCommissionRate();
}
```

**Features:**
- Different commission rates per waiter (e.g., senior vs junior staff)
- Variable rates based on order type (Dine-in vs Take-out)
- Bonus commissions for high-value orders
- Daily/weekly commission caps

## Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/restaurant-simulation.git
   cd restaurant-simulation
   ```

2. **Compile the project:**
   ```bash
   g++ -std=c++17 -o restaurant main.cpp Restaurant.cpp Order.cpp Waiter.cpp Menu.cpp SalesReport.cpp
   ```

3. **Run the simulation:**
   ```bash
   ./restaurant
   ```

## Usage Examples

### Creating Orders
```bash
# Dine-in order
Create Order → Dine-in → Waiter: John → Table 5
Add Item: Burger $12.99
Add Item: Coke $2.50
Finalize Order

# Take-out order  
Create Order → Take-out → Customer: Alice
Add Item: Pizza $15.99
Set Pickup Time: 18:30
```

### Viewing Reports
```bash
Main Menu → Reports
1. Today's Total Sales: $1,250.75
2. Order Type Breakdown:
   - Dine-in: $980.50 (78.4%)
   - Take-out: $270.25 (21.6%)
3. Waiter Performance:
   - John: $650.00 sales, $32.50 commission
   - Sarah: $330.50 sales, $16.53 commission
```

## Sample Output

```
=== RESTAURANT SALES DASHBOARD ===
Total Sales: $1,845.25
Total Orders: 47
- Dine-in: 32 orders ($1,420.75)
- Take-out: 15 orders ($424.50)

=== WAITER COMMISSIONS ===
John Doe:
  Total Sales: $850.00
  Commission (5%): $42.50
  Orders Served: 18

Sarah Smith:
  Total Sales: $570.75  
  Commission (4%): $22.83
  Orders Served: 14
```

## Project Structure

```
restaurant-simulation/
├── src/
│   ├── main.cpp              # Program entry point
│   ├── Restaurant.h/cpp      # Main controller class
│   ├── Order.h/cpp           # Base order class
│   ├── DineInOrder.h/cpp     # Dine-in specific orders
│   ├── TakeOutOrder.h/cpp    # Take-out specific orders
│   ├── Waiter.h/cpp          # Waiter management
│   ├── Menu.h/cpp            # Menu management
│   ├── MenuItem.h/cpp        # Individual menu items
│   └── SalesReport.h/cpp     # Reporting and analytics
├── data/
│   ├── menu_items.csv        # Menu configuration
│   └── waiters.csv           # Waiter database
├── README.md
└── Makefile
```

## Future Enhancements

- **Database Integration**: Persistent storage for orders and sales data
- **GUI Interface**: Graphical user interface for easier operation
- **Inventory Management**: Track ingredient usage and stock levels
- **Table Management**: Assign and track table occupancy
- **Advanced Analytics**: Sales trends, popular items, peak hour analysis
- **Multi-shift Support**: Track sales across different shifts
- **Customer Database**: Loyalty programs and customer preferences

## Technical Details

- **Language**: C++
- **Data Structures**: Vectors, Maps, Classes, Inheritance
- **File Handling**: CSV-based data persistence
- **Algorithms**: Sorting, searching, statistical calculations

## License

This project is licensed under the MIT License


Review at: https://preview--waiter-wonderland-57.lovable.app/
