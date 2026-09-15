# Battleship

Two-player, peer-to-peer Battleship that runs entirely from a static page —
host it on GitHub Pages and play with anyone, anywhere. Same connection scheme
as the other GameForAll games: both players pick Room 1, 2 or 3 and press
Play; the first to arrive hosts, the second joins automatically. The free
public PeerJS broker is used only for the WebRTC handshake, after which the
two browsers talk directly. Your ship positions never leave your browser until
the game is over (they are revealed to the opponent at the end).

## Rules (traditional)

- 10×10 grid, rows A–J, columns 1–10.
- Five ships: Carrier (5), Battleship (4), Cruiser (3), Submarine (3),
  Destroyer (2). Ships may touch but not overlap.
- Both players place their fleet (click to place, **R** or the Rotate button
  to turn, Random for a quick fleet, click a placed ship to pick it up again),
  then press **Ready**.
- Players alternate firing one shot per turn. Each shot is answered with
  Hit, Miss, or "You sank their &lt;ship&gt;".
- The first player to sink all five enemy ships wins. Who fires first
  alternates on rematches.

## Hosting

1. Create a GitHub repo named `battleShip` and push this folder.
2. Settings → Pages → deploy from the `main` branch, root folder.
3. The game will live at `https://<your-username>.github.io/battleShip/`.

"Return to menu" links point to `../Menu/`; change `MENU_URL` at the top of
the script in `index.html` if your menu repo has a different name.

## If connecting hangs

See the waiting screen's diagnostic line. A "Joining Room N…" that never
finishes means the room id is held by a dead session; the client waits 12 s
and then takes over the room. "A direct connection … could not be made" means
the WebRTC hole-punch failed between your two networks (usually mobile data or
a strict network) — a TURN relay would be needed; see the UltimateTTT README
for details.
