---
layout: post
title:  "Your classes should keep secrets"
date:   2024-10-30 17:43:48 +0200
categories: jekyll update
---

As software engineers, we all know what encapsulation is. For me, it's the best OOP principle, which could save you a lot of headaches in the long run. 
One thing that is constant in software engineering is requirement change. While you are developing a feature, requirements might change multiple times either from stakeholders or developers. This is still a cheap solution because you can adapt everything before your PR is merged. Once your changes are in production, every new requirement will require additional work or even refactoring if you haven't followed OOP principles correctly. 

During refinements and ticket creation, identify parts of the feature that are likely to be changed in the future. Even the smallest doubt that part of the system will change deserves a separate cohesive class, which would do one thing. Treat those classes as your house and expose minimum public API outside while keeping everything else secret. You don't want everybody to know what's in your house right? 

To give you an example, let's say you have part of the feature which should handle pizza orders. You would have some classes with only one public method, makeOrder(), which will be exposed. Everything else should be private, and if other dependencies are needed, such as UserCredentials or Receipt, then inject those, and you'll have even easier testing. Another example is changing UI components based on remote field change or database entry. All those points are named business logic, which are the core values of your software.

All of this should be followed anyway if you want to have cleaner and testable code. I would extract this principle as the first one to apply even before typing any code. Take a look at the complete feature, identify points that might change a lot, and write those tiny classes, preferably with a single exposed public method. 

When requirements change, you will have to deal with changing one of those tiny classes that do exactly one thing and have one reason for a change.  If you want to go a step further, incorporate TDD, and you'll be confident about all the cases being covered, and your code won't break anything else.
