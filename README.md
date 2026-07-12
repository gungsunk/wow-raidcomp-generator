# 🎲 WoW Raid Comp Generator (Wheel of Fun)

A smart, visually engaging, and highly dynamic World of Warcraft raid composition generator. 

Designed for guilds and raid leaders who want to inject some chaotic fun into "Alt Nights" or casual runs, this tool randomly assigns classes and specs to your roster. However, unlike a simple randomizer, it is powered by a **sophisticated weighting algorithm** that ensures your raid remains mathematically viable, perfectly scaled, and buff-optimized.

## ✨ Key Features

*   **The 13-Class Guarantee:** The algorithm prioritizes raid buffs by ensuring all 13 WoW classes are represented in your roster before it even considers handing out duplicate classes.
*   **Intelligent Role Distribution:** Players select their preferred roles (Tank, Healer, Melee, Ranged). The app dynamically buckets players based on preference, falling back to "Flex" assignments if mandatory roles are full.
*   **Dynamic Healer Scaling:** Healer requirements automatically scale based on your raid size (10 to 40 players). It uses an exponential probability curve at raid-size breakpoints (e.g., smoothly increasing the chance of adding a 3rd healer as your raid grows from 11 to 14 players, hard-capping at 15).
*   **DPS Elastic Balancer:** Prevents disastrous Melee/Ranged stacking (like a 10-4 split). It allows for organic randomness but steps in to force balance if one side pulls ahead by more than 2 players.
*   **Role-Isolated Duplicate Penalties:** If the raid size forces duplicate classes, the algorithm applies an exponentially decaying weight penalty. It specifically looks at *roles*—meaning a Marksmanship Hunter won't heavily penalize your chances of rolling a Survival Hunter, preserving playstyle variety while heavily punishing exact-spec duplicates.
*   **Guild Master Locks:** Pin specific players to a locked class and spec (e.g., your Main Tank). The algorithm intelligently deducts them from the requirements and builds the rest of the randomized roster around them.
*   **Theatrical Splash Reveal:** A sleek, animated overlay reveals each player's assigned class and spec one-by-one to build suspense in Discord voice calls (includes a "Fast Roll" toggle to skip animations).
*   **Quality of Life:** Saves your roster automatically to `localStorage`, includes built-in safeguards to prevent rolling if there aren't enough willing Tanks/Healers, and features a 1-click "Save Screenshot" button to export the comp for Discord.

## 🧠 Under the Hood: The Math

This app doesn't just pick random classes; it mimics the decision-making of a human Raid Leader.

*   **Buffer System:** The app constantly calculates the remaining roster slots vs. the remaining missing classes. If the buffer hits zero, it enters "Panic Mode" and strictly forces unrepresented classes so you don't miss out on the 13-class quota.
*   **Scaling Penalties:** The punishment for rolling duplicate specs relaxes as your raid size grows. At 10 players, duplicates are statistically near-impossible. At 30+ players, the math softens, allowing duplicates to naturally emerge without breaking the weight system.

## 🚀 How to Use

This project is built using pure **Vanilla HTML, CSS, and JavaScript**. No heavy frameworks, no `npm install`, and no build steps required.

Use the [github page](https://gungsunk.github.io/wow-raidcomp-generator/)

Or:

1. Clone or download the repository.
2. Open `index.html` in any modern web browser.
3. Add player names and check the boxes for the roles they are willing to play.
4. Click **Roll Comp!** and share your screen.

---

### *A Note on Class Icons*
*By default, the app expects a local folder named `/icons/` containing standard WoW spec icons (e.g., `spell_holy_holybolt.jpg`). You can easily batch-download these from WoWHead or map the image source strings directly to Blizzard's CDN.*
