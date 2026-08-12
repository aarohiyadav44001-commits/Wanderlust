# 🌍 WanderLust

### ✈️ Explore Places • Discover Stays • Create Memories

> **WanderLust** is a full-stack travel listing platform inspired by modern vacation-rental applications, built with **Node.js, Express.js, MongoDB and EJS**.

Discover beautiful destinations, explore available stays, view locations on interactive maps, upload property images, create your own listings and share your travel experiences through ratings and reviews.

---

## 🌐 Live Demo

🚀 **Try WanderLust:**
https://wanderlust-kv3c.onrender.com

> ⏳ **Note:** The application is deployed on Render's free tier. If the server has been inactive for some time, the first request may take approximately **30–60 seconds** to wake up.

---

# ✨ Features

## 🔐 Authentication & User Management

WanderLust includes a complete user authentication system powered by **Passport.js** and its Local Strategy.

* 📝 User signup
* 🔑 Login
* 🚪 Logout
* 🔒 Protected routes
* 👤 Session-based authentication
* 💾 Persistent sessions using MongoDB
* 🛡️ Authorization for protected actions

---

## 🏡 Listing Management

Users can manage travel/property listings through complete CRUD functionality.

* ➕ Create new listings
* 👀 Browse all listings
* 📄 View detailed listing information
* ✏️ Edit existing listings
* 🗑️ Delete listings
* 🖼️ Upload listing images
* 👑 Only listing owners can edit or delete their listings

---

## 🗺️ Interactive Map Integration

Every listing can display its location through an interactive **Mapbox GL JS** map.

The application uses geocoding to convert a location entered by the user into coordinates that can be displayed on the map.

📍 This gives users a visual way to understand the location of each property.

---

## ⭐ Reviews & Ratings

Users can share their experience through the built-in review system.

* ⭐ Rating system from **1–5 stars**
* 💬 Written comments
* 🔐 Authentication required for submitting reviews
* 👤 Review author information
* 🗑️ Author-only review deletion

---

## ☁️ Cloud Image Upload

Listing images are uploaded using **Multer** and stored on **Cloudinary**.

This provides persistent cloud storage for images instead of relying on the local server filesystem.

---

## 📱 Responsive Interface

The frontend uses **Bootstrap 5.3** along with custom CSS to provide a responsive experience across:

* 💻 Desktop
* 📱 Mobile
* 📟 Tablet

---

## 🛡️ Validation & Authorization

The application contains multiple levels of validation and access control.

* ✅ Joi server-side validation
* ✅ Bootstrap client-side validation
* 🔐 Authentication middleware
* 👑 Listing owner authorization
* 👤 Review author authorization
* ⚠️ Custom error handling
* 🧩 Async error handling

---

## 💾 Session Persistence

User sessions are maintained using:

**Express Session + Connect Mongo**

Sessions are stored in MongoDB so authentication can persist beyond a single server request.

---

# 🧰 Tech Stack

| Layer                  | Technology                 |
| ---------------------- | -------------------------- |
| 🟢 Runtime             | Node.js v24.18.0           |
| ⚙️ Backend             | Express.js 4.x             |
| 🎨 Template Engine     | EJS                        |
| 🖥️ Frontend           | HTML5, CSS3, Bootstrap 5.3 |
| 🗄️ Database           | MongoDB Atlas              |
| 🔗 ODM                 | Mongoose 9                 |
| 🔐 Authentication      | Passport.js                |
| 👤 Auth Strategy       | passport-local-mongoose    |
| ☁️ Image Storage       | Cloudinary v1              |
| 📤 File Upload         | Multer v2                  |
| 🗺️ Map Library        | Mapbox GL JS v3            |
| 📍 Map / Geocoding SDK | @mapbox/mapbox-sdk         |
| ✅ Validation           | Joi 18                     |
| 💾 Session Management  | express-session            |
| 🗃️ Session Store      | connect-mongo v6           |
| 🚀 Deployment          | Render                     |

---

# 🏗️ Project Structure

WanderLust follows a structured MVC-style architecture that separates application logic, database models, routes and frontend templates.

```text
WANDERLUST/
│
├── 📂 controllers/
│   ├── listings.js          # Listing CRUD operations
│   ├── reviews.js           # Review-related operations
│   └── users.js             # Authentication & user logic
│
├── 📂 models/
│   ├── listing.js           # Listing Mongoose schema
│   ├── review.js            # Review Mongoose schema
│   └── user.js              # User schema
│
├── 📂 routes/
│   ├── listing.js           # Listing routes
│   ├── review.js            # Review routes
│   └── user.js              # Authentication routes
│
├── 📂 views/
│   │
│   ├── 📂 layouts/
│   │   └── boilerplate.ejs  # Main layout
│   │
│   ├── 📂 includes/
│   │   ├── navbar.ejs       # Navigation bar
│   │   ├── flash.ejs        # Flash messages
│   │   └── footer.ejs       # Footer
│   │
│   ├── 📂 listings/
│   │   ├── index.ejs       # All listings
│   │   ├── show.ejs        # Listing details
│   │   ├── new.ejs         # Create listing
│   │   └── edit.ejs        # Edit listing
│   │
│   └── 📂 users/
│       ├── login.ejs       # Login page
│       └── signup.ejs      # Signup page
│
├── 📂 public/
│   ├── 📂 css/
│   │   └── style.css       # Custom styling
│   │
│   ├── 📂 js/
│       ├── script.js       # Frontend JavaScript
│       └── map.js          # Mapbox functionality
│   
│       
│
├── 📂 utils/
│   ├── ExpressError.js      # Custom error class
│   └── wrapAsync.js         # Async error wrapper
│
├── 📂 init/
│   └── index.js             # Database seed script
│
├── app.js                   # Main application entry point
├── cloudConfig.js           # Cloudinary + Multer setup
├── middleware.js            # Custom middleware
├── schema.js                # Joi validation schemas
├── .env                     # Environment variables
├── .gitignore
└── package.json
```

---

# 🔗 RESTful API Routes

WanderLust uses RESTful routing to manage **listings, reviews and users**.

---

## 🏠 Listing Routes

| Method   | Route                | Description                                         | Access           |
| -------- | -------------------- | --------------------------------------------------- | ---------------- |
| `GET`    | `/listings`          | Display all listings with search & category filters | 🌐 Public        |
| `GET`    | `/listings/new`      | Show form for creating a listing                    | 🔐 Authenticated |
| `POST`   | `/listings`          | Create a new travel listing                         | 🔐 Authenticated |
| `GET`    | `/listings/:id`      | Display listing details with map                    | 🌐 Public        |
| `GET`    | `/listings/:id/edit` | Show listing edit form                              | 👑 Owner         |
| `PUT`    | `/listings/:id`      | Update listing information                          | 👑 Owner         |
| `DELETE` | `/listings/:id`      | Delete a listing                                    | 👑 Owner         |

---

## ⭐ Review Routes

| Method   | Route                             | Description                   | Access           |
| -------- | --------------------------------- | ----------------------------- | ---------------- |
| `POST`   | `/listings/:id/reviews`           | Add rating and written review | 🔐 Authenticated |
| `DELETE` | `/listings/:id/reviews/:reviewId` | Delete an existing review     | 👤 Review Author |

---

## 👤 User & Authentication Routes

| Method       | Route     | Description                              | Access           |
| ------------ | --------- | ---------------------------------------- | ---------------- |
| `GET / POST` | `/signup` | Display signup form and register user    | 🌐 Public        |
| `GET / POST` | `/login`  | Display login form and authenticate user | 🌐 Public        |
| `GET`        | `/logout` | Logout current user                      | 🔐 Authenticated |

---

# 🔐 Authorization Rules

Different actions require different permission levels.

### 🌐 Public Access

Users can access:

* `/listings`
* `/listings/:id`
* `/signup`
* `/login`

### 🔑 Logged-in Users

Authentication is required for:

* Creating listings
* Adding reviews
* Accessing protected forms
* Logging out

### 👑 Listing Owners

Only the owner of a listing can:

* Edit the listing
* Update the listing
* Delete the listing

### 👤 Review Authors

Only the author of a review can:

* Delete that review

This prevents unauthorized users from modifying someone else's content.

---

# 💻 Local Development Setup

## 📋 Prerequisites

Before running the project locally, install or create:

* Node.js **v18 or newer**
* MongoDB local database or MongoDB Atlas
* Cloudinary account
* Mapbox account
* Git
* A code editor such as VS Code

---

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/ajayyaday4522/wanderlust.git
```

Then move into the project directory:

```bash
cd wanderlust
```

---

## 2️⃣ Install Dependencies

```bash
npm install
```

This installs all dependencies listed in `package.json`.

---

## 3️⃣ Create Environment File

Create a `.env` file in the project's root directory.

```env
ATLASDB_URL=mongodb://127.0.0.1:27017/wanderlust

CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret

MAP_TOKEN=your_mapbox_token

SECRET=your_session_secret
```

---

# 🔑 Environment Variables

| Variable           | Purpose                            |
| ------------------ | ---------------------------------- |
| `ATLASDB_URL`      | MongoDB database connection string |
| `CLOUD_NAME`       | Cloudinary cloud name              |
| `CLOUD_API_KEY`    | Cloudinary API key                 |
| `CLOUD_API_SECRET` | Cloudinary API secret              |
| `MAP_TOKEN`        | Mapbox access token                |
| `SECRET`           | Secret key used for sessions       |

> 🔒 **Security:** Keep your `.env` file private and add it to `.gitignore`. Never commit API keys, passwords or secret tokens to GitHub.

---

## 4️⃣ Seed the Database

To insert the project's sample listings into the database:

```bash
node init/index.js
```

This step is **optional**.

If you already have data in your database, you can skip it.

---

## 5️⃣ Start the Server

Using Nodemon:

```bash
nodemon app.js
```

Or using Node directly:

```bash
node app.js
```

---

## 6️⃣ Open the Application

Once the server is running, open:

```text
http://localhost:8080/listings
```

🎉 **WanderLust is now running locally!**

---

# 🚀 Deployment

WanderLust is deployed on **Render**.

## ☁️ Render Deployment Steps

### 1. Push the project to GitHub

Upload your latest project code to GitHub.

### 2. Create a Web Service

Create a new Web Service on Render and connect the GitHub repository.

### 3. Set Build Command

```bash
npm install
```

### 4. Set Start Command

```bash
node app.js
```

### 5. Add Environment Variables

Add all required environment variables in Render's **Environment** section:

```text
ATLASDB_URL
CLOUD_NAME
CLOUD_API_KEY
CLOUD_API_SECRET
MAP_TOKEN
SECRET
```

### 6. Configure MongoDB Atlas

Make sure MongoDB Atlas allows the required Render outbound access through its **Network Access** settings.

After successful deployment, Render will provide the live application URL.

---

# 🌐 Live Deployment

🚀 **WanderLust is live at:**

https://wanderlust-427v.onrender.com/listings

> Because the application uses Render's free hosting tier, the service may sleep when inactive and require some time to wake up.

---

# 📚 What This Project Demonstrates

This project brings together multiple full-stack development concepts.

### 🖥️ Frontend

* HTML5
* CSS3
* Bootstrap 5
* EJS templating
* JavaScript
* Responsive design
* Client-side validation

### ⚙️ Backend

* Node.js
* Express.js
* RESTful architecture
* MVC pattern
* CRUD operations
* Middleware
* Async/Await
* Error handling

### 🗄️ Database

* MongoDB
* MongoDB Atlas
* Mongoose
* Schema design
* Relationships
* Population

### 🔐 Authentication

* Passport.js
* Local Strategy
* passport-local-mongoose
* Sessions
* Authentication middleware
* Authorization middleware

### ☁️ External Services

* Cloudinary
* Mapbox
* MongoDB Atlas
* Render

---

# 🗺️ Application Flow

```text
                    🌍 WanderLust
                          │
              ┌───────────┴───────────┐
              │                       │
          👤 User                 🌐 Guest
              │                       │
       ┌──────┼──────┐                │
       │      │      │                │
     Login  Signup  Logout            │
       │                              │
       └──────────┬───────────────────┘
                  │
                  ▼
             🏠 Listings
                  │
        ┌─────────┼─────────┐
        │         │         │
      Search    Filter    Details
        │                   │
        │                   ▼
        │               🗺️ Mapbox
        │
        ▼
   🔐 Authenticated User
        │
   ┌────┼─────────────┐
   │    │             │
   ▼    ▼             ▼
 Create Edit        Delete
 Listing Listing    Listing
   │
   ▼
 ☁️ Cloudinary
   │
   ▼
 🖼️ Image Storage

Listing
   │
   ▼
 ⭐ Reviews & Ratings
```

---

# 🏷️ Available Categories

WanderLust currently supports **10 listing categories**:

* 🔥 Trending
* 🛏️ Rooms
* 🏙️ Iconic Cities
* 🏔️ Mountains
* 🏰 Castles
* 🏊 Amazing Pools
* ⛺ Camping
* 🚜 Farms
* 🛖 Domes
* 🚤 Boats

---

# 🔮 Future Improvements

Some features that can be introduced in future versions:

* ❤️ Wishlist / Favorites
* 💳 Online booking
* 💰 Payment gateway integration
* 📧 Email notifications
* 👤 User profile dashboard
* 📊 Host analytics
* 💬 Real-time messaging
* 🔔 Booking notifications
* 🌙 Dark mode
* 📍 Advanced location-based search

---

# 👨‍💻 Author

## Ajay Yadav

🎓 Full-Stack Web Development Project

🐙 **GitHub:**
https://github.com/ajayyaday4522

---

# 🙏 Acknowledgements

A big thanks to the technologies and platforms that helped make this project possible:

* 🏠 **Airbnb** — Inspiration for the travel-listing concept
* 🖼️ **Unsplash** — Sample listing images
* 🗺️ **Mapbox** — Interactive maps and geocoding
* ☁️ **Cloudinary** — Cloud-based image storage
* 🎓 **University of Engineering & Management, Jaipur** — Academic support and project environment

---

# 📄 License

This project is licensed under the **ISC License**.

---

<div align="center">

# 🌍 WanderLust

### ✈️ Discover. Explore. Stay. Repeat.

**Made with ❤️ using Node.js, Express.js, MongoDB & EJS**

⭐ If you found this project useful or interesting, consider giving it a **star**!

</div>
