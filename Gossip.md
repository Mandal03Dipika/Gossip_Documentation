# 💬 Gossip

Gossip is a real-time chat platform where users can connect, chat, and have fun together.
It’s designed for scalability, performance, and security, offering one-on-one and group conversations, friend management, and media sharing.

Built with React, Tailwind, Zustand, Express, MySQL, ShadCN UI, MongoDB, and Socket.IO, Gossip provides a seamless messaging experience across devices.

---

## 🛠️ Tech Stack

- **Frontend** : ⚛️ React, 🎨 Tailwind CSS, 🗂️ Zustand, 🔌 Socket.IO-client, 🎛️ ShadCN UI, TypeScript
- **App Backend** : 🚀 Express, 🗄️ MySQL, 🔑 JWT, TypeScript
- **Chat Backend** : ⚡ Express, 💬 Socket.IO, 🗄️ MongoDB, 🔑 JWT, TypeScript
- **File Server (DMS)** : ☕ Java, 🍃 Spring Boot, 🗄️ MySQL

---

## 🚀 Services

1. 🌐 **Web Application** — [Gossip v2.0.0 live](https://gossip.wishalpha.com)
2. 📱 **Mobile Application** — Android/iOS (future roadmap)
3. 💻 **Desktop Application** — (future roadmap)

---

## 👥 Team

- 🧪 **Observer/Testing** : Siddharth Sir, Samir Sir, Dipika
- 📝 **Documentation** : Dipika, Aditya
- 🎨 **Frontend** : Dipika, Avhisek, Sneha, Krishanu
- ⚙️ **Backend** : Siddharth Sir, Priyanshu
- 🔌 **Socket** : Samir Sir, Siddharth Sir, Priyanshu
- ☁️ **DevOps** : Dipika

---

## 🤝 GitHub Repositories

- **Backend (Reference)** : [Gossip_Backend](https://github.com/Mandal03Dipika/Gossip_Backend)
- **Frontend (Reference)** : [Gossip_Frontend](https://github.com/Mandal03Dipika/Gossip_Frontend)
- **Documentation** : [Gossip_Documentation](https://github.com/Mandal03Dipika/Gossip_Documentation)
- **Backend (Work)** :
- **Frontend (Work)** :

### ⚠️ Contribution Guidelines

- Work in **your own branch**
- Do **NOT merge into main** without prior discussion or approval from sir
- Follow proper commit messages & pull request reviews

---

### ⚙️ Functionalities

- 💬 **Conversations** : Supports both one-on-one and group chats.
- 📩 **Acknowledgements** : Sent, delivered, and read receipts for every message.
- 📎 **File Sharing** : Share images, videos, documents, and other media.
- 💾 **Persistent Storage** : Messages stored securely; delivered even if user was offline.
- 🔔 **Push Notifications** : Alerts for new messages, friend requests, and acceptances.
- 🔑 **Password Policy** : Strong passwords (min 8 chars, uppercase, lowercase, number, symbol).
- 🔐 **Data Security** : Sensitive data encrypted at frontend before sending to backend.
- 🎶 **Music Integration** : Play music/songs during chats; audible to both users.
- 🎮 **Private Room Chat** : Game-integrated chat rooms; deleted automatically once the game ends.

---

## 📊 Non-Functional Requirements

- ⚡ **Low Latency** : Instant message delivery.
- 📏 **Consistency** : Guaranteed in-order message delivery.
- ☁️ **High Availability** : System uptime and redundancy.
- 📈 **Scalability** : Can handle increasing users & daily messages.
- 🚀 **Flexible Deployment** : Supports Blue-Green / Red-Green deployment for smooth upgrades.

---

## ✅ Existing Features

### 🔐 Authentication & Account Management

- ✅ User Registration & Login with JWT
- 🔄 OTP Verification & Resend OTP
- 🔑 Forgot & Reset Password
- 🛡️ Secure Session Management (auto logout on token expiry)
- 📝 Profile Update & Auth Status Check

### 👥 Group & Chat Features

- 🆕 Create, Update & Delete Groups
- 📋 Get Single or All Groups
- 💬 Real-time Group Messaging
- 🗂️ Group List for Sidebar Navigation
- 🚪 Leave Group Functionality

### 💌 Direct Messaging & Friend Management

- 💬 One-on-One Messaging
- 🧹 Delete All Chats
- 🚫 Block & Unblock Users
- 🤝 Friend Requests (send, accept, reject, cancel, toggle)
- 👥 Manage Friends (unfriend, list, online friends)
- 📋 View Pending Friend Requests

### 🟢 Online Presence

- 🌐 Real-time Online User Tracking
- 👀 Get Online Friends

---

## 🏗️ Architecture

The Gossip app is designed as **modular services**:

Features like sign-in, sign-up, profile and etc, of a chat application could use traditional request/response method over HTTP.

We can break our Chat application into three major components:

- Stateful Service : Socket.IO-based real-time communication
- Stateless Service : Authentication, profile, API requests
- Third Party Integration : Document Management System (DMS)

---

## 📂 Database Schema (Core Tables)

### Users

```sql
id              -- Unique identifier
username        -- Email / phone number / auto-generated username
password        -- Hashed password
isVerified      -- Boolean flag for email/phone verification
authToken       -- JWT or session token
otp             -- One-Time Password for verification
otpExpiry       -- Expiration timestamp of OTP
otpCount        -- Number of OTPs sent
lastOtpSentTime -- Timestamp of last OTP sent
```

**_If required Otp can be managed in another table._**

### User Profile

```sql
id          -- Unique identifier
userId      -- Reference to Users table
name        -- Full name of the user
email       -- Email address
phoneNumber -- Phone number
profilePic  -- URL or path of profile picture
```

### Blocked Users

```sql
id              -- Unique identifier
userId          -- Reference to Users table
blockedUserIds  -- Array/list of blocked user IDs
```

### Friends

```sql
id              -- Unique identifier
userId          -- Reference to Users table
friendUserIds   -- Array/list of friend user IDs
```

### Friend Requests

```sql
id                     -- Unique identifier
userId                 -- Reference to Users table
friendRequestUserIds   -- Array/list of incoming friend request IDs
```

### Sent Requests

```sql
id                  -- Unique identifier
userId              -- Reference to Users table
sentRequestUserIds  -- Array/list of sent friend request IDs
```

### Groups

```sql
id              -- Unique identifier
chatId          -- One-to-one group or chat reference
name            -- Group name
description     -- Group description
profilePic      -- Group profile image
restrictions    -- Group restrictions (advanced features)
adminIds{}      -- IDs of group admins
```

**_Future advancement: segregate adminIds into a separate table._**

### Messages

```sql
id        -- Unique identifier
chatId    -- Reference to Chats table
memberId  -- Sender ID
message   -- Message content (text/file)
```

### Chats

```sql
id           -- Unique identifier
isGroupChat  -- Boolean flag (true = group chat, false = one-to-one)
memberIds    -- Array/list of member IDs in the chat
```

---
