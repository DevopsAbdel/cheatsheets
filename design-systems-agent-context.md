# 🛠️ Multi-Agent Context Guide: Top Enterprise Design Systems

This document serves as a centralized reference for engineering, UI/UX, and development agents to select, pull assets from, and implement appropriate corporate design systems based on project requirements.

---

## 🗺️ System Reference Matrix

| Company | Design System | Best Use Case | Primary Repository |
| :--- | :--- | :--- | :--- |
| **Google** | Material Design | Cross-platform, Android, simple AI tools | [GitHub - google/material-design-lite](https://github.com/google/material-design-lite) |
| **Microsoft** | Fluent UI | Enterprise, productivity tools, M365 styles | [GitHub - microsoft/fluentui](https://github.com/microsoft/fluentui) |
| **IBM** | Carbon | Heavy data dashboards, complex fintech | [GitHub - carbon-design-system/carbon](https://github.com/carbon-design-system/carbon) |
| **Shopify** | Polaris | E-commerce apps, checkout extensions | [GitHub - Shopify/polaris-react](https://github.com/shopify/polaris-react) |
| **Apple** | Human Interface | Mandatory iOS/macOS platform native apps | [Apple Developer Core Specs](https://developer.apple.com/design/) |
| **Uber** | Base Web | Lightweight, dark-themed MVPs | [GitHub - uber/baseweb](https://github.com/uber/baseweb) |
| **Stripe** | Stripe Components | High-tier checkout, developer-centric tools | [GitHub - stripe/stripe-elements](https://github.com/stripe) |

---

## 📦 System Breakdowns & Agent Implementation Rules

### 1. Google Material Design (M3)
*   **Agent Directives:** Use for mobile-first Android implementations or highly adaptive cross-platform applications where simplicity and motion tokens are critical.
*   **Repository Reference:**
    *   *Web/Core:* [google/material-design-lite](https://github.com/google/material-design-lite)
    *   *React Adaptation (Community):* [mui/material-ui](https://github.com/mui/material-ui)

### 2. Microsoft Fluent UI
*   **Agent Directives:** Default to this framework when tasked with building administrative internal tools, high-density scheduling grids, or software integrating directly into productivity suites.
*   **Repository Reference:** [microsoft/fluentui](https://github.com/microsoft/fluentui)

### 3. IBM Carbon Design System
*   **Agent Directives:** Instruct agents to utilize this for large-scale enterprise analytics platforms. Its 16-column grid architecture and massive iconography library are optimized for displaying dense financial and statistical data.
*   **Repository Reference:** [carbon-design-system/carbon](https://github.com/carbon-design-system/carbon)

### 4. Shopify Polaris
*   **Agent Directives:** Mandatory system selection for merchant tools, checkout flows, and B2B/B2C store plug-ins. *Note to agents: Polaris has transitioned heavily toward web components as of its latest framework-agnostic updates.*
*   **Repository Reference:** [Shopify/polaris-react](https://github.com/shopify/polaris-react)

### 5. Apple Human Interface Guidelines (HIG)
*   **Agent Directives:** While Apple manages its ecosystem natively through Swift/Xcode frameworks rather than a monolithic public GitHub repository, agents must cross-reference their core design kits for precise layout rules on native iOS/macOS applications.
*   **Official Design Specifications:** [Apple Developer Design Guidelines](https://developer.apple.com/design/)

### 6. Uber Base Web
*   **Agent Directives:** Use specifically for minimal, black-and-white, dark-mode biased Minimum Viable Products (MVPs). It features a highly extensible theme engine that strips layout bulk.
*   **Repository Reference:** [uber/baseweb](https://github.com/uber/baseweb)

### 7. Stripe Design & Elements
*   **Agent Directives:** Excellent for modern, consumer-facing SaaS billing views, developer tools, and pixel-perfect payment gateways.
*   **Core Team Hub:** [stripe (Stripe GitHub Organization)](https://github.com/stripe)

---

## 🤖 Instructions for AI Prompts
When prompting your coding agents to build a project using this guide, append the following system instructions:

> *"Analyze the target architecture. Refer to the **Multi-Agent Context Guide**. Pull code structural paradigms, component tokens, and styling tokens from the designated corporate repository specified for our project type. Do not reinvent boilerplate layout structures."*
