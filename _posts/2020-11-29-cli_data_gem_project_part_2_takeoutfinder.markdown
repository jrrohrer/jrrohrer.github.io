---
layout: post
title:      "CLI Data Gem Project Part 2: TakeoutFinder "
date:       2020-11-29 15:00:05 -0500
permalink:  cli_data_gem_project_part_2_takeoutfinder
---


It's done! (For now...)
[Here's the github repo if you want to check out the code](https://github.com/jrrohrer/takeout_finder)

After getting all of the initial setup for the gem done, I was finally able to layout my gem's functionality. There were a few decisions that I had made prior to starting to write code that ended up being dictated by the data and the layout of the website I am scraping. The flow of my gem is this:

1.     User starts app
2.     User is presented with a greeting and asked for two inputs (state, city). This is necessary to get the correct URL for              the city they want to search.
3.     New scraper is created with user input which collects data and creates category and restaurant objects
4.     User is presented with a list of restaurant categories
5.     User selects a category
6.     User is given a list of restaurants in that category
7.     User selects a restaurant
8.     User is given details for that restaurant (name, location, phone number, description)
9.     User is asked if they are done or if they want to start over. If done - exit, if start over - begin program again.

At any point, if the user types "exit" as a response to a prompt, the program will end. If they misspell a city name or enter an invalid state code, they will get a custom error that asks them to check their spelling and exits the program so they can start again. 

Initially, I was going to scrape just one city for restaurant suggestions, but decided that would give my program kind of a narrow focus. There is a #query method in the CLI class that greets the user and asks for two inputs: city and state. These inputs are stored as local variables and then used as arguements for the call to the Scraper class, which is instantiated with state and city arguements that get concatenated into the URL to be scraped. This allows the user to search any city for takeout. The previously mentioned custom error is also part of this #query method. Once the user enters their information, a new scraper is instantiated. This scrapes the website, then creates the Category and Restaurant objects. 

I waffled a little bit over whether the category and restaurant data should be handled by one class or two, and decided on two because it allows for more abstraction. The Category class is responsible for tracking the available restaurant categories in a given city, and it knows about the restaurants in each category. The Restaurant class stores data re: individual restaurants and is responsible for returning details about individual restaurants. It seemed like too much responsibility for one class. 

The Scraper class is responsible for scraping the custom URL for data re: available categories in the given city, and the details for the individual restaurants in the city. It collects the appropriate data, then stores it in individual category and restaurant objects. I had the Scraper instance methods that scrape for the data immediately use that data to create the appropriate objects. 

Understanding the self keyword was essential to creating this gem. The Category class and Restaurant class both use the self keyword at the class level to keep track of all of their instances. 

```
    def self.all
        @@all
    end
```

These can be used by calling:  `TakeoutFinder::Category.all` or  `TakeoutFinder::Restaurant.all` The return value would be an array of Category or Restaurant objects

The Category class uses a method just like one in an earlier lab to return a list of all the restaurants that belong to a category instance using the self keyword at the instance level:

```
def restaurants
        # creates array of restaurant objects with a category that matches the category instance.
        TakeoutFinder::Restaurant.all.select {|restaurant| restaurant.category == self.name}
end
```

Self in this method refers to the individual instance of Category. Maybe someone wants pizza. This method would return all the restaurants which have a category of "pizza". So self.name in this instance is "pizza". 

Overall, completing this project was a great learning experience. I am much more comfortable with using git, creating a file system with bundler, and thinking through how I want a program to work and then implementing it. I am still not quite sure that I laid everything out correctly, or that the different responsibilities are in the correct places. so I am looking forward to the refactoring section of the project review. Wish me luck!


