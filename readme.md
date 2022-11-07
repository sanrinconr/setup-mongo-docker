# Docker compose mongo db

Script to start a mongo db inside a container fast!

## How to
### Run script
```bash
./setup_mongo.sh
```

The script enter into the container, ready for the next step

### Creating users
First create the user root to manage the db, enter in db with:
```bash
mongosh
```
And after run the query:
```bash
use admin
db.createUser(
  {
     user: "root",
     pwd: "securepassword",
     roles:["root"]
  }
);   

```

Exit from console and enter again with:
```bash
mongosh -u root
```

Create the user for the database of the app:
```
use photos
db.createUser(
   {
      user: "photos",
      pwd: "securepassword",
      roles:[
         {
            role:"readWrite",
            db:"photos"
         }
      ]

   }
);
```

## Location of data
The data of db is saved in host folder, specifically `/var/lib/mongo`
