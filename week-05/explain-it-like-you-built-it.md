# Explain It Like You Built It — My Portfolio Navbar & Dark Mode

## What I Chose to Explain

I picked two connected pieces of my portfolio: the navigation bar and the dark/light mode toggle. These were interesting because they work differently on different screen sizes, and the dark mode toggle was something I wanted to understand properly rather than just copy-pasting.

---

## How My Navbar Works

My navbar has two versions: one for desktop and one for mobile. They're both in the same HTML, but I use Tailwind's responsive classes to show the right one at the right screen size.

### Desktop Navigation

On larger screens (tablets and desktops), the navbar shows:
Home | About | Projects | Contact

text

Each button calls a JavaScript function called `scrollToSection()` with the section ID. For example, clicking "About" calls `scrollToSection('about')`.

Instead of loading a new page (like a traditional website would), the page smoothly scrolls to that section on the same page. This keeps the site feeling fast and seamless, like a single-page application.

### Mobile Navigation

On smaller screens (phones), the desktop navigation disappears and you see a hamburger icon (☰) instead. Clicking it opens a dropdown menu with the same navigation items plus a dark/light mode toggle.

The mobile menu closes automatically when you click a link or tap outside it. This is handled by the `toggleMobileMenu()` function, which simply adds or removes a CSS class that hides or shows the dropdown.

### The Key Difference

| Version | When You See It | What It Contains |
|---------|-----------------|------------------|
| Desktop | Medium and large screens | Navigation links only |
| Mobile | Small screens | Navigation links + dark mode toggle |

---

## How the Dark/Light Toggle Works

The dark mode toggle is controlled by a button that calls `toggleDarkMode()` when clicked. This button appears in both the desktop navbar and the mobile dropdown.

### Behind the Scenes

1. **The Toggle**: Clicking the button runs `toggleDarkMode()`, which checks whether the `dark` class is currently on the `<html>` element.

2. **The Class**: The function adds or removes the `dark` class on the `<html>` element:
   - Light mode → `<html>`
   - Dark mode → `<html class="dark">`

3. **The Styling**: Once the `dark` class exists, Tailwind activates all the `dark:*` CSS classes I've used. For example, `dark:bg-gray-900` turns the background dark when dark mode is active.

4. **The Persistence**: The user's preference is saved in the browser's `localStorage`, so it persists even after refreshing the page or closing the browser.

### Why I Built It This Way

I used this approach because:
- It's clean and simple — just one class toggle
- It works with Tailwind's built-in dark mode support
- It doesn't require complicated state management
- It's easy to test and debug

---

## What I Learned

Before this, I understood that dark mode toggles exist, but I didn't fully understand how they work under the hood. Now I know:

1. It's just a CSS class toggle on the root HTML element
2. Tailwind's `dark:` prefix handles the rest
3. `localStorage` makes the preference stick

I also learned why my navbar has two versions instead of one — responsive design means thinking about different screen sizes, not just desktop and mobile as separate sites.

---

## How I'd Explain This to a Friend

If a friend asked me how my navbar works, I'd say:

> *"It's two menus in one. On a computer screen, you see the full menu at the top. On a phone, you see a hamburger icon that opens a dropdown. Both menus use JavaScript to scroll to the right section instead of reloading the page."*

And for the dark mode:

> *"It's just a light switch for the whole page. Clicking the button tells the browser to add or remove a 'dark' class on the main HTML element. All the colors that are supposed to be dark have been prepared in advance, so they change instantly when the class is toggled."*

---
