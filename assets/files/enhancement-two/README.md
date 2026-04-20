# Enhancement Two: Algorithms and Data Structure

## Narrative 

For this milestone, I selected my Travlr Getaways full-stack web application as the artifact for the algorithms and data structures category. As mentioned in enhancement one, this project was originally created in CS-465 and expanded over time. For this enhancement, I focused on the backend trip-management logic and the related Angular service and edit component, since those areas gave me the strongest opportunity to improve how data is validated, updated, and handled across the application.

I included this artifact in my ePortfolio because it gives me a realistic way to show algorithmic thinking without forcing a traditional textbook-style algorithm into the project just for the sake of it. The strongest part of this enhancement was the logic behind how the application processes, validates, updates, and protects trip data. That felt more honest about the kind of work I actually wanted to do. The trip controller already handled CRUD operations, but there were weaknesses in how input was validated, how repeated update logic was written, and how consistently the API responded to different situations. Those areas made it a good choice for this category because they involve decision-making, conditional logic, trade-offs, and data handling.

The specific components that best showcase my skills in data structures and algorithms are the trip controller in website/app_api/controllers/trips.js, the Angular trip-data.service.ts, and the trip-edit.component.ts file. In the trip controller, I improved the logic by adding stronger controller-level validation before database operations happen, making empty or invalid input easier to catch earlier, and making the API responses more consistent. I also cleaned up the update path, so it was less repetitive and easier to maintain. In the Angular service, I added centralized error handling, so the same logic did not have to be repeated in every component. In the edit component, I made the flow more defensive by handling missing data and error states more clearly. Altogether, the enhancement made the application more consistent and easier to reason through.
I do believe I met the course outcomes, although the emphasis shifted a little compared to the previous milestone. In enhancement one, I talked more about using well-founded techniques, skills, and tools to build solutions that deliver value, along with improving clarity for another developer through organization and documentation. That still applies here, but this milestone also pushed more directly into the outcome centered on designing and evaluating computing solutions using algorithmic principles and managing design trade-offs. In this case, the trade-offs were not abstract. They showed up in decisions like where validation should happen, how much logic should live in the controller versus the service layer, and how consistent API responses should be for the frontend. At this point, I don’t really have major updates to my outcome-coverage plans. This artifact still works well for the ePortfolio because it now shows progress in both software design and more logic-driven problem solving.

Working through this enhancement taught me that algorithms in real projects don’t always look the way they do in class assignments. A lot of the important thinking was in the control flow: validating route parameters, deciding how partial updates should behave, rejecting bad input cleanly, and making sure the frontend had a more reliable contract to work with. That kind of logic is easy to overlook because it’s not flashy, but it matters a lot in actual applications. I also learned that theres a difference between getting something to work and making it behave consistently under different conditions.

There were definitely some challenges. The biggest one was testing protected write operations through the Angular admin interface. The frontend was able to load trip data and open the edit screen, but the write actions still depended on a JWT token flow that was not wired into local storage in the current Angular admin setup. Once I confirmed that, I shifted to testing authenticated write operations in Postman instead, which ended up being the cleaner way to prove that the controller logic and validation changes were actually working. In the end, that was probably the most useful part of the process, because it forced me to separate a frontend authentication wiring issue from the actual backend enhancement itself. That distinction made the project easier to evaluate honestly.

Overall, I chose this artifact because it reflects the kind of applied problem solving, I want to show in my ePortfolio. This enhancement let me demonstrate more than whether the app simply runs. It let me show how I approach validation, update logic, response design, and error handling in a way that is more thoughtful and maintainable. That feels like a better representation of my growth than just adding another feature and calling it finished.

### Example enhancements made in app_api/controllers/trips.js:
Filters incoming request data to only allow approved fields, preventing unintended or malicious updates and improving data integrity at the controller level.

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

Introduces controller-level validation to catch invalid input before database operations, improving reliability and reducing dependence on schema-level validation alone.

```js
const validationErrors = validateTripData(tripData, true);

if (validationErrors.length > 0) {
  return sendErrorResponse(res, 400, "Invalid trip data", validationErrors);
}
```

Applies partial updates dynamically by merging only validated fields, allowing flexible updates without overwriting existing data.

```js
Object.assign(trip, updates);

const updatedTrip = await trip.save();
```

Centralizes API error handling into a reusable function, making sure of consistent response structure and improving maintainability across all endpoints.
```js
const sendErrorResponse = (res, status, message, details = null) => {
  const payload = { message };
  if (details) {
    payload.details = details;
  }
  return res.status(status).json(payload);
};
```

#### Enhancements made in the following code files:
- app_api/controllers/trips.js
- trip-data.service.ts
- app_admin/app/trip-edit.component.ts
