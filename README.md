# nosql-challenge

## Resources

### Tutoring:

I got help from a tutor in the NoSQL_setup_starter file, up until we reached the task that reads "Find how many documents have LocalAuthorityName as "Dover".

### Xpert: 

Below, I have listed the parts of my code that I submitted to Xpert for assistance, and then the changes that it recommended that I ended up using.

query = {"LocalAuthorityName": "Dover"}
count = establishments.find(query)

for results in count:
    count(results)

to

query = {"LocalAuthorityName": "Dover"}
count = 0

for results in establishments.find(query):
    count += 1

print(count)



establishments.update_many({}, [{"$set": {"RatingValue": {"$toInteger"}}}])

to

establishments.update_many({}, [{"$set": {"RatingValue": {"$toInt": "$RatingValue"}}}])


query = {"scores": {"Hygiene": 20}}

to

query = {"scores.Hygiene": 20}


Xpert also had me convert my results to a list before converting the data to a pandas dataframe.

query = { 
    {"LocalAuthorityName" : {"$regex": "London"}},
    {"RatingValue" >= 4}
}

to

query = { 
    "$and": [
        {"LocalAuthorityName": {"$regex": "London"}},
        {"RatingValue": {"$gte": 4}}
    ]
}

query = {
    "Location": {
        "$geoWithin": {
            "$centerSphere": [[longitude, latitude], degree_search / 3963.2]
        }
    },
    "RatingValue": 5
}

row_count = len(hygiene) (i forgot how to count the rows of a pandas dataframe)

I received some help regarding the syntax of my query in question #3 for the exploratory analysis, along with using the "$or" function to be able to find restaurants within 0.01 degrees in latitude or longitude to find which ones were the closest to "Penang Flavours".

Below is a pipeline example that I asked Xpert to create for me so that I had something to reference off of, when creating a pipeline for the final question:

pipeline = [
    { '$match': { 'category': 'electronics' } },
    { '$group': { '_id': '$brand', 'total_quantity': { '$sum': '$quantity' } } },
    { '$sort': { 'total_quantity': -1 } },
    { '$limit': 5 }
]

### AskBCS:

Recommended that I do a pprint for the last instruction in the setup_starter file instead of coding something to list every single datatype of each individual document.

I also received some help regarding the syntax of my query in question #3 for the exploratory analysis portion.
