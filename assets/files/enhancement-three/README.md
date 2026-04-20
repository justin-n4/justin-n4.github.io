
# Enhancement Three: Databases

## Narrative 

For this milestone, I selected my full-stack Travlr Getaways web application for the database category. This ties in the final portion of enhancements for the same application to showcase something complete and cohesive. This project gradually grew across several modules into a larger MEAN-style application with an Express backend, MongoDB database, Angular admin side, and JWT-based authentication. For this enhancement, I focused specifically on the database layer of the project, especially the trip and user models along with the controllers that interact with those collections. That made this a strong artifact for the database category because it let me work directly with schema design, validation, indexing, and database reliability rather than just the visual or routing side of the application.

I included this artifact in my ePortfolio because it shows a more realistic side of database work than just writing isolated queries. In this project, the database dictates how the application handles all data. Whether it's updating, storing, validating, or protecting it. That made it a good choice because it shows how the database can affect the rest of the system. The specific parts of the artifact that best showcases my skills are the travlr.js schema, the user.js schema, the trip controller, and the authentication controller. The trip schema improvement was probably the most important part because I strengthened validation rules, changed perPerson into a numeric field, and treated code as a true identifier instead of just another string field. On the user side, I improved the schema by adding stronger validation around email structure and tightening the model, so it better supports account integrity. In the controllers, I improved how database errors and validation failures are handled, especially around duplicate records and bad input. Altogether, the artifact became more structured, more consistent, and more trustworthy from a database perspective.

I do think this enhancement met the course outcomes I intended to address, especially the one focused on using well-founded techniques, skills, and tools to implement computing solutions that deliver value and align with industry-specific goals. This milestone also pushed that outcome in a more database-centered direction. Instead of focusing mainly on maintainability like I did in the software design milestone, this enhancement was more about data integrity, constraints, schema structure, and how the application behaves when the database receives bad or conflicting data. I also see overlap in some of the outcomes like managing trade-offs, because I had to think through practical database choices, like what should be validated at the schema level, what should be handled in the controller, and what should count as a clean error response for the client. 

The process of enhancing this artifact taught me a lot, mostly because it showed me that database work is not just about saving and retrieving records. A big part of it is making sure the data layer actually enforces the rules you think it does. One of the best examples of that came up during testing when I realized duplicate trip codes were still being inserted even after I added unique: true to the schema. That was frustrating at first but felt like one of the most necessary parts of the milestone because it showed me the difference between declaring a uniqueness rule in Mongoose and having MongoDB truly enforce it at the index level. I had to go into the collection, inspect the indexes, remove the duplicate record, and recreate the code index as unique before the database behaved the way I intended. That was probably the clearest lesson of the milestone: schema design on paper is one thing, but actual database enforcement is another. Once that was fixed, the duplicate test failed correctly and testing for invalid data also returned clean validation errors, which gave me good proof that the enhancement was working the way it should.

Overall, I chose this artifact because it gives me a strong way to show database knowledge in a practical setting. It shows that I can think more carefully about schema rules, validation, error handling, and data consistency, and that I can diagnose issues when the database doesn’t behave the way I expect. That felt like a meaningful improvement to include in my ePortfolio because it reflects a more mature understanding of how database design affects the reliability of the entire application.

### Example enhancements made in app_api/controllers/trips.js:
This enhancement restricts database writes to approved trip fields only, improving data integrity and preventing unintended or unauthorized values from being stored.

```js
const extractTripData = (body = {}) => {
  return TRIP_FIELDS.reduce((tripData, field) => {
    if (body[field] !== undefined) {
      tripData[field] = body[field];
    }
    return tripData;
  }, {});
};
```

This improvement centralizes database-related error responses, creating a more consistent and maintainable API contract across CRUD operations.
```js
const sendTripError = (res, status, message, details = null) => {
  const payload = { message };
  if (details) {
    payload.details = details;
  }
  return res.status(status).json(payload);
};
```

This update logic applies only validated, approved fields to the existing database document, allowing flexible changes without replacing the full record.
```js
Object.assign(trip, updates);

const updatedTrip = await trip.save();
```

### Example enhancements made in app_api/models/travlr.js:
This enhancement converts price values into a numeric type with normalization and validation, enabling accurate sorting, comparison, and enforcing consistent data storage at the database level.

```js
perPerson: {
  type: Number,
  required: [true, "Price per person is required"],
  min: [0, "Price per person cannot be negative"],
  set: normalizePrice,
},
```

This enforces uniqueness and format validation at the schema level, ensuring each trip has a consistent and reliable identifier within the database.

```js
code: {
  type: String,
  required: [true, "Trip code is required"],
  unique: true,
  index: true,
  trim: true,
  uppercase: true,
  match: [/^[A-Z0-9-]+$/, "Trip code format is invalid"],
},
```

Adds a compound index to optimize query performance and support efficient sorting by date and identifier.
```js
tripSchema.index({ start: 1, code: 1 });
```

#### Enhancements made in the following code files:
- app_api/models/travlr.js
- app_api/models/user.js
- app_api/controllers/trips.js
- app_api/controllers/authentication.js
