To start your mongo shell type the following command on CMD  :

mongosh


To create or switch to Database type the following command on CMD   :

use Database_LibraryDB


To create a collection or collections type the following command on CMD  :

db.createCollection("Books"),
db.createCollection("Authors"),
db.createCollection("Patrons")


To insert data into collection or collections type the following the following command on CMD  :


//BOOKS SECTION//

db.Books.insertMany([ { _id: 1, title: "1984", author_id: 1, genres: ["Dystopian", "Political Fiction"], published_year: 1949, available: true }, { _id: 2, title: "To Kill a Mockingbird", author_id: 2, genres: ["Southern Gothic", "Bildungsroman"], published_year: 1960, available: true }, { _id: 3, title: "The Great Gatsby", author_id: 3, genres: ["Tragedy"], published_year: 1925, available: true }, { _id: 4, title: "Brave New World", author_id: 4, genres: ["Dystopian", "Science Fiction"], published_year: 1932, available: true }, { _id: 5, title: "The Catcher in the Rye", author_id: 5, genres: ["Realist Novel", "Bildungsroman"], published_year: 1951, available: true }, { _id: 6, title: "Moby-Dick", author_id: 6, genres: ["Adventure Fiction"], published_year: 1851, available: true }, { _id: 7, title: "Pride and Prejudice", author_id: 7, genres: ["Romantic Novel"], published_year: 1813, available: true }, { _id: 8, title: "War and Peace", author_id: 8, genres: ["Historical Novel"], published_year: 1869, available: true }, { _id: 9, title: "Crime and Punishment", author_id: 9, genres: ["Philosophical Novel"], published_year: 1866, available: true }, { _id: 10, title: "The Hobbit", author_id: 10, genres: ["Fantasy"], published_year: 1937, available: true } ]),


//AUTHORS SECTION//

db.Authors.insertMany([ { _id: 1, name: "George Orwell", nationality: "British", birth_year: 1903, death_year: 1950 }, { _id: 2, name: "Harper Lee", nationality: "American", birth_year: 1926, death_year: 2016 }, { _id: 3, name: "F. Scott Fitzgerald", nationality: "American", birth_year: 1896, death_year: 1940 }, { _id: 4, name: "Aldous Huxley", nationality: "British", birth_year: 1894, death_year: 1963 }, { _id: 5, name: "J.D. Salinger", nationality: "American", birth_year: 1919, death_year: 2010 }, { _id: 6, name: "Herman Melville", nationality: "American", birth_year: 1819, death_year: 1891 }, { _id: 7, name: "Jane Austen", nationality: "British", birth_year: 1775, death_year: 1817 }, { _id: 8, name: "Leo Tolstoy", nationality: "Russian", birth_year: 1828, death_year: 1910 }, { _id: 9, name: "Fyodor Dostoevsky", nationality: "Russian", birth_year: 1821, death_year: 1881 }, { _id: 10, name: "J.R.R. Tolkien", nationality: "British", birth_year: 1892, death_year: 1973 } ]),


//PATRONS SECTION//

db.Patrons.insertMany([ { _id: 1, name: "Alice Johnson", email: "alice@example.com", borrowed_books: [] }, { _id: 2, name: "Bob Smith", email: "bob@example.com", borrowed_books: [1, 2] }, { _id: 3, name: "Carol White", email: "carol@example.com", borrowed_books: [] }, { _id: 4, name: "David Brown", email: "david@example.com", borrowed_books: [3] }, { _id: 5, name: "Eve Davis", email: "eve@example.com", borrowed_books: [] }, { _id: 6, name: "Frank Moore", email: "frank@example.com", borrowed_books: [4, 5] }, { _id: 7, name: "Grace Miller", email: "grace@example.com", borrowed_books: [] }, { _id: 8, name: "Hank Wilson", email: "hank@example.com", borrowed_books: [6] }, { _id: 9, name: "Ivy Taylor", email: "ivy@example.com", borrowed_books: [] }, { _id: 10, name: "Jack Anderson", email: "jack@example.com", borrowed_books: [7, 8] } ]),



/////////////////////////////////CRUD OPERATORS///////////////////////////////////

///READ///

To find all Books type the following command on CMD  :

db.Books.find()


To find a specific Book by title type the following command on CMD  :

db.Books.find({title: "The title of the book"})


To find all Books by a Specific Author type the following command on CMD  :

db.Authors.find({_id: 3})


To find all available Books type the following command on CMD  :

db.Books.find({available: true})




///UPDATE///

To update Book availability under a specific ID type the following command on CMD  :

db.Books.updateOne({ _id: 3 }, { $set: { availability: "borrowed" } })


To add a Genre to a specific Book type the following command on CMD  :

db.Books.updateOne({ _id: 3 }, { $addToSet: { genres: "Whatever genre it may be"} })


To add a borrowed Book to a patron's record type the following command on CMD  :

db.Patrons.updateOne({ _id: 3 }, { $addToSet: { borrowedBooks: 3 } })




///DELETE///

To delete Book by title type the following command on CMD  :

db.Books.deleteOne({ title: "Title of the Book" })


To delete an Author type the following command on CMD  :

db.Authors.deleteOne({ _id: 3 })




To find Books published after 1950 type the following command on CMD  :

db.Books.find({ published_year: { $gt: 1950 } })



To find All American Authors type the following command on CMD  :

db.Authors.find({ nationality: { $eq: "American" } })



To set All Books To available type the following command on CMD  :

db.Books.updateMany({}, { $set: { availability: "available" } })



To find All Books that are available and published after 1950 type the following command on CMD  :

db.Books.find({ availability: "available", published_year: { $gt: 1950 } })



To find Authors whose names contain "George" type the following command on CMD  :

db.Authors.find({ name: { $regex: "George", $options: "i" } })



To give the published year of "1869" an increment by 1 type the following command on CMD  :

db.Books.updateMany({ published_year: 1869 }, { $inc: { published_year: 1 } })