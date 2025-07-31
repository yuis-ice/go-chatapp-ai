# 🤝 Contributing to Go Real-time Chat App

First off, thanks for taking the time to contribute! ❤️

All types of contributions are encouraged and valued. See the [Table of Contents](#table-of-contents) for different ways to help and details about how this project handles them. Please make sure to read the relevant section before making your contribution. It will make it a lot easier for us maintainers and smooth out the experience for all involved. The community looks forward to your contributions. 🎉

> And if you like the project, but just don't have time to contribute, that's fine. There are other easy ways to support the project and show your appreciation:
> - ⭐ Star the project
> - 🐦 Tweet about it
> - 🔗 Refer this project in your project's readme
> - 📢 Mention the project at local meetups and tell your friends/colleagues

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [I Have a Question](#i-have-a-question)
- [I Want To Contribute](#i-want-to-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Enhancements](#suggesting-enhancements)
  - [Your First Code Contribution](#your-first-code-contribution)
  - [Improving The Documentation](#improving-the-documentation)
- [Styleguides](#styleguides)
  - [Go Code Style](#go-code-style)
  - [Frontend Code Style](#frontend-code-style)
  - [Commit Messages](#commit-messages)
- [Development Setup](#development-setup)
- [Pull Request Process](#pull-request-process)
- [Contributor License Agreement (CLA)](#-contributor-license-agreement-cla)

## Code of Conduct

This project and everyone participating in it is governed by our commitment to providing a welcoming and inclusive environment. By participating, you are expected to uphold this code. Please be respectful, considerate, and constructive in all interactions.

### Our Standards

**Examples of behavior that contributes to a positive environment:**
- Using welcoming and inclusive language
- Being respectful of differing viewpoints and experiences
- Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards other community members

**Examples of unacceptable behavior:**
- The use of sexualized language or imagery and unwelcome sexual attention or advances
- Trolling, insulting/derogatory comments, and personal or political attacks
- Public or private harassment
- Publishing others' private information without explicit permission
- Other conduct which could reasonably be considered inappropriate in a professional setting

## I Have a Question

> If you want to ask a question, we assume that you have read the available [Documentation](README.md).

Before you ask a question, it is best to search for existing [Issues](https://github.com/yuis-ice/go-chatapp-ai/issues) and [Discussions](https://github.com/yuis-ice/go-chatapp-ai/discussions) that might help you. In case you have found a suitable issue and still need clarification, you can write your question in that issue.

If you then still feel the need to ask a question and need clarification, we recommend the following:

- Open a [Discussion](https://github.com/yuis-ice/go-chatapp-ai/discussions/new?category=q-a)
- Provide as much context as you can about what you're running into
- Provide project and platform versions (Go version, OS, browser, etc.)
- Include relevant code snippets or error messages

We will then take care of the question as soon as possible.

## I Want To Contribute

> ### Legal Notice
> When contributing to this project, you must agree that you have authored 100% of the content, that you have the necessary rights to the content and that the content you contribute may be provided under the project license.

### Reporting Bugs

#### Before Submitting a Bug Report

A good bug report shouldn't leave others needing to chase you up for more information. Therefore, we ask you to investigate carefully, collect information and describe the issue in detail in your report.

- Make sure that you are using the latest version
- Determine if your bug is really a bug and not an error on your side (check documentation, Go version compatibility, etc.)
- To see if other users have experienced (and potentially already solved) the same issue you are having, check if there is not already a bug report existing for your bug or error
- Collect information about the bug:
  - Stack trace (Traceback)
  - OS, Platform and Version (Windows, Linux, macOS, x86, ARM)
  - Version of Go, browser, and possibly other relevant software
  - Can you reliably reproduce the issue? And can you also reproduce it with older versions?

#### How Do I Submit a Good Bug Report?

We use GitHub issues to track bugs and errors. If you run into an issue with the project:

- Open an [Issue](https://github.com/yuis-ice/go-chatapp-ai/issues/new/choose)
- Use the **Bug Report** template
- Explain the behavior you would expect and the actual behavior
- Please provide as much context as possible and describe the *reproduction steps* that someone else can follow to recreate the issue
- Provide the information you collected in the previous section

### Suggesting Enhancements

This section guides you through submitting an enhancement suggestion for the Go Real-time Chat App, **including completely new features and minor improvements to existing functionality**.

#### Before Submitting an Enhancement

- Make sure that you are using the latest version
- Read the [documentation](README.md) carefully and find out if the functionality is already covered
- Perform a [search](https://github.com/yuis-ice/go-chatapp-ai/issues) to see if the enhancement has already been suggested
- Find out whether your idea fits with the scope and aims of the project

#### How Do I Submit a Good Enhancement Suggestion?

Enhancement suggestions are tracked as [GitHub issues](https://github.com/yuis-ice/go-chatapp-ai/issues).

- Use the **Feature Request** template
- Use a **clear and descriptive title** for the issue to identify the suggestion
- Provide a **step-by-step description of the suggested enhancement** in as many details as possible
- **Describe the current behavior** and **explain which behavior you expected to see instead** and why
- **Explain why this enhancement would be useful** to most users
- List some other chat applications or similar projects where this enhancement exists

### Your First Code Contribution

Unsure where to begin contributing? You can start by looking through these `beginner` and `help-wanted` issues:

- [Beginner issues](https://github.com/yuis-ice/go-chatapp-ai/labels/good%20first%20issue) - issues which should only require a few lines of code, and a test or two
- [Help wanted issues](https://github.com/yuis-ice/go-chatapp-ai/labels/help%20wanted) - issues which should be a bit more involved than `beginner` issues

#### Local Development Setup

See [Development Setup](#development-setup) section below for detailed instructions.

### Improving The Documentation

Documentation improvements are always welcome! This includes:

- README improvements
- Code comments
- API documentation
- Tutorial content
- Example improvements

## Styleguides

### Go Code Style

- Follow standard Go formatting (`go fmt`)
- Use `go vet` to check for suspicious code
- Follow effective Go practices
- Write clear, self-documenting code
- Add comments for exported functions and complex logic
- Use meaningful variable and function names
- Keep functions small and focused

**Example:**
```go
// HandleWebSocket upgrades HTTP connections to WebSocket and manages the client lifecycle
func HandleWebSocket(hub *Hub, w http.ResponseWriter, r *http.Request) {
    conn, err := upgrader.Upgrade(w, r, nil)
    if err != nil {
        log.Printf("WebSocket upgrade failed: %v", err)
        return
    }
    
    username := getUsername(r)
    client := NewClient(conn, username)
    
    hub.Register(client)
    go client.ReadPump(hub)
    go client.WritePump()
}
```

### Frontend Code Style

- Use consistent indentation (2 or 4 spaces)
- Follow semantic HTML structure
- Use CSS classes over inline styles
- Write clear, readable JavaScript
- Use meaningful variable names
- Add comments for complex logic

**Example:**
```javascript
// Establish WebSocket connection with error handling
function connectToChat(username) {
    const wsUrl = `ws://${window.location.host}/ws?username=${encodeURIComponent(username)}`;
    
    socket = new WebSocket(wsUrl);
    socket.onopen = handleConnectionOpen;
    socket.onmessage = handleMessage;
    socket.onerror = handleConnectionError;
}
```

### Commit Messages

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters or less
- Reference issues and pull requests liberally after the first line
- Consider starting the commit message with an applicable emoji:
  - 🎉 `:tada:` when adding a new feature
  - 🐛 `:bug:` when fixing a bug
  - 📚 `:books:` when writing docs
  - 🎨 `:art:` when improving the format/structure of the code
  - ⚡ `:zap:` when improving performance
  - 🧪 `:test_tube:` when adding tests
  - 🔧 `:wrench:` when changing configuration files

**Examples:**
```
🎉 Add user presence indicators to chat interface

- Display online/offline status for users
- Update presence when users connect/disconnect
- Add green/gray indicator dots next to usernames

Fixes #123
```

## Development Setup

### Prerequisites

- **Go 1.21+** - [Install Go](https://golang.org/dl/)
- **Git** - [Install Git](https://git-scm.com/)
- **Modern web browser** - Chrome, Firefox, Safari, or Edge

### Setup Steps

1. **Fork the repository** on GitHub

2. **Clone your fork**
   ```bash
   git clone https://github.com/YOUR_USERNAME/go-chatapp-ai.git
   cd go-chatapp-ai
   ```

3. **Add upstream remote**
   ```bash
   git remote add upstream https://github.com/yuis-ice/go-chatapp-ai.git
   ```

4. **Install dependencies**
   ```bash
   go mod download
   ```

5. **Run the development server**
   ```bash
   go run main.go
   ```

6. **Open your browser** to `http://localhost:8080`

### Testing Your Changes

```bash
# Run all tests
go test ./...

# Run tests with coverage
go test -cover ./...

# Format code
go fmt ./...

# Vet code for issues
go vet ./...
```

### Keeping Your Fork Updated

```bash
# Fetch upstream changes
git fetch upstream

# Switch to main branch
git checkout main

# Merge upstream changes
git merge upstream/main

# Push updated main to your fork
git push origin main
```

## Pull Request Process

1. **Create a feature branch** from `main`
   ```bash
   git checkout -b feature/amazing-feature
   ```

2. **Make your changes** following the style guidelines

3. **Test your changes** thoroughly

4. **Commit your changes** with clear commit messages

5. **Push your branch** to your fork
   ```bash
   git push origin feature/amazing-feature
   ```

6. **Create a Pull Request** on GitHub
   - Use the provided PR template
   - Provide a clear description of changes
   - Link to any related issues
   - Include screenshots if applicable

7. **Respond to feedback** and make requested changes

8. **Celebrate!** 🎉 Your contribution will be reviewed and merged

### Pull Request Guidelines

- **One feature per PR** - Keep PRs focused and manageable
- **Update documentation** - Include relevant documentation updates
- **Add tests** - Include tests for new functionality
- **Follow conventions** - Maintain consistency with existing code
- **Be responsive** - Address review feedback promptly

## 🛡️ Contributor License Agreement (CLA)

By submitting a pull request or contribution, you agree to the following:

> You grant the project founder a **non-exclusive, irrevocable, worldwide, royalty-free license** to use, modify, sublicense, and relicense your contribution, including the right to incorporate it into dual-licensed or commercial versions of the project.

This ensures that the project can grow sustainably while preserving creator rights.

If you are contributing on behalf of a company or organization, please contact us in advance.

### Why We Need a CLA

- **Legal clarity** - Ensures we have the right to distribute your contributions
- **Future flexibility** - Allows for license changes if needed for project sustainability
- **Protection** - Protects both contributors and the project from legal issues
- **Open source sustainability** - Enables various distribution and commercialization models

### What This Means for You

- ✅ Your contributions remain open source under the current license
- ✅ You retain copyright to your contributions
- ✅ You can still use your contributions in your own projects
- ✅ The project gains the flexibility to evolve its licensing model
- ✅ Your contributions are protected and properly attributed

## 📞 Getting Help

If you need help with contributing:

- 💬 [Start a Discussion](https://github.com/yuis-ice/go-chatapp-ai/discussions)
- 📧 Email: [jobs.fumiya@pm.me](mailto:jobs.fumiya@pm.me)
- 📖 Read the [Documentation](README.md)

## Recognition

Contributors who make significant contributions may be:

- Added to the README acknowledgments
- Invited to be project collaborators
- Given special recognition in release notes
- Featured in project announcements

---

**Thank you for contributing to Go Real-time Chat App! 🚀**

Your contributions make this project better for everyone in the community.