# Justin Naimo

## CS-499 Computer Science Capstone | SNHU

This ePortfolio highlights my enhancements to the Travlr Getaways full-stack application across three key areas: software design, algorithms, and databases. I chose to focus all three enhancements on the same application because it felt more cohesive and, more importantly, gave me a better way to show a fuller understanding of computer science concepts and how they connect in a real project.

---

## Code Review
A full walkthrough of my original artifact, including identified design issues and areas for improvement.

[Watch Code Review](Link)

---

## Enhancement One: Software Design and Engineering

### Overview
The Travlr Getaways full-stack web application is perfect for this enhancement because it was one of the strongest examples of how my thinking has grown beyond just getting code to run. For this milestone, I focused on the software design and engineering side of the project by improving the server-side structure, making configuration more portable, and tightening the connection between the controller logic and what the user actually sees in the view. Overall, the work was to make the application cleaner, easier to follow, and more maintainable over time.

### Key Improvements
- Moved hard-coded runtime values like the port, client URL, and trips API URL into .env configuration.
- Updated app.js to rely on environment-based setup, making the application more portable across environments.
- Improved the travel controller by using a more consistent view model and handling empty or unavailable trip data more cleanly.
- Updated the HBS travel view and inline comments so the interface reflects controller messages properly and the code is easier to understand.

[View Full Code + Narrative](LINK)

---

## Enhancement Two: Algorithms and Data Structures

### Overview
For this enhancement, I focused on the logic behind how trip data is validated, updated, and handled across the backend and Angular admin side. What made this one meaningful to me was that it showed algorithmic thinking in a more practical way. Instead of forcing in some textbook-style algorithm, I was able to improve the actual control flow of the application by tightening validation, reducing repetitive update logic, and making responses and error handling more consistent. Overall, it made the project easier to reason through and closer to how real-world application logic should behave.

### Key Improvements
- Added stronger controller-level validation so bad or incomplete trip data is caught earlier.
- Cleaned up the trip update flow to reduce repetition and make the logic easier to maintain.
- Centralized API error handling in the Angular service so the same response logic is not repeated everywhere.
- Improved the Angular edit component by handling missing trip data and error states more defensively.

[View Full Code + Narrative](LINK)

---

## Enhancement Three: Databases

### Overview
This final enhancement focused on the database side of the application so the overall project would feel complete and cohesive. This part of the work centered on the trip and user models, along with the controllers that interact with them, because that’s where the project’s data integrity really lives. More than anything, it pushed me to think about how the database should actually enforce rules, not just how those rules look in the schema.

### Key Improvements
- Strengthened the trip schema with better validation rules and treated code as a true unique identifier.
- Changed perPerson to a numeric field so the data is more useful and reliable from a database standpoint.
- Improved the user model with stronger email validation and cleaner account integrity checks.
- Cleaned up controller-side database error handling for duplicate records, invalid input, and more consistent responses.

[View Full Code + Narrative](LINK)

---

## Professional Self-Assessment



---

## Project Overview

The core artifact for this portfolio is the Travlr Getaways application, a MEAN-style full-stack project built with:

- MongoDB
- Express
- Angular
- Node.js

[View Full Project Repository](LINK)
