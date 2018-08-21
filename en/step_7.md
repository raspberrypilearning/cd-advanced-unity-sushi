## Powerup!

You can have players get a bonus when they pick up a blue coin! Lets speed them up for 5 seconds.

To create a powerup you should make a method (a function in a class). A powerup controls your player so it makes sense to put the method in the **PlayerController** class.

+ So add this function to the **PlayerController** class: 
```csharp
void powerupSpeedUp(Player player)
{
    player.powerupTimeLeft -= Time.deltaTime;
    if (player.powerupTimeLeft > 0)
        player.movespeed = 5f;
    else
        player.movespeed = 2f;
}
```

--- collapse ---
---
title: What does the code do?
---

This checks the player's powerup time left and makes the player faster if the time left is greater than `0`.

The first line decreases the timer.

--- /collapse ---

+ Now you need to set the player's `powerupTimeLeft` to five seconds when you collide with it. So, you'll need to change the "Collisions" script.

The powerup coins are tagged as "powerup". So, you can use that to determine if a player collided with a powerup.

+ Add this code to the `OnCollisionEnter2D()` function in the "Collisions" script:

```csharp
if (col.gameObject.tag == "powerup")
{
    Destroy(col.gameObject);
    if (animal == "cat")
    {
        GameObject.Find("Platform").GetComponent<PlayerController>().cat.powerupTimeLeft = powerupTime;
    }
    if (animal == "dog")
    {
        GameObject.Find("Platform").GetComponent<PlayerController>().dog.powerupTimeLeft = powerupTime;
    }
}
```

--- collapse ---
---
title: What does the code do?
---

The `if` statements check which animal collided with the powerup then set that animal's `powerupTimeLeft` to five seconds.

--- /collapse ---

And that's it, you've made the power ups do something!

+ Test out your new speed when you pick up a powerup.