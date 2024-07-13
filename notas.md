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