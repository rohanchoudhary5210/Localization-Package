# 🌍 Unity Localization System (JSON-based)

A lightweight, scalable **localization system for Unity** using JSON, supporting **Text**, **TextMeshPro**, and runtime language switching with persistence.

---

## ✨ Features

* ✅ JSON-based localization
* ✅ Supports **Unity UI Text** and **TextMeshProUGUI**
* ✅ Runtime language switching
* ✅ Automatic UI refresh via events
* ✅ Language persistence using `PlayerPrefs`
* ✅ Singleton-based manager (safe across scenes)
* ✅ Easy to extend with new languages

---

## 📁 Folder Structure (Recommended)

```
Assets/
├── Localization/
│   ├── Data/
│   │   └── localization.json
│   ├── Scripts/
│   │   ├── LocalizationManager.cs
│   │   ├── LocalizedLegacyText.cs
│   │   └── LocalizedTMPText.cs
```

---

## 📄 Localization JSON Format

```json
{
  "play_button": {
    "en": "Play",
    "fr": "Jouer",
    "sp": "Jugar",
    "pt-BR": "Jogar",
    "id": "Main",
    "ar": "العب"
  },
  "exit_button": {
    "en": "Exit",
    "fr": "Quitter",
    "sp": "Salir",
    "pt-BR": "Sair",
    "id": "Keluar",
    "ar": "خروج"
  }
}
```

* **Key** → Unique identifier used in UI
* **Value** → Language-code-to-text mapping

---

## 🧠 How It Works

### 1️⃣ LocalizationManager

* Loads JSON on startup
* Stores current language
* Exposes `GetText(key)`
* Fires `OnLanguageChanged` event

### 2️⃣ UI Components

* `LocalizedLegacyText` → For **UnityEngine.UI.Text**
* `LocalizedTMPText` → For **TextMeshProUGUI**
* Automatically updates text when language changes

---

## 🚀 Setup Instructions

### Step 1: Add LocalizationManager

1. Create an empty GameObject (e.g. `LocalizationManager`)
2. Attach `LocalizationManager.cs`
3. Assign `localization.json` in the Inspector
4. Mark it **DontDestroyOnLoad** (already handled)

---

### Step 2: Localize UI Text

#### For TextMeshPro

1. Add `LocalizedTMPText` to a TMP object
2. Set `localizationKey` (e.g. `play_button`)

#### For Legacy Text

1. Add `LocalizedLegacyText` to a Text object
2. Set `localizationKey`

---

## 🌐 Supported Languages (Default)

| Language   | Code    |
| ---------- | ------- |
| English    | `en`    |
| Portuguese | `pt-BR` |
| Russian    | `ru`    |
| Spanish    | `sp`    |
| French     | `fr`    |
| Arabic     | `ar`    |

---

## 🔄 Change Language at Runtime

```csharp
LocalizationManager.Instance.SetEnglish();
LocalizationManager.Instance.SetFrench();
LocalizationManager.Instance.SetArabic();
```

Or directly:

```csharp
LocalizationManager.Instance.SetLanguage("fr");
```

Language choice is saved automatically using `PlayerPrefs`.

---

## 🧪 Fallback Behavior

* Missing key → `#key`
* Missing language → `#key_languageCode`
* Prevents crashes and makes missing entries obvious

---

## ⚠️ Notes

* Requires **Newtonsoft.Json**
* Ensure JSON keys are unique
* Arabic text rendering depends on font & RTL support

---


## 👤 Author

**Rohan Choudhary**
Unity Game Developer

---

