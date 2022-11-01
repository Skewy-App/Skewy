# Skewy App

## Table of Contents
1. [Overview](#Overview)
2. [Product Spec](#Product-Spec)
3. [Wireframes](#Wireframes)
4. [Schema](#Schema)

## Overview
### Description
Keeps track of vehicles currently being operated on in an auto repair shop. Technician will be able to include details of the repair, estimated wait time, if there are any delays, and billing information all in one area. 

### App Evaluation
[Evaluation of your app across the following attributes]
- **Category:** Auto Repair
- **Mobile:** Our main focus will be developing Skewy for mobile phone use. Having been to auto repair shops countless times ourselves, we've noticed that the technicians always have a work mobile device on their person to keep info updated.
- **Story:**  The way auto repair technicians update info is by texting/emailing updates to each other for those updates to later have to be re-uploaded onto the customer profile. Skewy both saves time, and contributes to decreasing margin of error. 
- **Market:** Our main target user base would be auto repair technicians, however the app will be designed in a way that any service-based business would be able to utilize it. 
- **Habit:** This app would be able to replace the current lacking reporting system in the auto repair industry, and would increase productivity on daily basis. 
- **Scope:** Our goal with the first launch of Skewy is to have it serve convenience and delegation in an auto repair shop by seeing which technician is working on what, and how long it took them to complete that task. Moving forward, we can see Skewy growing to be an application which can be used by different shops simultaneously so a chain can see their overall numbers in terms of how long each type of repair takes on average.

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* Technician would be able to create their own account.
* Technician would login with their own credentials.
* Technician can add a new work order.
* Orders in progress can be viewed.
* Past service orders with all details can be viewed.
* Technician can create/edit a bill, or formulate a quote for the customer.

**Optional Nice-to-have Stories**

* Having a timer next to each estimated finish time which would start when the entry is submitted.
* Adding status updates on each service order.

### 2. Screen Archetypes

* LogIn/SignUp
   * User can create a new account if it's their first time, or simpy log in with their existing credentials.
* Feed
   * User can view all service orders currently in progress.
   * User can tap on any of the work orders to reveal all details, including: car description, main technician working on the car, customer info, billing info, estimated time for the repair, and what exactly the car needs.
   
* Add an order
   * User can add all the same type of info they were able to view on the feed entired except on an entry that they've now created.
 
* Past orders
   * This screen will look very similar to the feed, except it'll be made up of all past orders that have been completed.
   
* Billing
   * User can create a new bill or quote which would autmatically provide the total by adding up all recorded charges and fees.
   

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Feed
* Add an order
* Past orders
* Billing
* Logout

**Flow Navigation** (Screen to Screen)

* LogIn/SignUp (after credentials are entered)
   * Enters to the feed of In-progress orders with tab bar controller on the bottom.
       * If an entry is tapped, then the user is moved to a screen where all details regarding that work order can be viewed. 
* Add an Order
   * Takes user to the screen where they can create a new work order with all the car, customer, and service details; with tab bar controller on the bottom.
* Past orders
   * Jumps to another feed screen, this time consisting of all past/completed work orders; with tab bar controller on the bottom.
      * Tapping any entry would, again, move to a page consisting of all order details.
* Billing
   * User would be able to create a new bill outlining all cost details, as well as a quote for customers who are simply requesting an estimate on their repairs.
   
## Wireframes
[Add picture of your hand sketched wireframes in this section]
<img src="https://github.com/Skewy-App/Skewy/blob/main/Skewy%20paper%20wireframe.jpg" width=600>

### [BONUS] Digital Wireframes & Mockups

### [BONUS] Interactive Prototype

## Schema 
[This section will be completed in Unit 9]
### Models
[Add table of models]
### Networking
- [Add list of network requests by screen ]
- [Create basic snippets for each Parse network request]
- [OPTIONAL: List endpoints if using existing API such as Yelp]
