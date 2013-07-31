# Integrating with external tools

## Firefox Developer Tools

Now that the entire tool suite can be accessed remotely, we need to identify compelling integration types and provide the developer community with well-maintained and documented sample implementations.

ID|Name|Story|User|Priority
--- | --- | :--- | --- | ---
dtapi-28|Integration docs|As a developer looking to integrate Firefox with $SomeIDE, I would like to be able to access documentation and tutorials on how to connect my application to Firefox via the remote protocol.|All
dtapi-29|Integration Sample|As a developer I would like a well documented sample implementation of each type of remote protocol integration that is available that I can easily run on my own system.|All

### Connecting to non-Gecko stacks

In order to help developers debugging modern, complex single-page web apps it could be beneficial to be able to  debug both client and server code in the same tools.

ID|Name|Story|User|Priority
--- | --- | :--- | --- | ---
dtapi-30|Node Support|As a full-stack developer I would love to be able to debug both client and server-side code in my express app.|All
dtapi-31|Attach from a process|In my web stack, I have not only webservers but also worker processes running, and in order to debug he full stack I need to be able to get the worker scripts to contact the debugger as well.|All
