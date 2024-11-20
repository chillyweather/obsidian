# CLASSES

## METHODS

One thing that makes classes cool is that we can define [methods](https://docs.python.org/3/tutorial/classes.html#method-objects) on them. A method is a function that's tied directly to a class and has access to all its properties.

```python
class Soldier:
    health = 5

    def take_damage(self, damage):
        self.health -= damage

soldier_one = Soldier()
soldier_one.take_damage(2)
print(soldier_one.health)
# prints "3"
```
## SELF

Methods are nested within the `class` declaration. Their first parameter is always the instance of the class that the method is being called on. By convention, it's called ["self"](https://docs.python.org/3/glossary.html#term-method). Because `self` is a reference to the object, you can use it to read and update the properties of the object.

Notice that methods are called directly on an object using the dot operator.

```python
my_object.my_method()
```


# CONSTRUCTORS (OR INITIALIZERS)

It's rare in the real world to see a class that defines properties the way we've been doing it:

```python
class Soldier:
    name = "Legolas"
    armor = 2
    num_weapons = 2
```

It's more practical to use a [constructor](https://en.wikipedia.org/wiki/Constructor_(object-oriented_programming)). In Python, if you name a method [`__init__`](https://docs.python.org/3/reference/datamodel.html#object.__init__), that's the constructor and it is called when a new object is created.

So, with a constructor, the code would look like this:

```python
class Soldier:
    def __init__(self):
        self.name = "Legolas"
        self.armor = 2
        self.num_weapons = 2
```

Now we can make the starting armor and number of weapons configurable with some parameters!

```python
class Soldier:
    def __init__(self, name, armor, num_weapons):
        self.name = name
        self.armor = armor
        self.num_weapons = num_weapons

soldier = Soldier("Legolas", 5, 10)
print(soldier.name)
# prints "Legolas"
print(soldier.armor)
# prints "5"
print(soldier.num_weapons)
# prints "10"
```

# CLASS VARIABLES VS INSTANCE VARIABLES

So far we've worked with both class variables and instance variables, but we haven't talked about the difference.

## INSTANCE VARIABLES

Instance variables vary from object to object and are **declared in the constructor.**

```python
class Wall:
    def __init__(self):
        self.height = 10

south_wall = Wall()
south_wall.height = 20 # only updates this instance of a wall
print(south_wall.height)
# prints "20"

north_wall = Wall()
print(north_wall.height)
# prints "10"
```

## CLASS VARIABLES

Class variables remain the same between instances of the same class and are **declared at the top level of a class definition**.

```python
class Wall:
    height = 10

south_wall = Wall()
print(south_wall.height)
# prints "10"

Wall.height = 20 # updates all instances of a Wall

print(south_wall.height)
# prints "20"
```

In other languages these types of variables are often called [static variables](https://en.wikipedia.org/wiki/Static_variable).


# SAMPLE 1

```python
class Student:
    def __init__(self, name):
        self.name = name
        self.__courses = {}

    def calculate_letter_grade(self, score):
        if score >= 90:
            return 'A'
        elif 80 <= score < 90:
            return 'B'
        elif 70 <= score < 80:
            return 'C'
        elif 60 <= score < 70:
            return 'D'
        else: 
            return 'F'


    def add_course(self, course_name, score):
        grade = self.calculate_letter_grade(score)
        self.__courses[course_name] = grade

    def get_courses(self):
        return self.__courses

```


# SAMPLE 2

```python

class Unit:
    def __init__(self, name, pos_x, pos_y):
        self.name = name
        self.pos_x = pos_x
        self.pos_y = pos_y

    def in_area(self, x1, y1, x2, y2):
        pass


class Dragon(Unit):
    def __init__(self, name, pos_x, pos_y, height, width, fire_range):
        super().__init__(name, pos_x, pos_y)
        self.fire_range = fire_range
        self.height = height
        self.width = width
        self.__hit_box = Rectangle((pos_x-self.width/2),(pos_y-self.height/2), (pos_x+self.width/2), (pos_y+self.height/2))

    def in_area(self, x1, y1, x2, y2):
        other_rect = Rectangle(x1,y1,x2, y2)
        return other_rect.overlaps(self.__hit_box)


# Don't touch below this line


class Rectangle:
    def overlaps(self, rect):
        return (
            self.get_left_x() <= rect.get_right_x()
            and self.get_right_x() >= rect.get_left_x()
            and self.get_top_y() >= rect.get_bottom_y()
            and self.get_bottom_y() <= rect.get_top_y()
        )

    def __init__(self, x1, y1, x2, y2):
        self.__x1 = x1
        self.__y1 = y1
        self.__x2 = x2
        self.__y2 = y2

    def get_left_x(self):
        if self.__x1 < self.__x2:
            return self.__x1
        return self.__x2

    def get_right_x(self):
        if self.__x1 > self.__x2:
            return self.__x1
        return self.__x2

    def get_top_y(self):
        if self.__y1 > self.__y2:
            return self.__y1
        return self.__y2

    def get_bottom_y(self):
        if self.__y1 < self.__y2:
            return self.__y1
        return self.__y2

```
# OPERATOR OVERLOAD REVIEW

As we discussed in the last assignment, operator overloading is the practice of defining custom behavior for standard Python operators. Here's a list of how the operators translate into method names.

| Operation           | Operator | Method       |
| ------------------- | -------- | ------------ |
| Addition            | +        | **add**      |
| Subtraction         | -        | **sub**      |
| Multiplication      | *        | **mul**      |
| Power               | **       | **pow**      |
| Division            | /        | **truediv**  |
| Floor Division      | //       | **floordiv** |
| Remainder (modulo)  | %        | **mod**      |
| Bitwise Left Shift  | <<       | **lshift**   |
| Bitwise Right Shift | >>       | **rshift**   |
| Bitwise AND         | &        | **and**      |
| Bitwise OR          | \|       | **or**       |
| Bitwise XOR         | ^        | **xor**      |
| Bitwise NOT         | ~        | **invert**   |

# OVERLOADING BUILT-IN METHODS

Last but not least, let's take a look at some of the built-in methods we can overload in Python. While there isn't a default behavior for the arithmetic operators like we just saw, there _is_ a default behavior for **printing** a class.

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y


p1 = Point(4, 5)
print(p1)
# prints "<Point object at 0xa0acf8>"
```

That's not super useful! Let's teach instances of our `Point` object to print themselves. The [`__str__`](https://docs.python.org/3/reference/datamodel.html#object.__str__) method (short for "string") lets us do just that. It takes no inputs but returns a string that will be printed to the console when someone passes an instance of the class to Python's `print()` function.

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"({self.x},{self.y})"

p1 = Point(4, 5)
print(p1)
# prints "(4,5)"
```

_Note: the [`__repr__`](https://docs.python.org/3/reference/datamodel.html#object.__repr__) method works in a similar way, you'll see it from time to time._


# WAR GAME

```python
import random


class CardGame:
    def __init__(self):
        self.deck = DeckOfCards()
        self.deck.shuffle_deck()

    def play(self):
        print("Nothing to play...")


class War(CardGame):
    def __init__(self):
        super().__init__()  # Correctly call the parent constructor
        self.player1_hand = []
        self.player2_hand = []

    def play(self):
        self.player1_hand = self.__deal_hand()
        self.player2_hand = self.__deal_hand()
        self.__battle()

    def __deal_hand(self):
        hand = []
        for i in range(5):  # 0 is the default start, so range(5) is fine
            card = self.deck.deal_card()
            hand.append(card)
        return hand
    
    # don't touch below this line

    def __battle(self):
        player1_pile = []
        player2_pile = []
        player1_score = 0
        player2_score = 0
        ties = 0
        while len(self.player1_hand) > 0 or len(self.player2_hand) > 0:
            if len(self.player1_hand) == 0:
                random.shuffle(player1_pile)
                self.player1_hand = player1_pile.copy()
                player1_pile.clear()
            if len(self.player2_hand) == 0:
                random.shuffle(player2_pile)
                self.player2_hand = player2_pile.copy()
                player2_pile.clear()
            card1 = self.player1_hand.pop()
            card2 = self.player2_hand.pop()
            print(f"{card1} vs {card2}")
            if card1 > card2:
                player1_pile.append(card1)
                player1_pile.append(card2)
                player1_score += 1
                print(f"Player 1 wins with {card1}")
            elif card2 > card1:
                player2_pile.append(card1)
                player2_pile.append(card2)
                player2_score += 1
                print(f"Player 2 wins with {card2}")
            else:
                ties += 1
                print("Tie! Both players draw a card and play again")
        print("------------------------------------------")
        print("Game over!")
        print("------------------------------------------")
        print(f"Player 1: {player1_score}")
        print(f"Player 2: {player2_score}")
        print(f"Ties: {ties}")
        print("==========================================")


SUITS = ["Clubs", "Diamonds", "Hearts", "Spades"]

RANKS = ["2", "3", "4", "5", "6", "7", "8", "9", "10", "Jack", "Queen", "King", "Ace"]


def index_of(lst, item):
    for i in range(len(lst)):
        if lst[i] == item:
            return i
    return None


class Card:
    def __init__(self, rank, suit):
        self.rank = rank
        self.suit = suit

    def __cmp(self, other):
        self_suit_i = index_of(SUITS, self.suit)
        other_suit_i = index_of(SUITS, other.suit)
        self_rank_i = index_of(RANKS, self.rank)
        other_rank_i = index_of(RANKS, other.rank)
        if self_rank_i > other_rank_i:
            return "gt"
        if self_rank_i < other_rank_i:
            return "lt"
        if self_suit_i > other_suit_i:
            return "gt"
        if self_suit_i < other_suit_i:
            return "lt"
        return "eq"

    def __eq__(self, other):
        return self.__cmp(other) == "eq"

    def __gt__(self, other):
        return self.__cmp(other) == "gt"

    def __lt__(self, other):
        return self.__cmp(other) == "lt"

    def __str__(self):
        return f"{self.rank} of {self.suit}"


class DeckOfCards:
    def __init__(self):
        self.__cards = []
        self.create_deck()

    def create_deck(self):
        for suit in SUITS:
            for rank in RANKS:
                self.__cards.append(Card(rank, suit))

    def shuffle_deck(self):
        random.shuffle(self.__cards)

    def deal_card(self):
        if len(self.__cards) == 0:
            return None
        return self.__cards.pop(0)


def test(seed):
    random.seed(seed)
    war = War()
    war.play()


def main():
    test(1)
    test(2)


main()

```