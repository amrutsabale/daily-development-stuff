#### Execute to see what process is bound to the port

```
lsof -i :5432
```

Some instance of Postgres is running. You can execute kill <pid> to kill it if you want. You can also use 5432 instead of 5432:5432 in your docker command or docker-compose file and let docker choose the host port automatically.

```
kill <pid>
```

once you have the PID you can terminate it with the following:
```
kill -9 <pid>

````
Doing the -9 on kill sends a SIGKILL (instead of a SIGTERM). SIGTERM has been ignored by node for me sometimes.
