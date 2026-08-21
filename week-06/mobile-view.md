# Week 6 — Open It on Your Phone
## Portfolio QA & Fix Log

### Testing
- Device: Android phone
- Mobile: tested on physical device
- Tablet: tested at ~768px viewport
- Desktop: tested at ~1440px viewport

### Before
The portfolio was already responsive, but I performed a real-device
check to identify usability and accessibility issues that were not
obvious from desktop development.

### Fixes

1. Mobile navigation
Before:
The navigation was usable on desktop but required a mobile-specific
menu for smaller screens.

After:
Verified the hamburger menu opens correctly and all navigation links
scroll to the correct sections.

2. Mobile project cards
Before:
Checked project content at mobile width for horizontal overflow.

After:
Verified project cards, technology tags and buttons wrap correctly
without causing horizontal scrolling.

3. Chat widget
Before:
Checked the floating AI chat interface on a small screen.

After:
Verified that the chat panel stays within the viewport and that the
input/send controls remain usable.

4. Typography
Before:
Checked headings, body text and buttons for readability on a phone.

After:
Adjusted any text sizes/spacing that were uncomfortable to read.

5. Links
Before:
Portfolio links had not all been verified from the deployed site.

After:
Tested GitHub, LinkedIn, CV, project repository, live demo and email
links.

6. Desktop/tablet verification
Before:
Mobile responsiveness had been implemented but cross-width QA had not
been formally documented.

After:
Checked the portfolio at mobile, tablet and desktop widths and fixed
any visible layout issues.
