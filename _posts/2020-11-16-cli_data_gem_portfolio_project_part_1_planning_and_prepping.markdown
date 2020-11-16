---
layout: post
title:      "CLI Data Gem Portfolio Project Part 1: Planning and Prepping"
date:       2020-11-16 20:07:03 +0000
permalink:  cli_data_gem_portfolio_project_part_1_planning_and_prepping
---


It has taken me longer than I hoped to get to this point in the curriculum, but I am excited to finally be starting the first project! I am doing my best to balance overseeing online learning for my 1st and 3rd graders, bootcamp coursework, and the added stress of every day living during a pandemic. So here we go!

Step number one was to come up with an idea and find a scrapable website to help implement it. I came up with the idea of an app that scrapes local restaurant data, returns to the user an option of food categories (such as "pizza", "fast food", "burgers', "pub food", "asian", etc), and then returns a list of restaurants that fit that category in your area. Choosing a restaurant name would return to the user the location, phone number, and a description for that restaurant. The website I chose was restaurantji.com, since it has a consistent html/css layout. I have experience with bulding websites with HTML and CSS, so I was pretty confident this site would work, but I ran it through the Scraper Checker tool listed in the project planning resources lesson just to be safe. 

The next step for me was to just sit and watch all of the recorded lectures and the Eden Project live build videos. I found them all to be immensely helpful. I will admit I was overwhelmed after reading the project requirements, and these resources were highly valuable. If you are a fellow student reading this blog post, I **highly** recommend that you don't skip over reviewing these resources. 

I also took the time to figure out how to represent my app in the form of a wireframe flowchart using draw.io. This was also very helpful, as I was able to hash out the basics of how I want my app to behave, what classes I will need, and how the CLI should run. Here is the first iteration (I am sure I will update this later as I work on my project): [TakeoutFinder Flowchart](https://drive.google.com/file/d/1_1dVGuF77mXSKIldd9_1agTrj4FksGUq/view)

Finally, I was ready to get started. I used the recommended IDE link in the CLI Data Gem Portfolio Project lab. This is the IDE sandbox, so I cleared out the files I had previously worked on to start with a blank slate. I then used bundler to create my gem's file structure. I ran `bundle gem takeout_finder`, answered no when asked if I wanted to generate tests, yes when asked if I wanted to generate a MIT license, and yes when asked if my gem should include a code of conduct. With the file structure created, my next step was to get the repo set up on GitHub so I didn't lose my work. 

Doing this step in a project always feels daunting to me for some reason. But here's how it went: 
I ran `cd takeout_finder` to move into my gem's directory, then `git status`. I could see the list of new files ready to be added and committed. I made a minor change to the generated README.md file, ran `git add -m README.md`, followed by `git commit -m "initial commit"`. Now that git is tracking my project, I can get the repo added to GitHub. In my GitHub profile, I chose "create new repo" and named it the same as my gem. On the next page, I followed the instructions for uploading existing files to the repo and (thankfully) ran into no errors. After those steps were complete, I was able to run the `git log` command to see that my initial commit showed up in the commit history. 

The last step for today is to get the executable bin file working. I created a new file in the bin directory and named it takeout_finder. I ran my new file to find (unsuprisingly) that it did not have executable permissions. Running `cd bin`, `ls -lah`, and then `chmod +x takeout_finder` gives executable permission to my new bin file. I ran the `ls -lah` command again to verify. Changing directory back to takeout_finder, I am now able to add a puts line in my bin/takeout_finder file and run `./bin/takeout_finder` in the console, and it sucessfully runs my puts line. 

I'm all set now to get my files talking to each other correctly so I can get down to coding the functionality for my app! The next step is to get my CLI class running with some fake data. Check back later for Part 2!




