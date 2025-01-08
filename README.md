# banku-pasarg-anai-
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance
        self.password = None  # Lai pievienotu paroli

    def set_password(self, password):
        """Iestata konta paroli."""
        self.password = password
        print("Parole veiksmīgi iestatīta!")

    def check_balance(self, password):
        """Pārbauda konta atlikumu tikai pēc paroles ievades."""
        if self.password == password:
            return f"Kontā ir {self.balance} EUR."
        else:
            return "Nederīga parole!"

    def deposit(self, amount, password):
        """Veic iemaksu, ja parole ir pareiza."""
        if self.password == password:
            if amount > 0:
                self.balance += amount
                return f"Veikta iemaksa {amount} EUR. Jaunais atlikums: {self.balance} EUR."
            else:
                return "Iemaksai jābūt pozitīvai!"
        else:
            return "Nederīga parole!"

    def withdraw(self, amount, password):
        """Veic izņemšanu, ja parole ir pareiza un atlikums ir pietiekams."""
        if self.password == password:
            if amount > 0 and amount <= self.balance:
                self.balance -= amount
                return f"Veikta izņemšana {amount} EUR. Jaunais atlikums: {self.balance} EUR."
            elif amount > self.balance:
                return "Nepietiekams atlikums!"
            else:
                return "Izņemšanai jābūt pozitīvai!"
        else:
            return "Nederīga parole!"

# Piemērs
client_account = BankAccount("John Doe")

# Iestatām paroli
client_account.set_password("secure123")

# Iemaksas un izņemšanas
print(client_account.deposit(100, "secure123"))
print(client_account.check_balance("secure123"))
print(client_account.withdraw(50, "secure123"))
print(client_account.check_balance("secure123"))
print(client_account.withdraw(100, "wrongpassword"))  # Neveiksmīga parole
print(client_account.check_balance("secure123"))
Izskaidrojums:
