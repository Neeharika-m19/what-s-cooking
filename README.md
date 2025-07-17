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

```

## 📦 Installation & Setup

1. **Clone the repository**

    ```bash
    git clone https://github.com/Neeharika-m19/your-project-name.git
    cd your-project-name
    ```

2. **Install dependencies**

    ```bash
    npm install
    ```
## ⚙️ Configuration

### Alexa Skill ID  
Set your skill’s application ID:
```bash
export ALEXA_APP_ID="amzn1.ask.skill.YOUR_SKILL_ID"

```
### Spoonacular API Key
Obtain a key from Spoonacular and export it:
```bash
export SPOONACULAR_KEY="YOUR_MASHAPE_KEY"

```
## DynamoDB Table
Create a DynamoDB table named `whatsCooking` with a primary key `userId` (String) for session persistence.

---
## ☁️ Deployment

### Zip your code
```bash
zip -r function.zip index.js package*.json node_modules

```

### In the AWS Lambda Console

1. **Create a new function**  
   - Runtime: Node.js 12.x

2. **Upload your code**  
   - Upload `function.zip` or connect via CLI

3. **Set environment variables**  
   - `ALEXA_APP_ID`  
   - `SPOONACULAR_KEY`  
   - `DYNAMODB_TABLE`

4. **Assign an IAM role** with the following managed policies:  
   - `AWSLambdaBasicExecutionRole`  
   - `AmazonDynamoDBFullAccess`

5. **Link your Lambda ARN**  
   - In the Alexa Developer Console, under **Endpoint**, paste your Lambda function ARN.

---

## 🎙️ Usage

Invoke your skill by name, then:

- **Get recipes:**  
  “Alexa, ask What’s Cooking what I can make with chicken and rice.”

- **Add ingredients:**  
  “Alexa, ask What’s Cooking to add tomatoes.”

- **Remove ingredients:**  
  “Alexa, ask What’s Cooking to remove chicken.”

- **Confirm & cook:**  
  “Yes” when Alexa proposes a recipe to hear instructions.

- **Next suggestion:**  
  “No” to hear another recipe suggestion.

---

## 🗂️ Interaction Model

- **Intent Schema** (`IntentSchema.json`):  
  Defines core intents:
  - `NewIngredientIntent`
  - `AddIngredientIntent`
  - `RemoveIngredientIntent`
  - `AMAZON.YesIntent`
  - `AMAZON.NoIntent`

- **Sample Utterances** (`utterances.txt`):  
  ```text
  NewIngredientIntent what can I make with {ingredients}
  AddIngredientIntent add {ingredients}
  RemoveIngredientIntent remove {ingredients}

## Slot Values
`INGREDIENTS.txt` contains all valid `{ingredients}` values.

## 📊 Data Visualization (Optional)
You can extend this skill by integrating a companion dashboard that visualizes your most-used ingredients or recipe trends using the stored DynamoDB data.

## 💡 Future Improvements
- 🧑‍🍳 **Multi-Ingredient Slots**: Support multi-word ingredients (e.g. `olive oil`).
- 🎛️ **User Profiles**: Store dietary preferences and restrictions.
- 🌐 **Globalization**: Add multi-language support.
- 🧪 **Unit Tests**: Automate handler tests with Mocha or Jest.

