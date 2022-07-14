# Project Plan

Pod Members: Jenny Lee, Aligary Patawaran, Dylan Cocoletzi

## Problem Statement and Description

- People struggle keeping up with the new sneaker releases and have to resort to paying highly inflated prices.
- Target audience: people who are interested in purchasing sneakers

The main purpose of our project is to create a platform for sneaker consumers to view trends and stats regarding their favorite products. This app will also be used to notify consumers regarding sneaker launches. 

## User Roles and Personas

- Reseller: a user who is looking to sell sneakers that they bought from someone else
- Everyday consumer: a user who is interested in browsing for sneakers and does not have much knowledge about them

Reseller
1. Ian is a local reseller in Los Angeles who just opened their brand new retail store Codepath Kicks at Melrose. He is a 19 years old entrepreneur who as a kid loved the shoe world and is ready to pursue his passion. The most important part of being a successful reseller is to have wide size ranges, shoe options, and new exclusive shoes. He is using our sneaker webpage to see when shoes are dropping, check the market price when selling and trading shoes, and where to obtain the new releases. He will mainly use our webpage on his phone in hopes of building his business.
2. Charlie is a 40-year-old reseller who can’t sell any shoes because he is unfamiliar with today’s mainstream fashion. He will be using our app to explore sneaker trends to update his inventory in hopes of being able to make money again.

Everyday Consumer
1. John, a 20-something-year-old, is looking to purchase his first pair of Jordans. He has not done much research on which sneakers he wants. He is looking to purchase a pair in the next 2 months. John will be using our webpage on his desktop to research which shoes fit his style and budget. Since he has little knowledge of the sneaker world, he will be using our app to see which shoes are popular.
2. Elizabeth is a mother of two teenagers. She is looking forward to buying them some new sneakers for the upcoming school year. She will be using our website to look for sneakers within a specific price range for a size 8 and a size 6. She hopes to find something that is trending and stylish.

## User Stories

1. As a reseller, I want to look for information about shoe sizes, so that I know what sizes are available.
2. As an everyday consumer, I want to look for information about shoe prices, so I can make the best purchase with my budget of $200.
3. As a reseller, I want to look for information about shoe stock for new incoming sneakers, so I can see how rare this shoe is going to be and predict its future value.
4. As a reseller, I want to look for information about shoe releases, so that I am prepared and don’t miss out on a new drop.
5. As an everyday consumer, I want to look for information about price history, so that I know I will be getting my money’s worth on a particular shoe.
6. As an everyday consumer, I want to see popular sneakers, so that I can browse through sneakers for something that I like that I have not seen before.
7. As an everyday consumer, I want to be able to register and log into an account, so that I can save sneakers into a wishlist and get personalized recommendations .
8. As an everyday consumer, I want to be able to save sneakers into a wishlist for my account so that I can view them later and on multiple devices.
9. As an everyday consumer, I want to sign up for email updates on sneakers. I will not check back on this site daily, but I do check my email everyday. This email feature will ensure that I am notified as quickly as possible.
10. As a reseller, I want to look for information about the sizes, prices, and stock for new incoming sneakers and releases. I want to look for this information because I want to increase my inventory.
11. As an everyday consumer, I am looking for a one-stop site to find all of the information that I need. I need a beginner-friendly site that will educate me about what I should be looking for in my next purchase.
12. As a reseller, I want to be able to see people’s asking price on a sneaker so that I can sell to them.
13. As an everyday consumer, I want to be able to see people’s bids on a sneaker to see if I can compete with them.
14. As an everyday consumer, I want to be able to contact the company so that I can ask them questions regarding their website. I also want to follow the company on social media.
15. As an everyday user, I want to be able to see similar sneakers to the one I am currently viewing so that I can explore other sneakers.

## Pages/Screens

List all the pages and screens in the app. Include wireframes for at least 3 of them.
[Hi-Fi Figma Wireframes](https://www.figma.com/file/U9nXsh6TG035u4lbtd5ohS/Untitled?node-id=0%3A1)

- Landing page
- Login page
- sign up page
- search results page
- trending shoes page
- profile page
- product details page

## Data Model

Describe your app's data model using diagrams or tables

**User table**
| Column name |  type  |      description     |
|---|---|---|
|     id      |      number     |       Primary key        |
|    email    |      string     |   User’s email address   |
|   password  |      string     |      User’s password     |
|  first_name |      string     |     User’s first name    |
|  last_name  |      string     |     User’s last name     |
|   country   | string(optional)|      User's country      |
|  shoe_size  | number(optional)| User's default shoe size |



**User Wishlist item**
| Column name |  type  |                     description                   |
|---|---|---|
|     id      |   number  |                    Primary key                    |
|   user_id   |   number  | Foreign key references User(id) on delete cascade |
|   shoe_id   |   number  | Foreign key references Shoe(id) on delete cascade |
|  created_at | Timestamp |         Time the wishlist item was created        |



**Shoe table**
|   Column name |   type  |     description     |
|---|---|---|
|      id      | number  |    Primary key      | 
|      name    | string  | Name of shoe model  |
|    brand     | string  |    Brand of shoe    |
| release_date |  date   |  Shoe release date  |
| description  | string  | Description of shoe |
|     price    | number  |   Price of shoe     |
|    img_url   |  text   |     Image url       | 


## Endpoints

List the API endpoints you will need to implement.

|  CRUD  | HTTP Verb |            Description           | Route | Request Body | Response Body |        User Stories         |
|---|---|---|---|---|---|---|
|  Read  |    GET    |    Get a shoe by search term     | BASE_URL/search?search_term | Search_term : STRING | Shoes: [{‘shoe’}] |        1,2,3,5,10,11,15      |
| Create |    POST   |     Create a new user account    | BASE_URL/auth/register | first_name: STRING, last_name: STRING, email: STRING, password: STRING, Country: STRING, Shoe_size: Number | { id: int, email: string, first_name: string, last_name: string, country: string, shoe_size: int } |               7              |
|  Read  |    GET    |        List trending shoes       | BASE_URL/trending | | {‘trending’: [{‘shoe’}]} |        1,2,4,5,6,10,11       |
| Update |   POST    |      Add shoe to wishlist        | BASE_URL/wishlist | Shoe_id: number | |            7,8              |
| Delete |  DELETE   |     Remove shoe from wishlist    | BASE_URL/wishlist | Shoe_id: number | |            7,8              |
| Update |   POST    |        Log in to account         | BASE_URL/auth/login | Email: STRING, Password: STRING | { id: int, email: string, first_name: string, last_name: string } |               7              |
|  Read  |    GET    |      Get a shoe by shoe id       | BASE_URL/product/:id | Shoe_id: number | Shoes: [{‘shoe’}] |  1,2,3,4,5,10,11, 12, 13, 15 |
| Create |    POST   | Send/receive emails to/from user | BASE_URL/email | Email: STRING, User_id: number | “Successfully sent email” |           9, 14            |


***Don't forget to set up your Issues, Milestones, and Project Board!***
