# CRM Lead Qualifier Agent

## Goal

To develop an AI agent that automatically enriches a new sales lead (identified by an email address) by gathering publicly available company information, checking for prior engagement in the internal CRM, and assigning a preliminary qualification score.

## Context

Sales representatives often spend valuable time manually researching leads and cross-referencing internal systems before a discovery call. This process is slow, inconsistent, and often leads to a poorly prepared first interaction.

## Agent Functionality

The agent must be able to:

1. Extract Domain: Take the email address and extract the company domain name (e.g., jane@acmecorp.com → acmecorp.com).

2. Enrich Company Data: Use the domain to look up (simulated) company details like industry, size, and annual revenue.

3. Check CRM History: Search the internal (simulated) CRM for any past contact or notes associated with the lead's email.

4. Calculate Lead Score: Synthesize all gathered data to assign a qualitative priority score (e.g., High, Medium, Low).

5. Final Summary: Present a concise, actionable summary of all findings to the sales representative.

# Technical Implementation

We will use the OpenAI client's Function Calling capability to define and execute the necessary business logic tools in a structured loop.

## What is function calling?

Function calling is the mechanism that bridges the gap between an AI model (which is just a text generator) and your actual code (which can perform actions).

Think of the Large Language Model (LLM) as a very smart receptionist. It understands what people want, but it doesn't have the keys to the file cabinet or the ability to make phone calls itself.

Function calling gives the receptionist a "menu" of services it can request from the back office (your code).

![](https://cdn.openai.com/API/docs/images/function-calling-diagram-steps.png)

### The Core Concept

* You provide the tools: You tell the model, "I have a function called get_weather(city) that takes a city name as an argument."

* The model "thinks": If a user asks, "What's the weather in Tokyo?", the model recognizes that your tool can solve this.

* The model outputs JSON (not text): Instead of replying to the user, the model pauses and gives you a structured request: {"function": "get_weather", "arguments": {"city": "Tokyo"}}.

* You execute: Your code sees this request, runs the actual Python function, and gets the result (e.g., "Sunny, 25°C").

* The model finishes: You feed that result back to the model, and it writes the final natural language answer: "It is currently sunny and 25 degrees in Tokyo."

### Why is this powerful?

Without function calling, LLMs are isolated text predictors—they can't "do" anything. With function calling, they become agents.

* **Structured Data Extraction**: Instead of hoping the model formats data correctly, you force it to output clean JSON that fits your database schema.

* **Connecting to the World**: It allows the AI to browse the web, query databases, send emails, or control software, merely by defining those actions as "functions."
