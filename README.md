Python Portfolio Projects
A collection of Python projects and exercises from university coursework and online learning platforms.

WK2EX9 [P] Postal Program
This program checks if a package meets postal requirements based on its weight, length, and diameter.

Python

weight = int(input('Enter weight (g) '))
length = int(input('Enter length (cm) '))
diameter = int(input('Enter diameter (cm) '))

if (weight <= 2000) and (length <= 90) and (length + (2*diameter) <= 104):
    print('Yes')
else:
    print('No')
WK2EX10 [P] Overlapping Events
A function that determines if two events, defined by a start time and duration, overlap.

Python

def overlapchecker(beginA, timeA, beginB, timeB):
    endA = beginA + timeA
    endB = beginB + timeB
    if endA <= beginB or endB <= beginA:
        return False
    else:
        return True

beginA = int(input("Enter what time event A began using numbers between 0-23:"))
timeA = int(input("Enter how long event A was in hrs: "))
beginB = int(input("Enter what time event B began using numbers between 0-23):"))
timeB = int(input("Enter how long event B was in hrs: "))

if overlapchecker(beginA, timeA, beginB, timeB):
    print("Events A and B do overlap")
else:
    print("Events A and B do not overlap")
WK3EX7 [P] Lojban Numbers
This program translates a given number into its equivalent in Lojban, a logical language.

Python

LojbanNumbers = {
    '0': 'no',
    '1': 'pa',
    '2': 're',
    '3': 'ci',
    '4': 'vo',
    '5': 'mu',
    '6': 'xa',
    '7': 'ze',
    '8': 'bi',
    '9': 'so'
}

number = input("enter any number: ").lstrip('0')

if number == '':
    TranslatingLojban = LojbanNumbers['0']
else:
    TranslatingLojban = ''.join(LojbanNumbers[digit] for digit in number)

print(TranslatingLojban)
WK3EX8 [P] Bingo Card
A program that generates and displays a random Bingo card.

Python

import random

numbers = list(range(11, 86))
random.shuffle(numbers)
grid_of_numbers = numbers[:25]
grid = [grid_of_numbers[i:i + 5] for i in range(0, 25, 5)]

for row in grid:
    print(" ".join(f"{num:2}" for num in row))
WK4EX7 [P] Count Multiples
This function counts how many numbers in a given list are multiples of a specific integer.

Python

def count_multiples(n, numlist):
    count = 0
    for element in numlist:
        if element % n == 0:
            count += 1
    return count
WK4EX8 [P] Longest Streak
A function that finds the longest consecutive streak of a specific word in a list of words.

Python

def longest_streak(word, word_list):
    max_streak = 0
    current_streak = 0
    for i in word_list:
        if i == word:
            current_streak += 1
            if current_streak > max_streak:
                max_streak = current_streak
        else:
            current_streak = 0
    return max_streak








