# Docker Projects

```  Projects are listed in the folders  ```

## Basic Requirements on OS
* pip
* python

## Projects:
```bash
Click on the Projects to view the code related to the resource/tool.
```
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


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.
