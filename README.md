# NoVA-Haul-and-Clear
🧠 Project Overview

I started this project with a real-world goal: I was launching a junk removal business in Northern Virginia with a $1,000 budget, and I needed a professional website that could compete with established companies like 1-800-GOT-JUNK and Gen Z Junk Removal.

Rather than paying $500–$2,000 for a web designer, I decided to build it myself. I used Claude AI as a coding assistant — similar to how a developer might use GitHub Copilot — to help me write, debug, and refine the code. Every decision about design, content, structure, pricing, and business strategy was mine. The AI helped me execute those decisions in code.

This project taught me how to take an idea from concept to a fully deployed, live website — and gave me hands-on experience with HTML, CSS, JavaScript, form handling, and deployment pipelines.


💡 What I Learned


How HTML documents are structured using semantic elements like <nav>, <section>, <form>, and <footer>
How CSS custom properties (variables) work and why they make styling consistent across a large file
How CSS Grid and Flexbox control layout and responsiveness across screen sizes
How JavaScript event listeners work to handle form submissions without reloading the page
How fetch() sends form data to an external API (Web3Forms) asynchronously
How Netlify and Vercel read and deploy static HTML files
How form spam protection works using a honeypot hidden field
How to connect a GitHub repository to Vercel for automatic deployments
How to write a professional README.md using Markdown



🤖 How I Used AI in This Project

I used Claude (Anthropic) as an AI coding assistant throughout this build. Here's specifically how:

My ContributionHow AI HelpedDecided the business name, branding, colors, and toneWrote the CSS color palette and typography based on my directionChose every section of the site and what content goes in eachTranslated my content decisions into HTML structureDefined the pricing, service list, and service areaCoded those sections based on the details I providedIdentified that the form wasn't working and debugged itExplained what data-netlify, name attributes, and fetch() do and why they're neededDecided to switch from Netlify Forms to Web3Forms when Netlify started chargingUpdated the form code to use the Web3Forms APIChose Vercel as the hosting platformExplained the deployment process step by stepDecided the README should showcase this for internship applicationsHelped format and structure this document

Using AI as a tool to build something real is a skill in itself. Knowing what to ask, how to debug, when to change direction, and how to evaluate output are all things I developed through this project.


✨ Features


Fully responsive — works on mobile, tablet, and desktop
Sticky navigation bar with smooth scroll to sections
Hero section with strong call-to-action
Trust bar highlighting key selling points
Services grid covering 6 job categories
3-step "How It Works" process section
Transparent pricing cards with featured tier
"Why Choose Us" differentiators section
Northern Virginia service area with 20 city tags
Customer quote request form with live submission handling
Spam protection via honeypot hidden field
Success confirmation message on form submit
Error handling if submission fails
Zero external frameworks — pure HTML, CSS, JavaScript



🗂️ File Structure

nova-haul-and-clear/
│
├── index.html        # Complete single-page website (all HTML, CSS, JS in one file)
└── README.md         # Project documentation

The entire site lives in a single index.html file. CSS is written in a <style> block in the <head> and JavaScript is in a <script> block before the closing </body> tag. This keeps deployment simple — one file is all you need to drag and drop to go live.


🎨 Design Breakdown

Color Palette

css:root {
  --ink: #1a1f1a;       /* Near-black for backgrounds and text */
  --green: #2d5c2d;     /* Forest green — primary brand color */
  --gold: #c8871a;      /* Gold — accent, CTAs, highlights */
  --bg: #f5f6f2;        /* Off-white — page background */
  --white: #ffffff;     /* Cards and elevated surfaces */
}

I chose this palette to feel trustworthy and professional without looking like a generic template. The dark charcoal + forest green + gold combination gives the site a bold, trade-business energy.

Typography

css/* Headlines */
font-family: 'Barlow Condensed', sans-serif;
font-weight: 800;

/* Body text */
font-family: 'Inter', sans-serif;
font-weight: 400;

Barlow Condensed gives the headlines a strong, no-nonsense feel. Inter keeps body text clean and readable at any size. Both are loaded from Google Fonts for free.

Layout System

The site uses CSS Grid for multi-column sections and Flexbox for navigation, badges, and inline groupings:

css/* Services grid — auto-fills columns based on screen width */
.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
}

/* Nav — space between logo and links */
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

Responsive Design

css@media (max-width: 640px) {
  .nav-links { display: none; }
  .hero { padding: 56px 5% 52px; }
  .form-grid { grid-template-columns: 1fr; }
}

On mobile, the nav links hide, the hero padding reduces, and the form collapses to a single column. The auto-fit grid means most sections reflow automatically without needing extra media queries.


📬 Form Handling

The quote request form submits to Web3Forms (free tier) using the fetch() API. Here's how it works:

javascript// Encode form data as URL parameters
function encode(data) {
  return Object.keys(data)
    .map(key => encodeURIComponent(key) + '=' + encodeURIComponent(data[key]))
    .join('&');
}

// Listen for form submit
document.getElementById('quoteForm').addEventListener('submit', function(e) {
  e.preventDefault(); // Stop the page from reloading

  fetch('https://api.web3forms.com/submit', {
    method: 'POST',
    headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
    body: encode(formData)
  })
  .then(() => {
    // Show success message
    document.getElementById('formSuccess').style.display = 'block';
  })
  .catch(() => {
    // Show error if submission fails
    alert('Something went wrong. Please call us directly.');
  });
});

Spam protection is handled by a honeypot field — a hidden input that real users never fill out, but bots do:

html<input type="hidden" name="botcheck" style="display:none">

If that field has a value when submitted, Web3Forms ignores the submission.


🚀 Deployment

The site is deployed on Vercel (free tier) connected to this GitHub repository.

How auto-deployment works:


I push any change to this repo
Vercel detects the new commit automatically
Vercel rebuilds and redeploys the site in under 30 seconds
The live URL updates with no manual steps


This is the same CI/CD workflow used in professional development teams.


📊 Business Strategy Behind the Site

This wasn't just a coding exercise — it was built to solve real business problems:


Local SEO: Service area section lists 20 NoVA cities so the site appears in location-based searches
Conversion focused: Every section ends with a path to the quote form
Trust signals: Upfront pricing, eco-friendly promise, and "locally owned" messaging address the top objections customers have
Realtor partnerships: Pricing section calls out realtors specifically — a high-value referral channel in the NoVA market
Competitor differentiation: Same-day service and donation-first disposal are called out repeatedly because research showed those are the two biggest gaps in the local market



📈 Next Steps


 Add before/after photo gallery section
 Integrate Google Analytics for traffic tracking
 Add Google Reviews widget
 Connect custom domain novahaulclear.com
 Add online booking / scheduling integration
 Build out a blog for local SEO content



🛠️ Tech Stack

ToolPurposeCostHTML5Page structureFreeCSS3Styling and layoutFreeJavaScriptForm handling, smooth scrollFreeGoogle FontsTypographyFreeWeb3FormsForm submission + email alertsFreeVercelHosting + auto-deploymentFreeGitHubVersion control + portfolioFree

Total cost to build and host this site: $0
