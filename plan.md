What i need to do
Database:
# ERD
Make Database
Connect the Database
Login SQL
Register SQL
Feed SQL
Account page SQL
Post SQL
Likes SQL

Pages:
Find CSS to use
Homepage
Login/Register
Feed
Account
Post



ERD https://dbdiagram.io/d
// Use DBML to define your database structure
// Docs: https://dbml.dbdiagram.io/docs

// Table follows {
//   following_user_id integer
//   followed_user_id integer
//   created_at timestamp
// }

Table account {
  id integer [primary key]
  username varchar
  password varchar
  email email
  PFP integer
  created_at timestamp
}

Table posts {
  id integer [primary key]
  title varchar
  body text [note: 'Content of the post']
  user_id integer [not null]
  created_at timestamp
}

Table comment {
  id integer [primary key]
  post_id integer
  body text
}

Table likes {
  like_id interger [primary key]
  user_id interger [not null]
  post_id interger [not null]
}

Ref: comment.post_id < posts.id

Ref user_posts: posts.user_id > account.id // many-to-one

Ref: account.id < likes.user_id

Ref: posts.id < likes.post_id

Ref: comment.id < likes.post_id

// Ref: account.id < follows.following_user_id

// Ref: account.id < follows.followed_user_id
