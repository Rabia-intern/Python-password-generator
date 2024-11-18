# Python-password-generator
import random
import string

def generate_password(length):
    # Define character sets
    lowercase_letters = string.ascii_lowercase
    uppercase_letters = string.ascii_uppercase
    digits = string.digits
    special_characters = string.punctuation

    # Combine all character sets
    all_characters = lowercase_letters + uppercase_letters + digits + special_characters

    # Ensure password includes at least one of each character type
    password = [
        random.choice(lowercase_letters),
        random.choice(uppercase_letters),
        random.choice(digits),
        random.choice(special_characters)
    ]

    # Fill the rest of the password length with random characters from all sets
    password += random.choices(all_characters, k=length - 4)

    # Shuffle the password to avoid predictable order
    random.shuffle(password)

    # Join list to form the final password string
    return ''.join(password)

# Prompt the user for password length
try:
    length = int(input("Enter the desired password length (minimum 4): "))
    if length < 4:
        print("Password length should be at least 4 for a strong password.")
    else:
        # Generate and display the password
        password = generate_password(length)
        print("Generated Password:", password)
except ValueError:
    print("Please enter a valid number for the password length.")
