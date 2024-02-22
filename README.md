Πανεπιστήμιο Ιωαννίνων
Τμήμα Μηχανικών Ηλεκτρονικών Υπολογιστών και Πληροφορικής







Ανάκτηση Πληροφορίας





Μέλη ομάδας:

Ελευθέριος-Χρήστος Δριτσώνας, 4668
Φωτόπουλος Στέφανος, 4829






ΑΚΑΔΗΜΑΪΚΟ ΕΤΟΣ 2023
ΠΑΡΑΔΟΣΗ: Παρασκευή 19 Mαΐου







  
 
Contents
1.Περιγραφή της εργασίας	3
Ερώτημα Α	3
Ερώτημα Β	4


 
 

1.Περιγραφή της εργασίας 

Το link για το github είναι το παρακάτω:
https://github.com/stef-fot/Anaktisi-Pliriforias.git





Ερώτημα Α 

Στην συγκεκριμένη αναφορά θα περιγράψουμε τα βήματα    που σχετίζονται με την υλοποίηση της 1ης φάσης στο μάθημα της Ανάκτησης Πληροφορίας.
ΣΥΛΛΟΓΗ ΕΓΓΡΑΦΩΝ

Σε αυτό το βήμα συλλέξαμε τα έγγραφα που θα χρησιμοποιήσουμε από τον παρακάτω σύνδεσμο:
https://www.kaggle.com/datasets/notshrirang/spotify-million-song-dataset
 (είναι ο σύνδεσμος που υπάρχει και στις διαφάνειες του μαθήματος).Στο συγκεκριμένο λίνκ περιέχονται 643 καλλιτέχνες με συνολικά 44824 τραγούδια(έγγραφα).
Στο GitHub όταν ανεβάσαμε το dataset διαμαρτυρήθηκε ότι το αρχείο ήταν μεγαλύτερο από τα 25ΜΒ με αποτέλεσμα να ανεβάσουμε το ίδιο αρχείο αλλά συμπιεσμένο(zip).

Το format του συγκεκριμένου αρχείου είναι σε μορφή .csv (comma separated values).

Στην πρώτη στήλη του αρχείου βλέπουμε το όνομα του καλλιτέχνη ή του συγκροτήματος.
Στη δεύτερη έχουμε το όνομα του τραγουδιού.
Η Τρίτη στήλη έχει το Link του τραγουδιου και τελειώνει σε .html.
Τέλος, η τέταρτη στήλη έχει όλα τα lyrics(στίχους) των τραγουδιών. 


 

Ερώτημα Β
Ανάλυση κειμένου και κατασκευή ευρετηρίου:
Αφού πρώτα δημιουργήσουμε έναν StandardAnalyzer και ένα ByteBuffersDirectory για να αποθηκεύουμε την πληροφορία θα χρειαστεί να φτιάξουμε και έναν IndexWriterConfig ο οποίος θα διατρέχει το ευρετήριο στην περίπτωση μας το αρχείο .csv με τα τραγούδια και θα καταγραφεί τις τιμές αυτού.
Έπειτα, θα έχουμε έναν QueryParser όπου θα εισάγουμε όλες τις πιθανές ερωτήσεις που μπορεί να κάνει ο χρήστης.Στη συνέχεια,υπάρχει ο DirectoryReader ο οποίος ανοίγει το ByteBuffersDirectory που δημιουργήσαμε και ένας IndexSearcher που έχει ως σκοπό να αναζητήσει πόσες φορές ικανοποιείται το query του χρήστη.
Αυτή την πληροφορία την κρατάμε σε έναν πίνακα hits όπου μετράμε τα scores. Επίσης, θα υπάρχει μια void συνάρτηση addDoc η οποία θα κατηγοριοποιεί τα πεδία του αρχείου .csv στα πεδία : Τίτλος τραγουδιού, Όνομα καλλιτέχνη , Ημερομηνία.  



Εισαγωγή: Ποιος είναι ο στόχος και η λειτουργικότητα του συστήματος

Ο στόχος για την συγκεκριμένη εργασία είναι να δημιουργήσουμε ένα interface στο οποίο ο χρήστης θα μπορεί να θέτει ερωτήματα τα οποία θα σχετίζονται με τραγούδια που είναι αποθηκευμένα στην Βάση Δεδομένων. Αυτό επιτυγχάνεται μέσω μιας γραφικής διεπαφής (GUI) για παράδειγμα όπως το search bar της μηχανής αναζήτησης της Google. 



Αναζήτηση: Πως θα γίνεται η αναζήτηση, τα είδη των ερωτημάτων
Αρχικά, η αναζήτηση θα γίνεται μέσω ενός search box το οποίο θα εμφανίζεται με σκοπό να εισάγει ο χρήστης την επιθυμητή ερώτηση που θέλει να κάνει στην βάση με τα τραγούδια. Τα επιτρεπτά ερωτήματα  που μπορεί να εισάγει είναι τα παρακάτω:
•	Το όνομα του καλλιτέχνη
•	Τον τίτλο κάποιου τραγουδιού
•	Κάποιον συγκεκριμένο στίχο ή στίχους από τραγούδι
•	Ημερομηνία Δημιουργίας του τραγουδιού




Παρουσίαση Αποτελεσμάτων: Πως θα παρουσιάζονται τα αποτελέσματα

Αρχικά, θα βρίσκουμε τα τραγούδια που ικανοποιούν το query(ερώτηση) που υπέβαλλε ο χρήστης και από αυτά θα εμφανίζονται σε ομάδες των 10 σε φθίνουσα σειρά με βάση τον αριθμό εμφανίσεων αυτού του ερωτήματος ανά τραγούδι. Έπειτα ο χρήστης θα έχει την επιλογή να δει τις επόμενες 10 πλειάδες(τραγούδια) που ικανοποιούν την ερώτηση.
Αυτό γίνεται μέχρι να τελειώσουν τα τραγούδια που έχουν αυτή την λέξη .Στο δεξί μέρος της γραμμής αναζήτησης θα υπάρχουν και suggested queries τα οποία μπορεί να επιλέξει ο χρήστης και να δει τα αποτελέσματά τους.



Σε αυτό το σημείο θα αναφέρουμε τα βήματα που χρειάζεται να κάνει κάποιος χρήστης που θέλει να τρέξει την εφαρμογή.

ΕΙΣΑΓΟΜΕΝΑ JARS:
οι βιβλιοθήκες που χρείαζεται να κάνει κάποιος Import για να τρέξει το πρόγραμμα είναι όλα τα jars που βρίσκονται εντός των φακέλων "modules","modules-thirdparty","modules-test-framework" που αφορούν την έκδοση της βιβλιοθήκης Lucene 9.5.0 για Java. Αυτοί οι φάκελοι θα γίνουν ορατοί στον χρήστη με την αποσυμπίεση του αρχείου lucene-9.5.0.zip.


ΒΗΜΑΤΑ ΕΚΤΕΛΕΣΗΣ


Βήμα 1:
Αρχικά θα πρέπει το συγκεκριμένο βήμα να εκτελεστεί μόνο 1 φορά. Συγκεκριμένα,θα πρέπει να τρέξουμε την κλάση LuceneInexer.java απλά πριν το κάνουμε αυτό θα πρέπει να ρυθμίσουμε 2 πράγματα.Εντός της κλασης και πιο συγκεκριμένα στο πεδίο INDEX_DIRECTORY θα πρέπει να ορίσουμε το path στο οποίο θα αποθηκευτεί το ευερετήριο για τα τραγούδια.Εμείς,by default έχουμε ορίσει το C:\temp\indexluc , όπου το indexluc είναι το όνομα του φακέλου του ευρετηρίου .Μετά από αυτό και εντός της main μεθόδου θα πρέπει να καθορίσουμε το όνομα του μονοπατιού στο οποίο είναι αποθηκευμένο το .csv αρχείο με τα τραγούδια που κατεβάσαμε από το  Kaggle έτσι ώστε το πρόγραμμα να μπορέσει να το διαβάσει.Μετά από αυτό το βήμα τρέχουμε αυτή την κλάση και ελέγχουμε αν όντως δημιουργήθηκε ο φάκελος του ευρετηρίου, με το όνομα indexluc στην περίπτωσή μας. Αφού επιβεβαιώσουμε ότι όλα είναι εντάξει πάμε στο Βήμα2.




Βήμα 2:
Σε αυτό το βήμα θα χρειαστεί να κάνουμε κάτι παρόμοιο και για την κλάση SeacrhHistoryItem.java. Συγκεκριμένα, εντός της κλάσης και εντός της μεθόδου addToHistory
θα πρέπει να γράψουμε το path στο οποίο θέλουμε να αποθηκευτεί το .txt αρχείο στο οποίο θα περιέχονται queries που έχουν υποβληθεί από χρήστες στο παρελθόν. Για να γίνει αυτό θα γράψουμε το path στην γραμμή 120( στην μεταβλητή file). ΠΡΟΣΟΧΗ: Το txt θα πρέπει να αποθηκευτεί εντός του φακέλου στον οποίο δημιορυγήσαμε το ευρετήριο με βάση όλα όσα αναφέρονται στο Βήμα1. Για παράδειγμα, στην δικιά μας περίπτωση όπου ο φάκελος του ευρετηρίου είναι ο indexluc το path που θα γράψουμε θα είναι το C:\temp\indexluc\search_history.txt, όπου search_history.txt το όνομα του .txt αρχείου με τα παλαιότερα queries.Προσαρμόστε τα αναλόγως.



Βήμα 3:
Μετά την πετυχημένη εκτέλεση του Βήματος 2 πάμε σε αυτό το τελευταίο βήμα στο οποίο θα ρυθμίσουμε 2-3 ακόμα paths έτσι ώστε να τρέξουμε την εφαρμογή.Βρίσκουμε την κλάση LuceneIndexerGUI.java και βάζουμε στην τιμή του πεδίου INDEX_DIRECTORY το path στο οποίο αποθηκεύσαμε το ευρετήριο σύμφωνα με το Βήμα1.Στην δικιά μας περίπτωση δηλαδή θα μπεί το C:\temp\indexluc. Μετά εντός του constructor της συγκεκριμένης κλάσης και στην τιμή του αντικειμένου file πάμε και εισάγουμε σαν path το path που βάλαμε στο Βήμα2, καθώς αφορά το txt αρχείο με τα queries. Στην περίπτωση μας βάζουμε το C:\temp\indexluc\search_history.txt.Ο χρήστης το προσαρμόζει αναλόγως.Επιπλεόν, βρίσκουμε την μέθοδο displayResults και πάμε στην γραμμή 314(File file = new File(....)) όπου και εδώ βάζουμε το ίδιο path με το Βήμα2
"C:\temp\indexluc\search_history.txt". Τέλος, πλοηγούμαστε και στην μέθοδο openFile() όπου στην 3η εντολή της μεθόδου(String fileName=... ) βάζουμε για path το path στο οποίο είναι αποθηκευμένο το αρχείο .txt με τα διανυσματικές αναπαραστάσεις του pretrained συνόλου που κατεβάσαμε από την ιστοσελίδα του Stanford(ο ακριβής σύνδεσμος αναγράφεται στην αναφορά). Επιλέξαμε να χρησιμοποιήσουμε το txt με τις 50 διαστάσεις "glove.6B.50d.txt"

Αφού επιβεβαιώσουμε ότι τα Βήματα1,2,3 ολοκληρώθηκαν με επιτυχία τρέχουμε την εφαρμογή μας απλώς εκτελώντας μόνο την κλάση LuceneIndexerGUI.java

*****ΣΗΜΑΝΤΙΚΟ******
Για να τρέξουμε την εφαρμογή απλώς εκτελόυμε ΜΟΝΟ  την κλάση LuceneIndexerGUI.java.Δεν χρειάζεται να ξανατρέξουμε τις άλλες 2 κλάσεις.Επίσης, θα πρέπει να κατεβάσετε το αρχείο .csv από το zip που έχουμε παραπάνω καθώς έχουν γίνει κάποιες αλλαγές από το αρχικό αρχείο του kaggle.

ΣΗΜΕΙΩΣΗ:
Σε περίπτωση που ο χρήστης διαγράψει τον φάκελο του ευρετηρίου(indexluc) θα πρέπει να επαναλάβει την ακολουθία των Βημάτων1,2,3 με την σειρά που καταγράφονται έτσι ώστε να δημιουργηθούν τα απαραίτητα έγγραφα για να μπορέσει να τρέξει η εφαρμογή μας 





University of Ioannina Department of Computer Science and Engineering

Information Retrieval

Team Members:

Eleftherios-Christos Dritsonas, 4668 
Stefanos Fotopoulos, 4829

Academic Year 2023 DELIVERY: Friday, May 19

Contents

Description of the task
Question A
Question B
1. Description of the task

The link for the GitHub repository is as follows: GitHub Link

Question A

In this report, we will describe the steps related to the implementation of Phase 1 in the Information Retrieval course. DATA COLLECTION

In this step, we collected the documents that we will use from the following link:https://www.kaggle.com/datasets/notshrirang/spotify-million-song-dataset Kaggle Dataset (the link also appears in the course slides). In this link, there are 643 artists with a total of 44824 songs (documents). When we uploaded the dataset to GitHub, it complained that the file was larger than 25MB, so we uploaded the same file compressed (zip).

The format of the file is in .csv (comma-separated values).

In the first column of the file, we see the name of the artist or the band. In the second column, we have the name of the song. The third column has the link of the song, ending in .html. Finally, the fourth column has all the lyrics of the songs.

Question B Text Analysis and Indexing:

After creating a StandardAnalyzer and a ByteBuffersDirectory to store the information, we need to create an IndexWriterConfig which will go through the index (in our case, the .csv file with the songs) and record its values. Then, we will have a QueryParser where we will enter all the possible queries that the user can make. Next, there is the DirectoryReader which opens the ByteBuffersDirectory we created and an IndexSearcher that aims to search how many times the user's query is satisfied. We keep this information in a hits array where we count the scores. There will also be a void function addDoc which categorizes the fields of the .csv file into the fields: Song Title, Artist Name, Date.

Introduction: What is the purpose and functionality of the system?

The goal for this specific task is to create an interface where the user can ask questions related to songs stored in the Database. This is achieved through a graphical interface (GUI) such as the search bar of the Google search engine, for example.

Search: How will the search be performed, the types of questions Initially, the search will be performed through a search box which will be displayed to allow the user to enter the desired question to the database with the songs. The permissible questions that can be entered are the following: • The name of the artist • The title of a song • A specific lyric or lyrics from a song • Date of creation of the song


Presentation of Results: How Results Will Be Presented

Initially, we will retrieve the songs that satisfy the query submitted by the user, and they will be displayed in groups of 10 in descending order based on the number of occurrences of that query per song. Then, the user will have the option to view the next 10 tuples (songs) that satisfy the query. This process continues until all the songs containing that word are exhausted. On the right side of the search bar, suggested queries will also be available for the user to select and view their results.

At this point, we will outline the steps that a user needs to take to run the application.

Imported JARS:
The libraries needed for importing to run the program are all the jars found within the folders "modules", "modules-thirdparty", "modules-test-framework", which concern the version of the Lucene library 9.5.0 for Java. These folders will become visible to the user upon extracting the file lucene-9.5.0.zip.

Execution Steps

Step 1:
Initially, this specific step needs to be executed only once. Specifically, we need to run the class LuceneInexer.java, but before doing so, we need to configure 2 things. Within the class, specifically in the field INDEX_DIRECTORY, we need to define the path where the index for the songs will be stored. By default, we have set it to C:\temp\indexluc, where indexluc is the name of the index directory. After that, within the main method, we need to specify the path where the .csv file with the songs downloaded from Kaggle is stored so that the program can read it. After completing this step, we run this class and check if the index directory, named indexluc in our case, has been created. Once we confirm that everything is in order, we proceed to Step 2.


Step 2:
In this step, we will need to do something similar for the SeacrhHistoryItem.java class. Specifically, within the class and within the addToHistory method, we will need to write the path where we want the .txt file to be saved, which will contain queries that have been submitted by users in the past. To do this, we will write the path on line 120 (in the variable file). CAUTION: The txt file should be saved within the directory where we created the index based on everything mentioned in Step 1. For example, in our case where the directory of the index is indexluc, the path we will write will be C:\temp\indexluc\search_history.txt, where search_history.txt is the name of the .txt file with the previous queries. Adjust accordingly.



Step 3: Configuring Additional Paths
After successfully completing Step 2, proceed to this final step where we will configure 2-3 additional paths to run the application.

1. Configuring INDEX_DIRECTORY:

  Locate the LuceneIndexerGUI.java class.
  In the INDEX_DIRECTORY field, set the path to the folder where you saved the index in Step 1.
  Example: C:\temp\indexluc
2. Configuring the path to the queries file:

  In the constructor of the LuceneIndexerGUI.java class, modify the path of the file object.
  Set the path to the txt file containing the queries, as specified in Step 2.
  Example: C:\temp\indexluc\search_history.txt
  Note: Adjust the path according to your system.
3. Configuring the path to the file of vector representations:
  
  Go to the displayResults method.
  In line 314 (File file = new File(....)), set the path to the txt file containing the vector representations of the pretrained set.
  Example: C:\temp\indexluc\glove.6B.50d.txt (the "glove.6B.50d.txt" file with 50 dimensions from Stanford)
4. Running the application:

  If you have successfully completed Steps 1, 2, and 3, you can now run the application.
  Run only the LuceneIndexerGUI.java class.
  Note: You do not need to run the other 2 classes again.


Important Information:
  
  Download the .csv file:
  The .csv file has been modified from the original Kaggle file.
  Download it from the provided zip.
  Deleting the index folder:
  If you delete the indexluc folder, repeat Steps 1, 2, and 3 in sequence to recreate the necessary files for the application to run.
Note:
  
  Follow the instructions carefully to ensure smooth operation of the application.
  Feel free to modify the paths and settings according to your specific needs.



