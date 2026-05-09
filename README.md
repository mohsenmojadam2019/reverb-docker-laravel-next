# Real-time Chat System with Laravel Reverb + Next.js

A complete real-time chat system between user and admin using Laravel 13, Reverb WebSocket, Next.js 16, and Docker.

------------------------------------------------------

## Features

- Real-time chat between user and admin
- Authentication with Laravel Sanctum
- Complete admin panel
- Real-time messages without page refresh
- Message history stored in database
- Dockerized and ready to run
- WebSocket support with Reverb

------------------------------------------------------

## Project Structure
├── src/ # Laravel 13 + Reverb
├── admin/ # Admin Next.js panel
├── front/ # User Next.js frontend
├── docker-compose.yml # Docker configuration
└── supervisor/ # Process management


------------------------------------------------------

## Installation & Setup

```bash
# Clone the repository
git clone https://github.com/your-repo/socket-chat.git
cd socket-chat

# Copy environment files
cp front/.env.example front/.env.local
cp admin/.env.example admin/.env.local

# Build and run with Docker
docker-compose build
docker-compose up -d

# Run migrations and seeders
docker exec -it socket-laravel bash
php artisan migrate:fresh --seed
exit

# Start Reverb WebSocket server
docker exec -it socket-laravel php artisan reverb:start --host=0.0.0.0 --port=8082

# Restart frontend and admin (in another terminal)
docker-compose restart admin
docker-compose restart front

Useful Commands
bash
# View container logs
docker-compose logs -f

# Restart specific service
docker-compose restart admin

# Enter Laravel container
docker exec -it socket-laravel bash

# Clear cache
php artisan optimize:clear

------------------------------------------------------

## Installation & Setup

```bash
# Clone the repository
git clone https://github.com/mohsenmojadam2019/reverb-docker-laravel-next.git
cd socket-chat

------------------------------------------------------
# Build and run with Docker
docker-compose build
docker-compose up -d
------------------------------------------------------
# Run migrations and seeders
docker exec -it socket-laravel bash
php artisan migrate:fresh --seed
exit
------------------------------------------------------
# Start Reverb WebSocket server
docker exec -it socket-laravel php artisan reverb:start --host=0.0.0.0 --port=8082
------------------------------------------------------
# Restart frontend and admin (in another terminal)
docker-compose restart admin
docker-compose restart front
------------------------------------------------------
Environment Variables (.env.local for front & admin)
NEXT_PUBLIC_API_URL=http://localhost:8210
NEXT_PUBLIC_REVERB_HOST=localhost
NEXT_PUBLIC_REVERB_PORT=8082
NEXT_PUBLIC_REVERB_APP_KEY=your-app-key-here
-------------------------------------------------------
Access URLs
Service	URL	Email	Password
Admin Panel	http://localhost:3001	admin@example.com	password
User Frontend	http://localhost:3000	user@example.com	password
PHPMyAdmin	http://localhost:8310	root	bV7c5smN2T8h4hlMzF90Bpum
--------------------------------------------------------
Architecture
text
User (Next.js) ←→ Laravel Reverb ←→ Admin (Next.js)
                        ↓
                   MySQL Database
--------------------------------------------------------
Important Files
Laravel (src/)
routes/api.php - API routes (login, send message)

routes/channels.php - WebSocket channels

app/Events/MessageSent.php - Message event

app/Http/Controllers/ChatController.php - Chat controller

Next.js Admin (admin/src/)
app/page.js - Admin dashboard

app/login/page.js - Admin login

lib/hooks/useAdminChat.js - Admin chat hook

lib/echo.js - WebSocket configuration

Next.js Front (front/src/)
app/chat/page.js - User chat page

app/login/page.js - User login

lib/hooks/useChat.js - User chat hook
--------------------------------------------------------
Star This Project ⭐
If you find this project useful, please give it a star on GitHub!
--------------------------------------------------------

