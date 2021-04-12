## Troubleshooting

### Port is already running for npm?
### First, you would want to know which process is using port 3000

```bash
sudo lsof -i :3000 ```

### this will list all PID listening on this port, once you have the PID you can terminate it with the following:

```bash
kill -9 {PID} ```