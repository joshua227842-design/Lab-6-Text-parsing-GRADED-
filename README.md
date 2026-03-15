# Lab-6-Text-parsing-GRADED-

# Joshua Vega to do 15-03-2026


```python
import re
#story ext for parsing
story = """
Once on a time and twice on a time, and all times together as ever I heard
tell of, there was a tiny lassie who would weep all day to have the stars
in the sky to play with...
The story is written by
Roger Federer &
Serina Williams
You can connect with the author at rfederer@tennis.com and
swilliams@tennis.com
Admin contact number: 1-888-111-2222
"""
#Geting the total character and word count
total_chars = len(story)
print("Characters:", total_chars)

all_words = story.split()
print("Words:", len(all_words))

#Word frequency using a list
my_unique_list = []
for w in all_words:
    clean_word = w.lower()
    if clean_word not in my_unique_list:
        my_unique_list.append(clean_word)

print("\nUnique words found:", len(my_unique_list))

#Frequency using a dictionary
freq_dict = {}
for w in all_words:
    low_word = w.lower()
    if low_word in freq_dict:
        freq_dict[low_word] += 1
    else:
        freq_dict[low_word] = 1

print("\nWord frequency using dictionary:")
for key in freq_dict:
    print(key, freq_dict[key])

#Extracting data with regex
found_emails = re.findall(r'\S+@\S+', story)
print("\nEmails found:", found_emails)

# find phone numbers
phone_numbers = re.findall(r'\d-\d{3}-\d{3}-\d{4}', story)
print("\nPhone numbers:", phone_numbers)

#et uernames and create hotmail list
user_list = []
new_hotmail_list = []

for mail in found_emails:
    # split to get the name before @
    user_name = mail.split("@")[0]
    user_list.append(user_name)
    # create the new email
    new_hotmail_list.append(user_name + "@hotmail.com")

print("\nUsernames:", user_list)
print("New emails list:", new_hotmail_list)
```
