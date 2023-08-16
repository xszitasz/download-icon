# Vue DownloadIcon Component

A Vue.js project that demonstrates a reusable component for downloading PDF and TXT files.

## Project Structure

- `src/App.vue`: The main Vue component that uses the `DownloadIcon` component.
- `src/components/DownloadIcon.vue`: The reusable component responsible for handling file downloads.
- `src/main.js`: The entry point of the Vue application.

## Getting Started

1. Clone the repository:

```bash
git clone https://github.com/xszitasz/download-icon.git
```

2. Navigate to the project directory:
```bash
cd vue-download-icon
```

3. Install dependencies:
```bash
npm install
```

4. Start the development server:
```bash
npm run serve
```

5. Open your browser and visit 'http://localhost:8080' to see the app in action.

## Installed NPM Libraries
- `axios`: Used for making HTTP requests to fetch file content from URLs.
- `@fortawesome/fontawesome-free`: Provides a collection of font icons for use in the application.
- `vue`: The core Vue.js framework.

## Usage
The 'DownloadIcon' component allows you to easily create download links for different file types. Simply include the component in your Vue application and provide the necessary props.

## 'DownloadIcon' Component
The 'DownloadIcon' component is responsible for handling the download functionality. It accepts the following props:

- `fileType`: The type of the file to download (e.g., 'pdf', 'txt').
- `file`: The URL of the file to download.
- `docName`: The name of the document to display.
  
For more details, refer to the DownloadIcon.vue file in the src/components directory.
