# TruthLens

TruthLens helps you check factual claims in text against web sources or an uploaded document. Built with Next.js, React, TypeScript, and Tailwind CSS, it uses Google Gemini for claim extraction and analysis, and Exa for web search.

## Features

- Extract individual claims from text and check them against web sources.
- Review verdicts, explanations, and supporting source links.
- Upload a PDF, DOCX, or TXT file (up to 10 MB) and verify a claim against its contents.
- View document-based verdicts, confidence scores, and relevant excerpts.

## Run locally

You need Node.js and npm, a [Google Gemini API key](https://aistudio.google.com/app/apikey), and an [Exa API key](https://dashboard.exa.ai/api-keys) for web searches.

1. Clone the repository and install dependencies:

   ```sh
   git clone https://github.com/sharma23Mukul/truthlens.git
   cd truthlens
   npm ci
   ```

2. Copy `.env.example` to `.env.local` in the repository root and replace the placeholders:

   ```dotenv
   GOOGLE_GENERATIVE_AI_API_KEY=your_gemini_api_key
   EXA_API_KEY=your_exa_api_key
   ```

   Keep real API keys in `.env.local`, which is excluded from Git.

3. Start the development server:

   ```sh
   npm run dev
   ```

4. Open [localhost:3000](http://localhost:3000) for web-based fact checking, or [localhost:3000/verify-document](http://localhost:3000/verify-document) for document verification.

## Production

```sh
npm run build
npm start
```

When deploying, use the repository root as the application directory and configure the same environment variables in your hosting platform.

## Project structure

```text
app/             Pages, API routes, fonts, and global styles
components/      Fact-checking interfaces and shared UI components
lib/             Gemini API integration and utility functions
public/          Static images and icons
.env.example     Environment variable template
package.json     Dependencies and development scripts
```

## How it works

For web checks, Gemini extracts claims, Exa retrieves relevant sources, and Gemini analyzes the evidence. For document checks, the browser extracts text from the uploaded file and Gemini evaluates a claim against that text.

AI-generated verdicts can be incorrect. Review the cited sources and excerpts before relying on a result.
