# Key Learnings — Day 60 / TRIAGE//44 Capstone

- A clean browser console does not mean a bug-free app — the Day 56 feedback-box issue only showed up by inspecting the actual DOM tree, not the console.
- Visual/CSS changes need to actually be seen rendered before being called "done" — Day 57's polish milestone waited for a real screenshot rather than trusting the code alone.
- Deployment assumptions should be checked, not assumed — Day 59's GitHub Pages deployment nearly hit a silent failure because the app lived in a subfolder GitHub Pages couldn't serve from directly; checking the real repo structure via a live fetch caught it early.
- Honest gaps are more valuable than false passes — screen-reader testing was never actually performed across the whole project and was documented as NOT VERIFIED rather than assumed working, on Day 58 and carried through to today.
- Small, disciplined daily scope (refusing to add "one more feature" per day) is what made a 10-day capstone actually finishable in 10 days.
- A public repository needs a README and LICENSE to be genuinely usable by anyone else — these are easy to forget once the app itself works, but they're what make a repo actually presentable.