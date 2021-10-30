Description:
Simple example of using a file to execute sql statements in a mysql pod. It does not uses the version from charts or the values.yaml file, its a basic example of how to get sql files into a pod. This chart can be improved.

Clone repo.

Start docker and minikube.

Run the following where test is the release name
```
helm install test ./helmexample 
```

You can view configmap and find the SQL statements both from the file location files/sample-file.sql using Files.Get and the other that was embedded into configmap called mysql_example.sql
```
kubectl describe configmap mysqlconfigmap
```

Inspecting the pod using the following command (note: no password has been set for the database this is not recommended to do for a Ops system, also replace mysql-7678988967-7vkvs with you pod name which can be achieved through: kubectl get pods)
```
kubectl exec -ti mysql-7678988967-7vkvs -- mysql -u root
```

You can then run mysql statements to check the databases available, and those that have been created, using this code it will be: test and samsDatabase2, with some additional default databases created by the mysql image
```
show databases;
```

To delete pod (note: test was used as the release name during the install command, hence used in command below)
```
helm delete test
```


