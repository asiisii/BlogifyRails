# Rails Articles and Comments Project

A simple Ruby on Rails application that demonstrates creating, reading, updating, and deleting (CRUD) for **articles** and their associated **comments**.

## Features
- **Articles**
  - List all articles
  - View a single article
  - Create a new article
  - Edit an existing article
  - Delete an article
- **Comments**
  - Add a comment to an article
  - Edit a comment
  - View all comments for an article
  - Delete a comment

---

## Prerequisites
- Ruby 3.0+
- Rails 7.0+
- SQLite3
- Node.js and Yarn

---

## Setup

1. Clone the repository:
   git clone <repository-url>
   cd <repository-folder>

2. Install dependencies:
   bundle install

3. Set up the database:
   rails db:create db:migrate

4. Start the server:
   rails server

5. Open your browser and visit:
   http://localhost:3000

---

## Routes

Here’s the list of all the routes available in the application:

### Articles
| Action        | HTTP Verb | Path            | Controller#Action  |
|---------------|-----------|-----------------|--------------------|
| List Articles | `GET`     | /articles       | `articles#index`   |
| Show Article  | `GET`     | /articles/:id   | `articles#show`    |
| New Article   | `GET`     | /articles/new   | `articles#new`     |
| Edit Article  | `GET`     | /articles/:id/edit | `articles#edit` |
| Create Article| `POST`    | /articles       | `articles#create`  |
| Update Article| `PATCH`   | /articles/:id   | `articles#update`  |
| Delete Article| `DELETE`  | /articles/:id   | `articles#destroy` |

### Comments
| Action          | HTTP Verb | Path                                | Controller#Action   |
|------------------|-----------|------------------------------------|---------------------|
| List Comments    | `GET`     | /articles/:article_id/comments     | `comments#index`    |
| New Comment      | `GET`     | /articles/:article_id/comments/new | `comments#new`      |
| Show Comment     | `GET`     | /articles/:article_id/comments/:id | `comments#show`     |
| Edit Comment     | `GET`     | /articles/:article_id/comments/:id/edit | `comments#edit` |
| Create Comment   | `POST`    | /articles/:article_id/comments     | `comments#create`   |
| Update Comment   | `PATCH`   | /articles/:article_id/comments/:id | `comments#update`   |
| Delete Comment   | `DELETE`  | /articles/:article_id/comments/:id | `comments#destroy`  |

---

## Key Files

### Articles
- **Controller**: `app/controllers/articles_controller.rb`
  - Handles CRUD operations for articles.
- **Views**: `app/views/articles`
  - Contains views for listing, showing, creating, and editing articles.

### Comments
- **Controller**: `app/controllers/comments_controller.rb`
  - Handles CRUD operations for comments associated with articles.
- **Views**: `app/views/comments`
  - Contains views for creating and editing comments.

---

## Relationships

- Articles and comments have a **one-to-many relationship**.
- Each article can have many comments.
- Each comment belongs to a single article.

### Models
- **Article**:
  - Fields: `title`, `body`
  - Associations: `has_many :comments, dependent: :destroy`
- **Comment**:
  - Fields: `commenter`, `body`
  - Associations: `belongs_to :article`

---