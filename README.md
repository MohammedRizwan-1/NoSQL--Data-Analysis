# NoSQL--Data-Analysis

This code repository encompasses the source code that facilitates analysis of the food hygiene ratings data for food establishments across the UK. The code is designed to import data from a JSON file, set up a MongoDB database, and subsequently update the database with new restaurant data.

Part 1: To initiate the database, the establishment data provided in the establishments.json file can be imported into the MongoDB database with the following command in the Terminal:
mongoimport --db uk_food --collection establishments --fileestablishments.json --jsonArray

Upon successful import, the code establishes a MongoClient instance, assigns the 'uk_food' database to a variable, and further assigns the 'establishments' collection to another variable. This enables the code to add new restaurant data to the database, and convert it to the suitable format for subsequent analysis.

Part 2: The code interacts with the MongoDB database created in part 1 using the 'pymongo' library in Python. The MongoClient instance is created to connect to the database:

mongo = MongoClient(port=27017)
db = mongo['uk_food']

The code then queries and filters the database to extract the relevant data as requested by the assignment. The outcomes of these queries are subsequently transformed into Pandas DataFrames, thereby facilitating further analysis.

df_query = db.establishments.find({ "scores.Hygiene": 20 })
df = pd.DataFrame(list(df_query))

This approach allows for efficient analysis of the food hygiene ratings data for food establishments in the UK, aiding in decision making and policy formulation.