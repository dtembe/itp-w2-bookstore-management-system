# Hint 1 - Data first

For any system is key to define the way your data is going to be structured. Once you nail down the design in terms of data, the "functionality" will just flow naturally.

Our bookstore is defined when we invoke the `create_bookstore` function. The object returned is the store that we'll use for our "functionality" functions.

For example, our bookstore will store author information, we'll need to:

* Add authors: `add_author(bookstore, name, nationality)`
* Search authors : `get_author_by_name, get_author_by_id`

All those methods receive the `bookstore` object (created with `create_bookstore`) as the first parameter.

Aside from authors, we also have to store the name of the author and also books. If we could define many lists as our bookstore, it'd be something like:

```python
# Our bookstore:
name = "Rmotr's bookstore"
authors = [poe, borges, austen]
books = [raven, ficciones]
```

The issue is that we need just 1 object to represent our bookstore. What'd be a good way to group all this information together? A dictionary might be a great idea (and that's why we chose it!):

```python
bookstore = {
    'name': "Rmotr's bookstore"
    'authors': [poe, borges, austen],
    'books': [raven, ficciones]
}
```

## Autogenerated IDs

Every new author or book that is added to the bookstore will require that bookstore to assign a unique ID. Our current tests don't impose any type of restrictions in regards of how you should implement the ID. But usually, using an auto-increment integer ID is a good recipe. We could add that data to the bookstore, so any time we want to add a new author or book, we just need to assign it to that object and increment it. So we'd end up with something like:

```python
def create_bookstore(name):
    return {
        'name': name,
        'last_author_id': 0,
        'last_book_id': 0,
        'books': [],
        'authors': []
    }
```