# Password-Generator\
import string
import random

def generate_password(length, use_letters=True, use_numbers=True, use_symbols=True):
    chars = ""
    if use_letters:
        chars += string.ascii_letters
    if use_numbers:
        chars += string.digits
    if use_symbols:
        chars += string.punctuation

    if not chars:
        print("Error: Please select at least one character type.")
        return None

    password = ''.join(random.choice(chars) for _ in range(length))
    return password

def main():
    print("Welcome to the Password Generator!")

    try:
        length = int(input("Enter the password length: "))
    except ValueError:
        print("Error: Please enter a valid number.")
        return

    use_letters = input("Include letters? (y/n): ").lower() == 'y'
    use_numbers = input("Include numbers? (y/n): ").lower() == 'y'
    use_symbols = input("Include symbols? (y/n): ").lower() == 'y'

    password = generate_password(length, use_letters, use_numbers, use_symbols)

    if password:
        print("\nGenerated Password:", password)

if __name__ == "__main__":
    main()
