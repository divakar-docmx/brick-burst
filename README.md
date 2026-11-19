# Brick Burst

A 2D brick-breaker for the browser. Get the ball through the gap in the wall, burst the bricks, and catch the falling **+3** from yellow blocks to split your ball into three.

**Play:** https://divakar-docmx.github.io/brick-burst/

On a phone, open the link and add it to your home screen. It installs as an app and works offline:

- **iPhone:** Safari → Share → Add to Home Screen
- **Android:** Chrome → ⋮ → Install app

## Controls

| Action | Keyboard | Touch / mouse |
|---|---|---|
| Move plank | ← / → (or A / D) | Drag anywhere |
| Launch ball | Space | Tap |
| Ball speed | ↑ / ↓ | − / + buttons |
| Choose level | L | ☰ Levels |
| Pause / sound | P / M | ❚❚ / 🔊 buttons |

## Development

There's no build step. Everything is plain HTML and JS in `index.html`. To run it locally, serve the folder (service workers don't work from `file://`):

```sh
python3 -m http.server 8000
```

To add a level, add an entry to `LEVELS` in `index.html`. When you change any file, bump `VERSION` in `sw.js` so installed copies update.
