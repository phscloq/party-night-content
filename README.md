# Party Night Content Repository

Remote content decks and word databases for the **Party Night** iOS application.

---

## 📁 Deck Files Inventory

| File | Game Mode | Description | Versioning |
| :--- | :--- | :--- | :--- |
| `trivia_decks.json` | Live Trivia | Multilingual speed & bluff trivia question decks (`en`, `fr`, `tr`, `id`) | `"version": 2` |
| `imposter_word_packs.json` | The Imposter | Undercover word pairs across categories and cultural editions | Array of word pairs |
| `whoami_decks.json` | Who Am I? | Character, celebrity, and object guessing cards | Category dictionary |
| `scale_prompts.json` | Scale Clue (Number Party) | Spectrum estimation prompts across 4 scale ranges | Array of prompts |
| `bomb_categories.json` | Bomb Pass | Rapid-fire category prompts for hot-potato ticking bomb rounds | Array of categories |

---

## 🚀 How to Add New Questions (Live Trivia)

1. Open `trivia_decks.json`.
2. **Increment the `version` number** (e.g., from `2` to `3`):
   ```json
   {
     "version": 3,
     "questions": [ ... ]
   }
   ```
3. Add your new question object ensuring translations are provided across all 4 supported languages (`en`, `fr`, `tr`, `id`):
   ```json
   {
     "id": "q_unique_id",
     "category": "Science & Space",
     "difficulty": "medium",
     "timeLimit": 15,
     "question": {
       "en": "...",
       "fr": "...",
       "tr": "...",
       "id": "..."
     },
     "correctAnswer": {
       "en": "...",
       "fr": "...",
       "tr": "...",
       "id": "..."
     },
     "distractors": {
       "en": ["...", "...", "..."],
       "fr": ["...", "...", "..."],
       "tr": ["...", "...", "..."],
       "id": ["...", "...", "..."]
     },
     "explanation": {
       "en": "...",
       "fr": "...",
       "tr": "...",
       "id": "..."
     }
   }
   ```
4. Commit and push to `main`:
   ```bash
   git commit -am "Add new trivia questions (v3)"
   git push origin main
   ```
5. The iOS application fetches fresh decks via the jsDelivr CDN endpoint:
   `https://cdn.jsdelivr.net/gh/phscloq/party-night-content@main/trivia_decks.json`
   Whenever a player launches the app or taps **"Check for New Questions"**, the new questions are downloaded and cached automatically without requiring an App Store review.
