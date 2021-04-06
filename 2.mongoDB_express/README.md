## Minikube
- mongoDB and mongoDB express -> stateful Set # persistent storage

* NAMESPACE - <your_defined_namespace>
* NAME - mongo-express-service
* TARGET PORT - 8081
* URL - http://<your_external_IP>:30000
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