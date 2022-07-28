# From Starting Point
FROM node

# This sets the working directory for docker
# All following commands will be executed from this directory
# Try Hover Documentation
WORKDIR /app

# COPY Source Dest
# When copying only the package.json file before the `npm install` layer, we can change the source code,
# and everything before and including the `npm install` layer will be cached
# Example
# => [1/5] FROM docker.io/library/node@sha256:fb040635dd58488aaa66d75e253997e414e1c4adf852ce
# => CACHED [2/5] WORKDIR /app
# => CACHED [3/5] COPY package.json /app
# => CACHED [4/5] RUN npm install
# => [5/5] COPY . /app
COPY package.json /app

# This will run on image creation/build, so this would not run when the image is "started"
RUN npm install

# COPY Source Dest
# Since we changed the working directory to `/app` the second `.`(dest) will represent `/app`
# Since /app is also a absolute path, it would still be correct if we are using `/app` and would be a little bit more explizit
COPY . /app

# Expose this port because it is defined in server.js
# I just want to clarify again, that EXPOSE 80 in the Dockerfile in the end is optional. 
# It documents that a process in the container will expose this port. 
# But you still need to then actually expose the port with -p when running docker run. 
# So technically, -p is the only required part when it comes to listening on a port. 
# Still, it is a best practice to also add EXPOSE in the Dockerfile to document this behavior.
EXPOSE 80

# After that start the server
CMD ["node", "server.js"]
