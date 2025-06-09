# CodingCard
A web app to learn coding concepts through interactive flashcards.

## How to Run
1. Clone the repo: `git clone <repo-url>`
2. Install dependencies: `npm install`
3. Start the server: `node server.js`
4. Open `http://localhost:3000` in your browser.

## Tech Stack
- HTML, CSS, JavaScript
- Node.js, Express
- JSON for data storage


CodingCard Architecture
Overview
CodingCard is a web application that allows users to study coding concepts through interactive flashcards. The application uses a client-server architecture with React for the frontend and Node.js for the backend, communicating via a REST API. Flashcard data is stored in a JSON file for simplicity, with the option to scale to a database later. The architecture prioritizes modularity, ease of development, and a smooth user experience.
Architecture Components
1. Frontend (React)

Purpose: Handles the user interface, displaying flashcards, and managing user interactions (e.g., flipping cards, submitting answers).
Responsibilities:
Render flashcards with questions and answers.
Provide interactive elements (e.g., buttons for flipping cards, input fields for answers).
Fetch flashcard data from the backend via API calls.
Manage client-side state (e.g., current card, user progress).


Libraries/Frameworks:
React: For building a dynamic, component-based UI.
Axios: For making HTTP requests to the backend.
Tailwind CSS: For responsive and modern styling.
React Router: For navigation between pages (e.g., home, study, results).


Key Components:
App.js: Main component that sets up routing and global state.
Flashcard.js: Component to display a single flashcard with flip animation and answer input.
Home.js: Landing page with a "Start Studying" button.
Progress.js: component to show user progress (e.g., cards completed).


State Management:
Use React’s useState and useEffect hooks for simplicity.
Example: Store the current card index and flip state in useState.
Fetch flashcards on component mount using useEffect.



2. Backend (Node.js + Express)

Purpose: Serves flashcard data and handles API requests from the frontend.
Responsibilities:
Provide RESTful API endpoints (e.g., GET /api/flashcards to retrieve all flashcards).
Read flashcard data from a JSON file.
Handle basic CRUD operations (e.g., retrieve flashcards, potentially add/edit cards in future iterations).


Libraries/Frameworks:
Express: Lightweight framework for building the REST API.
Node.js: Runtime for the backend server.
fs (File System): Built-in Node.js module to read/write JSON files.


Key Endpoints:
GET /api/flashcards: Returns all flashcards.
GET /api/flashcards/:id: Returns a specific flashcard by ID.
(Future) POST /api/flashcards: Add a new flashcard.


Data Storage:
Use a JSON file (flashcards.json) for simplicity in the MVP.
Example structure:[
  {
    "id": 1,
    "question": "Write a Python function to reverse a string",
    "answer": "def reverse_string(s): return s[::-1]"
  },
  {
    "id": 2,
    "question": "What is a JavaScript closure?",
    "answer": "A closure is a function that retains access to its outer scope's variables."
  }
]


Future scalability: Replace JSON with a database like MongoDB or SQLite.



3. Data Flow

User Interaction:
User loads the app → React frontend renders the homepage.
User clicks "Start Studying" → React fetches flashcards from the backend (GET /api/flashcards).
Backend reads flashcards.json and returns data.
React displays the first flashcard → User interacts (flips card or submits an answer).
Frontend updates UI based on user input (e.g., shows "Correct!" or "Try again").


API Communication:
Frontend sends HTTP requests (via Axios) to the backend.
Backend responds with JSON data.
Example: Fetching flashcards:axios.get('/api/flashcards').then(response => setFlashcards(response.data));



Error Handling:
Frontend: Display user-friendly messages (e.g., "Failed to load flashcards").
Backend: Return appropriate status codes (e.g., 500 for server errors).



4. Folder Structure
CodingCard/
├── client/                     # React frontend
│   ├── public/
│   │   ├── index.html         # Main HTML file
│   ├── src/
│   │   ├── components/
│   │   │   ├── Flashcard.js   # Flashcard component
│   │   │   ├── Home.js        # Homepage component
│   │   │   ├── Progress.js    # Progress tracking component
│   │   ├── App.js             # Main React app
│   │   ├── index.js           # Entry point for React
│   │   ├── styles.css         # Global styles (or Tailwind CSS)
│   ├── package.json           # Frontend dependencies
├── server/                     # Node.js backend
│   ├── data/
│   │   ├── flashcards.json    # Flashcard data
│   ├── routes/
│   │   ├── flashcards.js      # API routes for flashcards
│   ├── server.js              # Main server file
│   ├── package.json           # Backend dependencies
├── README.md                  # Project documentation
├── .gitignore                 # Ignore node_modules, etc.

Tech Stack

Frontend:
React (v18): For building a dynamic, component-based UI.
Axios: For making API requests to the backend.
Tailwind CSS: For rapid, responsive styling.
React Router: For client-side navigation.
CDN: Use cdn.jsdelivr.net for React and dependencies to simplify setup.


Backend:
Node.js (v20): Runtime for the server.
Express: Framework for building the REST API.
fs: For reading/writing JSON files.


Tools:
Visual Studio Code: Code editor.
Git/GitHub: Version control and hosting.
npm: Package manager for Node.js and React dependencies.
Postman: For testing API endpoints.


Hosting/Deployment:
Frontend: Deploy on Vercel or Netlify.
Backend: Deploy on Render or Heroku (JSON file can be bundled with the app).


Why This Stack?:
Node.js + Express: Lightweight, beginner-friendly, and aligns with JavaScript for full-stack consistency.
React: Ideal for dynamic, interactive UIs like flashcards with flip animations.
JSON File: Simplifies data storage for the MVP, avoiding database complexity.
Tailwind CSS: Speeds up styling without writing custom CSS from scratch.



Scalability Considerations

Data Storage: Replace JSON with MongoDB or SQLite for larger datasets or user-specific data.
Authentication: Add user accounts using JWT or OAuth for personalized progress tracking.
Performance: Implement pagination for API calls if the flashcard dataset grows large.
Features: Add categories, search functionality, or gamification (e.g., points for correct answers).

Development Workflow

Set Up Backend:
Initialize Node.js project (npm init -y).
Install Express (npm install express).
Create server.js and define API routes.
Test endpoints with Postman.


Set Up Frontend:
Create React app (npx create-react-app client).
Install Axios and Tailwind CSS.
Build Flashcard.js component with flip animation.


Integrate:
Connect frontend to backend via Axios.
Test data flow (e.g., fetching and displaying flashcards).


Deploy:
Push code to GitHub.
Deploy frontend to Netlify and backend to Render.


Iterate:
Add features like answer validation or progress tracking based on user feedback.



Sample Interaction Flow

User opens http://localhost:3000 → Sees homepage with "Start Studying" button.
Clicks button → React fetches flashcards from http://localhost:5000/api/flashcards.
Backend reads flashcards.json and returns data.
React renders a card with a question and a "Flip" button.
User clicks "Flip" → Card flips to show the answer (using CSS transform).
User enters an answer in an input field → React compares it with the correct answer and shows feedback.

Next Steps

Create the project folder structure as outlined.
Initialize the backend with a basic Express server and a sample flashcards.json.
Build the React frontend with a single Flashcard component.
Test the integration by fetching and displaying one flashcard.

