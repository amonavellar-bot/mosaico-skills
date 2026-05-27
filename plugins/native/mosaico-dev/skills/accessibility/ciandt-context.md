# CI&T Accessibility Context

> **Internal use only — CI&T employees.** This file contains internal contacts, tools, and resources specific to CI&T. Do not distribute externally.

For CI&T employees and the Mosaico group (grupo para pessoas com deficiência na CI&T).

## Internal Resources

- **Oráculo da Acessibilidade:** https://sites.google.com/ciandt.com/oraculo-da-acessibilidade/home
  The internal CI&T accessibility portal. It contains materials on laws and guidelines, assistive technology, validation tools, business perspective, business requirements, design and development best practices, accessibility testing, and a list of Flow agents related to accessibility.

- **Community:** Google Chat → `[CI&T] a11y / Acessibilidade`

- **Contacts:**
  - Eduardo Toledo Curti — @eduardo.curti
  - Jéssica Roberta de Lima — @jessicalima

## Laws and Regulations

### Brazil

**LBI — Lei Brasileira de Inclusão (Brazilian Law of Inclusion)**
A fundamental legal framework for the promotion of rights and social inclusion of people with disabilities in Brazil. It covers multiple aspects of life for people with disabilities and has direct implications for digital accessibility. The LBI does not define specific technical standards for digital accessibility like WCAG, but establishes accessibility as a fundamental right. This means all spaces and services — including digital ones — must be accessible to people with disabilities. The law imposes an obligation to make environments and services accessible through reasonable accommodations or assistive technologies.

### United States

**Section 508**
This law requires US federal agencies to ensure that the information and communication technologies (ICT) they acquire or use are accessible to people with disabilities. It directly affects government websites and applications, and is frequently used as a reference standard for the private sector.

**ADA — Americans with Disabilities Act**
Although not specific to the web, the ADA has been interpreted by some courts as applicable to websites and applications of private companies. The ADA prohibits discrimination against people with disabilities in public services and commercial establishments.

### European Union

**Directive (EU) 2016/2102**
This directive, which entered into force in 2016, establishes accessibility requirements for websites and mobile applications of public bodies in EU member states. It requires conformance with WCAG 2.1 Level AA as the accessibility standard.

## Assistive Technologies

Assistive technologies are tools and resources that help people with disabilities access and use computers and other digital devices, overcoming barriers to information and communication. They play a fundamental role in digital inclusion, enabling individuals with diverse special needs to fully participate in the digital society.

### Who Uses Assistive Technologies

- **Visual disabilities:** Screen readers, screen magnifiers, and text-to-speech software are essential for accessing information.
- **Motor disabilities:** Alternative keyboards, pointing devices, voice recognition software, and other aids are important for interacting with technology.
- **Cognitive disabilities:** Programs that facilitate organization and comprehension of information.
- **Dyslexia:** Software that assists with reading and writing, including correction and phonetic support features.
- **Deafness / Hard of hearing:** Captioning and transcription programs are essential for accessing audiovisual content.

### Screen Readers

Software that converts text and other screen elements into audio, enabling people with visual disabilities to access digital content. Screen readers work by interpreting semantic HTML code — this is why correct use of HTML is fundamental. Popular examples:

- **NVDA** (Windows, free and open source)
- **JAWS** (Windows, commercial)
- **TalkBack** (Android)
- **VoiceOver** (macOS and iOS)

### Screen Magnifiers

Programs that enlarge the computer screen, making it easier to view for people with low vision. They allow adjusting magnification level, contrast, and other settings to optimize readability.

- Windows built-in Magnifier

### Voice Recognition Software

Allows people with motor or visual disabilities to type text using voice commands.

- Windows native voice control
- Apple Voice Control
- Android Voice Control

## Validation Tools

Accessibility validation tools are essential for evaluating a site or application's conformance with WCAG (Web Content Accessibility Guidelines) and other accessibility standards. They help identify accessibility issues, enabling developers and designers to fix errors and improve the user experience for people with disabilities.

### Automatic Checkers

These tools analyze the source code of a site and identify common accessibility problems such as missing alternative text on images, low color contrast, and link issues. They are useful for quick analysis and identifying obvious errors, but do not replace a full manual evaluation. Automated tools can evaluate up to approximately 30% of accessibility defects.

- **WAVE (Web Accessibility Evaluation Tool):** A popular browser extension that highlights accessibility issues directly on the web page.
- **aXe (Accessibility Engine):** An open-source tool that can be integrated into different development workflows (such as IDE plugins) and runs accessibility tests. Also available as AXE DevTools.
- **Lighthouse (Google Chrome DevTools):** Includes an accessibility audit that checks various aspects including color contrast, alternative texts, and WCAG conformance.
- **Accessibility Insights for Web:** A Microsoft tool that helps identify accessibility barriers using multiple testing methods.
- **IBM Checker:** Tool for mapping hierarchy and validating accessibility.

### Color Contrast Tools

- **Accessible-Colors:** Validator for color contrast conformance.
- **WhoCanUse:** Simulates how different types of users perceive color combinations.
- **Colour Contrast Analyser:** Shows how different vision types perceive colors.

### Other Tools

- **Hierarchy tools:** For checking heading structure and reading order.
- **Readability tools:** For evaluating text legibility.
- **Alternative text tools:** For validating image descriptions.
- **Disability simulators:** For simulating the experience of users with various disabilities.
- **Bookmarklets:** Lightweight browser tools for quick accessibility checks.

### Testing Approaches

- **Automated tests:** Quick identification of common errors; covers ~30% of accessibility defects.
- **Manual tests:** Human evaluation using keyboard navigation and screen readers; catches what automation misses.
- **User tests:** Involving real people with disabilities to test usability and provide feedback.

**Testing organization methods:**
- **Checklists:** Based on WCAG criteria to ensure all fundamental aspects are covered.
- **Test cases:** Specific scenarios describing actions users would take, such as filling a form or navigating sections.
- **Combined approach:** Using checklists for baseline coverage and test cases for real-world scenario exploration.

**Testing team configurations:**
- **Pairs (recommended):** One sighted and one non-sighted tester provides diverse perspectives, cross-verification, and faster creative problem-solving. Requires more coordination.
- **Individual testers:** More autonomous and flexible but limited by single perspective and higher risk of missing issues.

## Business Case for Accessibility

Digital accessibility, often seen only as legal compliance or social responsibility, represents a significant growth and business opportunity. Investing in accessibility is not only the right thing to do — it is also strategic, generating tangible and intangible return on investment (ROI).

### ROI Benefits

- **Market expansion:** Making products and services accessible opens the business to a large and often underserved market. In Brazil, millions of people have some type of disability.
- **Improved User Experience (UX):** Accessibility practices frequently improve the experience for all users, not just people with disabilities. A well-structured site with intuitive navigation, adequate contrast, and clear content benefits everyone, increasing satisfaction and reducing bounce rates.
- **Better SEO:** Accessible sites tend to rank better in search engines. Search algorithms prioritize sites with better user experience, and accessibility contributes significantly to this.
- **Reduced litigation costs:** Lack of accessibility can lead to fines and lawsuits, generating significant costs. Investing in accessibility from the start avoids these risks.
- **Brand and reputation:** Demonstrating a commitment to inclusion and accessibility strengthens brand image, attracting customers and talent who value inclusion.

### Key Performance Indicators (KPIs) for Accessibility

- **Conversion rate:** Check whether conversion rates (purchase, sign-up, etc.) increased after implementing accessibility measures.
- **Bounce rate:** Observe whether bounce rate decreased.
- **Time on page:** Check whether users spend more time on pages after accessibility improvements.
- **Users with assistive technologies:** Monitor the number of users accessing the site using assistive technologies (via data analysis where possible).
- **Accessibility tool scores:** Use automatic tools to evaluate the accessibility score of the site — this score should improve over time.
- **User feedback:** Collect feedback from users, including those with disabilities, to identify areas for improvement.

## Key Statistics

### People with Disabilities

- More than **17% of the Brazilian population** has some type of disability (current data).
- Compared to 2010 data, **45% of the population** has some degree of disability (Censo Demográfico 2010 and PNS 2019 surveys).
- People with disabilities have an estimated **purchasing power of R$ 22 billion per year** in Brazil (Accenture study, 2018).
- Improved financial conditions for people with disabilities come from companies offering opportunities beyond legal hiring quotas.

### Elderly Population

- More than **30 million people aged 60 or older** in Brazil — approximately **17.7% of the total population**.
- The elderly population in Brazil **grew 57.4% in 12 years**.
- Elderly consumers account for **R$ 1.6 trillion in annual consumption**.
- With aging, many elderly people face challenges such as decreased vision, hearing, and motor skills. Accessible sites can offer simpler interfaces and more readable content.
- Elderly users tend to prefer practical and secure purchases, often choosing online channels that offer ease and comfort.

### Digitally Excluded / Low Digital Literacy

- **70% of the Brazilian population** has little or no experience with technology (Anatel Study, 2023).
- People with low digital literacy struggle to navigate complex sites. Digital accessibility allows these users to interact with intuitive interfaces and simplified content.

### Combined Market Opportunity

People with disabilities, the elderly, and digitally excluded users together represent a diverse and opportunity-rich market. Each group has unique characteristics influencing their choices: people with disabilities seek inclusive products, elderly users value convenience and well-being, and digitally excluded users tend to rely on traditional methods and personal recommendations. Understanding these groups is essential for companies seeking to stand out in an increasingly diverse market.

## Acceptance Criteria for Accessibility

When writing user stories, include accessibility in acceptance criteria from the start. The **Intopia Acceptance Criteria Generator** and **Magenta tool** can help — Magenta supports different components for both Web and native Apps, and can switch between Gherkin or condensed format.

### Example Acceptance Criteria

**Keyboard Navigation:**
- All interactive elements of the site must be accessible via keyboard.
- Users must be able to navigate the site using only the Tab and Enter keys, without a mouse.

**Color Contrast:**
- All text must have a contrast ratio of at least 4.5:1 against the background, per WCAG guidelines.

**Alternative Text for Images:**
- All images must include descriptive alternative text.
- Screen reader users must be able to understand the content and function of all images through their descriptions.

### Methods for Including Accessibility in Projects

1. Add accessibility requirements to acceptance criteria of existing user stories.
2. Create specific stories for users with disabilities (e.g., "As a blind user, I want to save my work so I can...").
3. Create broad stories for all users with disabilities (e.g., "As a person with a disability, I want an accessible experience in the system...").

## Development Best Practices (from Oráculo)

Nine key tips for accessible development:

1. **Know the accessibility guidelines** — WCAG provides clear recommendations for accessible web content.
2. **Use semantic HTML** — Use `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>` to structure content. Use `<label>` elements associated with form fields.
3. **Implement accessibility in CSS** — Do not use color alone to convey information. Use icons or alternative text. Check color contrast ratios.
4. **Create accessible navigation** — Ensure all interactive elements can be accessed and used via keyboard. Ensure visible focus styles.
5. **Use alternative text** — Always provide descriptive alt text for images, graphics, and videos. Provide captions and transcripts for video and audio.
6. **Test accessibility** — Use tools like WAVE, axe, or Lighthouse. When possible, involve real users with disabilities.
7. **Keep documentation accessible** — Use clear, direct language. Create accessibility guides for your team.
8. **Stay updated** — Attend workshops, webinars, and courses on accessibility. Participate in online communities.
9. **Integrate accessibility into the development cycle** — Include accessibility in early development phases, not just at the end. Check accessibility during code reviews.