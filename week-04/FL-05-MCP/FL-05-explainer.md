# FL-05 — Agent Concepts and MCP Basics

**Name:** Millyanne Wanjala  
**Assignment:** FL-05 — Agent Concepts and MCP Basics  
**Track:** General AI Fluency  
**Week:** 4  
**Date:** August 2026

---

## 1. What Is an Agent?

An AI agent is a software program that can interact with its environment,
collect data and use that data to perform self-directed tasks that meet
predetermined goals.

The difference between an agent and a normal chatbot is their 
complexity, personalisation and adaptability.
Unlike chatbots, agentic AI can perform multi-step tasks, adapt to user 
preferences and learn over time, making them flexible. 
An agent is not limited to generating text from the information already
available in the conversation. An agent can interact with external
systems through tools and can use the results of those actions to decide
what to do next.

For example, an agent working on a software project could inspect files,
search documentation, run tests, identify a problem, and then decide
which additional action is necessary.

---

## 2. Workflow vs Agent

A workflow is a predefined sequence of steps. Each step is designed in
advance, and the system generally follows the sequence provided by the
developer.

An agent is more dynamic. Instead of following only a fixed sequence,
it can decide which tools to use, interpret the results, and determine
What action should occur next based on the current state of the task?

A simple way to describe the difference is:

**Workflow:**

Research → Extract → Synthesize → Draft → Review

**Agent:**

Goal → Decide what information is needed → Use tools → Inspect results →
Decide next action → Continue until the goal is achieved

A workflow can therefore use AI without necessarily being an agent.

---

## 3. Classification of My FL-04 Pipeline

I classify my FL-04 pipeline as a **workflow**, rather than an agent.

My FL-04 pipeline follows a planned sequence:

1. Extract information.
2. Synthesize the information.
3. Draft an output.
4. Review the output.

The steps are predetermined and the AI does not independently decide
which tools to use or whether another research step is required.

Although AI is involved in the process, the overall structure is still
a defined workflow.

---

## 4. What Is MCP?

MCP stands for **Model Context Protocol**. It is a standard that allows
AI applications to connect to external tools and sources of information.

Instead of building a separate custom integration for every AI model
and every external service, MCP provides a common way for an AI client
to communicate with MCP servers.

In my implementation, VS Code acts as the MCP client and a local
filesystem MCP server provides access to files in my demonstration
directory.

The architecture is:

VS Code Agent → MCP → Filesystem MCP Server → Local Files

This allowed the AI agent to access information from files that were
stored on my local machine.

---

## 5. MCP Primitives

MCP provides three important primitives: **tools, resources, and
prompts**.

### Tools

Tools are actions that an AI model can invoke.

In my filesystem MCP server, examples included:

- `list_directory`
- `read_text_file`
- `read_multiple_files`
- `search_files`
- `get_file_info`

I used the filesystem tools to list directories and retrieve file
contents.

### Resources

Resources represent information that an MCP server can make available
to the AI application.

In my example, the local project files acted as the information that
the filesystem server exposed to the AI through its filesystem
capabilities.

### Prompts

Prompts are reusable instructions that can be provided through an MCP
server to guide how a model performs a particular task.

The important distinction is that MCP is not itself an AI model.
It provides a standardized connection between an AI client and
external capabilities.

---

## 6. My MCP Implementation

For this assignment, I connected VS Code to a local filesystem MCP
server.

The server was configured to access:

`/home/clear/FL-05-MCP/demo-files`

The directory contains three demonstration files:

- `project.md`
- `tasks.md`
- `requirements.md`

The MCP server exposed filesystem tools to the VS Code Agent.

I verified that the server was working because VS Code reported that
the filesystem MCP server was running and that it had discovered
multiple tools.

---

## 7. Evidence of MCP Tool Use

### Task 1 — List Directory

I asked the agent to use the MCP filesystem server to list the contents
of the `demo-files` directory.

The MCP tool returned:

- `project.md`
- `requirements.md`
- `tasks.md`

<img width="1366" height="728" alt="2026-08-14 (4)" src="https://github.com/user-attachments/assets/4b908c87-a497-4678-aa3b-ed743ffc6876" />

This demonstrates that the agent used an MCP filesystem tool to inspect
the local directory.

---

### Task 2 — Read a File

I asked the agent to use the `read_text_file` MCP tool to retrieve
`project.md` and then summarize its contents.

<img width="1366" height="728" alt="2026-08-14 (2)" src="https://github.com/user-attachments/assets/32f04e24-788c-41bf-8b7b-e49a4f57ee8e" />

This demonstrates an MCP tool retrieving information from a local file
and passing the result back to the AI for processing.

---

### Task 3 — Read Multiple Files

I asked the agent to use the `read_multiple_files` MCP tool to retrieve
`project.md`, `tasks.md`, and `requirements.md`.

The agent then analyzed the retrieved information and recommended the
most important development task.

<img width="1366" height="728" alt="2026-08-14 (3)" src="https://github.com/user-attachments/assets/015ba6a4-e846-423e-849e-eff75cc5fc32" />

This demonstrates that the agent can retrieve information from multiple
external files and use the results in its reasoning.

---
### Proof of Tool Use

In each task, the agent could access local files not included in the conversation. This demonstrates that the agent used MCP tools (`list_directory`, `read_text_file`, `read_multiple_files`) to retrieve information from outside its context window, which ordinary chat cannot do.

---

## 8. What Would Make My FL-04 Workflow an Agent?

My FL-04 workflow would need to become more autonomous.

Currently, the research process follows a predefined sequence:

Research → Extract → Synthesize → Draft → Review

To turn it into an agent, I would give the system a goal instead of
only giving it a fixed sequence.

For example, the goal could be:

"Produce a reliable research summary about a given topic."

The agent could then decide whether it has enough information, search
for additional sources when necessary, inspect the results, identify
missing information, and continue researching before producing the
final summary.

The agent would therefore be able to choose actions based on the
results it observes rather than simply executing a fixed sequence.

---

## 9. Proposed Agent Upgrade

One concrete upgrade for my FL-04 pipeline would be an **automatic
research expansion agent**.

The agent would initially research a topic and evaluate whether the
available information is sufficient. If important information is
missing, it could use an MCP search or research tool to obtain
additional sources.

The loop would be:

Goal → Research → Evaluate information → Need more information? →
Research again → Synthesize → Review → Final output

This would make the system more agent-like because it would decide
whether another action was necessary instead of always following the
same fixed number of steps.

---

## 10. Conclusion

This assignment helped me distinguish between using AI in a workflow
and building an agent that can make decisions and use tools.

I also learned that MCP is a standard connection layer between an AI
client and external capabilities. My filesystem demonstration showed
that an AI agent can use MCP tools to access local information that
would not be available through ordinary chat alone.

The key lesson for me is that an agent is not simply a chatbot with a
different name. The important characteristics are goal-directed
decision-making, tool use, observation of results, and ability to
determine what action should happen next.
