# Pen Duel

A 3D school-bench pen flicking game for 2 to 8 players. English and Bangla (বাংলা). Offline, or online with friends through a room code, with stats and a shared leaderboard.

The game is plain static files, so it can be hosted for free on GitHub Pages. Online play and the leaderboard need a small free database, set up once with Firebase (steps below). Without it the game still works offline.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole game |
| `firebase-config.js` | Your Firebase keys (you fill this in) |
| `database.rules.json` | Security rules to paste into Firebase |

## 1. Create the Firebase project (free)

1. Open https://console.firebase.google.com and choose **Add project**. Analytics is not needed.
2. **Build → Authentication → Get started → Sign-in method → Anonymous → Enable.**
3. **Authentication → Settings → Authorized domains → Add domain:** `YOUR-GITHUB-USERNAME.github.io`
4. **Build → Realtime Database → Create database.** Pick the closest region offered (Singapore is closest to Bangladesh). Start in locked mode.
5. In the database, open the **Rules** tab, paste the contents of `database.rules.json`, and **Publish**.
6. **Project settings (gear icon) → Your apps → Web (`</>`) → Register app.** Copy the `firebaseConfig` values into `firebase-config.js`. If `databaseURL` is missing there, copy it from the top of the Realtime Database page.

Stay on the free Spark plan. Firebase menus change now and then, so names may differ a little.

## 2. Put it on GitHub Pages

```
git init
git add .
git commit -m "Pen Duel"
git branch -M main
git remote add origin https://github.com/YOUR-GITHUB-USERNAME/pen-duel.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save.**
After a minute the game is live at `https://YOUR-GITHUB-USERNAME.github.io/pen-duel/`. Send that link to your friends.

## 3. Play with friends

One player taps **Play online → Create room** and shares the 4-letter code. Friends open the link, tap **Play online → Join room** and type the code. The host presses **Start game**.

## Notes

- Everyone who has the link can play and appears on the leaderboard under the name they type.
- Each player's score entry can only be written by that same browser (anonymous sign-in). It is a friends-level setup, not cheat-proof.
- Test locally with `python3 -m http.server` and open http://localhost:8000. `localhost` is already an authorized domain.
- Online play sends the game state through the database about 18 times a second during a flick. A friends group stays far under the free limits.

---

## বাংলায় সংক্ষেপে

1. Firebase-এ নতুন প্রজেক্ট খোলো। Authentication-এ **Anonymous** চালু করো এবং Authorized domains-এ `তোমার-github-নাম.github.io` যোগ করো।
2. Realtime Database বানাও এবং Rules ট্যাবে `database.rules.json`-এর লেখা পেস্ট করে Publish করো।
3. Project settings থেকে Web app-এর config কপি করে `firebase-config.js`-এ বসাও।
4. ফাইলগুলো GitHub-এ push করো এবং Settings → Pages থেকে `main` branch চালু করো।
5. লিংকটা বন্ধুদের দাও। একজন "অনলাইনে খেলো → নতুন রুম খোলো" চাপে, বাকিরা কোড দিয়ে ঢোকে, হোস্ট খেলা শুরু করে।
"# pen-duel" 
