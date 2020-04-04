Google's Cloud Launcher is now the GCP Marketplace





javascript search string

"Hello World!".startsWith("He"); // true

var haystack = "Hello world";
var prefix = 'orl';
haystack.startsWith(prefix); // false




### Query data
#### Query Documents
* Check if document exists
  * Firebase API:
        var docRef = db.collection("cities").doc("SF");
        docRef.get().then(function(doc) {
            if (doc.exists) {
                console.log("Document data:", doc.data());
            } else {
                // doc.data() will be undefined in this case
                console.log("No such document!");
            }
        }).catch(function(error) {
            console.log("Error getting document:", error);
        });

  * Angularfire API:
        this.afs.collection<Category>(`users/${u.uid}/categories`).snapshotChanges().pipe(
          map(actions => actions.map(a => {
            const data = a.payload.doc.data() as Category;
            const id = a.payload.doc.id;
            const queryPath = a.payload.doc.ref.path;
            const exists = a.payload.doc.exists;
            return { id, queryPath, exists, ...data };
          }))
        );

#### Query more than one document -- Creating a query with primitive/scalar values
Queries are created by building on the firebase.firestore.CollectionReference.

    afs.collection('items', ref => ref.where('size', '==', 'large'))

Range filters can only be specified on a single field:

    // WARNING: Do not copy and paste. This will not work!
    ref.where('state', '>=', 'CA')
       .where('population', '>', 100000)

Range filter and orderBy cannot be on different fields:

       // WARNING: Do not copy and paste. This will not work!
       ref.where('population', '>', 100000).orderBy('country')

 Range filters / orderBy cannot be used in conjuction with user-defined data, they require composite indexes be defined on the specific fields.

       // WARNING: Do not copy and paste. This will not work!
       ref.where('tags.awesome', '==', true).orderBy('population')
