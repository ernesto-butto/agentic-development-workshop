# PRP Framework Quick Start Workshop

Get hands-on with the PRP Framework in 30 minutes using a real Angular + Node.js + MongoDB project.

## Prerequisites

- Node.js (v16+)
- Docker
- Git
- An AI coding agent (Claude Code, Gemini CLI, etc.)

## Step 1: Setup Project (10 min)

Choose either **Option A** (using your AI agent) or **Option B** (manual setup):

### Option A: Setup with AI Agent (Recommended)

Ask your AI coding agent. These are the prompts I use with Claude Code. It only took this prompt to get everything set up: 

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

### Verify Everything Works

You should have:
- MongoDB running in Docker on port 27017
- Node.js backend on http://localhost:8080
- Angular frontend on http://localhost:8081

Test it: Open http://localhost:8081 in your browser and try creating a tutorial.

## Step 2: Create Project Context File (5 min)

Create a context file for your AI agent:

**For Claude Code:** Create `.claude/CLAUDE.md`
**For Gemini CLI:** Create `.gemini/GEMINI.md`

Ask your AI agent:

```
Create a [CLAUDE.md / GEMINI.md] file for this project.
Include project structure, tech stack, and key conventions.
```

## Step 3: Install PRP Framework (10 min)

### Clone the PRP Repository

```bash
git clone https://github.com/Wirasm/PRPs-agentic-eng.git
```

### Review the PRP Commands

Read these to understand the workflow:
- [The Project Foreman (/prp-task-create)](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#-the-project-foreman-prp-task-create) - Creates implementation plans
- [The Specialist Crew (/prp-task-execute)](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#-the-specialist-crew-prp-task-execute) - Executes the plan

### Copy PRP Commands to Your Project

**For Claude Code:**
```bash
cd angular-17-node-project
mkdir -p .claude/commands/prp-commands
cp ../PRPs-agentic-eng/.claude/commands/prp-commands/* .claude/commands/prp-commands/
```

**For Gemini CLI:**
```bash
cd angular-17-node-project
mkdir -p .gemini/commands/prp-commands
# Copy and adapt commands according to: https://cloud.google.com/blog/topics/developers-practitioners/gemini-cli-custom-slash-commands
```

Ask your AI agent to help adapt if needed:

```
I need to adapt these Claude Code slash commands to [your agent format].
Can you help me convert them?
```

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

Refer to [The Step-by-Step Process](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#the-step-by-step-process-) for detailed guidance.

## Next Steps (Optional)

### Try More Exercises

1. **Add Search by Category** - Filter tutorials by category
2. **Add Rating System** - Let users rate tutorials 1-5 stars
3. **Try `/prp-spec-create` → `/prp-spec-execute`** - For more complex features

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

---

**Questions?** Ask your AI coding agent for help. That's what they're there for!
