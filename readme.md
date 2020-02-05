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