*The purpose of this document is to answer the questions of the TPs from the DevOps class.*

**1-1 For which reason is it better to run the container with a flag -e to give the environment variables rather than put them directly in the Dockerfile?**

Using the -e flag keeps sensitive data like passwords secure, because hardcoding them in the Dockerfile exposes them to anyone who has access to the image.

**1-2 Why do we need a volume to be attached to our postgres container?**

We need to attach a volume to a Postgres container because container file systems are ephemeral, meaning all database records would be permanently lost if the container is removed or restarted. Using a volume ensures that the database data persists safely on the host machine independently of the container's lifecycle.

**1-3 Document your database container essentials: commands and Dockerfile.**

First, we have a base image like FROM postgres:14-alpine. Tgen, we are copying the SQL files to the initialization directory of PostgreSQL.

**1-4 Why do we need a multistage build? And explain each step of this dockerfile.**

A multistage build keeps the final Docker image lightweight and secure by discarding heavy build tools (like Maven) and source code, keeping only the compiled application. In the Dockerfile, the "Build stage" uses a JDK environment to compile the source code into a JAR, and the "Run stage" uses a lighter JRE to simply copy that built JAR and run it.

**1-5 Why do we need a reverse proxy?**

A reverse proxy acts as a secure intermediary that receives client requests and routes them to the appropriate backend containers.

**1-6 Why is docker-compose so important?**

Docker Compose is crucial because it lets us define, configure, and manage multi-container applications (like a database, backend, and proxy) in a single YAML file instead of juggling dozens of complex terminal commands.

**1-7 Document docker-compose most important commands.**

The most important commands are:
- docker compose up -d --> allows to launch all the services in detached mode
- docker compose logs --> debug
- docker compose down --> stop everything properly

**1-8 Document your docker-compose file.**

This file manages a complete three-tier architecture (database, backend, reverse proxy) by automating their setup, startup sequence, and data persistence. It effectively secures the application by isolating the database and API on internal networks, exposing only the HTTP server to the outside world via port 80.
