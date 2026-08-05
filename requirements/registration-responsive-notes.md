# Registration Screen — Responsive Notes

## Layout changes from Web → Mobile

| Element | Web (1200px) | Mobile (375px) | Why |
|---|---|---|---|
| Nav | Full nav bar (Jobs, Companies, About, Log in) | Hamburger icon only | Not enough width for horizontal links; menu items move behind a tap target |
| Hero illustration | Large image, 50% of width, next to the form | **Removed entirely** | Illustration is decorative, not functional — cutting it prioritizes the form, which is the actual task |
| Form layout | Two-column card sitting beside the illustration | Full-width, single column | No room for a side-by-side layout; form becomes the whole page |
| Password / Confirm password | Side-by-side (2 columns) | Stacked (1 column) | Side-by-side fields get too narrow to comfortably type in below ~600px |
| Field height / touch targets | 42px fields | Same height kept, but full-width | Mobile fields need to stay tall enough to tap accurately; width compensates instead of height |
| Resume upload | Drag-and-drop wording | "Tap to browse" wording | Drag-and-drop isn't a mobile gesture — copy should match the input method |
| Footer links | Full row (Privacy · Terms · Contact) | Dropped from this screen | Secondary; would push the primary action (Register) below the fold |
| Primary action (Register) | Fixed width inside the card | Full-width button | Matches mobile convention and gives a larger, easier tap target |

## What stayed the same
- Field order and labels (Full name → Email → Phone → Password → Confirm password → Resume → Terms → Register) — the task flow itself doesn't change with screen size, only how it's laid out
- The "Already have an account? Log in" link stays directly below the button on both

## Notes for the AI-twist comparison
When critiquing an AI-generated version of this screen, check specifically for:
- Whether it dropped the illustration on mobile deliberately, or just shrank everything (a common AI-tool miss — cramming the desktop layout into a small viewport instead of restructuring it)
- Whether an **error state** was designed at all (e.g. "Passwords don't match", invalid email) — AI tools frequently generate only the empty/default state
- Color contrast on the button and field borders against WCAG AA (4.5:1 for text, 3:1 for UI component borders) — light-gray borders in particular are an easy miss
