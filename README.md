import re
import getpass

def analyze_password(password):
    score = 0
    suggestions = []

    if len(password) >= 8:
        score += 1
    else:
        suggestions.append("Use at least 8 characters.")

    if re.search(r"[A-Z]", password):
        score += 1
    else:
        suggestions.append("Add an uppercase letter (A-Z).")

    if re.search(r"[a-z]", password):
        score += 1
    else:
        suggestions.append("Add a lowercase letter (a-z).")

    if re.search(r"[0-9]", password):
        score += 1
    else:
        suggestions.append("Add a number (0-9).")

    if re.search(r"[^A-Za-z0-9]", password):
        score += 1
    else:
        suggestions.append("Add a special character (!, @, #, etc.).")

    if score <= 2:
        strength = "Weak"
    elif score <= 4:
        strength = "Moderate"
    else:
        strength = "Strong"

    print("\n--- Password Strength Report ---")
    print("Password length:", len(password))
    print("Strength:", strength)

    if suggestions:
        print("\nSuggestions to improve your password:")
        for suggestion in suggestions:
            print("-", suggestion)
    else:
        print("Excellent! Your password meets all basic checks.")

password = getpass.getpass("Enter a password to analyze: ")
analyze_password(password)

output:

enter a password analyser:sush@123
--- Password Strength Report ---
Password length: 10
Strength: Strong
Excellent! Your password meets all basic checks.
