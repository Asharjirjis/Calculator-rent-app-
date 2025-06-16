# Calculator-rent-app-
# rent_calculator.py

def get_float_input(prompt):
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Invalid input. Please enter a number.")

def calculate_rent(total_rent, utilities, num_people):
    total_amount = total_rent + sum(utilities.values())
    individual_share = total_amount / num_people
    return total_amount, individual_share

def display_summary(total_rent, utilities, total_amount, individual_share, num_people):
    print("\n------ Rent Summary ------")
    print(f"Base Rent: ₹{total_rent:.2f}")
    for name, amount in utilities.items():
        print(f"{name.capitalize()}: ₹{amount:.2f}")
    print(f"Total Rent (including utilities): ₹{total_amount:.2f}")
    print(f"Number of People Sharing: {num_people}")
    print(f"Each Person Pays: ₹{individual_share:.2f}")
    print("---------------------------\n")

def main():
    print("Welcome to Rent Calculator 🏠")

  total_rent = get_float_input("Enter base rent amount: ₹")
    num_people = int(get_float_input("Enter number of people sharing the rent: "))

   # Collect utilities
  utilities = {}
    add_utilities = input("Do you want to add utility bills? (yes/no): ").strip().lower()
    while add_utilities == "yes":
        name = input("Enter utility name (e.g., electricity): ").strip()
        amount = get_float_input(f"Enter amount for {name}: ₹")
        utilities[name] = amount
        add_utilities = input("Add another utility? (yes/no): ").strip().lower()

   total_amount, individual_share = calculate_rent(total_rent, utilities, num_people)
    display_summary(total_rent, utilities, total_amount, individual_share, num_people)

if __name__ == "__main__":
    main()
