# StartHere_CS_03
Password Complexity Checker


import re


def check_password_strength(password):
    # Criteria for password strength
    criteria = {
        "Length": len(password) >= 8,
        "Uppercase letter": bool(re.search(r'[A-Z]', password)),
        "Lowercase letter": bool(re.search(r'[a-z]', password)),
        "Number": bool(re.search(r'[0-9]', password)),
        "Special character": bool(re.search(r'[@#$%^&+=!_]', password)),
    }

    # Check if password meets all criteria
    valid_criteria = [key for key, valid in criteria.items() if valid]
    invalid_criteria = [key for key, valid in criteria.items() if not valid]

    if len(invalid_criteria) == 0:
        password_strength = "Strong"
        feedback = "Password is strong. Well done!"
    else:
        password_strength = "Weak"
        feedback = f"Password is weak. It does not meet the following criteria: {', '.join(invalid_criteria)}"

    return password_strength, feedback


def main():
    # User input for password
    password = input("Enter a password to check its strength: ")

    # Check the password strength
    strength, feedback = check_password_strength(password)

    # Output the result
    print(f"Password Strength: {strength}")
    print(feedback)


if __name__ == "__main__":
    main()
