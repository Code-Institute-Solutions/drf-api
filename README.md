# Moments - API
## Project description
Moments is a social media platform. It has been designed for its users to share their life's moments. The application consists of the React app and an API. Welcome to the Django Rest Framework API project section.

## User stories
| Category  | as | I want to           | so that I can                                                                                    | mapping API feature                          |
| --------- | -------- | ------------------------------ | ------------------------------------------------------------------------------------------------ | -------------------------------------------- |
| auth      | user     | register for an account        | have a personal profile with a picture                                                           | dj-rest-auth<br>Create profile (signals)     |
| auth      | user     | register for an account        | create, like and comment on posts                                                                | Create post<br>Create comment<br>Create like |
| auth      | user     | register for an account        | follow users                                                                                     | Create follower                              |
| posts     | visitor  | view a list of posts           | browse the most recent uploads                                                                   | List/ Filter posts                           |
| posts     | visitor  | view an individual post        | see user feedback, i.e. likes and read comments                                                  | Retrieve post                                |
| posts     | visitor  | search a list of posts         | find a post by a specific artist or a title                                                      | List/ Filter posts                           |
| posts     | visitor  | scroll through a list of posts | browse the site more comfortably                                                                 | List/ Filter posts                           |
| posts     | user     | edit and delete my post        | correct or hide any mistakes                                                                     | Update property<br>Destroy property          |
| posts     | user     | create a post                  | share my moments with others                                                                     | Create post                                  |
| posts     | user     | view liked posts               | go back often to my favourite posts                                                              | List/ Filter posts                           |
| posts     | user     | view followed users' posts     | keep up with my favourite users' moments                                                         | List/ Filter posts                           |
| likes     | user     | like a post                    | express my interest in someone's shared moment                                                   | Create like                                  |
| likes     | user     | unlike a post                  | express that my interest in someone's shared moment has faded away                               | Destroy like                                 |
| comments  | user     | create a comment               | share my thoughts on other people's content                                                      | Create comment                               |
| comments  | user     | edit and delete my comment     | correct or hide any mistakes                                                                     | Update comment<br>Destroy comment            |
| profiles  | user     | view a profile                 | see a user's recent posts + post, followers, following count data                                | Retrieve profile<br>List/ filter posts       |
| profiles  | user     | edit a profile                 | update my profile information                                                                    | Update profile                               |
| followers | user     | follow a profile               | express my interest in someone's content                                                         | Create follower                              |
| followers | user     | unfollow a profile             | express that my interest in someone's content has faded away and remove their posts from my feed | Destroy follower                             |

## Entity Relationship Diagram
![ERD](https://res.cloudinary.com/dgjrrvdbl/image/upload/v1649155000/moments-api-erd_aw81vx.png)

## Models and CRUD breakdown
| model     | endpoints                    | create        | retrieve | update | delete | filter                   | text search |
| --------- | ---------------------------- | ------------- | -------- | ------ | ------ | ------------------------ | ----------- |
| users     | users/<br>users/:id/         | yes           | yes      | yes    | no     | no                       | no          |
| profiles  | profiles/<br>profiles/:id/   | yes (signals) | yes      | yes    | no     | following<br>followed    | name        |
| likes     | likes/<br>likes/:id/         | yes           | yes      | no     | yes    | no                       | no          |
| comments  | comments/<br>comments/:id/   | yes           | yes      | yes    | yes    | post                     | no          |
| followers | followers/<br>followers/:id/ | yes           | yes      | no     | yes    | no                       | no          |
| posts     | posts/<br>posts/:id/         | yes           | yes      | yes    | yes    | profile<br>liked<br>feed | title       |

## Tests
- Posts app:
    - logged out users can list posts
    - logged in users can create a post
    - logged out users can't create a post
    - logged out users can retrieve a post with a valid id
    - logged out users can't retrieve a post with an invalid id
    - logged in users can update a post they own
    - logged in users can't update a post they don't own

## Deployment steps
- set the following environment variables:
    - CLIENT_ORIGIN
    - CLOUDINARY_URL
    - DATABASE_URL
    - DISABLE_COLLECTSTATIC
    - SECRET_KEY
- installed the following libraries to handle database connection:
    - psycopg2
	- dj-database-url
- configured dj-rest-auth library for JWTs
- set allowed hosts
- configured CORS:
	- set allowed_origins
- set default renderer to JSON
- added Procfile with release and web commands
- gitignored the env&#46;py file
- generated requirements.txt
- deployed to Heroku

---

Happy coding!
