The most common commands in a dockerfile are:

### FROM
Syntax:
```dockerfile
FROM <image>
FROM 19-alpine
```
FROM must be the first non-comment instruction in a dockerfile.
It can appear multiple times in a dockerfile in order to create multiple images.

### WORKDIR
Syntax:
```dockerfile
WORKDIR </path/to/workdir>
WORKDIR /app
```

It sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, and `ADD` instruction that follow it.

It can appear multiple times in a dockerfile, and can also be used with a relative directory to the previous WORKDIR command.

### COPY
Syntax:
```dockerfile
COPY <source> <destination>
COPY . /app
```

Used to copy files or directories from **source** and adds them to the filesystem of the image at the path **destination**.

If the destination folder does not exist, it's created along with all missing directory paths.

The destination path can be absolute, or relative to the one set in WORKDIR.
The source path must be relative to the source directory in which the Dockerfile is being built.

### EXPOSE
Syntax:
```dockerfile
EXPOSE <port>
EXPOSE 3000
```

Used to inform docker that the container listens on the specified network port(s) at runtime.
EXPOSE does not make the ports of the container accessible to the host.

### ENTRYPOINT
Syntax:
```dockerfile
ENTRYPOINT ["<executable>", "param1", "param2"]
ENTRYPOINT ["dotnet", "WebAPI.dll"]
```

This instruction allows you to configure a container that will run as an executable.

The drawback from using this is that the executable will not receive UNIX signals nor will it have a Process Identified (PID).

### CMD
Syntax:
```dockerfile
CMD ["<executable>", "param1", "param2"]
CMD ["npx", "serve", "-s"]
```
The main purpose of this instruction is to provide a default command for the executing container. In case an executable was not included, an ENTRYPOINT must also be provided.

### RUN
Syntax:
```dockerfile
RUN ["<executable>", "param1", "param2"]
RUN ["npm", "run", "build"]
```
Used to run shell commands, and commiting them into the container image. It is not used as a startup command for the container.