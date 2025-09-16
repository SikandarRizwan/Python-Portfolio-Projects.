# WK2EX9 [P] Postal Program (4 marks)
# This program checks if a package meets postal requirements based on its weight, length, and diameter.
weight = int(input('Enter weight (g) '))
length = int(input('Enter length (cm) '))
diameter = int(input('Enter diameter (cm) '))

if (weight <= 2000) and (length <= 90) and (length + (2*diameter) <= 104):
    print('Yes')
else:
    print('No')


# WK2EX10 [P] Overlapping Events (4 marks)
# A function that determines if two events, defined by a start time and duration, overlap.
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


# WK3EX7 [P] Lojban Numbers (4 marks)
# This program translates a given number into its equivalent in Lojban, a logical language.
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


# WK3EX8 [P] Bingo Card (4 marks)
# A program that generates and displays a random Bingo card.
import random
numbers = list(range(11, 86))
random.shuffle(numbers)
grid_of_numbers = numbers[:25]
grid = [grid_of_numbers[i:i + 5] for i in range(0, 25, 5)]

for row in grid:
    print(" ".join(f"{num:2}" for num in row))


# WK4EX7 [P] count multiples (4 marks)
# This function counts how many numbers in a given list are multiples of a specific integer.
def count_multiples(n, numlist):
    count = 0
    for element in numlist:
        if element % n == 0:
            count += 1
    return count


# WK4EX8 [P] longest streak (4 marks)
# A function that finds the longest consecutive streak of a specific word in a list of words.
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


# WK6EX8 [P] words_containing (5 marks)
# A function that finds all words in a file that contain a specific substring.
def words_containing(file, substring):
    matching_words = []
    with open(file, 'r') as my_file:
        for line in my_file:
            words = line.split()
            for word in words:
                if substring in word:
                    matching_words.append(word)
    return matching_words


# WK6EX9 [P] average_rating (5 marks)
# This function calculates the average rating for a specific candidate from a file of ratings.
def average_rating(file, candidate):
    total_rating = 0
    rating_count = 0
    with open(file, 'r') as my_file:
        for line in my_file:
            voter_number, candidate_name, rating = line.split()
            if candidate_name == candidate:
                total_rating += int(rating)
                rating_count += 1
    if rating_count > 0:
        average = total_rating / rating_count
    else:
        average = 0
    return [rating_count, average]

def print_ratings(file):
    ratings_dict = {}
    with open(file, 'r') as my_file:
        for line in my_file:
            voter_number, candidate_name, rating = line.split()
            if candidate_name not in ratings_dict:
                ratings_dict[candidate_name] = []
            ratings_dict[candidate_name].append(int(rating))
    for candidate_name, ratings in ratings_dict.items():
        total_rating = sum(ratings)
        count = len(ratings)
        average = total_rating / count
        print (candidate_name, average)


# WK7EX10&11 [P] Marathon Program (8 marks)
# Functions to process marathon results data from a file.
def total_seconds(time_str):
    time_format = time_str.split(':')
    hours = int(time_format[0])
    minutes = int(time_format[1])
    seconds = int(time_format[2])
    return hours * 3600 + minutes * 60 + seconds

def read_file(filename):
    results = []
    with open(filename, 'r') as file:
        for line in file:
            ty_pe = line.strip().split(',')
            runner = {
                'id': ty_pe[0],
                'time': ty_pe[1],
                'firstname': ty_pe[2],
                'lastname': ty_pe[3]
            }
            results.append(runner)
    return results

def get_interval_data(start_seconds, end_seconds, results):
    count = 0
    total_time = 0
    for runner in results:
        time_in_seconds = total_seconds(runner['time'])
        if start_seconds <= time_in_seconds <= end_seconds:
            count += 1
            total_time += time_in_seconds
    if count == 0:
        return {'count': 0, 'mean': 0}
    mean = total_time / count
    return {'count': count, 'mean': mean}


# WK8EX9 [P] Inverting Triangle (4 marks)
# A program that creates an inverting triangle with a graphical user interface.
from tkinter import Tk, Canvas, Button
global triangle_state
triangle_state = 'down'
def flip_triangle():
    global triangle_state
    drawing_area.delete("all")
    if triangle_state == 'down':
        drawing_area.create_polygon(100, 200, 200, 200, 150, 100, fill="black")
        triangle_state = 'up'
    else:
        drawing_area.create_polygon(100, 100, 200, 100, 150, 200, fill="black")
        triangle_state = 'down'
app_window = Tk()
app_window.title("Triangle Flipper")
drawing_area = Canvas(app_window, width=300, height=300)
drawing_area.pack()
drawing_area.create_polygon(100, 100, 200, 100, 150, 200, fill="black")
flip_button = Button(app_window, text="Flip", command=flip_triangle)
flip_button.pack()
app_window.mainloop()


# WK8EX10 [P] Press Release (4 marks)
# A program that allows a user to draw black rectangles on a canvas by pressing and releasing the mouse button.
from tkinter import Tk, Canvas
start_x = 0
start_y = 0
def on_mouse_press (event):
    global start_x, start_y
    start_x = event.x
    start_y = event.y

def on_mouse_release (event):
    global drawing_canvas
    drawing_canvas.create_rectangle(start_x, start_y, event.x, event.y, fill="black")

app_window = Tk()
app_window.title("Draw Rectangles")
drawing_canvas = Canvas(app_window, width=500, height=500)
drawing_canvas.pack()
drawing_canvas.bind('<Button-1>', on_mouse_press)
drawing_canvas.bind('<ButtonRelease-1>', on_mouse_release)
app_window.mainloop()    print(" ".join(f"{num:2}" for num in row))


# WK4EX7 [P] count multiples (4 marks)
# This function counts how many numbers in a given list are multiples of a specific integer.

def count_multiples(n, numlist):
    count = 0
    for element in numlist:
        if element % n == 0:
            count += 1
    return count


# WK4EX8 [P] longest streak (4 marks)
# A function that finds the longest consecutive streak of a specific word in a list of words.

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








