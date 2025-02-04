# Video Synchronization System

## Project Overview

This system provides a scalable solution for synchronizing video playback across multiple browsers with millisecond-level precision. It allows clients to join mid-playback and maintains synchronization based on server-dictated timing.

## Technology Stack

- Backend: Go with Go Kit
- Frontend: React
- State Management: Redis
- Development Workflow: Tilt
- WebAssembly: TinyGo
- Container Orchestration: Kubernetes (local with Docker Desktop)

## Project Structure

```
video-sync-system/
├── .git/
├── .gitignore
├── Tiltfile
├── README.md
├── docker-compose.yml
├── .env
├── example.env
├── kubernetes/
│   ├── redis.yaml
│   ├── backend.yaml
│   ├── frontend.yaml
│   └── other-services.yaml
├── services/
│   ├── video-sync-backend/
│   │   ├── Dockerfile
│   │   ├── go.mod
│   │   ├── go.sum
│   │   ├── main.go
│   │   ├── .env
│   │   ├── example.env
│   │   └── internal/
│   ├── video-sync-frontend/
│   │   ├── Dockerfile
│   │   ├── package.json
│   │   ├── .env
│   │   ├── example.env
│   │   ├── public/
│   │   └── src/
│   └── other-service/
├── shared/
│   ├── protos/
│   └── utils/
└── scripts/
    ├── setup.sh
    └── deploy.sh
```

## Setup Instructions

1. Clone the repository:
   ```
   git clone https://github.com/elleshadow/video-sync-system.git
   cd video-sync-system
   ```

2. Set up environment variables:
   - Copy `example.env` to `.env` in the root directory
   - Copy `example.env` to `.env` in each service directory
   - Fill in the appropriate values in each `.env` file

3. Install dependencies:
   - For Go services:
     ```
     cd services/video-sync-backend
     go mod tidy
     ```
   - For React frontend:
     ```
     cd services/video-sync-frontend
     npm install
     ```

4. Set up Docker Desktop:
   - Install Docker Desktop
   - Enable Kubernetes in Docker Desktop settings

5. Install Tilt:
   - Follow the instructions at https://docs.tilt.dev/install.html

6. Start the development environment:
   ```
   tilt up
   ```

7. Access the services:
   - Backend: http://localhost:8080
   - Frontend: http://localhost:3000
   - Tilt dashboard: http://localhost:10350

## Development Workflow

1. Make changes to your code
2. Tilt will automatically detect changes and rebuild/redeploy as necessary
3. Use the Tilt dashboard to monitor services and view logs

## Adding a New Service

1. Create a new directory under `services/`
2. Add necessary Dockerfile and code
3. Create Kubernetes YAML in the `kubernetes/` directory
4. Update the Tiltfile to include the new service
5. Add any shared dependencies to the `shared/` directory

## Testing

- Run backend tests:
  ```
  cd services/video-sync-backend
  go test ./...
  ```
- Run frontend tests:
  ```
  cd services/video-sync-frontend
  npm test
  ```

## Deployment

(Add specific deployment instructions based on your production environment)

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License:

```
MIT License

Copyright (c) 2024 @elleshadow

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Contact

Eli Davidson - edavidson0@gmail.com

Project Link: https://github.com/elleshadow/video-sync-system