---
layout: default
title: RESTful blog API example
parent: Projects
nav_order: 8
permalink: /restful-blog-api/
---
_This article is a README that I wrote for a small API project to get to know Rails APIs better._

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

### About

This is an example of a blog api (the first I've ever written) using Ruby version 2.6.5. It allows for the CRUD actions of Posts and Comments, using these entities as endpoints.

All in all, I think it was a great exercise because it gave me a chance to play around with a few things that I've been wanting to look at. Namely:

- How to create an API (up until now I didn't even know there was a separate --api flag in Rails...)
- Testing with RSpec
- An excuse to look into Docker more (still a long way to go with this one)
- Gems

The main gems used for this project were:

- pg: for PostgreSQL
- faker: for initial seed data
- factory_bot_rails: for testing purposes
- rspec_rails: for RSpec testing
- shoulda-matchers: to make our testing syntax/ structure a little cleaner

### Setup

To run this project yourself, clone the repository into whichever directory you wish, then `cd` into the project folder. Run `bundle`, then `yarn`, and finally run `rails db:setup` to create the database.

Once that's done, you can then run `rails s` to begin serving on localhost:3000

### Running Tests

Tests are created with RSpec and cover associations and validations, models, and controllers. To run tests, simply ´cd` into the blog-rest-api project folder, and then run rake.

Alternatively, if you'd like to run individual tests rather than every test together in one go, you can do the following as an example:

**Running Post model tests**

`rspec ./models/post_spec.rb`

**Running Post controller tests**

`rspec ./spec/controllers/api/v1/posts_controller_spec.rb`

If you get a bundle error, re-run the above commands prepended with bundle exec. E.g. `bundle exec rspec ./spec/controllers/api/v1/posts_controller_spec.rb`

The tests should now run successfully.

### Making Requests

To make CRUD requests to the Blog API, you can use Postman, Insomnia or similar. Both Post and Comment entities follow the same format.

**GET #index**

For Posts: Choose a GET request and enter [http://localhost:3000/api/v1/posts]() as the URL. Send the request.

For Comments: Choose a GET request and enter [http://localhost:3000/api/v1/comments] as the URL. Send the request.

**GET #show**

For Posts: Choose a GET request and enter [http://localhost:3000/api/v1/posts/3]() as the URL. Send the request. You should receive a list of all posts in the database

For Comments: Choose a GET request and enter [http://localhost:3000/api/v1/comments/5]() as the URL. Send the request. You should receive a list of all comments in the database along with the post that each comment belongs to.

**POST #create**

For Posts: Choose a POST request and enter [http://localhost:3000/api/v1/posts]() as the URL. Click on the Headers tab and in Key enter Content-Type. For the Value enter application/json. Then click on the Body tab and select raw. You can then enter your request like so:

```json
{
   "title":"A really cool title for a really cool post",
   "body":"Some really cool stuff to post goes here"
}
```

You can then send the request.

For Comments: Choose a POST request and enter [http://localhost:3000/api/v1/comments]() as the URL. Click on the Headers tab and in Key enter Content-Type. For the Value enter application/json. Then click on the Body tab and select raw. You can then enter your request like so:

```json
{
    "post_id":"6",
	"name":"Lars Ulrich",
	"body":"Really cool post!!!!"
}
```

Send the request.

In both cases, you should get a response with the status Success, with a message telling you that your post/ comment has been saved.

**PATCH/PUT #update**

For Posts: Choose a PUT request and enter [http://localhost/api/v1/posts/8]() as the URL (We're going to update post number 8 in this example). Click on the Headers tab and in Key enter Content-Type. For the Value enter application/json. Then click on the Body tab and select raw. You can then enter your request with the new post information. Like so:

```json
{
	"title":"Updated test post title",
	"body":"Updated test post body"
}
```

You can then send your request.

For Comments: Choose a PUT request and enter [http://localhost/api/v1/comments/13]() as the URL (We're going to update comment number 13). Click on the Headers tab and in Key enter Content-Type. For the Value enter application/json. Then click on the Body tab and select raw. You can then enter your request with the new comment information like so:

```json
{
	"post_id":"13",
	"name":"James Hetfield",
	"body":"Super awesome post!!"
}
```

Send your request.

Again, you should get a response saying that your comment has been updated successfully

**DELETE #destroy**

For Posts: Choose a DELETE request and enter [http://localhost/api/v1/posts/18]() as the URL. (We'll delete post number 18). Send your request, and the response you get should look something like:

```json
{

  "status": "Success",
  "message": "Post has been deleted",
  "data": {
	 "id": 18,
	 "title": "A random title for a random post",
	 "body": "Random post body content",
	 "created_at": "2020-04-08T13:15:09.641Z",
	 "updated_at": "2020-04-08T13:15:09.641Z"
  }

}
```

For Comments: Choose a DELETE request and enter http://localhost/api/v1/comments/10 as the URL. (We'll delete comment number 9). Send your request, and the response you get should look something like:

```json
{

  "status": "Success",
  "message": "Comment has been deleted",
  "data": {
	 "id": 10,
	 "post_id": 10,
	 "name": "Miss Marlin Gutmann",
	 "body": "Veniam ipsa doloremque. Voluptatem facere consequatur. Error ut numquam.",
	 "created_at": "2020-04-08T12:33:08.048Z",
	 "updated_at": "2020-04-08T12:33:08.048Z"
   }
}
```

### Learning Outcomes & Closing Notes

This project has taught me how to get started with building a simple API, which is something I definitely want to continue looking into. It's now made me think about turning a couple of other projects into APIs, to leverage at a later date.

It also introduced me to RSpec testing, which was far further down my list until this assignment. I now feel that I can confidently write basic tests for different aspects of an application e.g. model validations and associations, controller actions etc. Adding test to some of my other applications to continue practicing with RSpec is what I plan on doing next.

For the future, I need to look at how to pass data from user input to the API and then return a response. I spent some time looking at this, and I'm not sure whether it was just the fact I was overthinking the API aspect (which I still find midly scary), but it stumped me either way.

Middleware is also still quite a mystery to me. I did do some reading around it, but it seems like there's a lot of ground to cover. Rack CORS and understanding how it works seems to be a good starting point, I feel.

Finally, getting started with Docker has opened my eyes to its usefulness and I can definitely see the value. Although I still find it incredibly confusing, it's something I'd love to get stuck into properly when I have a bit more experience and could make more sense of it.