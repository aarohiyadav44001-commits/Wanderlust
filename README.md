# 🌍 WanderLust

### ✈️ Explore Places • Discover Stays • Create Memories

Discover beautiful destinations, explore available stays, view locations on interactive maps, upload property images, create your own listings and share your travel experiences through ratings and reviews.

---

## 🌐 Live Demo

🚀 **Try WanderLust:**
https://wanderlust-kv3c.onrender.com

> ⏳ **Note:** The application is deployed on Render's free tier. If the server has been inactive for some time, the first request may take approximately **30–60 seconds** to wake up.

---

# ✨ Features

📌 Features
🔐 User Authentication — Signup, Login, Logout using Passport.js (Local Strategy)
🏠 Listings CRUD — Create, Read, Update, Delete travel listings with image upload
🗺️ Interactive Map — Mapbox GL JS with real-time geocoding on every listing page
⭐ Review System — Star ratings (1–5) + written comments with author-only delete
🔍 Search & Filter — Location-based search + 10 category filters
🖼️ Cloud Image Upload — Cloudinary + Multer for persistent image storage
📱 Responsive Design — Bootstrap 5 grid, mobile & desktop friendly
🔒 Authorization — Owner-only edit/delete for listings and reviews
✅ Validation — Joi server-side + Bootstrap client-side form validation
💾 Session Persistence — Sessions stored in MongoDB via connect-mongo
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
cd wanderlust
```
## 2️⃣ Install Dependencies

```bash
npm install
```
## 3️⃣ Create Environment File

```env
ATLASDB_URL=mongodb://127.0.0.1:27017/wanderlust
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
MAP_TOKEN=your_mapbox_token
SECRET=your_session_secret
```

> 🔒 **Security:** Keep your `.env` file private and add it to `.gitignore`. Never commit API keys, passwords or secret tokens to GitHub.

---

## 4️⃣ Seed the Database
```bash
node init/index.js
```
## 5️⃣ Start the Server
```bash
nodemon app.js
```
## 6️⃣ Open the Application
```text
http://localhost:8080/listings
```
🎉 **WanderLust is now running locally!**

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

# 🚀 Deployment

WanderLust is deployed on **Render**.
### 1. Push the project to GitHub
### 2. Create a Web Service
### 3. Set Build Command : npm install
### 4. Set Start Command : node app.js
### 5. Add Environment Variables
Add all required environment variables in Render's **Environment** section:
### 6. Configure MongoDB Atlas
Make sure MongoDB Atlas allows the required Render outbound access through its **Network Access** settings.

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

* 🔥 Trending * 🛏️ Rooms * 🏙️ Iconic Cities * 🏔️ Mountains * 🏰 Castles * 🏊 Amazing Pools
* ⛺ Camping* 🚜 Farms * 🛖 Domes * 🚤 Boats
---

# 👨‍💻 Author

## Kareena Yadav

🎓 Full-Stack Web Development Project

🐙 **GitHub:**
https://github.com/aarohiyadav44001

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
