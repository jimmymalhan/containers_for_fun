## Minikube
- mongoDB and mongoDB express -> stateful Set # persistent storage
|-----------|-----------------------|-------------|---------------------------------|
| NAMESPACE |         NAME          | TARGET PORT |            URL                  |
|-----------|-----------------------|-------------|---------------------------------|
| defined   | mongo-express-service |        8081 | http://<your_External_IP>:30000 |
|-----------|-----------------------|-------------|---------------------------------|

### Creating a New Database on the MongoExpress(URL) will lead you to following workflow per architecture:
- 1 -> New Database Name
- 2 -> MongoExpress External Service
- 3 -> Mongo Express Pod
- 4 -> Mongo DB Internal Service
- 5 -> Mongo DB Pod

#### Validating YAML?
```bash
brew install yamllint
yamllint <filename>```