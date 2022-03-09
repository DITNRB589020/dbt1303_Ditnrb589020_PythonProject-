# dbt1303_Ditnrb589020_PythonProject-
import random

# Generate a random number between 5 and 10
secret_number = random.randint(5, 10)
name = input("Hello!! What is your name?")
print("Hi," + name + ".What is the secret number between 5 & 10?")

# Initialize count
count = 0

# Continuously prompt user to guess a number
while True:
    user_input = int(input("\nGuess a number: "))

    # Increment the number of tries
    count += 1

    if int(user_input) > int(secret_number):
        print("Ups! Sorry," + name + ",Your Guess is greater than the secret number.")
    elif int(user_input) < int(secret_number):
        print("Ups! Sorry," + name + ",Your Guess is greater than the secret number.")
    else:
        print(f"Number of tries: {count}")
        print("Congratulation!" + name + "\nYour Guess is Correct!!")
        break

    # Convert user input and secret number to string
    user_input = str(user_input)
    secret_number = str(secret_number)

    # Initialize correctly placed and wrongly placed digits
    wrong_place = 0
    correct_place = 0
    checked = []

    # Determine number with less digits
    if len(user_input) > len(secret_number):
        shortest_length = len(secret_number)
    elif len(user_input) < len(secret_number):
        shortest_length = len(user_input)
    else:
        shortest_length = len(secret_number)

    # Determine digits guessed correctly in right place
    for i in range(shortest_length):
        if secret_number[i] == user_input[i]:
            correct_place += 1
            checked.append(user_input[i])

    # Determine digits gussed correctly in wrong place
    for digit1 in user_input:
        for digit2 in secret_number:
            if digit1 == digit2 and digit1 not in checked:
                wrong_place += 1
                checked.append(digit1)

    print(f"{correct_place} digits have been guessed correctly in the right place")
    print(f"{wrong_place} digits have been guessed correctly in the wrong place")

    # Print the number of trials
    print(f"Number of tries: {count}")
