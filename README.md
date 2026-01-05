# Simple Language

<div align="center">

![Simple Logo]([https://simplelang.dev/logo.png](https://i.postimg.cc/ZRYGvqJj/de301fe1-bb84-47d9-8388-4876c92f18c3.jpg))

**A modern, easy-to-learn backend programming language**

[![npm version](https://badge.fury.io/js/simple-lang.svg)](https://www.npmjs.com/package/simple-lang)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Downloads](https://img.shields.io/npm/dm/simple-lang.svg)](https://www.npmjs.com/package/simple-lang)

[Website](https://simplelang.dev) • [Documentation](https://docs.simplelang.dev) • [Examples](https://github.com/simple-lang/examples) • [Discord](https://discord.gg/simplelang)

</div>

---

## 🚀 What is Simple?

Simple is a modern programming language designed specifically for backend development. It combines the clarity of VB.NET with the power of modern web frameworks, making it perfect for beginners while remaining powerful enough for professionals.

**Key Features:**
- ✅ **Crystal-clear syntax** - No cryptic symbols, just readable English
- ✅ **Built-in web framework** - Routes, middleware, and REST APIs out of the box
- ✅ **Strong type system** - Catch errors before runtime with optional type inference
- ✅ **Compiles to JavaScript** - Runs on Node.js, deploy anywhere
- ✅ **Zero boilerplate** - Get started in seconds
- ✅ **Beginner-friendly** - Learn in hours, not weeks

---

## 📦 Installation

### Global Installation (Recommended)

```bash
npm install -g simple-lang
```

### Local Installation

```bash
npm install simple-lang --save-dev
```

### Requirements
- Node.js >= 14.0.0
- npm >= 6.0.0

---

## ⚡ Quick Start

### Create Your First Project

```bash
# Create a new project
simple init my-api

# Navigate to project
cd my-api

# Install dependencies
npm install

# Compile and run
npm start
```

Your API is now running at `http://localhost:3000`! 🎉

### Hello World Example

Create a file `app.smp`:

```simple
Function Greet(name As String) Returns String
    Return "Hello, " + name + "!"
End

Route GET "/"
    message = Greet("World")
    Return JSON({ message: message })
End
```

Compile and run:

```bash
simple compile app.smp
node dist/app.js
```

Visit `http://localhost:3000` and see your API in action!

---

## 📚 Language Examples

### Variables and Types

```simple
Variable name As String = "Alice"
Variable age As Integer = 25
Variable active As Boolean = True
Variable price As Float = 19.99

// Type inference
Variable city = "Milan"        // String
Variable count = 10            // Integer
```

### Functions

```simple
Function Add(a As Integer, b As Integer) Returns Integer
    Return a + b
End

Function Greet(name As String) Returns String
    Return "Hello, " + name + "!"
End

// Optional parameters
Function CreateUser(name As String, age As Integer = 18) Returns String
    Return "Created user: " + name
End
```

### REST API Routes

```simple
// GET endpoint
Route GET "/users"
    users = Database.Query("SELECT * FROM users")
    Return JSON(users)
End

// GET with parameters
Route GET "/users/:id"
    userId = Request.Params.id
    user = Database.FindById("users", userId)
    
    If user Is Nothing Then
        Return NotFound()
    End
    
    Return JSON(user)
End

// POST endpoint
Route POST "/users"
    data = Request.Body
    user = Database.Insert("users", data)
    Return Created(user)
End

// PUT endpoint
Route PUT "/users/:id"
    userId = Request.Params.id
    data = Request.Body
    updated = Database.Update("users", userId, data)
    Return JSON(updated)
End

// DELETE endpoint
Route DELETE "/users/:id"
    userId = Request.Params.id
    Database.Delete("users", userId)
    Return NoContent()
End
```

### Control Flow

```simple
// If statements
If age >= 18 Then
    Print("Adult")
ElseIf age >= 13 Then
    Print("Teenager")
Else
    Print("Child")
End

// Loops
For i = 0 To 10 Do
    Print(i)
End

Variable count = 0
While count < 10 Do
    count = count + 1
End

// For Each
Variable numbers = [1, 2, 3, 4, 5]
For Each num In numbers Do
    Print(num)
End
```

### Middleware

```simple
Middleware AuthRequired
    token = Request.Header("Authorization")
    
    If token Is Nothing Then
        Return Unauthorized()
    End
    
    user = JWT.Verify(token, SECRET_KEY)
    Request.User = user
    Continue()
End

// Use middleware
Route GET "/protected" Use AuthRequired
    Return JSON({ user: Request.User })
End
```

### Database Operations

```simple
// Find all
Variable users = User.FindAll()

// Find by ID
Variable user = User.FindById(1)

// Find with condition
Variable adults = User.FindWhere(age >= 18)

// Create
Variable newUser = User.Create({
    name: "Bob",
    email: "bob@example.com",
    age: 30
})

// Update
User.Update(1, { age: 31 })

// Delete
User.Delete(1)
```

---

## 🛠️ CLI Commands

### `simple compile`
Compile .smp files to JavaScript

```bash
simple compile app.smp
simple compile app.smp -o build/
```

### `simple run`
Compile and execute a .smp file

```bash
simple run server.smp
```

### `simple watch`
Watch directory for changes and auto-recompile

```bash
simple watch src/
```

### `simple init`
Create a new Simple project with template

```bash
simple init my-project
```

### `simple version`
Show version information

```bash
simple version
```

### `simple help`
Display help information

```bash
simple help
```

---

## 📖 Full Documentation

### Language Guide
- [Syntax Overview](https://docs.simplelang.dev/syntax)
- [Data Types](https://docs.simplelang.dev/types)
- [Functions](https://docs.simplelang.dev/functions)
- [Classes & OOP](https://docs.simplelang.dev/classes)
- [Error Handling](https://docs.simplelang.dev/errors)

### Web Framework
- [Routing](https://docs.simplelang.dev/routing)
- [Middleware](https://docs.simplelang.dev/middleware)
- [Request/Response](https://docs.simplelang.dev/http)
- [Authentication](https://docs.simplelang.dev/auth)
- [File Uploads](https://docs.simplelang.dev/files)

### Database
- [Models](https://docs.simplelang.dev/models)
- [Queries](https://docs.simplelang.dev/queries)
- [Relationships](https://docs.simplelang.dev/relationships)
- [Migrations](https://docs.simplelang.dev/migrations)

### Advanced Topics
- [Async Operations](https://docs.simplelang.dev/async)
- [Testing](https://docs.simplelang.dev/testing)
- [Deployment](https://docs.simplelang.dev/deployment)
- [Performance](https://docs.simplelang.dev/performance)

---

## 🎯 Project Structure

```
my-api/
├── src/
│   ├── app.smp              # Main application
│   ├── routes/
│   │   ├── users.smp
│   │   └── posts.smp
│   ├── models/
│   │   ├── User.smp
│   │   └── Post.smp
│   └── middleware/
│       └── auth.smp
├── dist/                    # Compiled JavaScript
├── tests/
│   └── app.test.smp
├── package.json
└── README.md
```

---

## 🔧 Configuration

Create a `simple.config.json` file:

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "strict": true,
    "sourceMap": true
  },
  "server": {
    "port": 3000,
    "host": "0.0.0.0"
  },
  "database": {
    "type": "postgresql",
    "host": "localhost",
    "port": 5432
  }
}
```

---

## 🌟 Why Simple?

### For Beginners
- **No prior experience needed** - Simple's syntax reads like English
- **Learn by doing** - Build real APIs in your first hour
- **Helpful error messages** - Clear explanations, not cryptic errors
- **Great documentation** - Tutorials, examples, and guides

### For Professionals
- **Fast development** - Less boilerplate, more productivity
- **Type safety** - Catch bugs before runtime
- **Modern features** - Async/await, pattern matching, and more
- **JavaScript interop** - Use npm packages seamlessly

### For Teams
- **Readable code** - New team members onboard quickly
- **Maintainable** - Clear structure and conventions
- **Scalable** - From prototype to production
- **Compatible** - Runs anywhere Node.js runs

---

## 🚀 Real-World Examples

### Blog API

```simple
Model Post
    Property Id As Integer Primary Key Auto
    Property Title As String Required
    Property Content As String
    Property Published As Boolean Default(False)
End

Route GET "/posts"
    posts = Post.FindAll()
    Return JSON(posts)
End

Route POST "/posts"
    data = Request.Body
    post = Post.Create(data)
    Return Created(post)
End
```

### User Authentication

```simple
Import JWT From "auth"
Import Hash From "crypto"

Route POST "/register"
    data = Request.Body
    
    hashedPassword = Hash.Make(data.password)
    user = User.Create({
        email: data.email,
        passwordHash: hashedPassword
    })
    
    Return Created({ id: user.Id })
End

Route POST "/login"
    data = Request.Body
    user = User.FindOne({ email: data.email })
    
    If Not Hash.Verify(data.password, user.PasswordHash) Then
        Return Unauthorized()
    End
    
    token = JWT.Sign({ userId: user.Id }, SECRET_KEY)
    Return JSON({ token: token })
End
```

---

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md).

### Development Setup

```bash
# Clone the repository
git clone https://github.com/simple-lang/simple.git
cd simple

# Install dependencies
npm install

# Run tests
npm test

# Build
npm run build
```

---

## 📝 Roadmap

### v1.1 (Q2 2024)
- [ ] Standard library expansion
- [ ] TypeScript output option
- [ ] WebSocket support
- [ ] GraphQL integration

### v1.2 (Q3 2024)
- [ ] Visual Studio Code extension
- [ ] Debugger support
- [ ] Package manager (spm)
- [ ] Module system improvements

### v2.0 (Q4 2024)
- [ ] Self-hosting compiler
- [ ] WASM compilation target
- [ ] Native binary output
- [ ] Advanced optimizations

---

## 🐛 Bug Reports

Found a bug? Please [open an issue](https://github.com/simple-lang/simple/issues) with:
- Simple version (`simple version`)
- Operating system
- Code sample that reproduces the issue
- Expected vs actual behavior

---

## 💬 Community

- **Discord**: [Join our server](https://discord.gg/simplelang)
- **Twitter**: [@SimpleLang](https://twitter.com/simplelang)
- **Stack Overflow**: Tag `simple-lang`
- **Reddit**: [r/SimpleLang](https://reddit.com/r/simplelang)

---

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

Simple is inspired by:
- **VB.NET** - Clear, readable syntax
- **Python** - Simplicity and elegance
- **Express.js** - Web framework design
- **TypeScript** - Type system
- **Ruby on Rails** - Convention over configuration

---

## ⭐ Show Your Support

If you find Simple useful, please consider:
- ⭐ Starring the [GitHub repository](https://github.com/simple-lang/simple)
- 📢 Sharing with your network
- 🐛 Reporting bugs and suggesting features
- 💻 Contributing code
- 📝 Writing tutorials and blog posts

---

<div align="center">

**Made with ❤️ by the Simple community**

[Website](https://simplelang.dev) • [Docs](https://docs.simplelang.dev) • [GitHub](https://github.com/simple-lang/simple)

</div>
