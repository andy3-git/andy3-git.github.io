---
layout: project
type: project
image: img/JambaJuice.jpg
title: "Object Oriented Programming With Jamba Juice"
date: 2025
published: true
labels:
  - Typescript
  - GitHub
summary: "A Typescript Project made during ICS 314 that showcases Classes and Constructor in the theme of Jamba Juice"
---

<img src="/img/JambaJuiceMenu.jpg" alt="Jamba Juice Menu" width="300" height="300">

## About
Jamba Juice is a quick service chain that serves healthy foods and beverages such as Smoothies, Acaí, and healthy foods.
In this project assigned during ICS 314 I am create a menu with three beverages.
These beverages contain a name, a list of ingredients, prices corresponding to a list of sizes, and calories corresponding to a list of sizes.
The list of sizes in this code are as follows, small, medium, and large.

## Code
Down below is the foundation of this project.
Within this class, I have four parameters with various datatypes.
All objects within the class are then availible for use via a constructor.
The describe function just prints all information regarding an menuItem to console.

<pre>
class MenuItem {
  name: string;
  ingredients: string[];
  prices: Record<Size, number>;
  calories: Record<Size, number>;

  constructor (
  name: string,
  ingredients: string[],
  prices: Record<Size, number>,
  calories: Record<Size, number>,
  ) {
    this.name = name;
    this.ingredients = ingredients;
    this.prices = prices;
    this.calories = calories;

  }

  describe(): void {
    console.log(this.name, "constains: ", this.ingredients.join(", "));
    console.log("Prices: ", this.prices);
    console.log("Calories: ", this.calories);
  }
}
  </pre>

We can create an item with the following...

<pre>
  // Create New MenuItems here 
const PapayaSunrise = new MenuItem(
  "Papaya Sunrise",
 ["papaya", "strawberry", "peach"],
 {small: 5.15, medium: 5.75, large: 6.55}, 
 {small: 190, medium: 280, large: 330}
 )
</pre>

To push new menuItems into the menu.
We create a menu class.
Then we use the command addMenuItem(item: MenuItem); 
This allows us to push our newly created object for later use.

<pre>
class Menu {
  private items: MenuItem[] = [];

    addMenuItem(item: MenuItem): void {
      this.items.push(item);
    }

    findMenuItems(ingredient: string): MenuItem[] {
      return this.items.filter(item => item.ingredients.includes(ingredient.toLowerCase())
      );
    }

    listAllItems(): void {
      this.items.forEach(item => item.describe());
    }
}

const menu = new Menu();
</pre>

[Jamba Juice TypeScript Here](https://tinyurl.com/yc84a74x)
