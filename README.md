# AI Web Summarizer Chrome Extension

An AI-powered Chrome Extension that extracts content from the currently active webpage and generates a concise summary using an open-source NLP model. The extension is built using **React.js**, **JavaScript**, **Chrome Extension Manifest V3**, and the **Hugging Face Inference API**.

---

## Features

* Extracts text from the currently active webpage.
* Generates AI-powered summaries using an open-source model.
* Built with Chrome Extension Manifest V3 architecture.
* React-based popup UI.
* Uses Chrome Tabs API to access active tab information.
* Uses Chrome Storage API for local persistence.
* Implements message passing between popup, content scripts, and background service worker.
* Lightweight and easy to extend with other AI models.

---

## Tech Stack

### Frontend

* React.js
* JavaScript
* CSS

### Chrome Extension APIs

* Chrome Tabs API
* Chrome Storage API
* Chrome Runtime Messaging API

### AI Model

* Hugging Face Inference API
* facebook/bart-large-cnn

### Architecture

* Manifest V3
* Service Worker
* Content Scripts

---

## Project Structure

```text
ai-web-summarizer/
│
├── public/
│   ├── manifest.json
│   ├── background.js
│   ├── contentScript.js
│   └── icons/
│       └── icon128.png
│
├── src/
│   ├── App.js
│   ├── App.css
│   ├── index.js
│   │
│   └── services/
│       └── api.js
│
├── .env
├── package.json
└── README.md
```

---

## System Architecture

```text
React Popup UI
       │
       ▼
Chrome Tabs API
       │
       ▼
Content Script
(Extract Webpage Text)
       │
       ▼
Chrome Message Passing
       │
       ▼
Background Service Worker
       │
       ▼
Hugging Face API
(BART-Large-CNN)
       │
       ▼
Generated Summary
       │
       ▼
React UI Display
```

---

## Installation

### Clone Repository

```bash
git clone https://github.com/your-username/ai-web-summarizer.git

cd ai-web-summarizer
```

### Install Dependencies

```bash
npm install
```

---

## Environment Variables

Create a `.env` file in the root directory.

```env
REACT_APP_HF_API_KEY=YOUR_HUGGINGFACE_API_KEY
```

Generate a free API key from Hugging Face.

---

## Running the Project

### Start Development Server

```bash
npm start
```

### Create Production Build

```bash
npm run build
```

---

## Loading the Extension in Chrome

1. Open Chrome.
2. Navigate to:

```text
chrome://extensions
```

3. Enable **Developer Mode**.
4. Click **Load unpacked**.
5. Select the generated `build` folder.
6. The extension will appear in the Chrome toolbar.

---

## Workflow

### Step 1: Open Any Webpage

The user navigates to any webpage.

### Step 2: Click Extension Icon

The React popup UI opens.

### Step 3: Extract Webpage Content

The content script extracts visible text from the webpage.

### Step 4: Generate Summary

The extracted content is sent to the Hugging Face API.

### Step 5: Display Results

The generated summary is displayed inside the extension popup.

---

## Key Chrome APIs Used

### Chrome Tabs API

Used to identify the currently active tab.

```javascript
chrome.tabs.query({
  active: true,
  currentWindow: true
});
```

### Chrome Runtime Messaging

Used for communication between popup and content scripts.

```javascript
chrome.tabs.sendMessage(
  tabId,
  { action: "GET_PAGE_TEXT" }
);
```

### Chrome Storage API

Used for storing generated summaries.

```javascript
chrome.storage.local.set({
  summary: summaryText
});
```

---

## Future Enhancements

* Multi-language summarization
* Copy summary to clipboard
* Download summary as PDF
* Summary history management
* Support for multiple AI models
* Dark mode
* Article-focused extraction instead of full page extraction


