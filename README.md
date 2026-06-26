# Freedom Finance
## Project Overview

**Freedom Finance** is a personal finance dashboard designed to help users track their income, expenses, and monthly budgets without compromising their data. 

* **The User Problem:** Many users want intelligent insights into their spending habits but are hesitant to connect their bank accounts or share sensitive financial data with cloud-based AI services. 
* **The Solution:** Freedom Finance bridges this gap by integrating **Spark AI**—a local, browser-based artificial intelligence. This guarantees zero data exfiltration while still providing users with actionable, intelligent insights into their financial health.

## Design Philosophy & UX Principles
-------------------------------------------------------------------------------------------
* **Minimizing Cognitive Load:** Financial data can be overwhelming. The interface is designed to transform raw numbers into intuitive, scannable visual insights to reduce the user's cognitive effort.
* **Privacy by Design:** Trust is the core of the user experience. By running the LLM entirely on the client side, the design implicitly communicates safety and security.
* **Inclusive & Accessible Design:** The interface prioritizes accessibility, ensuring that data visualizations and typography are legible and navigable for a diverse range of users.

## Key Features & User Experience
-------------------------------------------------------------------------------------------
* **At-a-Glance Dashboard:** Users are greeted with a comprehensive but clean overview of their net balance, total income, expenses, and savings. Visual progress tracking provides immediate context without requiring users to dig through spreadsheets.
* **Spark AI (Frictionless Contextual Help):** An embedded assistant that answers financial questions naturally. To ensure a seamless UX and prevent user frustration, the AI utilizes a hybrid architecture: it relies on fast, deterministic paths for mathematical accuracy and gracefully falls back to an LLM for conversational flexibility.
* **Smart Budgeting Alerts:** Users can set limits for custom categories. The UI utilizes dynamic visual graphs that shift states (on track, nearing limit, over budget) to provide immediate visual feedback before a user overspends.
* **Advanced Transaction Management:** A frictionless data-entry experience allows users to add, edit, delete, and instantly search transactions without page reloads.
* **Data Visualization & Portability:** Interactive charts break down spending habits. Recognizing that users need to share or store their data, the app includes a seamless PDF export feature for financial history.

## Prototyping & Technology Stack
-------------------------------------------------------------------------------------------
The technology stack was chosen to support a seamless, offline-capable, and highly responsive user interface.

### Design & Prototyping
* **Figma:** Wireframing, UI/UX prototyping, and layout planning

### Frontend & Visualizations
* **HTML, CSS, JavaScript**
* **D3.js:** Dynamic Data Visualization & Graph Generation
* **jsPDF & jsPDF-AutoTable:** Client-side PDF Generation
* **Web Storage API:** Simulated authentication and persistent local state management

### Local AI Integration
* **Rivescript.js:** Rule-based conversational routing for instant UI feedback
* **Transformers.js & LangChain.js:** In-browser machine learning and prompt engineering
* **Hugging Face Models:** SmolLM-135M-Instruct

----------------------------------------------------------------------------------------------

## UX Learnings & Takeaways
-------------------------------------------------------------------------------------------
1. **Designing for AI Trust (Hallucination Prevention):** Successfully deploying a Hugging Face transformer model in the browser taught me the importance of prompt engineering (using strict ChatML formatting) to constrain the AI. From a UX perspective, preventing hallucinations is critical to maintaining user trust in a financial application.
2. **Balancing Conversational UI with Deterministic UI:** I discovered the limitations of small-parameter models when handling raw math. To protect the user experience, I engineered a JavaScript fallback solution for complex algorithmic calculations (like finding the highest expense). This ensures the user always receives accurate data, even if the AI doesn't calculate it directly.
3. **Frictionless Onboarding:** By utilizing the Web Storage API for state management, users can immediately experience the app's value and start managing data without the friction of a traditional backend database signup process.
