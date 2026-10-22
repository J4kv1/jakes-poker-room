# Jake's Poker Room

A free Texas Hold'em trainer that runs in your browser. No sign-up, no account, no ads.

I made this because every online poker training site wants you to make an account first. I asked Claude to build a game to help me get better at poker, and this is what came out. It was built with AI assistance.

## What it does

- Play 6-max no-limit hold'em against five bots with different styles (tight, calling station, maniac, rock, solid). Blinds are $5/$10 and everyone starts with $1,000.
- A coach shows your position, pot odds, outs and equity, and recommends a play when you ask.
- Every decision is graded **on target**, **acceptable** or **mistake**, with the reason. Bet sizes get feedback too.
- A Stats tab tracks your accuracy, VPIP/PFR, net winnings, your biggest leaks and recent mistakes. Stats are saved in your browser only.
- A Ranges tab shows which hands to open, call or 3-bet by position, with your current hand highlighted.
- A Hands tab lists the ten hand rankings with how often each occurs.
- Dealing, chip and check animations, plus card and chip sound effects.

## Run it

It is a single static file. Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
```

To host it free, turn on GitHub Pages for this repo (Settings, Pages, deploy from the `main` branch).

## How the coach works

- **Preflop:** hands are scored with the [Chen formula](https://en.wikipedia.org/wiki/Texas_hold_%27em_starting_hands#Chen_formula) and compared against position-based thresholds. This is a simplification, not a solver.
- **Postflop:** equity comes from a Monte Carlo simulation. When you face a bet, opponents are sampled from hands that would plausibly make that bet, not random cards. The recommendation compares your equity to the break-even equity from pot odds.
- **Bots** use the same decision logic with a tightness/aggression offset per personality.
- Decks are shuffled with the browser's cryptographic random generator.

## Credits

- Card and chip sounds: [Casino Audio](https://kenney.nl/assets/casino-audio) by Kenney, CC0.
- Showdown hand names: [pokersolver](https://github.com/goldfire/pokersolver) (MIT), loaded from a CDN.
- Win confetti: [canvas-confetti](https://github.com/catdad/canvas-confetti) (ISC), loaded from a CDN.
- Fonts: Big Shoulders Display, IBM Plex Sans and IBM Plex Mono from Google Fonts.

## License

MIT. See [LICENSE](LICENSE).
