class PersonalFinance:
    def __init__(self, income):  # Use double underscores for __init__
        self.income = income

36.        self.expenses = []
        self.savings = 0

    def add_expense(self, amount, category):
        """Adds an expense with a specified amount and category."""
        self.expenses.append({"amount": amount, "category": category})
        print(f"Added expense: {category} - ${amount:.2f}")

    def add_savings(self, amount):
        """Adds savings."""
        self.savings += amount
        print(f"Added savings: ${amount:.2f}")

    def total_expenses(self):
        """Calculates the total expenses."""
        return sum(expense['amount'] for expense in self.expenses)

    def current_balance(self):
        """Calculates the current balance (Income - Expenses + Savings)."""
        return self.income - self.total_expenses() + self.savings

    def summary(self):
        """Prints a summary of income, expenses, savings, and balance."""
        print("\nPersonal Finance Summary:")
        print(f"Income: ${self.income:.2f}")
        print(f"Total Expenses: ${self.total_expenses():.2f}")
        print(f"Savings: ${self.savings:.2f}")
        print(f"Current Balance: ${self.current_balance():.2f}")

# Example Usage

def main():
    # Set your monthly income here
    income = float(input("Enter your monthly income: $"))

    # Initialize the PersonalFinance object
    pf = PersonalFinance(income)

    # Example loop for entering expenses
    while True:
        category = input("Enter expense category (or 'done' to finish): ")
        if category.lower() == 'done':
            break
        amount = float(input(f"Enter amount for {category}: $"))
        pf.add_expense(amount, category)

    # Optionally, add savings
    add_savings = input("Do you want to add savings? (y/n): ")
    if add_savings.lower() == 'y':
        savings = float(input("Enter savings amount: $"))
        pf.add_savings(savings)

    # Print the financial summary
    pf.summary()


# Correct check for running the script directly
if __name__ == "__main__":
    main()
