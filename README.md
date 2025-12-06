# share

# ContentGenius AI 🛍️

**ContentGenius AI** is a professional-grade, high-fidelity SaaS application designed for e-commerce merchants, agencies, and copywriters. It leverages **Google's Gemini 2.5 Flash** model to generate conversion-optimized product titles, descriptions, SEO metadata, and social media copy.

![App Status](https://img.shields.io/badge/Status-Production%20Ready-success)
![Tech Stack](https://img.shields.io/badge/Tech-React%20%7C%20Tailwind%20%7C%20Gemini%20API-blue)

## ✨ Key Features

### 1. Single Product Mode (Multimodal)
- **Visual Analysis**: Drag & drop product images. The AI analyzes visual traits (color, material, texture) to enrich descriptions.
- **Detailed Inputs**: Configure Brand, Category, Features, Tone, Channel, and Language.
- **Comprehensive Output**: Generates:
  - **Strategy Note**: Why the copy was written this way.
  - **Optimized Title**: High-visibility naming.
  - **Feature Bullets**: 5 key selling points.
  - **HTML Description**: Ready-to-paste rich text.
  - **SEO Package**: Meta Title, Description, and Keywords.
  - **Social Post**: Instagram/Facebook ready copy with hashtags.

### 2. Bulk Upload Engine 🚀
- **Mass Generation**: Process hundreds of products via **CSV** or **JSON**.
- **Queue Management**: Real-time progress tracking with `Idle` -> `Pending` -> `Success` states.
- **Error Handling**: Skips failed items without stopping the queue.
- **Batch Export**: Download all generated content in a single JSON file.

### 3. Export & Integration
- **Formats**: Export individual results as **DOCX**, **PDF**, or **JSON**.
- **Clipboard**: One-click copy for all sections.

---

## 🛠️ Technical Stack

- **Frontend**: React 19, TypeScript
- **Styling**: Tailwind CSS (Custom "Slate & Blue" SaaS Theme)
- **Icons**: Lucide React
- **AI Model**: Google Gemini 2.5 Flash (via `@google/genai` SDK)
- **State Management**: React Hooks (Local State)

---

## 🚀 Getting Started

### Prerequisites
- Node.js (v18+)
- A Google Gemini API Key

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/content-genius-ai.git
   cd content-genius-ai
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure Environment**
   Ensure your API key is available in your environment variables.
   ```bash
   export API_KEY="your_gemini_api_key_here"
   ```

4. **Run the Application**
   ```bash
   npm start
   ```

---

## 📂 Project Structure

```
├── components/
│   ├── ui/                 # Reusable atoms (Button, Input, Icons)
│   ├── Dashboard.tsx       # Main Layout & Tab Controller
│   ├── SingleProductMode.tsx # Single Item Generation Logic
│   ├── BulkProductMode.tsx   # Bulk Queue & CSV Parsing Logic
│   ├── ProductContentPreview.tsx # Output Display & Export Logic
├── services/
│   └── geminiService.ts    # Gemini API Integration (Multimodal)
├── types.ts                # TypeScript Interfaces
├── App.tsx                 # Root Component
└── index.tsx               # Entry Point
```

---

## 🎨 Design System

The UI follows a modern **"Clean SaaS"** aesthetic:
- **Background**: Soft White `#F8FAFD`
- **Primary Color**: Royal Blue `#2563EB`
- **Typography**: Inter (Google Fonts)
- **Cards**: White with subtle borders & soft shadows
- **Interactive Elements**: Hover states, focus rings, and active scaling.

---

## 🗂️ Data Flow Diagram (OpenAI Only)
```mermaid
graph TD
    User -->|Login| Frontend[React App]
    Frontend -->|Product Data/CSV Upload| Backend[Node.js/Express]
    Backend -->|Validate & Store| DataStore[(JSON Files)]
    Frontend -->|Generate Request| Backend
    Backend -->|Prompt| OpenAI[OpenAI API]
    OpenAI -->|Response| Backend
    Backend -->|Send Generated Content| Frontend
    Frontend -->|Export/Download| User
```

## ⚙️ Technical Flow Diagram
```mermaid
sequenceDiagram
    participant U as User
    participant F as Frontend (React)
    participant B as Backend (Express)
    participant O as OpenAI API
    U->>F: Login / Upload Product Data
    F->>B: Send Data (REST API)
    B->>O: Build Prompt & Call OpenAI
    O-->>B: Return Generated Content
    B-->>F: Send Content
    F->>U: Display & Export
```

## 🏗️ Architecture Diagram
```mermaid
flowchart LR
    subgraph Frontend
        F1[React 19]
        F2[Tailwind CSS]
        F3[Lucide Icons]
    end
    subgraph Backend
        B1[Node.js/Express]
        B2[OpenAI SDK]
        B3[Data Storage (JSON)]
    end
    F1 -->|REST API| B1
    F2 --> F1
    F3 --> F1
    B1 --> B2
    B1 --> B3
    B2 -->|API Call| OpenAI
```

## 🔄 Workflow Diagram (Single Product & Bulk)
```mermaid
flowchart TD
    A[User Login] --> B[Select Mode]
    B --> C1[Single Product]
    B --> C2[Bulk Upload]
    C1 --> D1[Enter Details & Upload Image]
    D1 --> E1[Click Generate]
    E1 --> F1[Frontend Validates]
    F1 --> G1[Send to Backend]
    G1 --> H1[Backend Builds Prompt]
    H1 --> I1[OpenAI API Call]
    I1 --> J1[Receive Content]
    J1 --> K1[Display in UI]
    K1 --> L1[Export/Copy]
    C2 --> D2[Upload CSV/JSON]
    D2 --> E2[Parse & Queue]
    E2 --> F2[Process Each Item]
    F2 --> G2[OpenAI API Call]
    G2 --> H2[Collect Results]
    H2 --> I2[Batch Export]
```

---

## 📄 License

MIT License. Free to use for personal and commercial projects.
