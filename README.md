# MindSpace: Exam Wellness Companion

## 🎯 Chosen Vertical
**Mental Health & Wellness in Education (EdTech)**
Specifically tailored for Gen Z and late Millennial students preparing for high-stakes, high-pressure exams (e.g., JEE, NEET, UPSC, CAT). 

## 🧠 Approach and Logic
The journey of preparing for competitive exams is often isolating, extremely stressful, and emotionally draining. Generic wellness apps or clinical meditation apps failed to capture the nuances of "study burnout" or "academic anxiety." 

**Core Philosophies:**
1. **Empathy through Pop Culture:** We built the engine persona to act as an empathetic peer rather than a clinical therapist. By weaving in subtle, tasteful pop-culture nods (e.g., *Kota Factory*, *Game of Thrones*, *Harry Potter*, *Marvel*), the app speaks the user's language, generating an immediate sense of comfort and relatability.
2. **Privacy First (Local-First Architecture):** Journaling is highly personal. To maximize trust, the application is built as a single-file, client-side application. No servers, no databases. All data is persisted entirely in the browser's `localStorage`.
3. **Structured Action from Unstructured Chaos:** Students often just need to "brain-dump" their anxiety. Using Google's **Gemini AI**, we take unstructured, emotional rants and structurally parse them into actionable metadata: identifying hidden triggers, finding emotional footprints, and automatically generating bite-sized, gamified mitigation strategies.
4. **Resilience over Perfection:** Tracking "Deep Work" endurances (Pomodoro) and providing a Weekly Summary celebrates consistency. Earning gamified achievements for completing wellness micro-tasks helps students restore their "HP" instead of letting burnout compound.

## ⚙️ How the Solution Works
MindSpace operates entirely in the browser (HTML + Tailwind CSS + Vanilla JS) and consists of three core pillars:

1. **The Brain Dump Dashboard:**
   - Users select their current operational status (e.g., "Locked-In", "Burnout", "Anxious") accompanied by a dynamic pop-culture greeting.
   - Users type their raw frustration or thoughts into the journal.
   - **AI Pipeline:** The app securely calls the Gemini API (`gemini-1.5-flash`), explicitly injecting a system prompt instructing the AI to adopt a witty, supportive persona. The AI returns a strictly formatted JSON object containing:
     - *Hidden Stress Triggers*
     - *Emotional Patterns*
     - *Personalized Wellness Toolkit* (Actionable micro-quests).
   - Checking off wellness toolkit tasks triggers gamified pop-up rewards (e.g., "Achievement Unlocked: Master of the Mystic Arts!").

2. **Deep Work Protocol (Pomodoro):**
   - A built-in 25/5 minute timer lets users track their study cycles directly inside their wellness companion.
   - Cycle completions are persisted and tallied for the weekly review, enforcing a healthy balance between deep focus and mandatory rest.

3. **Weekly Reflection & Report Generation:**
   - The app aggregates the last 7 days of mood logs and calculated study cycles.
   - Evaluates the dominant emotional state and provides an adaptive, pop-culture-themed AI mentoring quote (e.g., acknowledging an "elite streak" or suggesting they "rest in the batcave").
   - Users can securely export their insights via the **Download Report** functionality, which synthesizes their data into a clean, strictly local `.txt` file using the native JavaScript `Blob` API.

**Security & Configuration:** 
Users load their own Gemini API key into the hidden "Configuration Settings" drawer. The key is securely tucked away into browser `localStorage` and dispatched directly to the API endpoints—ensuring no middleware sniffing or central data logging ever occurs.

## 📝 Assumptions Made
1. **Bring Your Own Key (BYOK):** We assumed users are willing to provide their own Gemini API key to operate the AI features. This avoids the need for maintaining a proprietary backend wrapper or API quotas during the MVP phase.
2. **Local Storage Reliability:** We assume the user is using a modern web browser that supports `localStorage` up to 5MB, which is more than sufficient for storing lightweight text journals, completed cycles, and keys. Data is device-specific.
3. **Network Availability:** While data is stored locally, we assume an active internet connection is available to interface with the external Gemini AI inference servers. 
4. **Familiarity with Pop Culture:** We assumed the selected demographic possesses a general awareness of popular memes, shows, and movies to ensure the personalized greetings and achievements land correctly.
