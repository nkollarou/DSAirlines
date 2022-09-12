# DS Airlines Project
Το project DS Airlines αποτελεί μια υπηρεσία κράτησης αεροπορικών εισητηρίων που υλοποιείται με την χρήση Python και Flask και συνδέεται με ένα container της MongoDB όπου υπάρχει η βάση δεδομένων DSAirlines, η οποία αποθηκεύει τα απαραίτητα δεδομένα που χρειάζεται η υπηρεσία για την λειτουργία της στα αντίστοιχα collections. Με το άνοιγμα ενός browser στην διεύθυνση `http://0.0.0.0:5000/` θα εμφανιστεί η αρχική σελίδα της υπηρεσίας.

## Πρόσβαση στην υπηρεσία
Προκειμένου ένας χρήστης να έχει πρόσβαση στην υπηρεσία DS Airlines μπορεί να κατεβάσει τα αρχεία του σγκεκριμένου repository και να πληκτρολογήσει στο terminal την εντολή `(sudo) docker-compose up -d`, αφότου έχει μεταβεί στο directory που τα έχει αποθηκεύσει.
**Σημείωση:** Το `sudo` είναι απαραίτητο σε περίπτωση που το λειτουτγικό σύστημα του υπολογιστή είναι linux.

# Περιγραφή Υπηρεσίας
Στην υπηρεσία DS Airlines υπάρχουν χρήστες δύο ειδών, οι διαχειριστές (admins) και οι απλοί χρήστες (users). 
Οι απλοί χρήστες έχουν πρόσβαση στα παρακάτω endpoints:
- /sign_up
- /login
- /menu
- /search_flight
- /book_ticket
- /show_bookings
- /cancel_booking
- /show_all_bookings
- /show_bookimgs_cost
- /show_bookinhs_destination
- /deactivate_account
- /activate_account
- /logout

Οι διαχειριστές έχουν την δυνατότητα πρόσβασης στα παρακάτω endpoints:
- /login_admin
- /update_password
- /menu_admin
- /create_flight
- /create_admin
- /update_flight
- /delete_flight
- /logout

# Endpoints
## Endpoint '/'
Το endpoint '/' είναι η αρχική σελίδα της υπηρεσίας. Σε αυτό εμφανίζεται η αρχική σελίδα της υπηρεσίας από όπου ο χρήστης μπορεί να επιλέξει την υπηρεσία που επιθυμεί να εκτελέσει. Οι επιλογές του χρήστη είναι: α) εγγραφή ως απλός χρήστης, β)σύνδεση ως απλός χρήστης, γ) σύνδεση ως διαχειριστής, δ) ενεργοποίηση λογαριασμού, ε) αποσύνδεση από την υπηρεσία. Έπειτα, ανάλογα με την επιλογή του, οδηγείται στο αντίστοιχο endpoint.  

![image](https://user-images.githubusercontent.com/103967806/189339955-e93ec8d3-1015-4de9-8544-037c250010fe.png)

## Endpoint 'sign_up'
Στο endpoint αυτό μπορεί ένας χρήστης να δημιουργήσει λογαριασμό στην υπηρεσία συμπληρώνοντας μια φόρμα με τα στοιχεία του (email, ονοματεπώνυμο, όνομα χρήστη, κωδικός, αριθμός διαβατηρίου). Όλα τα πεδία είναι υποχρεωτικά και η παράλειψη συμπήρωσης κάποιου από αυτά εμποδίζει την υποβολή της φόρμας, καθώς παράλληλα εμφανίζεται σχετικό μήνυμα στην οθόνη. Το email, το όνομα χρήστη και ο αριθμός διαβατηρίου είναι μοναδικά στοιχεία για τον κάθε χρήστη, επομένως στην φόρμα συμπληρωθούν αυτά τα πεδία με στοιχεία που χρησιμοποιούνται ήδη από άλλον χρήστη, η εγγραφή δεν ολοκληρώνεται και υπάρχει σχετική ενημέρωση στην οθόνη. Επιπλέον, ο κωδικός που θα συμπληρωθεί πρέπει να αποτελείται από τουλάχιστον οχτώ χαρακτήρες, εκ των οποίων ο ένας πρέπει να είναι αριθμός. Σε περίπτωση που ο κωδικός δεν είναι έγκυρος η εγγραφή δεν πραγματοποιείται και ο χρήστης ενημερώνεται με σχετικό μήνυμα στην οθόνη που υποδεικνύει και τα απαραίτητα στοιχεία που πρέπει να εμπεριέχονται στον κωδικό. Τέλος, ο αριθμός διαβατηρίου πρέπει να αποτελείται από δύο χαρακτήρες που ακολοθούνται από επτά αριθμούς. Σε περίπτωση που αυτό το κριτήριο δεν πληρείται ο χρήστης καλείται να επαναλάβει την εγγραφή του και να συμπληρώσει σωστά τον αριθμό διαβατηρίου.   

![image](https://user-images.githubusercontent.com/103967806/189340030-0b812cf9-55c2-4479-a255-e037c4487bf4.png)
Παράδειγμα δημιουργίας λογαριασμού:

![image](https://user-images.githubusercontent.com/103967806/189343371-6f3925d4-9816-4c29-8540-ade32e4e64df.png)

Ο λογαριασμός δημιουργήθηκε με επιτυχία:

![image](https://user-images.githubusercontent.com/103967806/189343610-0a5f9d10-79ea-44ba-9505-900d76dc50ad.png)

Εάν επιχειρηθεί δημιουργία λογαριασμού με το ίδιο email, όνομα χρήστη ή αριθμό διαβατηρίου η εγγραφή δεν είναι δυνατή:

![image](https://user-images.githubusercontent.com/103967806/189343951-b2837211-148b-4eb4-a189-2193239da2b6.png)

![image](https://user-images.githubusercontent.com/103967806/189344497-f79e4956-c75b-46a5-8966-c85644d2c5b4.png)

![image](https://user-images.githubusercontent.com/103967806/189344617-2f7e6557-c437-4968-b969-bd264ae6b182.png)

Εάν ο κωδικός δεν έχει την κατάλληλη μορφή:

![image](https://user-images.githubusercontent.com/103967806/189345833-a6890ac2-2ccc-4ee6-af51-5a12dbfe1b1d.png)

![image](https://user-images.githubusercontent.com/103967806/189345944-5acc904f-3edd-4664-b0c1-0a15e72b4cbc.png)

Εάν ο αριθμός διαβατηρίου δεν έχει την κατάλληλη μορφή:

![image](https://user-images.githubusercontent.com/103967806/189346138-d299956d-0289-4134-b128-b6a76ab2765f.png)

![image](https://user-images.githubusercontent.com/103967806/189346276-00e1abfd-aaae-4e59-9bfd-5b8e7eebe890.png)


## Endpoint 'login'
Στο endpoint αυτό μπορεί ένας απλός χρήστης να συνδεθεί με τον λογαριασμό του στην υπηρεσία συμπληρώνοντας σε μία φόρμα το όνομα χρήστη του ή το email του και τον κωδικό του.  

![image](https://user-images.githubusercontent.com/103967806/189346408-43d8e87b-8b50-4639-b013-c59d863e71e3.png)

Σύνδεση με όνομα χρήστη:

![image](https://user-images.githubusercontent.com/103967806/189486517-5baf67ed-032c-437f-a7af-8f36e5525b22.png)

Σύνδεση με email:

![image](https://user-images.githubusercontent.com/103967806/189486537-d46a3a1d-3e30-49d3-b19b-749c26c8e723.png)

Εφόσον τα στοιχεία είναι σωστά πραγματοποιείται σύνδεση.

![image](https://user-images.githubusercontent.com/103967806/189486573-abe7399c-b052-4965-9604-40456c24c2d2.png)

 Εάν το email ή το username του χρήστη δεν είναι σωστό εμφανίζεται σχετικό μήνυμα:
 
 ![image](https://user-images.githubusercontent.com/103967806/189346608-a4691716-c120-4b2a-909b-b61cccb19bca.png)

Εάν ο κωδικός δεν είναι σωστός εμφανίζεται ανάλογο μήνυμα:

![image](https://user-images.githubusercontent.com/103967806/189346749-cb7b18ea-b128-428c-8a3c-27d5afd2a3d3.png)

## Endpoint '/menu'
Σε αυτό το endpoint έχουν πρόσβαση οι απλοί χρήστες που έχουν συνδεθεί στην υπηρεσία. Μέσω αυτού υπάρχει η δυνατότητα επιλογής τις υπηρεσίες που ο χρήστης επιθυμεί. 
Συγκεκριμένα, οι διαθέσιμες υπηρεσίες είναι α) αναζήτηση πτήσης, β) κράτηση εισητηρίου, γ) εμφάνιση κράτησης, δ) ακύρωση κράτησης, ε)εμφάνιση όλων των κρατήσεων, στ) εμφάνιση των κρατήσεων με την υψηλότερη και την χαμηλότερη τιμή, ζ) εμφάνιση όλων των κρατήσεων για έναν προορισμό, η) απενεργοποίηση λογαριασμού και θ)αποσύνδεση.

![image](https://user-images.githubusercontent.com/103967806/189487682-e466948d-1cb2-49ea-be08-b947b63e7a29.png)

## Endpoint '/search_flight'
Στο endpoint αυτό έχουν πρόσβαση οι απλοί χρήστες αφού συνδεθούν. Μέσω αυτού μπορούν να ανζητήσουν πτήσεις με βάση ορισμένα κριτήρια που θα συμπληρώσουν στην ακόλουθη φόρμα. 

![image](https://user-images.githubusercontent.com/103967806/189487633-3dd3d132-f9fd-4eb6-af26-36d8ea395e85.png)

Εφόσον υπάρχει κράτηση με τα στοιχεία που ζητήθηκαν, εμφανίζονται λεπτομέρειες για αυτήν.

![image](https://user-images.githubusercontent.com/103967806/189487593-9ceed2d8-c2f3-4a54-8d66-974968d682b9.png)

## Enpoint '/book_ticket'
Στο endpoint αυτό μπορεί ένας συνδεδεμένος χρήστης να πραγματοποιήσει κράτηση ενός εισητηρίου συμπληρώνοντας την πρακάτω φόρμα.

![image](https://user-images.githubusercontent.com/103967806/189487539-8f9d0e59-aead-4dd4-831b-3988075fbe78.png)

Έπειτα από την επιτυχή καταχώρηση των στοιχείων για την κράτηση, εμφανίζονται όλα τα στοιχεία για αυτήν.

![image](https://user-images.githubusercontent.com/103967806/189535839-fa822423-83de-4eb1-a7b8-cc9374d7f502.png)

Σε περίπτωση που η πιστωτική κάρτα που συμπληρώνεται στο αντίστοιχο πεδίο, δεν αποτελείται από 16 αριθμούς, εμφανίζεται σχετικό μήνυμα που ενημερώνει τον χρήστη. 

![image](https://user-images.githubusercontent.com/103967806/189535584-ecfd5e73-6470-444e-8280-c6ea45128669.png)

Επιπλέον, εάν ο μοναδικός αριθμός πτήσης δεν αντιστοιχεί σε κάποια υπάρχουσα πτήση η κράτηση δεν πραγματοποιείται και ο χρήστης παροτρείνεται να ξαναπροσπαθήσει.

![image](https://user-images.githubusercontent.com/103967806/189535610-9e30af69-9d67-4fc8-94eb-4f33185f9f40.png)

Τέλος, εάν η πτήση που επιλέχθηκε δεν έχει διαθέσιμες θέσεις, ο χρήστης ενημερώνεται με σχετικό μήνυμα. 

## Endpoint '/show_booking'
Στο endpoint αυτό μπορεί ένας απλός χρήστης, που έχει συνδεθεί, να συμπληρώσει τον κωδικό μιας κράτησης που έχει πραγματοποιήσει προκειμένου να του εμφανιστούν στοιχεία για αυτήν.

![image](https://user-images.githubusercontent.com/103967806/189594049-5e830865-cdb5-4f2e-b4b1-e71b40cfec73.png)

Εάν ο κωδικός είναι σωστός, εμφανίζονται τα στοιχεία της κράτησης.

![image](https://user-images.githubusercontent.com/103967806/189593992-47cc80e5-1235-451c-a040-35aaac401e3f.png)

## Endpoint '/cancel_booking'
Στο endpoint '/cancel_booking' μπορεί ένας συνδεδεμένος χρήστης να διαγράψει μια κράτηση που έχει πραγματοποιήσει, συμπληρώνοντας τον κωδικό της κράτησης. 

![image](https://user-images.githubusercontent.com/103967806/189536151-b6b88eee-96fe-451c-80f9-aa8420f7f681.png)

## Endpoint '/show_all_bookings'
Στο endpoint αυτό μπορεί ένα συνδεδεμένος χρήστης να εμφανίσει όλες τις κρατήσεις του σε χρονολογική σειρά. Μπορεί να επιλέξει εάν θέλει πρώτα να εμφανίζονται οι νεότερες ή οι παλιότερες κρατήσεις. 

![image](https://user-images.githubusercontent.com/103967806/189536347-69ca780a-c627-470e-9ffd-4f429bdcb089.png)

## Endpoint '/show_bookings_cost'
Στο endpoint αυτό εμφανλιζονται οι κρατήσεις με την χαμηλότερη και υψηλότερη τιμή που έχει πραγματοποιήσει ένας συνδεδεμένος χρήστης. 

![image](https://user-images.githubusercontent.com/103967806/189536477-39f3098b-d669-4a0e-ae16-6a89111e43d2.png)


## Endpoint '/show_bookings_destination'
Στο endpoint αυτό ένας χρήστης μπορεό να συμπληρώσει στην φόρμα έναν προορισμό και στην συνέχεια θα του εμφανιστούν όλες οι κρατήσεις που έχει πραγματοποιήσει για τον προορισμό αυτό. 

![image](https://user-images.githubusercontent.com/103967806/189536577-d7de919a-0061-444a-9739-50b59fc29149.png)

Εάν συμπληρώσει έναν προορισμό για τον οποίο δεν έχει πραγματοποιήσει καμία κράτηση, εμφανίζεται σχετικό μήνυμα. 

![image](https://user-images.githubusercontent.com/103967806/189536624-53a671d3-b29f-4dbc-9d53-68516e0fc14b.png)

## Endpoint '/deactivate_account'
Ο χρήστης μεταβαίνοντας σε αυτό το endpoint επιλέγει να απενεργοποιήσει τον λογαριασμό του. Αφού τον απενεργοποιήσει εμφανίζεται ένας κωδικός που είναι απαραίτητος για την επαναφορά του λογαριασμού.

![image](https://user-images.githubusercontent.com/103967806/189536808-dc6c47cc-84cf-4e99-8fb4-beac5968972c.png)


## Endpoint '/activate_account'
Σε αυτό το endpoint μπορεί ένας χρήστης να κάνει αίτηση για ενεργοποίηση του λογαριασμού του συμπληρώνοντας τον κωδικό ενεργοποίησης του. 

![image](https://user-images.githubusercontent.com/103967806/189540359-061d5f67-b29e-4425-afa1-de5baa1c4af7.png)

Εάν ο κωδικός είναι σωστός τότε ο λογαριασμός ενεργοποιείται και πάλι.

![image](https://user-images.githubusercontent.com/103967806/189541410-ca218891-8ea8-46fa-80ee-77f82abfc671.png)


## Endpoint '/login_admin'
Στο endpoint αυτό μπορούν να συνδεθούν οι διαχειριστές. Ο πρώτος διαχειριστής που δημιουργείται με την έναρξη του συστήματος έχει email "admin@unipi.gr" και κωδικό πρόβασης "pass123". Μετά την πρώτη σύνδεση ο διαχειριστής καλείται να αλλάξει κωδικό. 

![image](https://user-images.githubusercontent.com/103967806/189541531-464e338d-60af-46a4-abbb-175a69f857a3.png)

Εάν ο κωδικός είναι σωστός ο διαχειριστής μεταβαίνει στο menu για διαχειριστές.

![image](https://user-images.githubusercontent.com/103967806/189541557-bd410c68-84e7-4042-be75-091edfc287bb.png)

## Endpoint '/create_admin'
Σε αυτό το endpoint μπορεί ένας συνδεδεμένος διαχειριστής να δημιουργήσει νέους διαχειριστές συμπληρώνοντας τα στοιχεία τους στην φόρμα. Ο κωδικός πρόσβασης που συμπληρώνεται σε αυτή την φόρμα είναι προσωρινός. Κάθε διαχειριστής μετά την πρώτη του σύνδεση καλλείται να αλλάξει τον κωδικο του.

![image](https://user-images.githubusercontent.com/103967806/189541602-e9c0b87d-eb3a-4e2d-88e7-24994d598d83.png)

## Endpoint '/update_password'
Σε αυτό το endpoint μεταφέρεται ένας διαχειριστής που συνδέεται για πρώτη φορά για να συμπληρώσει τον νέου του κωδικό.

## Endpoint '/create_flight'
Στο endpoint αυτό μπορεί μόνο ο αρχικός διαχειριστής του συστήματος, με email "admin@unipi.gr" να δημιουργήσει νέες πτήσεις.

![image](https://user-images.githubusercontent.com/103967806/189541888-8b75b783-e7fc-49b6-91a1-4dd5311349c4.png)

Κατά την δημιουργία της πτήσης πραγματοποιείται έλεγχος προκειμένου να μην υπάρχουν περισσότερες από μία πτήσεις με τον ίδιο κωδικό. 

![image](https://user-images.githubusercontent.com/103967806/189541899-d2cabf9d-bd39-499e-b484-142fda1abd58.png)

## Endpoint '/update_flight'
Στο endpoint αυτό μπορεί ένας συνδεδεμένος διαχειριστής να διορθώση την τιμή κάποιας υπάρχουσας πτήσης, εφόσον αυτή είναι άδεια. Σε άλλη περίπτωση εμφανίζεται σχετικό μήνυμα στην οθόνη που τον ενημερώνει.

![image](https://user-images.githubusercontent.com/103967806/189541997-df1bb7c9-0232-4332-bb68-961ec6cd1724.png)

## Endpoint '/delete_flight'
Σε αυτό το endpoint μπορεί κάποιος συνδεδεμένος διαχειριστής να διαγράψει μία πτήση εισάγωντας τον μοναδικό κωδικό της. 

![image](https://user-images.githubusercontent.com/103967806/189542120-7ea2e999-1cfc-44f5-ae14-13590187901e.png)

## Endpoint '/logout'
Το endpoint αυτό είναι κοινό για τους απλούς χρήστες και τους διαχειριστές. Μεταβαίνοτνας σε αυτό μπορούν και οι δυο κατηγορίες να αποσυνδεθούν.
