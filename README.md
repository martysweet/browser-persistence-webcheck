# browser-persistence-webcheck

A simple webpage which mutates client state. Used for testing Session persistence.

## Overview

This tool provides a straightforward way to test browser session persistence and cookie functionality across different browser environments. It's particularly useful for validating that headless browsers and API-driven browser automation tools properly maintain state between page interactions.

## Why Use This Tool?

This repository is especially valuable for testing browser persistence in:

- **Headless browsers**: Verify that cookies and session state persist correctly when running browsers in headless mode
- **API-driven browsers**: Test persistence in programmatic browser environments like [headless-render-api](https://github.com/martysweet/headless-render-api)
- **Automated testing**: Ensure your browser automation scripts properly handle session state
- **Cross-browser compatibility**: Validate that different browser engines handle persistence consistently

The tool creates persistent cookies on first visit and maintains a counter that increments with each button click, making it easy to verify that state is properly maintained across page reloads, browser restarts, or different automation scenarios.

## Usage

### Live Demo

The application is automatically deployed to GitHub Pages: [https://martysweet.github.io/browser-persistence-webcheck/](https://martysweet.github.io/browser-persistence-webcheck/)

[![Deploy to GitHub Pages](https://github.com/martysweet/browser-persistence-webcheck/actions/workflows/deploy.yml/badge.svg)](https://github.com/martysweet/browser-persistence-webcheck/actions/workflows/deploy.yml)

### Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/martysweet/browser-persistence-webcheck.git
   cd browser-persistence-webcheck
   ```

2. Start a local web server:
   ```bash
   # Using Python 3
   python3 -m http.server 8000
   
   # Using Node.js
   npx http-server
   
   # Using PHP
   php -S localhost:8000
   ```

3. Open your browser and navigate to `http://localhost:8000`

### Testing Browser Persistence

1. **Initial Visit**: When you first load the page, it will create cookies with the current timestamp and set the counter to 0.

   ![Initial page load with counter at 0](https://github.com/user-attachments/assets/4c642e85-5b29-4a22-a101-5315cc4c3457)

2. **Increment Counter**: Click the "Increment Counter" button to increase the counter value. Each click updates both the counter and the "Last Updated" timestamp.

   ![After incrementing the counter](https://github.com/user-attachments/assets/1404a1ed-5826-432f-82f9-f6a77506afd3)

3. **Test Persistence**: 
   - Reload the page to verify the counter value persists
   - Close and reopen the browser to test long-term cookie persistence
   - Use the "Reset Counter" button to reset the counter and update the creation timestamp

### What Gets Tested

The application tests the following browser persistence features:

- **Cookie Creation**: Creates persistent cookies with a 1-year expiration
- **State Persistence**: Maintains counter value across page reloads
- **Timestamp Tracking**: Records when cookies were created and last updated
- **Interactive Updates**: Real-time UI updates that reflect current state

### API Usage

For headless browser testing or automation, you can interact with the page programmatically:

```javascript
// Check if cookies are being set
console.log(document.cookie);

// Simulate button clicks
document.querySelector('button[onclick="incrementCounter()"]').click();

// Verify counter updates
const counterValue = document.getElementById('counterValue').textContent;
console.log('Current counter:', counterValue);
```

## Deployment

The application is automatically deployed to GitHub Pages using GitHub Actions. The deployment workflow is triggered on every push to the main branch.

**GitHub Actions Workflow**: [View Deployment Status](https://github.com/martysweet/browser-persistence-webcheck/actions/workflows/deploy.yml)

## License

MIT License - see [LICENSE](LICENSE) file for details.
