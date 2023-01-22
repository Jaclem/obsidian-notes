Answer from Stack Overflow

The resource you need to be editable needs to be stored somewhere. Whether that is a database or just a Markdown file you are reading - it's up to you.

Then once you have that information stored, you can request it from your frontend application. Users will be able to navigate to a page where that resource will be requested and shown.

In your admin interface you can also create a view in which you load the contents you want to edit and then send the modified back to where it was originally stored.

That is, you can write to the file or send a POST request to your backend which will write it to your database, so that when users will request it again it will contain the updated, edited information.

The same principle can be applied to other types of resources as well - e.g. for structured data you can use a simple JSON file that you read and then write or use a database.

Based on your question you are most likely just starting out especially with the backend side of things, you might want to look into solutions like Firebase where you can consume and manipulate data right from your frontend code in a rather easy manner.