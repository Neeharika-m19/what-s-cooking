# 🍳 What’s Cooking? Alexa Skill

A voice-driven recipe assistant powered by the Spoonacular API. Ask Alexa what you can cook with your pantry ingredients, add or remove items on the fly, and get step-by-step instructions—all with persistent session support via DynamoDB.

---

## 📌 Table of Contents
1. [Features](#-features)
2. [Tech Stack](#-tech-stack)
3. [File Structure](#-file-structure)
4. [Installation & Setup](#-installation--setup)
5. [Configuration](#-configuration)
6. [Deployment](#-deployment)
7. [Usage](#-usage)
8. [Interaction Model](#-interaction-model)
9. [Ingredients List](#-ingredients-list)
10. [Future Improvements](#-future-improvements)
11. [Author](#-author)
12. [License](#-license)

---

## 🚀 Features

- **Find Recipes by Ingredients**: Tell Alexa your ingredients and get recipe suggestions.
- **Dynamic Ingredient List**: Add or remove ingredients during the session.
- **Step-by-Step Instructions**: Confirm a recipe and hear the full cooking instructions.
- **Session Persistence**: Remembers your ingredient list across invocations with DynamoDB.
- **Fallback & Help**: Built‑in Alexa intents for help, stop, cancel, and unhandled requests.

---

## 🛠️ Tech Stack

| Category           | Technology                         |
|--------------------|------------------------------------|
| Language & Runtime | JavaScript (Node.js v12+)          |
| Voice Framework    | Amazon Alexa SDK (`alexa-sdk`)     |
| HTTP Client        | `unirest`                          |
| Database           | AWS DynamoDB                       |
| API                | Spoonacular Recipe & Nutrition API |
| Deployment         | AWS Lambda                         |

---

## 📁 File Structure

```bash
what-s-cooking/
├── index.js            # Skill handlers & API calls
├── IntentSchema.json   # Alexa intent definitions
├── utterances.txt      # Sample voice utterances
├── INGREDIENTS.txt     # Slot values for ingredients
├── package.json        # NPM dependencies & metadata
├── package-lock.json   # Locked dependency tree
└── README.md           # This documentation
