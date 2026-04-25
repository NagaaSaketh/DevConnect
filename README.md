# DevConnect

DevConnect is a full-stack developer networking platform that enables users to connect, chat in real-time, and collaborate. It includes authentication, profile management, connection requests, and live messaging using WebSockets.

---

## Demo Link

[Demo Link](https://dev-connect-collab.vercel.app/)

---

## Login

> **Guest** <br>
> Username: `guest123@gmail.com` <br>
> Password: `guest1234`

---

## Quick Start

```
git clone https://github.com/NagaaSaketh/DevConnect.git
cd DevConnect
npm install
npm run dev
```

---

## Environment Variables

- PORT=your_port_number
- MONGO_URI=your_mongodb_uri
- JWT_SECRET=your_secret_key
- GOOGLE_CLIENT_ID=your_google_client_id
- GOOGLE_CLIENT_SECRET=your_google_client_secret
- GOOGLE_REDIRECT_URI=your_redirect_uri
- GITHUB_CLIENT_ID=your_github_client_id
- GITHUB_CLIENT_SECRET=your_github_client_secret
- FRONTEND_URL=your_frontend_url

---

## Technologies

### Frontend

- React JS
- React Router

### Backend

- Node.js
- Express.js
- MongoDB (Mongoose)

### Authentication

- JWT (Cookie-based authentication)
- Google OAuth
- GitHub OAuth

### Realtime

- Socket.IO

---

## Authentication Flow

- User logs in (JWT / OAuth)
- Token stored in HTTP-only cookie
- Middleware (userAuth) validates user
- User data attached to req.user

## Features

**Authentication**

- Signup/Login with JWT
- Secure HTTP-only cookies
- Google & GitHub OAuth login

**Profile Management**

- View profile
- Edit profile (including image upload)
- Update password
- Cloudinary integration for profile images

**Connections System**

- Send connection requests
- Accept / Reject requests
- View received requests
- View all connections
- Smart feed (excludes connected & requested users)

**Real-time Chat**

- One-to-one chat system
- Auto chat creation
- WebSocket-based messaging
- Only connected users can chat
- Secure room generation using hashing

**Smart Feed**

- Pagination support
- Filters out:
  - Yourself
  - Existing connections
  - Ignored users

---

## API References

### Auth Routes

### **POST /api/signup**

Create new user

Sample Response :

```
{

  message: User added successfully,
  data: { _id,emailID,firstName,... }

}
```

### **POST /api/login**

Login User

Sample Response :

```
{ _id,emailID,firstName,...}
```

### **POST /api/logout**

Logout User

### **GET /api/auth/google**

### **GET /api/auth/google/callback**

Google OAuth

### **GET /api/auth/github**

### **GET /api/auth/github/callback**

Github OAuth

### Profile Routes

### **GET /api/profile/view**

Get logged-in user profile

Sample Response :

```
{ _id,emailID,firstName,...}
```

### **PUT /api/profile/edit**

Update profile

Sample Response :

```
{
    message:Profile updated successfully,
    data:{ _id,emailID,firstName,...}
}
```

### PUT /api/profile/password

Update password

```
{ message:Password updated successfully }
```

### Connection Routes

### **POST /api/request/send/:status/:toUserId**

Send connection request

Sample Response :

```
{ message: User A interested/ignored in User B }
```

### **POST /api/request/review/:status/:requestId**

Accept or reject request

Sample Response :

```
{ message: Connection request accepted/rejected }
```

### **GET /api/user/requests/received**

Get received connection requests

Sample Response :

```
{
    message: Data fetched successfully!,
    connectionRequests: [{_id,fromUserId,ToUserId,status}]
}
```

### **GET /api/user/connections**

Get all connections

Sample Response :

```
[{_id,fromUserId,ToUserId,status}]
```

### **GET /api/feed?page=1&limit=10**

Get user feed

Sample Response :

```
[{_id,fromUserId,ToUserId,status}]
```

### Chat Routes

### **GET /api/chat/:targetUserId**

Get or create chat between users

```
{
    participants:[fromUserId,toUserId],
    messages:{[senderId,text,_id]}
}
```

---

## Contact 

For bugs or feature requests, please reach out to vadlamanisaketh25@gmail.com
