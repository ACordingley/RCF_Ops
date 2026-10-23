# Brisbane CBD Marine Ops Dashboard - Windy.com Live

Immersive high-res marine dashboard with traffic-light safety system.

## Features
- Windy.com Map API v4 (wind, rain, radar, waves, thunder/lightning)
- Traffic light GO/NO-GO (RED/AMBER/GREEN) for marine crews
- Detailed current conditions: temp, feels like, dew, humidity, QNH/MSL, wind kt/kmh, gust, rainfall p/hr, rainfall since 9am, visibility, cloud oktas, lightning counts
- Brisbane Bar tides: Low 00:27 0.42m, High 06:25 1.54m, Low 12:21 0.53m, High 18:36 1.91m
- Day/night auto swap at sunrise 05:08 / sunset 17:52 AEST
- 10-min auto-refresh, BOM + Open-Meteo live fallback

## GitHub Pages Setup (Safe)

**DO NOT commit your Windy API key.**

1. Create new GitHub repo `brisbane-marine-ops`
2. Upload `index.html`, `config.example.js`, `.gitignore`, `README.md` - **do NOT upload `config.js` with real key**
3. Settings > Pages > Deploy from main branch /root
4. Your site will be at https://USERNAME.github.io/brisbane-marine-ops/

### Add your key privately (2 options)

**Option A - Browser localStorage (recommended for Pages):**
Open your deployed site, open DevTools Console (F12) and run:
```
localStorage.setItem('WINDY_KEY','25qsWNtkLdPBSyBVkAWW0un0QKCPWygK')
location.reload()
```

**Option B - Local config.js (for local dev):**
```
cp config.example.js config.js
# edit config.js with your real key
```

The code checks in order: localStorage > window.WINDY_API_KEY (from config.js) > YOUR_WINDY_API_KEY placeholder.

## API Keys
- Windy.com: https://api.windy.com/keys - get yours free
- BOM observations: public, no key, proxied via allorigins
- Open-Meteo: free, no key, CORS enabled

## Marine thresholds
- Wind: <15kt GREEN, 15-25 AMBER, >25 RED
- Gust: >30kt RED
- Rain rate: <2.5 GREEN, 2.5-10 AMBER, >10 RED
- Rain since 9am: <10 GREEN, 10-25 AMBER, >25 RED
- Visibility: <1km RED, 1-5 AMBER, >5 GREEN

Made for Brisbane CBD (-27.4698, 153.0251) - change lat/lon in index.html to relocate.
