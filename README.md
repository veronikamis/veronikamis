# My Projects

Small, personal software and hardware, mostly built around a kitchen garden, a wardrobe, and a house in which everything stays local when it can. Most of the repos are private; the write-ups live at [sloveller.com](https://sloveller.com).

## Soil to Signal
Soil moisture sensing — and, later, automatic watering — for the kitchen garden. A capacitive probe in each pot, an ESP32 node that reads it, applies its own calibration, and will eventually decide on its own whether to water. A Raspberry Pi 5 indoors polls the nodes over WiFi and draws a dashboard in a 3D-printed case. No hub, no cloud, no server in the greenhouse: each node owns its own decision, so a bed keeps watering correctly even when the house WiFi is down. ESPHome on the nodes, a week of watching data before anything is allowed to touch water.
→ [Write-up](https://sloveller.com/journal/soil-to-signal) · [Shopping list](https://sloveller.com/journal/soil-to-signal-shopping-list)

## Peas & Quiet
A kitchen garden app, at [garden.sloveller.com](https://garden.sloveller.com). Next.js on Vercel, tracking what's planted, what needs doing, and what the weather is about to do to it. It pulls from Open-Meteo, which is the rare weather API that gives you soil temperature and evapotranspiration rather than just a cheerful sun icon. Tasks can be logged by NFC tap — a tag on the watering can, a tap, and the watering is recorded without touching a phone screen with muddy hands.

Alongside it, the **Seed Studio** — a little browser studio for designing seed stickers, packets, and almanac cards by hand, plus a printable planting guide and botanical spice-jar labels from the same design system.
→ [Seed Studio](https://sloveller.com/seed-studio) · [Write-up](https://sloveller.com/journal/peas-and-quiet-seed-studio) · [Spice labels](https://sloveller.com/journal/botanical-spice-jar-labels)

## NothingToWear
A stylist for the clothes you already own, at [wardrobe.sloveller.com](https://wardrobe.sloveller.com). The idea is simple and the execution isn't: photograph a wardrobe, let the app understand what's in it, and have it suggest outfits that account for the weather, the occasion, and what you've actually worn lately. Wear-logging happens by tapping an NFC tag rather than opening an app, because nobody opens an app to say they wore a jumper. Under the hood: CLIP embeddings for the garments, pgvector on Supabase for retrieval, and an LLM doing the judgement calls that a similarity score can't. The interface leans warm-terminal — cream ground, plum monospace, a boot sequence borrowed from a fashion atelier.

## Performance OS
A personal training and nutrition advisor, at [workout.sloveller.com](https://workout.sloveller.com). Recovery signals, training load, and food combined into one daily decision: how hard should today be, and how should eating support that. Activities arrive from Strava webhooks, recovery from Garmin, body composition from a Renpho scale. A deterministic rules engine does the scoring; an LLM explains the reasoning rather than replacing it. Cycle-aware, because a fat-loss plan that ignores luteal-phase water retention will misread the scale and push a deficit exactly when the body resists one. Next.js, Supabase, Recharts.

## Travel Diary
A diary for trips — stops, journal entries, photos, maps, and a PDF at the end. Two builds: an Expo / React Native app with a dark memory-book aesthetic, and a Next.js web version with a "Wayfarer" paper-scrapbook theme, Mapbox for the maps, Supabase for auth and photos, and an AI writing assist that streams suggestions while you write.

## Bertie
The assistant that sits over all of the above. A long-lived Node service that holds the API key, spawns MCP servers, long-polls Telegram, and runs Claude's tool-use loop — you text it, it texts back, and mornings it pushes a briefing. It has no database of its own: `sloveller-mcp` wraps each app in a small tool surface (garden tasks, body snapshot, wardrobe suggestions, journal, Obsidian vault, portfolio, weather), so each app stays the source of truth and Bertie just calls them.

## Cyberdeck
A dual-screen Raspberry Pi 5 cyberdeck in the shape of a cloth-bound notebook — it opens flat like a book, with a 5" touchscreen on the left page for reading and a smaller dashboard screen on the right. It holds a curated ebook library (19th-century novels, gothic and weird, philosophy and essays, adventure and detective) synced from my Mac, and the right-hand screen is destined to become a physical control surface for the projects above. Custom CAD frame, because nothing off the shelf fits an object that doesn't exist yet. Cream and plum, with a powder-compact sensibility.

**Cyberdeck Home** is the launcher on the Pi: four tiles — Garden, Books, Movies, Soil-to-signal — paper by day, dark after 22:00. A stdlib Python server, a Chromium kiosk, and a timer that pulls the repo every minute, so pushing from the Mac is deploying to the Pi.

## Elsewhere
[sloveller.com](https://sloveller.com) — journal, garden diaries, and the write-ups for everything here.
