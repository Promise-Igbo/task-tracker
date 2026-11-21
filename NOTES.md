## At least three things i would improve, and why.

# 1. Add API and form validation, plus meaningful HTTP errors. Tasks should not accept a missing or blank title, invalid priorities, or invalid due dates; validation prevents unusable records and gives users clear feedback.

# 2. Handle failed requests and loading states in React. The UI currently assumes every fetch() succeeds, so checking res.ok, displaying loading feedback, and showing an error message would make network failures understandable instead of silent or confusing.

# 3. Use functional state updates and split repeated UI behavior into smaller components. Updating tasks with setTasks(currentTasks => ...) avoids stale-state closures, while smaller form, filter, and task-row components would make App.jsx easier to read and maintain.


## The prompts and AI tools i used to explore the app.

# On Copilot on VScode: You are a senior react developer, i am a beginner learning react. Analyze the entire project, inspect relevant files, explain and help me understand how this code, existing components and services work, what each part does and how the pieces fit together. Keep each explanation as comment or sentence, do not change or add any new libraries, show only the code explanation and three things i can improve and why.

# I use Chatgpt to check if there was any explanation copilot got wrong: You are a senior react developer, i am a beginner learning react trying to understand certain components. What do you notice is wrong here? Do not bother on the indentation because it is a copy and paste interraction. If there is none, reply None only. If there is, tell me the specific place(s) and provide a one line correction.

## One thing AI got wrong or missed, and how i noticed.

# I use chatgpt for this

# 1. React component and state: useEffect with an empty dependency array runs after the first render and calls fetch("/api/tasks") once.

   // Correction: It runs after the initial mount, but the fetch can run twice in React Strict Mode during development.

# 2. React component and state: checked={!!t.done} converts SQLite's 0 or 1 value into a boolean checkbox value.

    // Correction: None needed, assuming done is consistently stored as 0 or 1.

# 3. Database: run() executes an INSERT, UPDATE, or DELETE, saves the database, and returns the most recently inserted row ID.

    // Correction: UPDATE and DELETE do not insert rows, so describe the return value as the last inserted row ID only when an INSERT occurs.