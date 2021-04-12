## Troubleshooting

### Port is already running with npm?
#### First, you would want to know which process is using port 3000 <port_name>

```
sudo lsof -i :3000
```

### this will list all PID listening on this port, once you have the PID you can terminate it with the following:

```
kill -9 {PID} 
```
