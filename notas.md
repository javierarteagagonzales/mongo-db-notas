* Método update many
``` 
db.movieDetails.find({rated: null})

// Eliminar el campo rated de todos los documentos si su valor es null
db.movieDetails.updateMany ( 
 {rated: null} , 
 {$unset: { 
  rated: ""
  }
 })
``` 

* UPSERTS
``` 
 UPSERTS = UPdate + inSERTS

 
Cluster: 
   -videoRedesPlus.pelisBasura

db.pelisBasura.find()

db.pelisBasura.updateOne ( 
 {_id: "tt0110913"} , 
 {$set: { 
  "title":"Pulp Fiction",
  "year":1994,  
  "director":"Quentin Tarantino"  
  }
``` 

* ReplaceOne
``` 
 REPLACEONE

db.nombColec.replaceOne(filter,replacement,options)

https://docs.mongodb.com/manual/refer...

  replacement: 
 -no puede contener operadores de actualización

Cluster: REDES PLUS
   -videoRedesPlus.pelisBasura

 updateOne vs replaceOne


db.pelisBasura.find()

db.pelisBasura.replaceOne(
 {title: "Django Unchained"}, 
 {
  "title":"Django Unchained",
  "director":"Quentin Tarantino",
  "cast": ["Jamie Foxx","Christoph Waltz","Leonardo  DiCaprio","Kerry Washington"]
 })
``` 