# ATM-in-python

class ATM:
    def __init__(self):
        self.balance = 0
        self.transaction_history = []

    def check_balance(self):
        return self.balance

    def deposit(self, amount):
        self.balance += amount
        self.transaction_history.append(f'Deposit: +${amount}')

    def withdraw(self, amount):
        if amount > self.balance:
            return "Insufficient funds"
        else:
            self.balance -= amount
            self.transaction_history.append(f'Withdrawal: -${amount}')
            return amount

    def change_pin(self, new_pin):
        self.pin = new_pin
        return "PIN changed successfully"

    def show_transaction_history(self):
        return self.transaction_history


def main():
    atm = ATM()
    atm.deposit(1000)  # Initial deposit for testing

    while True:
        print("\n=== ATM Simulator ===")
        print("1. Check Balance")
        print("2. Withdraw Cash")
        print("3. Deposit Cash")
        print("4. Change PIN")
        print("5. Transaction History")
        print("6. Exit")
        
        choice = input("Enter your choice: ")

        if choice == '1':
            print(f"Your balance is ${atm.check_balance()}")

        elif choice == '2':
            amount = float(input("Enter the amount to withdraw: "))
            result = atm.withdraw(amount)
            if isinstance(result, str):
                print(result)
            else:
                print(f"Withdrawal successful. Remaining balance: ${atm.check_balance()}")

        elif choice == '3':
            amount = float(input("Enter the amount to deposit: "))
            atm.deposit(amount)
            print(f"Deposit successful. Current balance: ${atm.check_balance()}")

        elif choice == '4':
            new_pin = input("Enter new PIN: ")
            print(atm.change_pin(new_pin))

        elif choice == '5':
            print("Transaction History:")
            for transaction in atm.show_transaction_history():
                print(transaction)

        elif choice == '6':
            print("Thank you for using the ATM. Goodbye!")
            break

        else:
            print("Invalid choice. Please enter a number from 1 to 6.")


if __name__ == "__main__":
    main()
