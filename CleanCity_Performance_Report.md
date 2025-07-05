
# CleanCity Web App – Performance Test Report

**Test Date:** July 04, 2025  
**Tested Pages:** `index.html` (Home, Login, Registration, Awareness)  
**Test Environment:** Localhost (`http://127.0.0.1:5500/`)  
**Tool Used:** Google Lighthouse v12.6.0 (Chrome DevTools)

---

## ✅ Desktop Performance Summary

| Metric                        | Result | Score |
|-------------------------------|--------|-------|
| First Contentful Paint        | 0.8 s  | 94%   |
| Largest Contentful Paint      | 1.3 s  | 87%   |
| Speed Index                   | 0.9 s  | 98%   |
| HTTPS                         | ✅ Yes | 100%  |
| Viewport Tag                  | ✅ Yes | 100%  |

### Comments:
- Excellent performance across all desktop metrics.
- Fast visual load and interactivity.
- Fully responsive layout and secure connection.

---

## 📱 Mobile Performance Summary

| Metric                        | Result | Score |
|------------------------------|--------|-------|
| First Contentful Paint       | 1.7 s  | 93%   |
| Largest Contentful Paint     | 2.9 s  | 81%   |
| Speed Index                  | 1.7 s  | 100%  |
| HTTPS                        | ✅ Yes | 100%  |
| Viewport Tag                 | ✅ Yes | 100%  |

### Comments:
- Mobile performance is good, with minor LCP delays.
- LCP of 2.9 seconds slightly exceeds Google's 2.5s target.
- Likely caused by large images or banner content on Awareness/Home page.

---

## ⚠️ Observations and Recommendations

1. **LCP Optimization:**  
   - Compress or lazy-load images, especially hero/awareness page content.
   - Consider reducing font size/weight or layout shifts during load.

2. **Run in Production:**  
   - Tests were done on `localhost`, so HTTP→HTTPS redirection, CDN behavior, and external asset caching were not measured.
   - Repeat tests after deploying the site online (e.g., GitHub Pages, Netlify).

3. **No Bugs Found:**  
   - No script or style errors.
   - All forms and pages loaded correctly.
   - Navigation and page structure are functional.

---

## 📌 Conclusion

The CleanCity web app shows excellent performance results on both desktop and mobile. Minor improvement on mobile LCP will further enhance user experience. The current implementation demonstrates responsive design, fast loading, and solid UI responsiveness. Final testing is recommended on a live deployment to validate full production readiness.

