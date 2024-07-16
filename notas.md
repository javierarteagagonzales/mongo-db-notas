
# Mongo DB Notas

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

## Operadores de consultas

* Comparación
``` 

 • $eq  -  { field: { $eq: value } }

 Equivalente a { field: value }

 • $ne
incluye documentos que no contienen el campo.

 • $gt  -  {field: {$gt: value} }
 • $gte
 • $lt
 • $lte


 • $in
{ field: { $in: [value1, value2, ... valueN ] } }

 • $nin
``` 

* Elementos 💲exists 💲type
```

 • $exists  -  { field: { $exists: boolean } }

   - true :  documentos que contienen el campo (null)
   - false:  documentos que no contienen el campo 

 { title : "The Martian" }

 
 • $type    -  { field: { $type: BSON type } }
   -video.movies

 - double = Double
 - int    = 32-bit integer
 - long   = 64-bit integer
 - string = String
```

* 💲and 💲or 💲nor 💲not
```
 $or 
 Une las cláusulas con un OR lógico 
   
   { $or: [ { selector1 }, { selector2 }, ... ] }

 • $nor 
 Une cláusulas de consulta con un NOR lógico 
 
   { $nor: [ { selector1 }, { selector2 }, ... ] }

 • $and 
 Une cláusulas de consulta con un AND lógico 

   { $and: [ { selector1 }, { selector2 }, ... ] }

 • $not 
 Invierte el efecto de una expresión de consulta.

   { campo: { $not: { selector } } }
```

* Operadores para Vectores 💲all💲size💲elemMatch
```

 • $all 

 Solo Documentos que contienen el campo vector con todos los valores
   { campo: {$all: [valor1, valor2, ...] } }

   - Pueden tener más valores, nunca menos
   - No tienen que estar en el mismo orden
 

 • $size

  Solo Documentos que contienen el campo vector con el tamaño indicado.
 
 { campo: { $size: 2 } } )
 
   - no acepta rangos de valores. 



 • $elemMatch
 
  Solo Documentos que contienen un elemento del campo vector que coincide con todas las condiciones especificadas 

   { campo: { $elemMatch: { selector1 , selector2 , ... } } }
```

* Operador 💲regex
```

 • $regex 

  {campo: { $regex: /pattern/ options } }
   

   / / para delimitar la expresión regular
   ^   significa comenzar desde el principio 
   .   comodín (cualquier carácter) 
   *   cualquier carácter varias veces
```