# Fuseball

Bomb tag for 2–8 mates, in the browser. One player holds a lit bomb. Tag someone or throw it at them to pass it on, and don't be holding it when it blows. The blast catches anyone nearby, the court shrinks as people drop, and the last one standing takes the round. Everyone except the winner drafts a stacking perk, and the first to 3 (or 5, or 7) round wins takes the match.

**Play:** https://officialprotondev.github.io/Fuseball/

## Playing with mates

1. Open the site and click **Create game**.
2. Click **Copy invite link** and send it to your mates. Nobody needs an account.
3. Pick the match length and how many bots to add, then click **Start match**.

Controls: WASD to move, mouse to aim, click to throw, Space to dash, 1–5 for banter, M to mute. Keyboard and mouse only.

## How it works

- The whole game is `index.html`. There's no build step and no server of our own.
- Players connect browser to browser over WebRTC using [PeerJS](https://peerjs.com), which is inlined in the page (MIT licence). The free PeerJS cloud server only introduces players to each other. Game traffic goes directly between browsers, or through PeerJS's public TURN relay when a network blocks direct connections.
- The game creator's browser relays everyone's updates and runs the match. If they leave, the earliest remaining joiner takes over and the match carries on.
- `.github/workflows/pages.yml` deploys `index.html` and `og.png` to GitHub Pages on every push to `main`.
