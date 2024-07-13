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

* deleteOne y deleteMany

``` 
db.nombColec.deleteOne (filter,options)
db.nombColec.deleteMany(filter,options)

https://docs.mongodb.com/manual/refer...

use videoRedesPlus
db.pelisBasura.find()
//DELETE ONE
db.pelisBasura.deleteOne( {_id: "tt0110912" } )
db.pelisBasura.deleteOne( {title: "Django Unchained" } )

//DELETE MANY
db.pelisBasura.deleteMany( {director: "Quentin Tarantino"} )
db.pelisBasura.deleteOne ( {director: "Quentin Tarantino"} )

//
db.pelisBasura.deleteOne ( {year: {$gt:2000}} )
db.pelisBasura.deleteMany( {year: {$gt:2000}} )
``` 

*  CARGAR UN FICHERO .js DESDE LA CONSOLA

``` 
mongo "mongodb+srv://[SUSTITUYE].mongodb.net/test" --username m001-student  nombreArchivo.js
   -u = --username 
   -p = --password

mongo "mongodb+srv://[SUSTITUYE].mongodb.net/test" -u m001-student -p password
 
  Cluster: REDES PLUS
   -videoRedesPlus.pelisBasura

  use videoRedesPlus
  
  db.pelisBasura.find().pretty()
  ``` 