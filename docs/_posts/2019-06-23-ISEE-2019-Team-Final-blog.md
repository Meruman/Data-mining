---
layout: post
title: "ISEE 2019: Testing And Test Case Design"
---
Welcome to our fourth blog entry of this project. In this entry we will inform you about our progress and about testing in *Catch Your Mon€y*

# TESTING AND TEST CASE DESIGN
## What is Testing?

The following picture shows why we test applications and what exactly testing is.
![What is Testing?]({{site.baseurl}}/images/firstone.jpg){:height="100%" width="100%"}
## Types of software testing

Testing can be broken down to different types of software tests shown in the picture below. In this blog entry we mainly focus on the functional testing.
![Types of software testing]({{site.baseurl}}/images/secondone.jpg){:height="100%" width="100%"}
## Testing Classification

![Testing Classification]({{site.baseurl}}/images/thirdone.jpg){:height="100%" width="100%"}

# BLACK BOX TESTING
## What is Black Box Testing?

Black box testing is a method of software testing, in which tests are developed on the basis of the requirements . This tests are developed without knowledge of the inner implementation of the system under test. The program is treated as a black box . Only externally visible behavior flows into the test.

![What is Black box Testing?]({{site.baseurl}}/images/fourthone.jpg){:height="100%" width="100%"}

The purpose of this test is to check the compliance of a software system with its specification. The software to be examined is considered as a whole, only its external behavior is used in the evaluation of the test results.

This method attempts to find errors in the following categories:

* Incorrect or missing functions
* Interface errors
* Errors in data structures or external database access
* Behavior or performance errors
* Initialization and termination errors

Black Box Testing method is applicable to the following levels of software testing:
* Integration Testing
* System Testing
* Acceptance Testing 

## Black Box Test Scenarios
The following table shows 5 exemplary scenarios for the black box testing method we applied to our app.

![CASES]({{site.baseurl}}/images/excel.jpg){:height="200%" width="200%"}


# WHITE BOX TESTING
## What is White Box Testing?

The white box testing refers to a method of software testing in which the tests are developed with knowledge of the inner workings of the software under consideration.

![What is White Box Testing?]({{site.baseurl}}/images/fifthone.jpg){:height="120%" width="120%"}

For the examination of subsystems and the inner working of the system, we used White Box Testing.

White box testing techniques include:

* Statement Coverage: This testing technique verifies whether every line of code executes at least once.
* Branch Coverage: This testing technique verifies whether every branch executes at least once.
* Path Coverage: This testing technique inspects all of the paths described by the program.

White Box Testing method is applicable to the following levels of software testing:

* Unit Testing
* Integration Testing
* System Testing

In the following we have a look at the code snippets of some examples of the white box testing.

## Code Snippet-Login Activity

In the Login activity the user needs to enter his/her password. If the passphrase is entered correctly the user is redirected to the home screen. If not a message pops up to inform the user that he/she entered the wrong password.

![Code Snippet-Login Activity]({{site.baseurl}}/images/lastbut6.jpg){:height="150%" width="150%"}

## Code Snippet-Add Category
In this method the user should enter a new for his/her new category and choose a corresponding icon.
If no name is entered the users sees a warning message that a name has to be entered. In case the name and icon are selected the category will be added to the app.

![Code Snippet-Add Category]({{site.baseurl}}/images/lastbut5.jpg){:height="150%" width="150%"}

## Code Snippet-Add Transaction

For adding a transaction the user needs to enter the type, category, date, amount and payment method. If one or multiple of these inputs are missing a warning messages will pop up. Otherwise the transaction is stored in the database.

![Code Snippet-Add Transaction]({{site.baseurl}}/images/lastbut4.jpg){:height="150%" width="150%"}

![Continuation....]({{site.baseurl}}/images/lastbut3.jpg){:height="150%" width="150%"}

## Code Snippet-Delete Category

Category selection and the selected category can be deleted. Moreover, for the confirmation for the category deletion, an "Alert confirmation message" is shown as well. The category is only delete if the user varifies it in the alert message.

![Code Snippet-Delete Category]({{site.baseurl}}/images/lastbut2.jpg){:height="150%" width="150%"}

## Code Snippet-Home screen buttons

On the home screen depending on what button the user presses he/she will be redirected to the corresponding screen.

![Code Snippet-Home button]({{site.baseurl}}/images/lastbut1.jpg){:height="150%" width="150%"}

## Summary of Changes

* We have implemented the "budget planning" option, such as,

 1. The user can define a 'monthly budget' for a particular category of his choice. Moreover, the user can also view the history of the     previously added budgets.
 
 2. With every new transaction, the system will check if the user has exceeded the limited amount of the budget or not. Incase the user     has exceeded the limit, he/she will be notified by an "Alert Message".

* We have also changed the Home Screen, to make it more user friendly.

* Minor changes in the User Interface. Also, some modifications in the Bar Chart and Pie Chart for an easier visualization of the          history of transactions with respect to the 'expense/income' and 'categories' respectively.

That is all for now! It has been a real good experience!
If you want to check out our app, you can download it [here](https://github.com/DBSE-teaching/isee2019-NOOBS.apk/blob/master/Apk%20files/CatchYourMoneyV03.apk)!

_**Thanks for visting our blog!**_
