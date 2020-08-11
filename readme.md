# TQDM is a very useful python library

Extremely simple progress bar for any iterable

```python
from tqdm import tqdm
for thing in tqdm(some_iterable_thing):
	# ...
```

For iterating rows in a dataframe:
```python
for index, row in tqdm(df.iterrows(), total=df.shape[0]):
	# ...
```


# Bash number list expansion

In bash, `{1..9}` will expand to the list `1 2 3 4 5 6 7 8 9`
This can be used in conjunction with a for loop, so for instance to cancel a
bunch of consecutively numbered jobs 546963-546987:
```bash
for job in 5469{63..87}
do
scancel $job
done
```


# Python Array Unpacking

Value unpacking works for arrays, not just tuples:

```python
>>> things = [1, 2, 3]
>>> thing1, thing2, thing3 = things
>>> print(thing1)
1
>>> print(thing2)
2
>>> print(thing3)
3
```


# Python Pseudo-tables

You can pad out any string (`str`) to take up any number of character's worth of space
with `ljust(num)`:

```python
>>> "hello".ljust(20)
'hello               '
```

# JSON Pretty Print Output

the `json` module can pretty print the data with the `indent` arg when it saves:

```python
with open("mydatafile.json", 'w') as outfile:
	json.dump(mythings, outfile, indent=4)
```

# Dictionary and array unwrapping in function calls

`*` and `**` aren't just fancy delimiters for `*args` and `**kwargs` in a function definition, you can use them anywhere you would need to "unwrap" an array (with the single `*`) or a dictionary (with the double `**`) in a function call:

```python
def dothing(name, message):
    print(name, "says", message)


>>> mydata = {"name": "Nathan", "message": "Hello world!"}
>>> dothing(**mydata)
Nathan says Hello world!
```

This is particularly useful if, say, you're loading in experiment parameters from a json file and don't want to have to manually add code to pass each individual parameter explicitly to the function


# String multiplication

Strings can be multiplied with a number, and python automagically repeats the string that many times:

```python
>>> print("="*80)
================================================================================
```

This is useful if you want a readable and consistent way to make breaks in output logs: 

```python
>>> print("="*30, "TRAINING", "="*30)
============================== TRAINING ==============================
```

# IPython save lines

Using ipython's `%history` magic allows you to collect lines together:

For example:
```ipython
%history 1 3-4
```
will print out code line 1 and 3 through 4 together. You can append a `-f
[filename]` flag to have it output to a file


# Dump unserializable things to JSON


If you're trying to dump json stuff just for debugging or inspection purposes and you have a ton of stuff that's not serializable (and you really just want whatever python's REPL would print out with `str()`) you can use the `default` arg in `json.dump` (takes a function param and applies it to anything it can't serialize correctly):

```python
my_unserializable_dict = {}
with open(some_path, "w") as outfile:
    json.dump(my_unserializable_dict, outfile, default=lambda x: str(x))
```

# Python conditional syntactic sugar

you can do conditional one-liners after assignment syntax to make it "read" better (one of the only pieces of syntactic sugar in ruby I actually liked):

```python
>>> thing = "hello" if True else "no"
>>> thing
"hello"
```

```python
>>> thing = "hello" if False else "no"
>>> thing
"no"
```

# Python reverse index search

If you need to find the last occurrence of a substring in a string, you can just use `rindex`, instead of manually iterating with `index`:

```python
haystack = "this is a string example"
needle = "is">>> print(haystack.rindex(needle))
5
>>> print(haystack.index(needle))
2
```
