# Planning Monk

A zero-code agent that already lives in Claude. A planning assistant that is nothing more than a chat with a job description, walked through your projects on whatever cadence you want. No code, no build, no maintenance.

## What it does
It takes a brain dump from you, checks your email, calendar, meeting notes and whatever else you point it at via Claude connectors or drop in as project files, walks through your active projects to see where each was left off, and hands you one briefing plus a place to start. Then it gets out of the way.

## Setup (about five minutes)

1. **Make a project** called "Planning Monk" in your AI tool of choice. This is written for Claude Projects. When creating the project:
   - **Name:** Planning Monk
   - **Description:** "Planning assistant that walks my projects, email, meeting notes, and calendar each session, plus any other sources I point it to."
2. **Paste the instruction doc** (`planning-monk-generic.md`) into that project's custom instructions (found in project settings, not the description field). This is what makes every chat started in the project behave as the Monk from the first message.
3. **Connect your tools.** It needs to reach your email and your meeting notes. Works with whatever your AI supports. I use Gmail and Granola. Office 365 plug-ins may also pull in Teams. Use what you've got. A calendar connection is a nice-to-have, not required.

## The ritual

1. **Start a fresh chat** in the project each session. Fresh chat, not one long-running thread, so the context budget stays clean and the Monk shows up with present eyes.
2. **It reads the last brief.** If there's a previous brief in the project (a dated markdown file from the last session), the Monk reads it to know where things stood. Light context, not an audit.
3. **It asks for your brain dump.** Tell it the date and what's on your plate and what matters right now. If you forget the date, it'll ask. It needs the date to make sense of what's recent across your email, meetings, and project chats.
4. **It checks email and meeting notes** against your dump, confirming what you flagged and filling in what you missed.
5. **The project lap, the key move.** This is the part that makes it work. One at a time, move the chat into each of your active projects. At each stop, tell the Monk where you put it: "I moved you to [Project Name]." It immediately searches that project's recent chats, gives you a short readout of what's active and open, and asks if you want to dig into anything or move on. When you're ready for the next stop, it says "Move me and tell me where I am." It keeps everything it has gathered as it travels, so by the end it has walked your whole world in a single conversation.
6. **It comes back with one brief** and asks where you want to start.
7. **Save the brief.** The Monk writes a dated markdown file at the end of the session. Click "Add to project" on the artifact so next session's Monk can see where things stood.

## How the memory works
Each session ends with a dated brief written as a markdown artifact. You add it to the project with one click (the "Add to project" option in the artifact dropdown). Next session, the fresh Monk reads the most recent brief before starting rounds. That's the whole memory layer. No database, no external tools, no code. Old briefs accumulate in the project but they're tiny. Prune monthly if you want, or just let them stack.

## Why the lap works this way
Project chat history is usually walled off per project, so a chat can only see the project it is currently in. Moving the one chat from project to project lets it read each one in turn while carrying the running context forward. That manual hop, about thirty seconds per project, is the whole orchestration. No code doing it, just you walking the Monk around.

## The travel card
Project instructions don't follow a chat when it moves to a different project. That means the Monk loses its job description the moment it leaves home. To fix this, the Monk writes a compact version of its behavioral rules into the conversation before the first move. This "travel card" lives in the conversation history, which does travel everywhere the chat goes. It's the thing that keeps the Monk acting like a Monk instead of reverting to a default assistant at each stop.

## Cadence
Use it however it fits. Weekly on Monday mornings is the natural starting point. Some people will want it daily. Others might do a Monday planning pass and a Friday retro. The instructions are cadence-agnostic so you can find your rhythm without editing anything.

## How many projects to visit
You don't have to walk every project every session. The Monk asks how many stops you're planning so it can calibrate depth. Two or three projects means deeper readouts at each stop. Five or six means high-level only. Prioritize the projects you know you'll be working on if you want detail. Walk all of them if you just want a landscape view. The Monk adjusts its fidelity automatically based on the number you give it. This is context window management disguised as one question.

## Model notes
Use Opus 4.6 or higher. Tested on Claude Opus 4.6. Sonnet tends to get conversational when it should be scanning and reporting. The Monk follows procedural instructions precisely, and Opus is better at that than Sonnet. If you're on Sonnet and the Monk starts asking questions instead of scanning, or starts working on things instead of just reporting, switch to Opus.

## The point
People are building elaborate chief-of-staff agents to do this. This does the same job with a page of instructions and a chat that makes rounds. Agents live on a wide spectrum now, from this to fully autonomous multi-agent systems. This is the far simple end, and for a planning pass, the far simple end is enough.
