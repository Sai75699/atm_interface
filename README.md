# atm_interface
class ATM:
    def __init__(self, balance=0):
        self.balance = balance

    def check_balance(self):
        print(f"Your current balance is: ${self.balance:.2f}")

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"Deposited ${amount:.2f}. New balance: ${self.balance:.2f}")
        else:
            print("Invalid deposit amount.")

    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            print(f"Withdrawn ${amount:.2f}. Remaining balance: ${self.balance:.2f}")
        elif amount > self.balance:
            print("Insufficient funds.")
        else:
            print("Invalid withdrawal amount.")


def main():
    user_atm = ATM(balance=1000)  # Initial balance set to $1000
    
    while True:
        print("\n===== ATM Menu =====")
        print("1. Check Balance")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Exit")
        
        try:
            choice = int(input("Enter your choice: "))
            
            if choice == 1:
                user_atm.check_balance()
            elif choice == 2:
                amount = float(input("Enter deposit amount: "))
                user_atm.deposit(amount)
            elif choice == 3:
                amount = float(input("Enter withdrawal amount: "))
                user_atm.withdraw(amount)
            elif choice == 4:
                print("Thank you for using the ATM. Goodbye!")
                break
            else:
                print("Invalid choice. Please try again.")
        except ValueError:
            print("Please enter a valid number.")


if __name__ == "__main__":
    main()
