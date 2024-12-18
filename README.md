# valid_input

valid_input is a lightweight Python library for performing commonly used input checks like making the user input a valid int or float or a specific option

## Index
- [Installation](#installation)
- [Usage](#usage)
  - [input_int](#input_int)
  - [input_float](#input_float)
  - [input_option](#input_option)
  - [input_yes_no](#input_yes_no)
  - [input_date](#input_date)
  - [input_with_length](#input_with_length)
  - [input_list](#input_list)
  - [input_num_in_range](#input_num_in_range)
  - [input_with_regex](#input_with_regex)
  - [validated_input](#validated_input)
- [License](#license)

## Installation

You can install valid_input using pip:

```bash
pip install valid_input
```

## Usage

You can pass to all the examples below an additional parameter error_msg to 
override the default error message of the input function

### input_int
```python
from valid_input.tools import input_int
age = input_int("Introduce your age: ")  # Returns an integer
```

### input_float
```python
from valid_input.tools import input_float
height = input_float("What's your height? (in meters): ")  # Returns a float
```

### input_option
```python
from valid_input.tools import input_option

# Returns the element chosen from the list
sex = input_option("What's your sex? (male/female/other): ", ["male", "female", "other"])

# The returned value will be the original element in the list
# For example, if we have this list:
options = [1, 2, "3", 4]

# The user can choose between 1, 2, 3 or 4
option = input_option("Choose a number between 1 and 4: ", options)

# If the user chooses 3, the returned value will be '3' as a string; otherwise, it will be the chosen number as an integer
```

### input_yes_no
```python
from valid_input.tools import input_yes_no

# Returns True if the user inputs 'yes' or 'y', and False if the user inputs 'no' or 'n' (case insensitive)
is_student = input_yes_no("Are you a student? (yes/no): ")
```

### input_date
```python
from valid_input.tools import input_date

# Returns a datetime object (by default expects the date in the format "YYYY-MM-DD")
birthday = input_date("Introduce your birthday (YYYY-MM-DD): ")

# You can specify the date format
birthday = input_date("Introduce your birthday (DD/MM/YYYY): ", date_format="%d/%m/%Y")
```

### input_with_length
```python
from valid_input.tools import input_with_length

# Returns a string with defined minimum and maximum length
name = input_with_length("Introduce your name: ", min_length=3, max_length=50)

# You can define only the minimum or maximum length
name = input_with_length("Introduce your name: ", min_length=3)  # Returns a string with at least 3 characters
name = input_with_length("Introduce your name: ", max_length=50)  # Returns a string with at most 50 characters
```

### input_list
```python
from valid_input.tools import input_list

# Returns a list of elements that match the validation function
numbers = input_list("Introduce a list of numbers separated by commas: ", item_validation_func=int)

# You can define a custom separator
numbers = input_list("Introduce a list of numbers separated by semicolons: ", item_validation_func=int, separator=";")

# You can also allow an empty list (by default, it is not allowed)
numbers = input_list("Introduce a list of numbers separated by commas: ", item_validation_func=int, allow_empty=True)
```

### input_num_in_range
```python
from valid_input.tools import input_num_in_range

# Returns a number in the specified range
age = input_num_in_range("Introduce your age: ", 0, 120)  # Returns a number between 0 and 120

# The range is inclusive
# You can define only the lower or upper limit
age = input_num_in_range("Introduce your age: ", min_value=18)  # Returns a number greater or equal to 18
age = input_num_in_range("Introduce your age: ", max_value=120)  # Returns a number less or equal to 120

# You can also disallow the user to input a float number
age = input_num_in_range("Introduce your age: ", 0, 120, allow_float=False)  # Returns an integer between 0 and 120
```

### input_with_regex
```python
from valid_input.tools import input_with_regex

# Returns a string that matches the regex
isbn = input_with_regex("Introduce the ISBN of the book: ", r"\d{9}[\d|X]")
```

### validated_input
```python
from valid_input.tools import validated_input

# Returns a string that passes the validation function

def validation_func(value: str):
    value = int(value)
    
    if value % 2 != 0:
        raise ValueError("The number must be even")
        
    return value

number = validated_input("Introduce an even number: ", validation_func)
```

## License

valid_input is distributed under the MIT License.
