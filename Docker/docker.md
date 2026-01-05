# 🐳 Docker – Detailed Learning Notes

These are my personal notes while learning Docker by doing hands-on practice.
This is not a tutorial — it’s what I understood while breaking and fixing things.

---

## 1. What Docker actually does

Docker helps package an application along with all its dependencies into a
single unit called an **image**.

When this image is run, it becomes a **container**.

This solves the common problem:
> “It works on my system but not on yours.”

---

## 2. Image vs Container (this confused me initially)

**Image**
- Blueprint / template
- Read-only
- Built using a Dockerfile
- Cannot run by itself

**Container**
- Running instance of an image
- Actually executes the application
- Can be started, stopped, deleted
- Multiple containers can run from the same image

One image ➝ many containers.

---

## 3. Dockerfile (line-by-line explanation)

Example Dockerfile:

```dockerfile
FROM node:18-alpine
```
Base image for the container

Comes with Node.js preinstalled

alpine is lightweight, so image size is small

```
 WORKDIR /app
```
Sets /app as the working directory inside the container

All next commands run inside this folder

If /app does not exist, Docker creates it

```
COPY package*.json ./
```
Copies package.json and package-lock.json

Done before copying full code to use Docker cache

Helps avoid reinstalling dependencies every time

```
RUN npm install
```
RUN npm install
Runs during image build time

Installs all dependencies inside the image

```
COPY . .
```
Copies remaining application files into the container

```
EXPOSE 8000
```
Documents the port the app uses

Does NOT expose the port by itself

Actual port mapping happens while running the container

```
CMD ["node", "app.js"]
```
Command that runs when the container starts

JSON array format is important
I initially made a mistake like this:
```
CMD["node","app.js"]
```
which caused a Dockerfile parse error

## 4. Building and Running a Docker Image
**Build the image**
```
docker build -t my-app .
```
-t my-app gives a name to the image

. tells Docker to look for Dockerfile in current directory

**Run the container**
```
docker run -p 8000:8000 my-app
```
First 8000 → host machine port

Second 8000 → container port

## 5. localhost vs 0.0.0.0 (important concept)
**Inside a container:**
localhost refers only to the container itself

The app must listen on 0.0.0.0 to be accessible from outside

Correct example:
```
app.listen(8000, "0.0.0.0");
```
If the app binds to localhost, the browser cannot access it.

This was one of my biggest confusions initially.

## 6. Viewing Container Logs (Debugging)
**To see container logs:**
```
docker logs <container_id>
```
**To see live logs:**
```
docker logs -f <container_id>
```
Logs help debug:

App crashes

Port issues

Environment variable problems

## 7. Container Lifecycle (mental model)
```
Image → Container → Stop → Remove
```
**Useful commands:**
```
docker ps
docker ps -a
docker stop <id>
docker rm <id>
docker rmi <image_id>
```
## 8. Common Mistakes I Made
CMD syntax error in Dockerfile

Confusion between image and container

Using localhost instead of 0.0.0.0

Forgetting to map ports while running container

Fixing these helped me understand Docker better.
## 9. Key Takeaways
Docker is not hard, but small mistakes break things

Understanding ports and networking is very important

Logs are the best way to debug containers

Hands-on practice teaches more than theory
