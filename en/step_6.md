## Losing lives

Let's finish up the code in the "Collisions" script.

You are going to create an **array**.

--- collapse ---
---
title: What's an array?
---

An **array** is a collection of elements (of the same type) that can be accessed with an **index**.

In C# programming an **index** starts at `0`. So, the first item in an array will be the `0th` element. An array with three elements in it will have elements `0`, `1`, and `2`.

--- /collapse ---

You will create an **array** of **GameObjects**. There are three hearts for each player, so you can use an **array** because they are all the same type (type **GameObject**).

Declaring an array is easy, all you need to do is add square brackets to the end of a data type (example: `int[] numbers;`).

+ Look at the top of the "Collisions" script, where all the variables are declared. You should see the `hearts` array declared. You can tell it is an array because of the `[]`:
```csharp
private GameObject[] hearts;
``` 

Now you need to **initialise** the array. 

--- collapse ---
---
title: What does initialise mean?
---

**Initialising** is when you create an array. The number of elements in a C# array need to be known when you create the array.

--- /collapse ---

To do this you need to use the `new` keyword again. You need to know the size of an array when it is created, and you know it should be three because their are three hearts!

+ So, add this line to `Start()` under `// Array declaration`, which will initialize your array with 3 elements: `hearts = new GameObject[3];`.

Note: Whatever number you put where the three is will change the size of an array. so `hearts = new GameObject[10];` will create an array with ten elements.

Now you need to assign values to each element of an array. To access a specific element you use this syntax: `array[x]` where x is the element you want to access. **Remember!** Arrays are `0` indexed so the first element will be `array[0]`!

+ Add these lines of code under `hearts = new GameObject[3];`:

```csharp
hearts[0] = GameObject.Find(animal + "Heart3");
hearts[1] = GameObject.Find(animal + "Heart2");
hearts[2] = GameObject.Find(animal + "Heart1");
``` 

Now if you want to make the player lose a heart, all you need to do is delete the number in the array that you want. To know which heart to delete I've given you a `lives` counter variable. Every time the player falls off the screen the `lives` counter will subtract `1`. All you need to do is **Destroy** the array element that is a heart.

+ Add this line of code into the `OnCollisionEnter2D(Collision col)` function: 

```csharp
Destroy(hearts[lives]);
```

Now you can run the game and the lives will disappear!

+ Try it out now.  
