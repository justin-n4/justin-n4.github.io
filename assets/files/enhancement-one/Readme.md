
# Enhancement One: Software Design and Engineering

## Narrative 

For this milestone, I selected my Travlr Getaways full-stack web application as the artifact for the software design and engineering category. This project was originally developed in CS-465 and built up over multiple modules, beginning as a static Express site and gradually evolving into a fuller MEAN-style application with MVC organization, a MongoDB database, API routes, an Angular admin side, and JWT-based authentication. For this enhancement, I focused specifically on the software design and engineering side of the project by revisiting the server-side structure and improving parts of the application that affected maintainability, portability, and clarity.
	
I chose this artifact because it’s one of the clearest examples of my growth as a computer science student. Since it’s a layered application with routes, controllers, views, an API, a database connection, and configuration concerns that all have to work together, that made it a strong choice for my ePortfolio. It shows more than just whether I can write code that runs. It shows that I can work within an application structure, evaluate the design decisions inside that structure, and improve them in a way that makes the project more realistic and more maintainable. In less words, it reflects the kind of thinking that matters in actual software development, where readability, portability, and long-term upkeep matter just as much as whether something technically functions.
	
The specific parts of the artifact that best showcases my software design and engineering skills are the Express application setup, the MVC route/controller/view structure, and the travel page controller. In my earlier code review, I identified a few weak spots that stood out from a design perspective. The biggest issues were that some important configuration values were hard-coded directly into the source files, the travel controller depended on a fixed internal API URL, the error handling was limited, and the view was not fully reflecting the controller logic because a message variable was being created but not actually displayed to the user. I also noted that while the code was readable, the comments were very light and didn’t do much to explain the design choices behind the implementation.
	
To improve the artifact, I moved runtime values such as the port, client URL, and trips API URL into the. env configuration, so the application is less tied to one local setup. I updated app.js to use environment-based configuration instead of relying on hard-coded values, which made the application more portable across environments. I also improved the comments throughout the files I selected for this milestone so they explain intent more clearly instead of just labeling sections. In the travel controller, I cleaned up the structure by using a consistent view model and improving the handling of empty or unavailable trip data. On the front end, I updated the HBS travel view so it can actually display the message passed in by the controller. That way, the interface now reflects more of the application state rather than silently ignoring part of the backend logic. These changes did not radically change how the application looks, but they made the codebase cleaner, easier to understand and maintain, which was my goal.
	
This enhancement supported the course outcomes I originally planned to address, especially the outcome focused on using well-founded techniques, skills I’ve learned, and tools available to add computing solutions that deliver value and adhere with industry-specific goals. I believe this milestone showed progress in that area because the work was centered on refining application structure and improving maintainability rather than simply adding new features. It also supported the written communication outcome, since part of the enhancement involved making the project easier for another developer to understand through better organization and clearer inline documentation. Currently, I don't have any major updates to my outcome coverage plans. This artifact still fits the software design and engineering category well, and the work I completed here aligns with what I originally intended to demonstrate.
	
The process of enhancing the artifact taught me a lot, mostly because it pushed me to look at the difference between code that works and code that is designed well. Earlier in my coursework, I was usually focused on getting the application running and making sure the visible output matched what the assignment required. This milestone forced me to slow down and think more critically about structure. I had to look at where configuration belonged, how tightly coupled certain parts of the app were, and whether the view layer was actually supporting the logic in the controller. That kind of reflection felt more like real software maintenance than just completing the assignment, and I think that made it valuable.
	
I also learned that improvement is rarely as clean as it sounds when you describe it afterward. Some parts were straightforward, like moving values into environment variables and tightening comments. Other parts were a little messier. Testing failure behavior was one of the more annoying parts of the process. For example, when I temporarily stopped MongoDB to test the travel page during an outage, the behavior was not always as clean or dramatic as expected. Sometimes the app recovered once MongoDB came back up, and sometimes the error-handling path did not present itself in the browser as neatly as I thought it would. Even so, that was still useful, because it reminded me that there is a difference between designing cleaner logic and perfectly simulating every failure state in a development environment. That was probably one of the more honest lessons in this milestone. Software improvement is incremental, and even when a change is valid, the testing experience can still reveal rough edges.
	
Overall, I included this artifact in my ePortfolio because it represents meaningful progress in how I approach software development. It shows that I can move beyond simply building functionality and start thinking more seriously about architecture and maintainability. The enhancement process also made me more aware of the practical trade-offs involved in software design. Sometimes the best improvement is not the flashiest one. Sometimes it makes a project easier to configure, easier to follow, and easier to troubleshoot. That's exactly what I aimed to do here, and I think this artifact reflects that growth well.


### Example enhancement in code:
This change replaces a hard-coded API dependency with environment-based configuration and introduces a consistent view model, improving portability, reducing coupling, and making sure predictable controller-to-view data flow.

```js
const TRIPS_API_URL = process.env.TRIPS_API_URL || "http://localhost:3000/api/trips";

const buildTravelViewModel = (trips = [], message = null) => ({
  title: "Travlr Getaways",
  trips,
  message,
});
```

Basic response validation was added to make sure API failures are handled explicitly rather than silently failing.
```js
if (!response.ok) {
  throw new Error(`Trips API returned status ${response.status}`);
}
```
