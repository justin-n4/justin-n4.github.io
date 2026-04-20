---
layout: default
---

# CS-499 | Computer Science Capstone | SNHU

## Self-Assessment
Completing this ePortfolio gave me a much clearer picture of how much I’ve grown throughout the Computer Science program. When I first started, I was mainly focused on learning the material, getting through each course, and building enough confidence to keep moving forward. Over time, that shifted. I became more aware of how the different parts of computer science connect, and I started thinking less like someone trying to finish assignments and more like someone trying to build real, usable solutions. Putting this portfolio together made that even more obvious because it forced me to step back and look at the bigger picture of what I’ve actually developed.

Overall, my experience in the program was a good one, but it definitely was not smooth the whole way through. In fact, almost every term seemed to come with some different obstacle, whether that was a technical issue, a frustrating environment, unclear instructions, or just the pressure of balancing everything at once. Looking back, those problems ended up helping me. They forced me to become resourceful. I had to find workarounds, learn to troubleshoot, and get comfortable figuring things out when the straightforward answer was not there. That ended up being one of the most valuable parts of the program because real-world technical work is rarely perfect or neatly packaged.

The way the program was structured also shaped me quite a bit. Because it was online and required a lot of independent effort, it really pushed self-reliance. I had to become a better time manager, a more self-sufficient learner, and someone who could take initiative without waiting around for everything to be spelled out. A lot of the time, the solution meant going beyond the exact tools or examples used in class. That exposed me to different technologies, different methods of problem solving, and different ways of learning. More than anything, it made me more curious. Instead of just trying to get past a problem, I started wanting to understand why it was happening and what other options existed.

This portfolio brings those experiences together through my capstone enhancements to the Travlr Getaways application across software design, algorithms and data structures, and databases. I chose to focus all three enhancements on the same project because it felt more cohesive and gave me a better way to show how those concepts actually work together in a complete application. Each section reflects a different area of growth, but together they tell one larger story about how I learned to think more critically about structure, logic, data integrity, and maintainability rather than just whether something runs.

At this point, I see this ePortfolio as more than just a final assignment but a reflection of how I approach work now compared to when I first began the program. I'm more patient with debugging, more comfortable under pressure, and more confident in solving problems independently. Just as importantly, I’ve learned that growth in computer science is not always about the flashiest feature or the cleanest path. A lot of it comes from working through the messy parts, adapting when things break, and learning how to keep moving forward. That mindset is probably one of the biggest things I’ll carry with me from this program.

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

[View Full Code + Narrative](https://github.com/justin-n4/justin-n4.github.io/tree/main/assets/files/enhancement-one)

---

## Enhancement Two: Algorithms and Data Structures

### Overview
For this enhancement, I focused on the logic behind how trip data is validated, updated, and handled across the backend and Angular admin side. What made this one meaningful to me was that it showed algorithmic thinking in a more practical way. Instead of forcing in some textbook-style algorithm, I was able to improve the actual control flow of the application by tightening validation, reducing repetitive update logic, and making responses and error handling more consistent. Overall, it made the project easier to reason through and closer to how real-world application logic should behave.

### Key Improvements
- Added stronger controller-level validation so bad or incomplete trip data is caught earlier.
- Cleaned up the trip update flow to reduce repetition and make the logic easier to maintain.
- Centralized API error handling in the Angular service so the same response logic is not repeated everywhere.
- Improved the Angular edit component by handling missing trip data and error states more defensively.

[View Full Code + Narrative](https://github.com/justin-n4/justin-n4.github.io/tree/main/assets/files/enhancement-two)

---

## Enhancement Three: Databases

### Overview
This final enhancement focused on the database side of the application so the overall project would feel complete and cohesive. This part of the work centered on the trip and user models, along with the controllers that interact with them, because that’s where the project’s data integrity really lives. More than anything, it pushed me to think about how the database should actually enforce rules, not just how those rules look in the schema.

### Key Improvements
- Strengthened the trip schema with better validation rules and treated code as a true unique identifier.
- Changed perPerson to a numeric field so the data is more useful and reliable from a database standpoint.
- Improved the user model with stronger email validation and cleaner account integrity checks.
- Cleaned up controller-side database error handling for duplicate records, invalid input, and more consistent responses.

[View Full Code + Narrative](https://github.com/justin-n4/justin-n4.github.io/tree/main/assets/files/enhancement-three)

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
