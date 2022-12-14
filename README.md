# Skewy App

## Demo Day video walkthrough

<img src='https://github.com/Skewy-App/Skewy/blob/main/Demoday.gif'/>

## Build Sprint (Final) video walkthrough

Here's a walkthrough of implemented user stories:
All user stories are working as intended. will now spend time preparing our presentation and make appeal-based changes to the app.

<img src='https://github.com/Skewy-App/Skewy/blob/main/Skewy_FinalSprint.gif' />



## Build Sprint 3 video walkthrough

Here's a walkthrough of implemented user stories:
this week we are pretty much done with necessary user stories so I tried doing different doing approaches of what we had and changed anything that could've been made more practical for the user, or simply went better with the app layout.

<img src='https://github.com/Skewy-App/Skewy/blob/main/Skewy_Sprint3.gif' />


## Build Sprint 2 video walkthrough

Here's a walkthrough of implemented user stories:

<img src='https://github.com/Skewy-App/Skewy/blob/main/Skewy_Sprint2.gif' />



## Build Sprint 1 video walkthrough

Here's a walkthrough of implemented user stories:

<img src='https://github.com/Skewy-App/Skewy/blob/main/Skewy_Sprint1.gif' />





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

- [x] Technician would be able to create their own account.
- [x] Technician would login with their own credentials.
- [x] Technician can add a new work order.
- [x] Orders in progress can be viewed.
- [x] Past service orders with all details can be viewed.

**Optional Nice-to-have Stories**

- [ ] Having a timer next to each estimated finish time which would start when the entry is submitted.
- [ ] Adding status updates on each service order.

### 2. Screen Archetypes

- [x] LogIn/SignUp
   * User can create a new account if it's their first time, or simpy log in with their existing credentials.
* Feed
   - [x] User can view all service orders currently in progress.
   - [x] User can tap on any of the work orders to reveal all details, including: car description, main technician working on the car, customer info, billing info, estimated time for the repair, and what exactly the car needs.
   
* Add an order
   - [x] User can add all the same type of info they were able to view on the feed entired except on an entry that they've now created.
 
* Past orders
   - [x] This screen will look very similar to the feed, except it'll be made up of all past orders that have been completed.
   
   

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
   
## Wireframes
<img src="https://github.com/Skewy-App/Skewy/blob/main/Skewy%20paper%20wireframe.jpg" width=600>


## Schema 

### Models
**Post**

|    Property     |   Type   |                      Description                         |
| --------------- | -------- | -------------------------------------------------------- |
| objectId        | String   | unique id for the user post (default field)              |
| licensePlate    | String   | each car???s tag number                                    |
| technicianName  | String   | main technician working on the vehicle                   |
| vehicleChar     | String   | vehicle identifying information                          |
| finishTime      | DateTime | expected end time of car maintenance                     |
| serviceInfo     | String   | details of the work being done on the car                |
| timeTaken       | Number   | total time taken from start to finish (past orders tab)  |
| serviceName     | String   | name of service done as it would appear on the bill      |




### Networking
**List of network requests by screen**
* In Progress
  * (Read/GET) Query all posts where ???Complete??? is NOT selected.
  ```swift
  let query = PFQuery(className:???Status???)
  query.whereKey(???Status???, equalTo: NotComplete)
  query.findObjectsInBackground { (orders: [PFObject]?, error: Error?) in
   if let error = error { 
      print(error.localizedDescription)
   } else if let orders = orders {
      print("Successfully retrieved \(orders.count) orders.???)
   }  }
  ```
  * (Update/PUT) Edit existing work order.
  ```swift
     let query = PFQuery(className:"orders")
     query.getObjectInBackground { (orders: PFObject?, error: Error?) in
   if let status = "Complete" {
       print(error.localizedDescription)
   } else if let status = NotComplete {
     orders["InProgress"] = true
     orders.saveInBackground()
    }}
  ```
  * (Delete/DELETE) Delete existing work order.

  ```swift
  query.findObjectsInBackground { (orders, error) in
        if error == nil,
            let status = ???NotComplete??? {
            for orders in ???InProgress??? {
                order.deleteInBackground()
            }}
    ```
* Add Order
  * (Create/POST) Create a new order
  ```swift
  let query = PFQuery(className:"AddOrder")
        query.includeKeys(["licensePlate", "technicianName", "vehicleChar", "finishTime", "serviceInfo"])
  ```

* Past Orders
  * (Read/GET) Query all posts where ???Complete??? is selected.
  ```swift
  let query = PFQuery(className:???Status???)
  query.whereKey(???Status???, equalTo: Complete)
  query.findObjectsInBackground { (orders: [PFObject]?, error: Error?) in
   if let error = error { 
      print(error.localizedDescription)
   } else if let orders = orders {
      print("Successfully retrieved \(orders.count) orders.???)
   }  }
  ```

  

