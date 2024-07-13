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