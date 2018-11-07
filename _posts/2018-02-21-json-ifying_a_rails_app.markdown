---
layout: post
title:      "JSON-ifying a Rails App"
date:       2018-02-21 12:11:19 -0500
permalink:  json-ifying_a_rails_app
---


Up to this point, each portfolio project was built from scratch.  First a Ruby GEM that scrapped a recipe site providing a CLI interface for a user to search recipes.  Then a Sinatra app that provided a basic homeschool tracker to record subjects for multiple children implementing REST conventions.  Then, building on the understanding gained from Sinatra, a Rails app allowing users to track their personal book libraries, including the ability to make multiple notes and comments on each book.

But that 'from-scratch' approach has taken a detour this the current project.  Instead of a new app from scratch, I a took that Rails app and have JSON-ified the front end, while keeping the Rails backend.  

First, I added a serializer using the `gem 'active_model_serializers'`

Next, I modified my backend methods to handle JSON.  My index, show and create actions will now return data in JSON format:

```
def index
    @books = Book.all
    respond_to do |f|
      f.html
      f.json {render json: @books}
    end
  end
```
	
This index action is hit when the user clicks on "See Your Books".  It returns the users' entire collection of books. The goal in this project is to display the returned information without reloading the page.  Do to this I first have to attach an event listener to that button so that when the button is clicked, that click is *heard*.  Next, I want to prevent that click from it's normal, defaul action of loading a show page.  Instead I want to retrieve the information from the database, return that information to the browser and replace the current html on the same view page with the new information.


```
const bindIndexPage = () => {
  $('.allBooks').on('click', (e) => {
    e.preventDefault(e)
```

 This attaches a click handler onto the button that has a class="allBooks"
 
   const url = e.currentTarget.attributes[1].value

    fetch(`${url}.json`, {
      credentials: 'include'
    })
        .then(res => res.json())
        .then(data => {
    
		 Retrieves the URL target
		 Uses the fetch api to make the data request to the backend. 
		 Take the retrieved data and puts it into json format


      ```    let uniqueBooks = UniqueBookList(data)```
				
		 returns an array of unique book objects so that no book title is repeated

          ```
  $(".app-container").html('').append(`<h1>Your Books</h1><table><tbody class='book-list'><tr>
                    <th class="table"> Title </th>
                    <th class="table"> Author </th>
                    <th class="table"> Category </th>
                    </tbody></table>`)
```

Creates the table format I will want to use as the display

```
uniqueBooks.forEach(book => {
	book.user_id = data.id
	let newBook = new Book(book)
	let bookHtml = newBook.formatIndex()
	$(".book-list").append(bookHtml)
})})
})}
```



Iterates through each book object, utilizes helper methods to format the books data and on each iteration appends that formatted book data onto the webpage.

The requirements for this project were that an index page, a view and a form were converted over, so much of the original code remains where a complete http request cycle takes place, however I now have the confidence and skill to know that I can either convert an existing app or write one from scratch that uses AJAX to create a single page app.




