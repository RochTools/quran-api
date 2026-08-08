# 📖 Quran API — RochTools

> **بِسۡمِ ٱللَّهِ ٱلرَّحۡمَٰنِ ٱلرَّحِيمِ**

Free Quran data in **10 languages** as JSON files — for developers building Islamic applications.  
No API key. No sign up. No cost. Just fetch and use.

---

## 🌍 Available Languages

| Code | Language | زبان |
|------|----------|-------|
| `bn` | Bengali | বাংলা |
| `en` | English | English |
| `es` | Spanish | Español |
| `fr` | French | Français |
| `id` | Indonesian | Indonesia |
| `ru` | Russian | Русский |
| `sv` | Swedish | Svenska |
| `tr` | Turkish | Türkçe |
| `ur` | Urdu | اردو |
| `zh` | Chinese | 中文 |

---

## 📁 Repository Structure

```
quran-api/
└── Quran/
    ├── bn/
    │   ├── 1.json      ← Surah Al-Fatihah
    │   ├── 2.json      ← Surah Al-Baqarah
    │   └── ...114.json
    ├── en/
    ├── es/
    ├── fr/
    ├── id/
    ├── ru/
    ├── sv/
    ├── tr/
    ├── ur/
    └── zh/
```

---

## 🔗 How to Fetch

**URL Pattern:**
```
https://raw.githubusercontent.com/RochTools/quran-api/main/Quran/{lang}/{surah_number}.json
```

**Examples:**
```
# Surah Al-Fatihah in English
https://raw.githubusercontent.com/RochTools/quran-api/main/Quran/en/1.json

# Surah Al-Baqarah in Urdu
https://raw.githubusercontent.com/RochTools/quran-api/main/Quran/ur/2.json

# Surah Al-Ikhlas in Turkish
https://raw.githubusercontent.com/RochTools/quran-api/main/Quran/tr/112.json
```

---

## 📦 JSON Structure

Each file follows this structure:

```json
{
  "id": 1,
  "name": "الفاتحة",
  "transliteration": "Al-Fatihah",
  "translation": "The Opening",
  "type": "meccan",
  "total_verses": 7,
  "verses": [
    {
      "id": 1,
      "text": "بِسۡمِ ٱللَّهِ ٱلرَّحۡمَٰنِ ٱلرَّحِيمِ",
      "translation": "In the name of Allah, the Entirely Merciful, the Especially Merciful.",
      "transliteration": "Bismi Allahi alrrahmani alrraheemi"
    }
  ]
}
```

| Field | Type | Description |
|---|---|---|
| `id` | Number | Surah number (1–114) |
| `name` | String | Surah name in Arabic |
| `transliteration` | String | Surah name in Roman script |
| `translation` | String | Surah name translated |
| `type` | String | `meccan` or `medinan` |
| `total_verses` | Number | Number of verses |
| `verses[].id` | Number | Verse number |
| `verses[].text` | String | Arabic Quranic text |
| `verses[].translation` | String | Translated text |
| `verses[].transliteration` | String | Roman transliteration |

---

## 💻 Code Examples

**JavaScript / React Native**
```javascript
async function fetchSurah(surahNumber, lang = 'en') {
  const url = `https://raw.githubusercontent.com/RochTools/quran-api/main/Quran/${lang}/${surahNumber}.json`;
  const response = await fetch(url);
  return await response.json();
}

// Usage
const surah = await fetchSurah(1, 'ur');
surah.verses.forEach(verse => {
  console.log(verse.text);        // Arabic
  console.log(verse.translation); // Urdu
});
```

**Python**
```python
import requests

def get_surah(surah_number, lang="en"):
    url = f"https://raw.githubusercontent.com/RochTools/quran-api/main/Quran/{lang}/{surah_number}.json"
    return requests.get(url).json()

surah = get_surah(1, "en")
for verse in surah["verses"]:
    print(verse["id"], "-", verse["text"])
    print("  ↳", verse["translation"])
```

**Dart / Flutter**
```dart
import 'dart:convert';
import 'package:http/http.dart' as http;

Future<Map> fetchSurah(int number, String lang) async {
  final url = Uri.parse(
    'https://raw.githubusercontent.com/RochTools/quran-api/main/Quran/$lang/$number.json'
  );
  final res = await http.get(url);
  return jsonDecode(res.body);
}
```

---

## ⚠️ Important Notice

> **إِنَّا نَحْنُ نَزَّلْنَا ٱلذِّكْرَ وَإِنَّا لَهُۥ لَحَٰفِظُونَ**  
> *"Indeed, it is We who sent down the reminder, and indeed, We will be its guardian."*  
> — Surah Al-Hijr (15:9)

This data contains the **Holy Quran** — the word of Allah.  
You are strictly **NOT permitted** to modify, alter, or edit any part of this text.  
Display it exactly as provided.

If you believe you found a data error, please [open an issue](../../issues) — do **not** edit the data yourself.

---

## 📄 License

This repository is provided under a **Read-Only, No Derivatives** license.  
You may use and fetch this data freely, but you may **NOT** modify it in any way.  
See [LICENSE.md](./LICENSE.md) for full terms.

---

## ⭐ Support

If this project helped you, please consider giving it a **star** on GitHub.  
It helps other Muslim developers find this resource.

**RochTools — Serving the Muslim Developer Community**
