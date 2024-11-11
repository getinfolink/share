# Check What’s Using Port 5672
To see which process is currently using port 5672, run the following command:

```bash
sudo lsof -i :5672
```
This will show you the process ID (PID) and application currently using the port. You can also check the PID directly with:

```bash
sudo netstat -tuln | grep 5672
```


2. Kill the Process Using Port 5672 (If Safe to Do So)
If you determine that the process using port 5672 can be stopped safely, you can terminate it with:

```bash
sudo kill -9 <PID>
```
Replace <PID> with the process ID found from the previous step. 
However, be cautious with this, as killing the wrong process can disrupt other services.

3. Change the Port in Your Configuration
If you cannot stop the process on port 5672, you can change the port your application is trying to bind to. For example, if this is related to RabbitMQ or a Docker container, you can change the binding port to a different one.

In Docker Compose, you could specify a different port mapping in the ports section:

yaml
ports:
  - "5673:5672"  # Change host port to 5673 if 5672 is in use
4. Restart Docker
Sometimes, Docker containers do not release ports properly when they exit. Restarting Docker can help clear this up:

```bash
sudo systemctl restart docker
```

5. Remove Exited Docker Containers
If you’re using Docker and there are old containers that haven’t released the port, you can remove them with:

```bash
docker ps -a
docker rm <container_id>
```
Or, to remove all stopped containers:

```bash
docker container prune
```
After taking these steps, try running your application or Docker container again.