Mongodb
=======

# Commandos in de Mongo shell

zoeken in een Mongodb database kan met het commando mongo::

    mongo
    show dbs
    use "database naam"
    show collections

    db."collectienaam".find({})

op de commandline:

    echo "db.collectienaam.find({})" | mongo databasenaam

# Handmatig updaten van records

    db.collectienaam.updateOne({ "_id" : ObjectId("objectidnummer") }, { $set : { "veld naam" : waarde } } )

    db.collectienaam.update  is deprecated.

# Mongodb database dump
    mongodump databasenaam 

