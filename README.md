# 📚 Quiz CLI

## Overview

**Quiz CLI** is a modern, interactive command-line quiz game built with Node.js using ES Modules. This educational application provides an engaging way to test your programming knowledge through a beautifully styled terminal interface. The application demonstrates best practices in modern JavaScript development, including ES Modules, async/await, OOP design patterns, and interactive CLI development.

### What Makes This Project Special

- **🎨 Beautiful Terminal UI**: Colorized output with styled banners and interactive prompts
- **📊 Category-Based Learning**: Organized quiz questions by programming topics
- **🔄 Flexible Quiz Sessions**: Choose the number of questions (3, 5, or all available)
- **♻️ Replay Functionality**: Keep playing and improving your scores
- **🏆 Instant Feedback**: Real-time scoring and detailed results after each quiz
- **📦 Modern Architecture**: Clean separation of concerns with modular design

## Features

### Interactive Terminal UI
- **Category Selection**: Choose from multiple programming topics
- **Question Count Selection**: Pick "All questions", "3 questions", or "5 questions" based on availability
- **Press Enter Flow**: Smooth transitions between questions with user-controlled pacing
- **Play Again Loop**: Continuous learning with instant replay capability
- **Styled Output**: Eye-catching colors and formatted text for better readability

### Data-Driven Quiz System
- Questions dynamically loaded from `data/questions.json`
- Flexible category structure for easy content expansion
- Support for multiple-choice questions with validation

### OOP Quiz Engine
- Complete quiz lifecycle management
- Built-in completion tracking (`isComplete`)
- Automatic scoring system
- Professional results display

### Modern Node.js Architecture
- **ES Modules**: Full `import/export` syntax with `import.meta.url`
- **Async File Operations**: Non-blocking I/O via `node:fs/promises`
- **Path Resolution**: Cross-platform compatibility with `fileURLToPath`
- **Terminal Styling**: Custom color utilities for enhanced UX
- **Comprehensive Error Handling**: Graceful errors with detailed stack traces

## Technology Stack

- **Runtime**: Node.js 18+ (ES Modules)
- **Core Modules**: 
  - `node:fs/promises` - Async file operations
  - `node:readline` - Interactive user input
  - `node:path` - Cross-platform path handling
  - `node:url` - ES Module URL utilities
- **Architecture**: Object-Oriented Programming with modern JavaScript

## Project Structure

```text
quiz-cli/
├── data/
│   └── questions.json        # Quiz categories and questions database
├── src/
│   ├── input.js              # User input handling (select, confirm, pressEnter)
│   ├── quiz.js               # Quiz class (lifecycle, scoring, results)
│   └── colors.js             # Terminal color and styling utilities
├── index.js                  # CLI entry point and main application loop
├── package.json              # Project configuration and dependencies
└── README.md                 # This file
```

### File Descriptions

#### `index.js` (Main Entry Point)
- Application bootstrapping and initialization
- Question loading from JSON file
- Main game loop implementation
- Category and question count selection flow
- Quiz instantiation and execution
- Results display and replay logic
- Error handling and graceful shutdown

#### `src/input.js`
- **`createInterface()`**: Creates readline interface for user input
- **`select()`**: Interactive menu selection with numbered options
- **`confirm()`**: Yes/No prompt for binary choices
- **`pressEnter()`**: Pause execution until user continues

#### `src/quiz.js`
- **`Quiz` Class**: Core quiz engine
  - **`askQuestion()`**: Display question and collect answer
  - **`checkAnswer()`**: Validate user responses
  - **`updateScore()`**: Track correct/incorrect answers
  - **`showResults()`**: Display final score and performance
  - **`isComplete`**: Check if all questions answered

#### `src/colors.js`
- Terminal color utilities (cyan, green, red, yellow)
- Text styling functions (bold, dim, underline)
- Predefined semantic colors (success, error, info, warning)
- Banner and highlight formatting

#### `data/questions.json`
JSON structure for quiz content:
```json
{
  "categories": {
    "categoryId": {
      "name": "Category Name",
      "questions": [
        {
          "question": "Question text?",
          "options": ["Option 1", "Option 2", "Option 3", "Option 4"],
          "correctAnswer": 0
        }
      ]
    }
  }
}
```

## Getting Started

### Prerequisites

- **Node.js 18.0.0 or higher** (Required for ES Modules support)
- Terminal with color support (for best experience)

Check your Node.js version:
```bash
node --version
```

### Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd quiz-cli
   ```

2. **Install dependencies** (if any):
   ```bash
   npm install
   ```

### Running the Application

#### Option 1: Direct Execution
Run directly with Node.js:
```bash
node index.js
```

#### Option 2: Using npm Scripts
Use the predefined start script:
```bash
npm start
```

#### Option 3: As a Global CLI Tool (Recommended)

1. **Ensure executable permissions** (macOS/Linux):
   ```bash
   chmod +x index.js
   ```

2. **Link the package globally**:
   ```bash
   npm link
   ```

3. **Run from anywhere**:
   ```bash
   quiz-cli
   ```

4. **To uninstall globally**:
   ```bash
   npm unlink -g quiz-cli
   ```

## Usage

### Starting a Quiz

1. **Launch the application**:
   ```bash
   npm start
   ```

2. **Choose a category**:
   - Use arrow keys or enter the number
   - Categories are loaded from `data/questions.json`

3. **Select question count**:
   - "All questions" - Complete quiz
   - "3 questions" - Quick quiz
   - "5 questions" - Medium quiz

4. **Answer questions**:
   - Read each question carefully
   - Enter the number of your chosen answer
   - Press Enter to continue after seeing if you're correct

5. **View results**:
   - See your final score
   - Review your performance percentage
   - Choose to play again or exit

### Sample Session

```
╔═══════════════════════════════════════════╗
║                                           ║
║   📚 QUIZ CLI                            ║
║   Test your programming knowledge!       ║
║                                           ║
╚═══════════════════════════════════════════╝

? Choose a category:
  1. JavaScript Basics
  2. Node.js
  3. Web Development
> 1

? How many questions?
  1. All questions
  2. 3 questions
  3. 5 questions
> 2

Starting quiz...
Select your answer by entering the number.

Press Enter to continue...

Question 1/3: What is JavaScript?
  1. A programming language
  2. A coffee brand
  3. A framework
  4. A database

Your answer: 1
✓ Correct!

[... more questions ...]

Quiz Complete!
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Score: 2/3 (67%)
Great job! Keep practicing! 🎉

? Would you like to play again? (Y/n)
```

## Customization

### Adding New Questions

Edit `data/questions.json`:

```json
{
  "categories": {
    "newCategory": {
      "name": "Your New Category",
      "questions": [
        {
          "question": "Your question here?",
          "options": [
            "Option 1",
            "Option 2",
            "Option 3",
            "Option 4"
          ],
          "correctAnswer": 0
        }
      ]
    }
  }
}
```

**Important Notes**:
- `correctAnswer` is zero-indexed (0 = first option, 1 = second option, etc.)
- Ensure valid JSON syntax (no trailing commas)
- All questions must have an `options` array and `correctAnswer` field

### Modifying Colors

Edit `src/colors.js` to customize terminal colors:
- Change color codes (e.g., `\x1b[36m` for cyan)
- Add new styling functions
- Create custom semantic color groups

### Adjusting Question Limits

In `index.js`, modify the question count options:

```javascript
const countOptions = ['All questions', '3 questions', '5 questions', '10 questions'];
```

Update the logic to handle new counts:

```javascript
if (countChoice.includes('10')) questionCount = 10;
```

## Development

### Code Architecture

The application follows a modular architecture with clear separation of concerns:

```
┌─────────────────┐
│   index.js      │  ← Entry point & orchestration
└────────┬────────┘
         │
    ┌────┴────┬──────────────┬───────────┐
    │         │              │           │
┌───▼────┐ ┌─▼──────┐ ┌─────▼────┐ ┌────▼─────┐
│ input  │ │  quiz  │ │  colors  │ │questions │
│  .js   │ │  .js   │ │   .js    │ │  .json   │
└────────┘ └────────┘ └──────────┘ └──────────┘
```

### Key Concepts Demonstrated

1. **ES Modules**:
   ```javascript
   import { readFile } from 'node:fs/promises';
   export { Quiz };
   ```

2. **Async/Await**:
   ```javascript
   async function loadQuestions() {
     const data = await readFile(filePath, 'utf-8');
     return JSON.parse(data);
   }
   ```

3. **Destructuring**:
   ```javascript
   const { index } = await select(rl, 'Choose:', options);
   ```

4. **Template Literals**:
   ```javascript
   console.log(`Score: ${score}/${total} (${percentage}%)`);
   ```

5. **Array Methods**:
   ```javascript
   const options = categoryIds.map(id => data.categories[id].name);
   ```

6. **Class-Based OOP**:
   ```javascript
   class Quiz {
     constructor(questions, categoryName) { ... }
     async askQuestion(rl) { ... }
   }
   ```

### Testing

Run tests (if test suite exists):
```bash
npm test
```

### Linting

Consider adding ESLint for code quality:
```bash
npm install --save-dev eslint
npx eslint index.js src/
```

## Troubleshooting

### Common Issues

**"Cannot find module" errors**:
- Ensure `"type": "module"` is set in `package.json`
- Check that all import paths are correct and use `.js` extensions

**Questions not loading**:
- Verify `data/questions.json` exists and contains valid JSON
- Check file permissions
- Ensure the path resolution in `index.js` is correct

**Colors not displaying**:
- Verify your terminal supports ANSI color codes
- Try a different terminal emulator
- Check if colors are disabled in terminal settings

**Node.js version issues**:
- Update Node.js to version 18 or higher
- Use `nvm` (Node Version Manager) to manage multiple versions

### Error Messages

The application includes comprehensive error handling:
- **File not found**: Check that `data/questions.json` exists
- **Parse errors**: Validate JSON syntax in questions file
- **Input errors**: Ensure readline interface is properly initialized

## Contributing

Contributions are welcome! Here are some ideas:

### Enhancement Ideas
- ✅ Add timer mode for timed quizzes
- ✅ Implement difficulty levels
- ✅ Add leaderboard with score persistence
- ✅ Support for true/false questions
- ✅ Add hint system
- ✅ Multi-language support
- ✅ Question randomization
- ✅ Add sound effects (terminal beeps)
- ✅ Export results to file
- ✅ Add statistics tracking over time

### How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Best Practices Demonstrated

- ✅ **Modular Design**: Separation of concerns across multiple files
- ✅ **ES6+ Features**: Modern JavaScript syntax and patterns
- ✅ **Error Handling**: Try/catch blocks with detailed error messages
- ✅ **Async Operations**: Non-blocking I/O with promises
- ✅ **User Experience**: Clear prompts, colors, and flow control
- ✅ **Code Documentation**: JSDoc comments explaining functionality
- ✅ **Package Configuration**: Proper npm setup with scripts and metadata

## Learning Outcomes

By studying this project, you'll learn:

1. **ES Module System**: How to structure modern Node.js applications
2. **Async JavaScript**: Promises, async/await, and file operations
3. **CLI Development**: Building interactive command-line interfaces
4. **OOP in JavaScript**: Class-based architecture and encapsulation
5. **User Input Handling**: Working with readline and user prompts
6. **File I/O**: Reading and parsing JSON files asynchronously
7. **Error Handling**: Graceful error management and user feedback
8. **Terminal Styling**: ANSI escape codes for colored output
9. **Application Flow**: Managing state and control flow in interactive apps
10. **Package Management**: npm configuration and executable scripts

## License

MIT License - Feel free to use this project for learning and development.

## Acknowledgments

- Built with ❤️ as an educational tool for learning Node.js
- Demonstrates real-world CLI application patterns
- Inspired by the need for interactive programming education

## Support

For issues, questions, or suggestions:
- Open an issue in the repository
- Review the troubleshooting section
- Check Node.js documentation for core module references

---

**Happy Learning! 📚✨**

*Remember: The best way to learn is by doing. Fork this project, modify it, break it, fix it, and make it your own!*
