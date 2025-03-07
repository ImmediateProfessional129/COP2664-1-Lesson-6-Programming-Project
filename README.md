# COP2664-1-Lesson-6-Programming-Project
This repository is a submission link for COP2664-1: Lesson 6 Programming Project

// This program is designed to operate as an electronic menu for a restaurant that displays the menu, allows the user to order food, and then displays the total cost of the order.

import Foundation // Imports the Foundation framework, which contains the necessary functions for the program to run.

struct MenuItem { // Defines a struct called MenuItem that contains the properties of a menu item.
    var name: String // Declares a property called name of type String.
    var price: Double // Declares a property called price of type Double.
    var category: String // Declares a property called category of type String.
}
struct Menu {
    var items: [MenuItem] = [ // Declares a property called items of type [MenuItem] and initializes it with an empty array.
        MenuItem(name: "Tacos", price: 3.80, category: "Food"), // Creates a MenuItem object with the name "Tacos", the price 3.80, and the category "Food".
        MenuItem(name: "Quesadillas", price: 11.90, category: "Food"), // Creates a MenuItem object with the name "Quesadillas", the price 11.90, and the category "
        MenuItem(name: "Mexican Coca-Cola", price: 3.85, category: "Drink"), // Creates a MenuItem object with the name "Mexican Coca-Cola", the price 3.85,
        MenuItem(name: "Chips & Salsa", price: 2.25, category: "Food"), // Creates a MenuItem object with the name "Chips & Salsa", the price 2.25, and the category "
        MenuItem(name: "Food Bowl", price: 14.30, category: "Food"), // Creates a MenuItem object with the name "Food Bowl", the price 14.30, and the category "
        MenuItem(name: "Flan", price: 4.50, category: "Dessert"), // Creates a MenuItem object with the name "Flan", the price 4.50, and the category "
        MenuItem(name: "Lemonade", price: 3.25, category: "Drink"), // Creates a MenuItem object with the name "Lemonade", the price 3.25, and the category "
        MenuItem(name: "Root Beer", price: 5.97, category: "Drink"), // Creates a MenuItem object with the name "Root Beer", the price 5.97, and the category "
        MenuItem(name: "Mini Churros with Chocolate Sauce", price: 5.59, category: "Dessert") // Creates a MenuItem object with the name "Mini Churros with Chocolate Sauce", the price 5.59
    ] // The items property is an array of MenuItem objects that contains the menu items for the restaurant.
}
struct Order { // Defines a struct called Order that contains the properties of an order.
    var items: [MenuItem] = [] // Declares a property called items of type [MenuItem] and initializes it with an empty array.
    var total: Double = 0.0 // Declares a property called total of type Double and initializes it with 0.0.
}
class Restaurant { // Defines a class called Restaurant that contains the properties and methods of a restaurant.
    var menu: Menu // Declares a property called menu of type Menu and initializes it with a Menu object.
    var order: Order // Declares a property called order of type Order and initializes it with an Order object.
    var discount: Double = 0.0 // Declares a property called discount of type Double and initializes it with 0.0.
    init(menu: Menu, order: Order, discount: Double) { // Initializes a new instance of the Restaurant class with the specified menu, order, and discount.
        self.menu = menu // Sets the value of the menu property to the value of the menu parameter.
        self.order = order // Sets the value of the order property to the value of the order parameter.
        self.discount = discount // Sets the value of the discount property to the value of the discount parameter.
    }
    func displayMenu() { // Defines a method called displayMenu that takes no parameters and has no return value.
        print("Menu:") // Prints the string "Menu:" to the console.
        for item in menu.items { // Iterates over each MenuItem object in the menu.items array.
            print("\(item.name) - $\(item.price)") // Prints the name and price of each MenuItem object to the console.
        }
    }
    func addItem(name: String) { // Defines a method called addItem that takes a String parameter called name and has no return value.
        for item in menu.items { 
            if item.name == name { // Checks if the name parameter matches the name of any MenuItem object in the menu.items array.
                order.items.append(item) // Adds the MenuItem object to the order.items array.
                order.total += item.price // Adds the price of the MenuItem object to the order.total property.
                print("\(item.name) added to order.") // Prints a message to the console indicating that the MenuItem object was added to the order.
                return // Exits the method.
            }
        }
        print("Item not found in menu.") // Prints a message to the console indicating that the specified item was not found in the menu.
    }
    func viewOrderTotal() { // Defines a method called viewOrderTotal that takes no parameters and has no return value.
        print("Order Total: $\(order.total)") // Prints the value of the order.total property to the console.
    }
    func applyDiscount() { // Defines a method called applyDiscount that takes no parameters and has no return value.
        if discount > 0 { // Checks if the value of the discount property is greater than 0.
            let discountedTotal = order.total - (order.total * discount) // Calculates the discounted total by subtracting the discount from the order.total property.
            print("Discount Applied: $\(discountedTotal)") // Prints the value of the discountedTotal property to the console.
        }
    }
    func viewItemsByCategory(category: String) { // Defines a method called viewItemsByCategory that takes a String parameter called category and has no return value.
        print("Items in \(category):") // Prints a message to the console indicating the category of the items.
        for item in menu.items { // Iterates over each MenuItem object in the menu.items array.
            if item.category == category { // Checks if the category parameter matches the category of any MenuItem object in the menu.items array.
                print("\(item.name) - $\(item.price)") // Prints the name and price of each MenuItem object in the specified category to the console.
            }
        }
    }
}
let menu = Menu() // Creates a new instance of the Menu class and assigns it to the menu constant.
let order = Order() // Creates a new instance of the Order class and assigns it to the order constant.
let restaurant = Restaurant(menu: menu, order: order, discount: 0.0) // Creates a new instance of the Restaurant class with the specified menu, order, and discount.

// Main program loop to display menu options and handle user input.
var running = true // Initializes a variable called running with the value true.
while running { // Starts a while loop that continues as long as the value of the running variable is true.
    print("\nWelcome to the Restaurant Ordering System!") // Prints a welcome message to the console.
    print("Choose an option:") // Prints a message to the console indicating that the user can choose an option.
    print("1. View Menu") // Prints a message to the console indicating that the user can view the menu.
    print("2. Add Item to Order") // Prints a message to the console indicating that the user can add an item to the order.
    print("3. View Order Total") // Prints a message to the console indicating that the user can view the order total.
    print("4. Apply Discount") // Prints a message to the console indicating that the user can apply a discount.
    print("5. View Items by Category") // Prints a message to the console indicating that the user can view items by category.
    print("0. Exit") // Prints a message to the console indicating that the user can exit the program.
    if let input = readLine(), let choice = Int(input) { // Checks if the user has entered a valid integer input and assigns it to the choice constant.
        switch choice { // Starts a switch statement based on the value of the choice constant.
          case 1: // If the user chooses option 1,
            restaurant.displayMenu() // Calls the displayMenu method of the restaurant object.
          case 2: // If the user chooses option 2,
            print("Enter item name:") // Prints a message to the console indicating that the user can enter an item name.
            if let itemName = readLine() { // Checks if the user has entered a valid input and assigns it to the itemName constant.
                restaurant.addItem(name: itemName) // Calls the addItem method of the restaurant object with the itemName parameter.
            }
          case 3: // If the user chooses option 3,
            restaurant.viewOrderTotal() // Calls the viewOrderTotal method of the restaurant object.
          case 4: // If the user chooses option 4,
            print("Enter discount percentage (e.g., 0.10 for 10%):") // Prints a message to the console indicating that the user can enter a discount percentage.
            if let input = readLine(), let discountPercentage = Double(input) { // Checks if the user has entered a valid input and assigns it to the discountPercentage constant.
                restaurant.discount = discountPercentage // Sets the value of the discount property of the restaurant object to the value of the discountPercentage constant.
                restaurant.applyDiscount() // Calls the applyDiscount method of the restaurant object.
            } else { // If the user has not entered a valid input,
                print("Invalid discount value.") // Prints an error message to the console.
            }
          case 5: // If the user chooses option 5,
            print("Enter category (Food, Drink, or Dessert):") // Prints a message to the console indicating that the user can enter a category.
            if let category = readLine() { // Checks if the user has entered a valid input and assigns it to the category constant.
                restaurant.viewItemsByCategory(category: category) // Calls the viewItemsByCategory method of the restaurant object with the category parameter.
            }
          case 0: // If the user chooses option 0,
            print("Exiting...") // Prints a message to the console indicating that the program is exiting.
            running = false // Sets the value of the running variable to false, causing the while loop to exit.
          default: // If the user has entered an invalid option,
            print("Invalid choice.") // Prints an error message to the console.
        }
    } else { // If the user has not entered a valid integer input, they are prompted to try again.
        print("Please enter a valid number.") // Prints an error message to the console.
    } 
}
