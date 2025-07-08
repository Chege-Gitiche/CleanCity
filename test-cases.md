 1. Accessibility Testing (A11y)

| Test Area                  | What to Check                                          | Tools/Methods                                                            | Issues Found                                               |
| -------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| **Semantic HTML**          | Proper use of headings (`h1`-`h3`), lists, tables      | Manual inspection                                                        | ✅ Mostly correct, but navigation `<li>` has multiple links (fix applied earlier) |
| **Alt Text for Images**    | All images must have meaningful `alt` text             | Manual tst                                                                           | ❌ Missing `alt` in Awareness images                                              |
| **Keyboard Navigation**    | Can everything be navigated with `Tab` + `Enter` keys? | Manual test in browser                                                   | 🚨 Needs JS support for page switching—without it, navigation breaks             |
| **Color Contrast**         | Sufficient contrast between text and background        | Manual test                                                              | everything looks clear                                                           |
| **ARIA Roles & Landmarks** | Use ARIA where necessary (`role="navigation"`, etc.)   | Manual + axe DevTools                                                    | 🚨 Missing ARIA on navigation, buttons                                           |


2.  Compatibility Testing

| Browser                  | What to Check                                     | Result (Status)                                  |
| ------------------------ | ------------------------------------------------- | ------------------------------------------------ |
| **Chrome (latest)**      | Layout, navigation, form submission               | ✅ **Working as expected** (Tested)               |
| **Firefox (latest)**     | Layout, CSS grid/flex, navigation, form behavior  | ✅ **Working correctly** (Tested)                 |
| **Edge (latest)**        | Visual styles, icons, responsiveness, forms       | ✅ **Working correctly** (Tested)                 |
| **Safari (Mac/iOS)**     | Font rendering, CSS compatibility, responsiveness | ✅ **Working, minor font loading delay** (Tested) |
| **Mobile Browsers**      | Responsiveness, hamburger menu, touch interaction | ✅ **Working on Android & iOS** (Tested)          |
| **Internet Explorer 11** | Deprecated—no need to support                     | ❌ **Unsupported** (Not Applicable)               |



Tools:
BrowserStack (for multiple OS/browser tests)

Chrome/Firefox Mobile Emulation

3. Usability Testing

| Area                       | What to Check                                                     | Observations & Recommendations                                                                   |
| -------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| **Navigation**             | Can users easily find Home, Login, Register, Feedback, Dashboard? | 🔧 Page-switching needs functional JS or it's unusable. Add visual feedback when changing pages. |
| **Form Validation**        | Are required fields clearly marked? Are errors shown clearly?     | ✅ Fields marked, but error messages need visual emphasis (`.error-message` sometimes empty).     |
| **Success/Error Feedback** | Are users clearly informed when actions succeed or fail?          | ✅ Success messages exist but hidden initially—ensure they appear correctly after action.         |
| **Mobile Usability**       | Are forms easy to fill on small screens? Buttons large enough?    | user is able to fill a form on a small screen.                                                      |
| **Consistency**            | Are buttons, cards, and pages visually consistent?                | ✅ Good visual hierarchy in cards; verify CSS matches (needs visual test).                        |
| **Demo Accounts Info**     | Is demo account info easy to find for first-time users?           | ✅ Clearly provided on Login page.                                                                |
| **Help/Contact Info**      | Can users easily find how to get help or report issues?           | ✅ Present in Awareness page but could also be added to Footer/Global area for quicker access.    |



