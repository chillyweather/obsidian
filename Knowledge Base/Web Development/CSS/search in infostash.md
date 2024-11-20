


Ok
I made first improvement to my final project, which is not just fixing some stupid mistakes i made that wasn't noticed by reviewer. 

Sorting saved articles.

Nothing really special and nothing to brag about, but i found out a couple of new (for me) things while working on this small project. Maybe they'll be useful for somebody else.


-- гиф

So, in our case we have a list of saved news articles (which we get from https://newsapi.org/) in form of array of objects.

Each object looks like: 
```js
{

 "_id": "622cd770c67c1c00bd615451",

 "keyword": "pentax",

 "title": "Irix announces the 21mm f/1.4 lens for Canon EF, Nikon F and Pentax K",

 "text": "Well, I didnt think wed have to wait long after Januarys Irix Cine 21mm T1.5 lens announcement before wed see its photography counterpart, the Irix 21mm f/1.4. Now, the company has officially announc… [+2581 chars]",

 "date": "2022-03-11T12:32:18Z",

 "source": "DIYphotography",

 "link": "https://www.diyphotography.net/irix-announces-the-21mm-f-1-4-lens-for-canon-ef-nikon-f-and-pentax-k/",

 "image": "https://www.diyphotography.net/wp-content/uploads/2022/03/irix-21mm-f14.jpg",

 "owner": "622cce50c67c1c00bd615432",

 "__v": 0

 }
```

I wanted to implement search by keyword, article publishing date, and date when article was saved to the database by user.

Sorting by keyword and publishing date are pretty straightforward, since we have those properties in our object.

sortingOrder - state variable

1. Keyword
```js
if (sortingOrder === 'Keyword (A-Z)') {

 return array.sort((a, b) => a.keyword.localeCompare(b.keyword));

 }

if (sortingOrder === 'Keyword (Z-A)') {

 return array.sort((a, b) => b.keyword.localeCompare(a.keyword));

 }
```

2. Publishing date

```jsx
if (sortingOrder === 'Oldest') {

 return array.sort((a, b) => {

 const date1 = new Date(a.date);

 const date2 = new Date(b.date);

 return date1 - date2;

 });

 }

 if (sortingOrder === 'Latest') {

 return array.sort((a, b) => {

 const date1 = new Date(a.date);

 const date2 = new Date(b.date);

 return date2 - date1;

 });

 }
```

3. Article savе date

This one a bit more interesting. We don't have a property for 'date added' in our object. And the last thing I wanted to do - to change back-end.
So, we have _id property like "_id": "622cd770c67c1c00bd615451"

According to MongoDB documentation the 12-byte ObjectId consists of:

-   A 4-byte timestamp, representing the ObjectId's creation, measured in seconds since the Unix epoch.
-   A 5-byte random value generated once per process. This random value is unique to the machine and process.
-   A 3-byte incrementing counter, initialized to a random value.

In my case hexadecimal 622cd770 is 1647105904 seconds since the Unix epoch which is actually Saturday, March 12, 2022 5:25:04 PM.

So the sorting function looks like:

```jsx
if (sortingOrder === 'Last Added') {

 return array.sort((a, b) => {

 const id1 = parseInt(a._id.substring(0, 8), 16);

 const id2 = parseInt(b._id.substring(0, 8), 16);

 return id2 - id1;

 });

 }

 if (sortingOrder === 'First Added') {

 return array.sort((a, b) => {

 const id1 = parseInt(a._id.substring(0, 8), 16);

 const id2 = parseInt(b._id.substring(0, 8), 16);

 return id1 - id2;

 });

 }
```