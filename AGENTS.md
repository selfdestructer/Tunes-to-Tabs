# AI Agent Instructions for Music Tab Generation Project

This document provides instructions for AI agents working on this repository. The goal is to build a Node.js application that can both generate guitar tabs from uploaded music files and generate music from uploaded guitar tabs.

## Core Technologies

*   **Backend:** Node.js, Express, TypeScript
*   **Frontend:** React
*   **Cloud Provider:** Google Cloud Platform (GCP)
*   **Core AI Model:**
    *   **Google Gemini 2.5 Pro:** For all AI-driven tasks, including audio analysis, tab generation, and music generation.

## Agent Workflow & Prompting Strategy

Your primary role is to implement the features for this application. Follow these workflows and prompting strategies.

### 1. Music-to-Tabs Conversion

1.  **User Upload:** The user uploads an audio file (e.g., .mp3, .wav) through the React frontend.
2.  **Tab Generation (Gemini):**
    *   The backend receives the audio file. Your task is to implement a pipeline that sends this audio directly to the Gemini 2.5 Pro model.
    *   The model will be responsible for analyzing the audio and generating the guitar tab in one step.
    *   **Prompt Example Idea:** "Analyze the provided audio file which contains a guitar performance. Transcribe the guitar part and generate a standard ASCII guitar tab for a 6-string guitar in standard tuning. Group the notes into measures based on a 4/4 time signature."
3.  **Display:** The generated tab is sent to the frontend to be displayed in an interactive viewer.

### 2. Tabs-to-Music Conversion (Reverse Operation)

This is a secondary, experimental feature.

1.  **User Upload:** The user uploads a guitar tab, either as plain text or in a structured format.
2.  **Tab Parsing (Gemini):**
    *   If the tab is unstructured text, use Gemini 2.5 Pro to parse it and convert it into a structured format (e.g., JSON).
    *   **Prompt Example Idea:** "Parse the following ASCII guitar tab. Convert it into a JSON object where each note has a 'string', 'fret', 'duration', and 'timing' attribute. Assume a 4/4 time signature and 120 bpm if not specified."
3.  **Music Generation (Gemini):**
    *   This is the experimental part. You will need to investigate the capabilities of Gemini 2.5 Pro for generating audio from a structured text or JSON representation.
    *   **Prompting Strategy:** The prompt to Gemini should include the structured note data and request the generation of an audio file.
    *   **Prompt Example Idea:** "Generate a realistic acoustic guitar audio performance from the following JSON data representing musical notes. Use a tempo of 120 bpm. Output the result as an MP3 file."
4.  **Playback:** The generated audio file is made available for the user to play back in the frontend.

## Frontend Development Guidelines

*   The initial focus is on building a landing page with specific, retro-themed UI elements as per the user's request.
*   **Landing Page:** Must have a parallax effect for the main taglines.
*   **File Upload:** Must be styled to look like an "old school" file uploader.
*   **Loading Animation:** Must mimic a classic Windows file transfer dialog.

## General Development Guidelines

*   Follow the phased development approach mentioned in `scout-prompt.md`.
*   Infrastructure configurations for GCP should be kept in a separate `/infrastructure` directory.
*   Prioritize creating a robust API between the frontend and backend.
*   Write unit and integration tests for all major functionality.
