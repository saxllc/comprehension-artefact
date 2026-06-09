# Comprehension Artefact — PoC

One screen, one transaction, two records. The DEPA-style consent artefact records **permission**;
the proposed comprehension artefact records **understanding**. Toggle "Today's flow" vs
"With comprehension layer" to see the difference. EN / HI. Zero API keys — nothing can fail in a pitch room.

Audio uses on-device speech synthesis as a stand-in; production swaps in Sarvam Bulbul TTS.
Schema draft: `comprehension-artefact/v0.1` (visible via "show machine record" in the demo).

## Deploy (new standalone Vercel app)

```powershell
# 1. Create the GitHub repo (one time)
cd C:\Users\dhuli\Documents\Claude\Projects\comprehension-artefact-demo
git init
git add .
git commit -m "feat: comprehension artefact PoC v0.1"
gh repo create saxllc/comprehension-artefact --public --source . --push
# (if gh is not installed: create the repo at github.com/new, then:)
# git remote add origin https://github.com/saxllc/comprehension-artefact.git
# git push -u origin main
```

2. Go to vercel.com → Add New → Project → import `saxllc/comprehension-artefact` → Deploy.
   No env vars, no build settings — it is a static site. Vercel auto-deploys on every `git push` after this.

## Local preview (no server needed)

```powershell
Start-Process "C:\Users\dhuli\Documents\Claude\Projects\comprehension-artefact-demo\index.html"
```

## Demo script (90 seconds)

1. Mode = "Today's flow", EN. Tick the box, tap I Agree. Right panel: consent artefact appears;
   comprehension slot reads "The tap was captured; comprehension was not."
2. Switch to "With comprehension layer", switch to हिं. Tap I Agree → plain-language checkpoint
   (play audio) → answer the teach-back question **wrong** on purpose → simpler re-explanation →
   answer right → both records appear, side by side. Open "show machine record."
3. Reset, answer wrong twice → flow pauses, assisted help recommended, and **no consent artefact
   is created** — the record is honest in both directions.
