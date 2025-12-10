# PRP Framework Quick Start Workshop

Get hands-on with the PRP Framework in 30 minutes using Gemini or another agentic tool, using a real Angular + Node.js + MongoDB project.

## Prerequisites

- Node.js (v16+)
- Docker
- Git
- An AI coding agent (Gemini CLI, Codex CLI, Cursor, Claude Code, etc... )

## Step 1: Setup Project (10 min)

We'll be working with the [Bezkoder Angular 17 + Node.js project](https://github.com/bezkoder/angular-17-node-project). This is a simple CRUD (Create, Read, Update, Delete) application for managing tutorials. It's deliberately simple so we can focus on learning the PRP framework rather than wrestling with complex application logic.

Choose either **Option A** (using your AI agent) or **Option B** (manual setup):

### Option A: Setup with AI Agent

⚠️ This path requires giving the agent access to the terminal, meaning running it with the yolo mode flag: ` gemini --yolo`, allows the AI to automatically execute actions and commands without user confirmation. 

If you still feel uncomfortable with this, then proceed to the Option B: manual setup to start building the confidence.  

These are the prompts I use with Claude Code. It only took this prompt to get everything set up: 

```
Can you checkout and start the server and client of this project locally?
https://github.com/bezkoder/angular-17-node-project/blob/master/README.md
```

When asked about the database, respond:

```
I do not have any of them, could you help me set up a docker container
with a MongoDB database so we can use the 1st option?
```

### Option B: Manual Setup

```bash
# Clone the repository
git clone https://github.com/bezkoder/angular-17-node-project.git
cd angular-17-node-project

# Start MongoDB in Docker
docker run -d \
  --name mongodb-bezkoder \
  -p 27017:27017 \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=password \
  mongo:latest

# Setup and start the backend
cd node-express-mongodb-server
npm install
# Edit app/config/db.config.js to match your MongoDB settings if needed
node server.js &

# Setup and start the frontend (in a new terminal)
cd ../angular-17-client
npm install
ng serve --port 8081 &
```

Detailed instructions in https://github.com/bezkoder/angular-17-node-project.git

### Verify Everything Works

You should have:
- MongoDB running in Docker on port 27017
- Node.js backend on http://localhost:8080
- Angular frontend on http://localhost:8081

Test it: Open http://localhost:8081 in your browser and try creating a tutorial.

## Step 2: Create Project Context File (5 min)

Create a context file for your AI agent:

**For Gemini CLI:** Create `GEMINI.md` at the rood folder.

- You can start by copying [this example](https://codelabs.developers.google.com/gemini-cli-hands-on#9), and adjusting it a bit

## Step 3: Install PRP Framework (10 min)

### Clone the PRP Repository and copy the contents

- See instructions in https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README.md
- It's ok to copy al files to a `.claude/` folder, we will move what we need and adjust it to a `.gemini/` folder later.


### Review the PRP Commands

From the PRP `README-for-DUMMIES` file in the PRP repo

Read these to understand the workflow:
- [The Project Foreman (/prp-task-create)](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#-the-project-foreman-prp-task-create) - Creates implementation plans
- [The Specialist Crew (/prp-task-execute)](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#-the-specialist-crew-prp-task-execute) - Executes the plan

### Copy PRP Commands to Your Project

- Review these two slash commands in your project, should be inside `.claude/commands/prp-commands`
- Copy them to the gemini folder e.g. `.gemini/commands/prp-commands` (Create the path if it does not exist)
- Adapt the command format to the agentic tool, in this case to Gemini: See [Gemini Custom Slash Command blog post](https://cloud.google.com/blog/topics/developers-practitioners/gemini-cli-custom-slash-commands)
- Tip: You can try and ask your AI agent to do this adaptation for you, giving it the documentation


## Step 4: Try the PRP Workflow (15 min)

### Exercise: Add a Category Field

**Step 1 - Plan:** Run `/prp-task-create` with:

```
Add a "category" field to tutorials:
- Required string field in the database model
- Display in tutorial list and detail views
- Editable when creating/updating tutorials
- Add validation
```

**Step 2 - Review:** Read the generated plan carefully. Does it cover:
- Database model changes?
- Backend API updates?
- Frontend form and display changes?

**Step 3 - Execute:** If the plan looks good, run:

```
/prp-task-execute
```

**Step 4 - Test:**
- Restart your servers
- Create a new tutorial with a category
- Verify it displays correctly

### Key Workflow

```
Describe task → /prp-task-create → Review plan → /prp-task-execute → Test
```

Refer to [The Step-by-Step Process](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#the-step-by-step-process-) to refresh the workflow and commands.

## Next Steps (Optional)

### Try More Exercises

- **Try `/prp-spec-create` → `/prp-spec-execute`** - For more complex features

### Learn More

- [PRP README for DUMMIES](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md) - Complete framework guide
- [Common Mistakes to Avoid](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#common-mistakes-dont-do-these-)
- [Command Chaining](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#-command-chaining)

## Quick Reference

### Useful Docker Commands

```bash
docker ps                      # Check if MongoDB is running
docker stop mongodb-bezkoder   # Stop MongoDB
docker start mongodb-bezkoder  # Start MongoDB
docker logs mongodb-bezkoder   # View logs
```

### Project Structure

```
angular-17-node-project/
├── angular-17-client/          # Frontend (Angular)
├── node-express-mongodb-server/ # Backend (Node.js + Express)
```

### Key Links

- [Project Repository](https://github.com/bezkoder/angular-17-node-project)
- [PRP Framework](https://github.com/Wirasm/PRPs-agentic-eng)
- [Gemini Custom Slash Commands](https://cloud.google.com/blog/topics/developers-practitioners/gemini-cli-custom-slash-commands)
