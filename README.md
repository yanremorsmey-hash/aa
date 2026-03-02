# Quiz CLI 📚

## High-Level Description

**Quiz CLI** is an interactive command-line quiz game built with Node.js (ES Modules). It loads quiz categories and questions from a JSON file, lets the user choose a category and question count, runs an interactive quiz session, and displays results at the end. The app demonstrates modern JavaScript patterns including async/await, filesystem access, and a small OOP-based quiz engine.

## Features

- **Interactive Terminal UI**
  - Category selection with arrow key navigation
  - Question-count selection (All / 3 / 5 questions depending on availability)
  - "Press Enter to continue" flow between questions
  - "Play again" loop for continuous learning
  - Beautiful ASCII art banner

- **Data-Driven Questions**
  - Questions loaded from `data/questions.json`
  - Three built-in categories:
    - **JavaScript Basics** - Core JavaScript concepts (const, arrays, equality, data types)
    - **Node.js Fundamentals** - Node.js specific features (fs module, event loop, npm, ES6 imports)
    - **General Programming** - Universal programming concepts (APIs, recursion, JSON, callbacks, version control)
  - Each question includes:
    - Multiple choice options
    - Correct answer
    - Detailed explanation for learning

- **OOP Quiz Engine**
  - Quiz class lifecycle management (`isComplete` property)
  - Question asking with user input validation
  - Real-time scoring and progress tracking
  - Comprehensive results display with explanations

- **Modern Node.js + ES Modules**
  - `import/export` syntax throughout
  - `import.meta.url` with `fileURLToPath` for path resolution
  - No CommonJS dependencies

- **Async Filesystem Loading**
  - Reads and parses JSON via `node:fs/promises`
  - Proper error handling for file operations

- **Terminal Styling**
  - Colorized output via `src/colors.js`
  - Color-coded feedback (success, error, info, warnings)
  - Highlighted text and dimmed hints

- **Error Handling**
  - Graceful error messages with colored output
  - Stack traces for debugging
  - Proper process exit codes

## Project Structure

```text
.
├── data/
│   └── questions.json        # Quiz categories and questions database
├── src/
│   ├── input.js              # User input utilities (createInterface, select, confirm, pressEnter)
│   ├── quiz.js               # Quiz class (question management, scoring, results display)
│   └── colors.js             # Terminal color and styling utilities
├── index.js                  # CLI entry point and main application loop
├── package.json              # Project metadata and dependencies
└── README.md                 # This file
```

## Quiz Categories

### 1. JavaScript Basics
- Variable declarations (const, let, var)
- Array methods (push, pop, shift, unshift)
- Equality operators (=== vs ==)
- Primitive vs reference types
- JavaScript quirks (typeof null)

### 2. Node.js Fundamentals
- File system (fs) module
- Event loop architecture
- NPM and package management
- Command-line arguments (process.argv)
- ES6 module syntax

### 3. General Programming
- API concepts
- Recursion
- JSON format
- Callback functions
- Version control systems

## Getting Started

### Prerequisites
- **Node.js 18+** (required)  
  The app uses ES Modules and `node:fs/promises`.

### Install
Clone the repository and install dependencies:
```bash
git clone <repository-url>
cd quiz-cli
npm install
```

### Run (Direct Execution)
If your entry file is `index.js`:
```bash
node index.js
```

Or using npm scripts:
```bash
npm start
```

### Run as CLI Command (Recommended)

1. **Ensure executable permissions** (macOS/Linux):
   ```bash
   chmod +x index.js
   ```

2. **Link globally** to run from anywhere:
   ```bash
   npm link
   quiz-cli
   ```

3. **Or install globally**:
   ```bash
   npm install -g .
   quiz-cli
   ```

## Usage

1. **Start the quiz**: Run `node index.js` or `npm start`
2. **Choose a category**: Use arrow keys to select from JavaScript, Node.js, or General Programming
3. **Select question count**: Choose all questions or a subset (3 or 5)
4. **Answer questions**: Enter the number corresponding to your answer choice
5. **Review results**: See your score, percentage, and detailed explanations
6. **Play again**: Choose to continue learning or exit

### Example Session

```
  ╔═══════════════════════════════════════════╗
  ║                                           ║
  ║   📚 QUIZ CLI                             ║
  ║   Test your programming knowledge!        ║
  ║                                           ║
  ╚═══════════════════════════════════════════╝

? Choose a category:
  ❯ JavaScript Basics
    Node.js Fundamentals
    General Programming

? How many questions?
  ❯ All questions
    3 questions
    5 questions
```

## Customizing Questions

Edit `data/questions.json` to add or modify quiz content. The expected structure:

```json
{
  "categories": {
    "category-id": {
      "name": "Category Display Name",
      "questions": [
        {
          "question": "Your question text?",
          "options": ["Option A", "Option B", "Option C", "Option D"],
          "answer": 0,
          "explanation": "Why this is the correct answer..."
        }
      ]
    }
  }
}
```

**Fields:**
- `question`: The question text
- `options`: Array of possible answers
- `answer`: Zero-based index of the correct option
- `explanation`: Educational context shown after answering

## Code Highlights

### Modern JavaScript Patterns
- **Async/Await**: Clean asynchronous code without callbacks
- **Destructuring**: `const { index } = await select(...)`
- **Template Literals**: Dynamic string formatting
- **Array Methods**: `map`, `filter`, `slice` for data manipulation
- **Classes**: OOP-based Quiz engine

### ES Modules Path Resolution
```javascript
const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);
```

### User Input Handling
The app uses a custom input wrapper around Node.js readline for:
- Single-select menus (arrow key navigation)
- Yes/no confirmations
- "Press Enter to continue" prompts

## Technical Details

### Dependencies
- **Node.js Core Modules Only**
  - `node:fs/promises` - File system operations
  - `node:readline` - Terminal input handling
  - `node:path` - Path utilities
  - `node:url` - URL and file path conversion

### Engine Requirements
- Node.js >= 18.0.0 (specified in package.json)

## Learning Outcomes

This project demonstrates:
1. **ES6+ Syntax**: Modern JavaScript features
2. **Async Programming**: Promises and async/await patterns
3. **File I/O**: Reading and parsing JSON files
4. **User Interaction**: Terminal-based UI with readline
5. **OOP Concepts**: Class-based architecture
6. **Error Handling**: Try-catch and graceful degradation
7. **Module System**: ES Module imports and exports
8. **Project Structure**: Organized file layout for CLI apps

## License

MIT License

## Contributing

Feel free to:
- Add more quiz categories
- Improve the UI/UX
- Add difficulty levels
- Implement score persistence
- Add timed quizzes

---

**Happy Learning! 🚀**
