---

# Chapter 01 - Introduction to Playwright

# Batch 3 of 5

> **Topic:** Understanding Playwright Architecture & Internal Working

---

# Table of Contents

1. Browser Automation Architecture
2. Components of Playwright
3. Playwright Internal Working
4. Browser Engines
5. Browser vs BrowserContext vs Page
6. Playwright Communication Model
7. Request Lifecycle
8. Why Playwright is Fast
9. Internal Flow of page.goto()
10. Internal Flow of page.click()
11. Interview Questions with Answers
12. Summary
13. Revision Notes

---

# 1. Browser Automation Architecture

Before Playwright, most automation tools followed a browser driver architecture.

Example:

```
Test Script
      │
      ▼
Selenium API
      │
      ▼
ChromeDriver
      │
      ▼
Chrome Browser
```

Problems:

- Separate driver management
- Version mismatch
- Additional network communication
- Extra maintenance

---

## Playwright Architecture

Playwright follows a modern architecture.

```
Your Test

      │

      ▼

Playwright Client Library

      │

      ▼

Browser Communication Channel

      │

      ▼

Browser Process

      │

      ▼

Browser Engine

      │

      ▼

Web Application
```

Instead of relying on WebDriver for every action, Playwright communicates with browser engines using browser-specific protocols, enabling reliable automation and modern features.

---

# 2. Components of Playwright

Playwright consists of several important components.

```
Playwright

│

├── Browser

├── BrowserContext

├── Page

├── Frame

├── Locator

├── APIRequestContext

├── Test Runner

├── Trace Viewer

└── Inspector
```

Each component has a specific responsibility.

We'll study every component in detail later.

---

# Browser

A Browser represents an actual browser process.

Examples:

- Chromium
- Firefox
- WebKit

Think of it as opening Chrome on your computer.

Example:

```typescript
const browser = await chromium.launch();
```

This launches a browser process.

---

# BrowserContext

A BrowserContext is an isolated browser session.

Each BrowserContext has its own:

- Cookies
- Local Storage
- Session Storage
- Cache
- Permissions

Think of BrowserContext as an Incognito window.

```
Browser

│

├── BrowserContext A

│        └── User A

│

├── BrowserContext B

│        └── User B

│

└── BrowserContext C

         └── Admin
```

This allows multiple independent users to exist inside one browser.

---

# Page

A Page represents a browser tab.

```
Browser

│

└── BrowserContext

        │

        ├── Page 1

        ├── Page 2

        └── Page 3
```

Example:

```typescript
const page = await context.newPage();
```

Every automation script eventually interacts with a Page.

---

# Frame

A Frame represents an HTML iframe.

Many websites embed content inside iframes.

Example:

```
Main Page

│

├── Header

├── Sidebar

├── Payment Frame

└── Advertisement Frame
```

Playwright can switch between frames using dedicated APIs.

---

# Locator

A Locator is Playwright's recommended way to find elements.

Example:

```typescript
page.getByRole("button", { name: "Login" });
```

Unlike older element handles, locators are evaluated when an action is performed, which helps them work reliably with dynamic pages.

---

# 3. Playwright Internal Working

Let's understand what happens when you execute:

```typescript
await page.click("#login");
```

Many beginners think Playwright immediately clicks the element.

That is not true.

Internally several operations happen first.

```
Your Code

↓

Locator Resolution

↓

Find Element

↓

Is Element Attached?

↓

Is Element Visible?

↓

Is Element Stable?

↓

Is Element Enabled?

↓

Can Receive Mouse Events?

↓

Scroll Into View

↓

Perform Click

↓

Wait For Completion
```

This entire sequence usually happens within milliseconds.

---

# Why Is This Important?

This is the primary reason Playwright tests are generally more stable than scripts that rely heavily on explicit waits.

Instead of blindly clicking,

Playwright first verifies whether the element is actually ready.

---

# 4. Browser Engines

Playwright supports three browser engines.

```
Playwright

│

├── Chromium

├── Firefox

└── WebKit
```

Notice:

Playwright supports browser **engines**.

Many browsers are built on Chromium.

Example:

Chromium

↓

Google Chrome

↓

Microsoft Edge

↓

Brave

↓

Opera

One automation API can therefore cover multiple Chromium-based browsers.

---

# 5. Browser vs BrowserContext vs Page

This is one of the most commonly asked interview questions.

```
Browser

↓

BrowserContext

↓

Page
```

Think of it like a hotel.

Browser

↓

Entire Hotel

BrowserContext

↓

Individual Room

Page

↓

Person inside the room

Every room is isolated.

Guests cannot access each other's belongings.

Similarly,

BrowserContexts cannot share:

- Cookies
- Session Storage
- Local Storage

unless you explicitly configure sharing.

---

# 6. Communication Model

How does your code reach Chrome?

```
TypeScript Test

↓

Playwright Client

↓

Communication Protocol

↓

Browser

↓

Rendering Engine

↓

DOM

↓

User Interface
```

Every action follows this communication pipeline.

---

# 7. Request Lifecycle

Example:

```typescript
await page.goto("https://example.com");
```

Internal lifecycle:

```
page.goto()

↓

Create Navigation Request

↓

Browser Sends HTTP Request

↓

Server Responds

↓

Browser Parses HTML

↓

Downloads CSS

↓

Downloads JavaScript

↓

Build DOM

↓

Execute Scripts

↓

Render Page

↓

Playwright Waits

↓

Navigation Completes
```

Notice:

Playwright does not simply send a URL.

It waits for the navigation state according to its navigation and actionability rules before continuing.

---

# 8. Why Playwright Is Fast

Several design choices contribute to Playwright's performance.

- Efficient browser communication
- Automatic waiting instead of fixed delays
- Parallel execution
- Browser Context reuse
- Smart locator resolution
- Reduced synchronization code

---

# 9. Internal Flow of page.goto()

```
page.goto()

↓

Validate URL

↓

Send Navigation Command

↓

Browser Starts Navigation

↓

HTTP Request

↓

Receive Response

↓

Create DOM

↓

Load Resources

↓

Execute JavaScript

↓

Render Page

↓

Playwright Waits

↓

Return Control To Test
```

---

# 10. Internal Flow of page.click()

```
Locate Element

↓

Retry If Needed

↓

Wait Until Visible

↓

Wait Until Stable

↓

Scroll Into View

↓

Perform Click

↓

Wait For Navigation (if applicable)

↓

Continue Execution
```

---

# Real Project Example

Imagine a login page.

```
Username

Password

Login Button
```

Your code:

```typescript
await page.getByRole("button", { name: "Login" }).click();
```

Behind the scenes:

- Playwright searches for the button.
- Confirms it is attached to the DOM.
- Ensures it is visible.
- Verifies it is enabled.
- Scrolls it into view if necessary.
- Clicks it.
- Waits for any triggered navigation.

All of this happens automatically.

---

# Interview Questions with Answers

## Question 7

### What is the difference between Browser, BrowserContext, and Page?

### Answer

A **Browser** represents the browser process.

A **BrowserContext** is an isolated browser session within that process.

A **Page** represents a single tab inside a BrowserContext.

Think of it as:

- Browser = Hotel
- BrowserContext = Room
- Page = Person inside the room

---

### Interviewer's Expectation

The interviewer wants to verify that you understand Playwright's isolation model.

Many candidates confuse Browser with BrowserContext.

---

## Question 8

### Why are BrowserContexts important?

### Answer

BrowserContexts allow multiple isolated user sessions to run inside a single browser process.

Each context maintains separate:

- Cookies
- Local Storage
- Session Storage
- Cache

This enables efficient parallel testing and realistic multi-user scenarios without launching multiple browser instances.

---

## Question 9

### Why is Playwright considered more reliable than many traditional automation approaches?

### Answer

Playwright performs automatic waiting and actionability checks before interacting with elements. It also provides isolated browser contexts, robust locator APIs, and consistent cross-browser behavior, all of which help reduce flaky tests and simplify automation code.

---

# Summary

In this batch, you learned:

- The high-level architecture of Playwright.
- The roles of Browser, BrowserContext, and Page.
- How Playwright communicates with browsers.
- The internal lifecycle of navigation and click actions.
- Why Playwright's architecture contributes to reliable automation.

---

# Revision Notes

- Browser = Browser process.
- BrowserContext = Isolated browser session.
- Page = Browser tab.
- Locators are re-evaluated before actions.
- Playwright performs actionability checks before interacting with elements.
- Automatic waiting is a core feature that improves reliability.
- Understanding the internal request flow helps with debugging and interview discussions.