Phase 1: Foundation (Days 1–3)
Day 1 — Project Setup

Create Django project & virtual environment
Install dependencies: django, djangorestframework, channels, redis, pillow, python-decouple
Setup PostgreSQL, connect to Django
Custom User model (do this NOW, painful to change later)
Basic settings structure (.env file, decouple)
Git init, first commit

Day 2 — Auth System

Register endpoint (DRF)
Login / Logout endpoint
Token authentication setup
IsAuthenticated permission globally
Test everything in Postman/Thunder Client

Day 3 — User Profile

Profile model (avatar, bio, last_seen)
Auto-create profile on user register via signals
Get/Update profile API
Avatar upload working

💬 Phase 2: Core Chat Models & APIs (Days 4–7)
Day 4 — Design & Build Your Models
User
Conversation (is_group, name, created_by)
Membership (user, conversation, joined_at)
Message (sender, conversation, content, created_at, is_deleted)
Attachment (message, file, file_type)
MessageStatus (message, user, is_read, read_at)
Write them all. Migrate. Done.
Day 5 — Conversation APIs

Create a DM (find or create conversation between 2 users)
Create a group chat
Add/remove members from group
List all conversations for logged-in user
Get single conversation detail

Day 6 — Message APIs

Send a message (HTTP, no real-time yet)
Get message history for a conversation (paginated)
Delete a message (soft delete, set is_deleted=True)
Attach a file to a message

Day 7 — Read Receipts (HTTP version)

Mark messages as read endpoint
Get unread count per conversation
Bulk mark all messages in a conversation as read

🎨 Phase 3: Basic Frontend (Days 8–10)
You need something to see. Keep it dead simple.
Day 8 — HTML/CSS Shell

Sidebar: list of conversations
Main panel: message history
Input box at the bottom
Fetch conversations & messages from your DRF APIs using fetch()

Day 9 — Sending Messages via UI

Type message, hit send → POST to API → re-render messages
Show sender name, timestamp
Show attachments (images inline, files as download link)

Day 10 — Auth UI

Register page
Login page
Store auth token in memory (not localStorage)
Redirect after login, protect routes

⚡ Phase 4: Real-Time with Django Channels (Days 11–16)
This is the hard part. Take it slow.
Day 11 — Channels Setup

Switch from WSGI to ASGI
Install & configure Redis channel layer
Write a basic echo WebSocket consumer (just to confirm it works)
Test with a WebSocket client (browser console or Postman)

Day 12 — Auth in WebSocket

Authenticate user inside consumer via token in query string
Reject unauthenticated connections
Store self.user from scope

Day 13 — Real-Time Messaging

On connect: join conversation group
On receive: save message to DB, broadcast to group
Frontend: open WS connection, receive messages, append to UI instantly
Remove the manual "refresh" — it's now live

Day 14 — Typing Indicator

Frontend sends {"type": "typing", "conversation_id": x} over WS
Consumer broadcasts to group (NO database, pure event)
Frontend shows "User is typing..." and hides after 3 seconds

Day 15 — Online/Offline Presence

On WS connect: set user status to online in Redis
On WS disconnect: set to offline, update last_seen in DB
Broadcast presence change to relevant users
Show green/grey dot in frontend

Day 16 — Real-Time Read Receipts

When user opens a conversation: send read event over WS
Consumer marks messages as read in DB
Broadcasts {"type": "read", "user_id": x, "message_id": y} to group
Frontend shows ✓✓ (double tick) when read

🔒 Phase 5: Security & Edge Cases (Days 17–18)
Day 17 — Security

Users can only access conversations they're members of
Can't read/send messages in conversations they don't belong to
Can't delete other people's messages
Validate all WebSocket incoming data (don't trust the client)
Rate limit message sending

Day 18 — Edge Cases

What if user sends empty message?
What if file is too large? (set max upload size)
What if user leaves a group?
Conversation with yourself prevention
Handle WS reconnection on frontend (dropped connection)

🚀 Phase 6: Deploy (Days 19–21)
Day 19 — Prep for Production

requirements.txt
Separate settings: settings/dev.py, settings/prod.py
whitenoise for static files
gunicorn for HTTP, daphne for WebSocket (ASGI)

Day 20 — Docker
yamlservices:
web: # Django + Daphne
redis: # Channel layer
db: # PostgreSQL
Write Dockerfile + docker-compose.yml, make it run locally in Docker
Day 21 — Deploy to Railway / Render

Push to Railway (supports Django + Redis + Postgres easily)
Set environment variables
Run migrations on deploy
Test everything end to end in production

📋 Daily Rules

Commit every day — even broken code. Message: day-13: WS consumer auth working
Build first, perfect later — ugly code that works beats clean code that doesn't exist
When stuck >30 min — ask AI with your actual code and exact error
No new features until current one works — finish before you add
Test each API in Postman before moving on

🗺️ What You'll Have Built
DayMilestone3Auth system working7Full chat API (no real-time)10You can chat via a basic UI13Real-time messages live16Full Discord features working18Production-ready code21Live on the internet
