<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Canva Crash Course</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@600;700&family=Manrope:wght@400;500;700;800&display=swap" rel="stylesheet">
  <style>
    :root {
      --panel: rgba(248, 239, 221, 0.96);
      --panel-soft: rgba(255, 248, 234, 0.86);
      --text: #2e1a40;
      --muted: #66507b;
      --purple: #71419b;
      --purple-deep: #29123f;
      --gold: #d7b15c;
      --red: #b43b4d;
      --green: #368856;
      --line: rgba(113, 65, 155, 0.15);
      --shadow: 0 24px 60px rgba(8, 2, 15, 0.35);
      --radius: 28px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }

    body {
      margin: 0;
      font-family: "Manrope", sans-serif;
      background:
        radial-gradient(circle at top left, rgba(215, 177, 92, 0.12), transparent 22%),
        radial-gradient(circle at 85% 15%, rgba(113, 65, 155, 0.24), transparent 24%),
        linear-gradient(160deg, #0f0618 0%, #1c0c2c 38%, #30124b 72%, #12081d 100%);
      color: #f9f0dc;
      line-height: 1.6;
      min-height: 100vh;
    }

    .page {
      width: min(1180px, calc(100% - 32px));
      margin: 0 auto;
      padding: 28px 0 56px;
    }

    .hero {
      position: relative;
      overflow: hidden;
      padding: 56px 42px;
      border-radius: 0 0 34px 34px;
      background: linear-gradient(140deg, #160920 0%, #341552 34%, #71419b 70%, #d7b15c 100%);
      box-shadow: var(--shadow);
      isolation: isolate;
    }

    .hero::before,
    .hero::after {
      content: "";
      position: absolute;
      border-radius: 50%;
      background: rgba(255,255,255,0.08);
      filter: blur(2px);
      z-index: -1;
    }

    .hero::before {
      width: 260px;
      height: 260px;
      top: -100px;
      right: -60px;
    }

    .hero::after {
      width: 180px;
      height: 180px;
      bottom: -60px;
      left: 10px;
    }

    .eyebrow,
    .section-label,
    .pill {
      display: inline-flex;
      align-items: center;
      padding: 7px 14px;
      border-radius: 999px;
      font-size: 11px;
      font-weight: 800;
      letter-spacing: 0.12em;
      text-transform: uppercase;
    }

    .eyebrow {
      background: rgba(255,255,255,0.14);
      border: 1px solid rgba(255,255,255,0.22);
      color: #fff5dd;
    }

    .section-label {
      background: rgba(215, 177, 92, 0.16);
      color: var(--purple);
      margin-bottom: 14px;
    }

    .pill {
      background: rgba(113, 65, 155, 0.1);
      color: var(--purple-deep);
      margin: 0 6px 8px 0;
      letter-spacing: 0.08em;
    }

    h1, h2, h3 {
      margin: 0;
      font-family: "Cinzel", serif;
      font-weight: 700;
      letter-spacing: 0.02em;
    }

    h1 {
      margin-top: 18px;
      font-size: clamp(2.6rem, 7vw, 5rem);
      line-height: 0.96;
      max-width: 11ch;
    }

    .hero p {
      max-width: 72ch;
      margin: 18px 0 0;
      font-size: 1.04rem;
      color: rgba(255, 248, 235, 0.92);
    }

    .hero-grid,
    .grid-2,
    .grid-3,
    .grid-4,
    .pdf-gallery {
      display: grid;
      gap: 16px;
      margin-top: 18px;
    }

    .hero-grid {
      grid-template-columns: repeat(4, minmax(0, 1fr));
      margin-top: 28px;
    }

    .grid-2 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
    .grid-3 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
    .grid-4 { grid-template-columns: repeat(4, minmax(0, 1fr)); }
    .pdf-gallery { grid-template-columns: repeat(2, minmax(0, 1fr)); }

    .hero-stat {
      padding: 16px;
      border-radius: 18px;
      background: rgba(255,255,255,0.12);
      border: 1px solid rgba(255,255,255,0.16);
      backdrop-filter: blur(8px);
    }

    .hero-stat strong {
      display: block;
      font-size: 1.2rem;
      margin-bottom: 4px;
      color: #fff5dd;
    }

    .section,
    .cta {
      margin-top: 18px;
      padding: 28px;
      background: var(--panel);
      color: var(--text);
      box-shadow: var(--shadow);
      border-radius: var(--radius);
      border: 1px solid rgba(255,255,255,0.28);
    }

    .section h2 {
      font-size: clamp(1.8rem, 4vw, 2.7rem);
      line-height: 1.02;
      margin-bottom: 12px;
    }

    .section p {
      margin: 0 0 14px;
      color: var(--muted);
    }

    .card,
    .lesson-card,
    .template-card,
    .warning-card,
    .pdf-page {
      background: var(--panel-soft);
      border: 1px solid var(--line);
      border-radius: 22px;
      padding: 18px;
    }

    .lesson-card { border-top: 4px solid var(--purple); }
    .warning-card { border-top: 4px solid var(--red); }
    .template-card { border-top: 4px solid var(--green); }

    .pdf-page {
      padding: 12px;
      overflow: hidden;
      border-top: 4px solid var(--purple);
    }

    .pdf-page img {
      display: block;
      width: 100%;
      border-radius: 14px;
      border: 1px solid rgba(113, 65, 155, 0.14);
    }

    .pdf-page span {
      display: block;
      margin-top: 10px;
      color: var(--purple-deep);
      font-weight: 800;
      font-size: 0.86rem;
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    .card h3,
    .lesson-card h3,
    .template-card h3,
    .warning-card h3 {
      font-size: 1.08rem;
      color: var(--purple-deep);
      margin-bottom: 8px;
    }

    ul,
    ol {
      margin: 0;
      padding-left: 20px;
      color: var(--muted);
    }

    li { margin-bottom: 8px; }

    code,
    pre {
      font-family: Consolas, "Courier New", monospace;
    }

    pre {
      white-space: pre-wrap;
      margin: 12px 0 0;
      padding: 14px;
      border-radius: 16px;
      background: rgba(41, 18, 63, 0.08);
      border: 1px solid rgba(113, 65, 155, 0.12);
      color: var(--purple-deep);
      font-weight: 700;
    }

    a {
      color: var(--purple-deep);
      font-weight: 800;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 18px;
      overflow: hidden;
      border-radius: 18px;
      background: rgba(255, 248, 234, 0.72);
    }

    th,
    td {
      padding: 13px 14px;
      text-align: left;
      border-bottom: 1px solid var(--line);
      vertical-align: top;
      color: var(--muted);
      font-size: 0.95rem;
    }

    th {
      color: var(--purple-deep);
      background: rgba(215, 177, 92, 0.18);
      font-weight: 800;
    }

    tr:last-child td { border-bottom: 0; }

    .quote {
      padding: 18px;
      margin-top: 18px;
      border-radius: 22px;
      background: linear-gradient(135deg, rgba(215, 177, 92, 0.18), rgba(113, 65, 155, 0.08));
      border: 1px solid rgba(215, 177, 92, 0.22);
      color: var(--purple-deep);
      font-weight: 700;
    }

    .cta {
      text-align: center;
      background: linear-gradient(135deg, rgba(41, 18, 63, 0.98), rgba(113, 65, 155, 0.92));
      color: #fff4de;
    }

    .cta h2 {
      font-size: clamp(1.9rem, 4vw, 3rem);
      margin-bottom: 12px;
    }

    .cta p {
      max-width: 66ch;
      margin: 0 auto;
      color: rgba(255, 243, 221, 0.88);
    }

    @media (max-width: 980px) {
      .hero-grid,
      .grid-2,
      .grid-3,
      .grid-4,
      .pdf-gallery {
        grid-template-columns: 1fr;
      }

      table,
      thead,
      tbody,
      th,
      td,
      tr {
        display: block;
      }

      th { display: none; }

      td {
        border-bottom: 0;
        padding: 10px 14px;
      }

      tr {
        border-bottom: 1px solid var(--line);
        padding: 8px 0;
      }
    }

    @media (max-width: 640px) {
      .page {
        width: min(100% - 16px, 1180px);
      }

      .hero,
      .section,
      .cta {
        padding: 22px;
      }
    }
  </style>
</head>
<body>
  <div class="page">
    <section class="hero">
      <span class="eyebrow">Module 7</span>
      <h1>Canva Crash Course</h1>
      <p>Learn how to use Canva to create clean social posts, digital products, lead magnets, mockups, thumbnails, and branded content without needing advanced design skills.</p>
      <div class="hero-grid">
        <div class="hero-stat">
          <strong>Create</strong>
          <span>Build posts, templates, workbooks, covers, and digital products</span>
        </div>
        <div class="hero-stat">
          <strong>Brand</strong>
          <span>Use consistent colors, fonts, logos, and layouts</span>
        </div>
        <div class="hero-stat">
          <strong>Batch</strong>
          <span>Make content faster with templates and repeatable systems</span>
        </div>
        <div class="hero-stat">
          <strong>Export</strong>
          <span>Download the right file type for social, print, products, or Canva sharing</span>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Why It Matters</div>
      <h2>Design Helps the Offer Feel Real</h2>
      <p>Canva gives beginners a fast way to make their ideas look professional. Students can create social content, digital downloads, sales graphics, mockups, worksheets, lead magnets, and simple brand assets without learning complicated design software.</p>
      <div class="quote">The goal is not to make every design fancy. The goal is to make every design clear, readable, branded, and useful.</div>
    </section>

    <section class="section">
      <div class="section-label">Course Companion</div>
      <h2>Canva Crash Course PDF</h2>
      <p>Use the companion PDF as an extra walkthrough resource while completing this module. Open it alongside the lessons, follow the setup steps, and use it as a quick reference when practicing inside Canva.</p>
      <div class="grid-2">
        <div class="template-card">
          <h3>Open the PDF</h3>
          <p>The PDF is stored locally in the main Codex Files folder so it stays with the module.</p>
          <pre>Canva Crash Course .pdf</pre>
          <div class="quote"><a href="file:///F:/COdex%20Files/Canva%20Crash%20Course.pdf">Open the Canva Crash Course PDF</a></div>
        </div>
        <div class="template-card">
          <h3>How to Use It</h3>
          <ol>
            <li>Open the PDF before starting Lesson 1.</li>
            <li>Keep Canva open in another tab.</li>
            <li>Practice each step instead of only reading.</li>
            <li>Save one finished design after every major section.</li>
            <li>Add notes about anything you want to turn into a student worksheet.</li>
          </ol>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">PDF Preview</div>
      <h2>Visual Pages From the Canva Crash Course</h2>
      <p>These page images were pulled from the companion PDF so students can preview the course visually inside this module.</p>
      <div class="pdf-gallery">
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-01.jpg" alt="Canva Crash Course PDF page 1"><span>Page 1</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-02.jpg" alt="Canva Crash Course PDF page 2"><span>Page 2</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-03.jpg" alt="Canva Crash Course PDF page 3"><span>Page 3</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-04.jpg" alt="Canva Crash Course PDF page 4"><span>Page 4</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-05.jpg" alt="Canva Crash Course PDF page 5"><span>Page 5</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-06.jpg" alt="Canva Crash Course PDF page 6"><span>Page 6</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-07.jpg" alt="Canva Crash Course PDF page 7"><span>Page 7</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-08.jpg" alt="Canva Crash Course PDF page 8"><span>Page 8</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-09.jpg" alt="Canva Crash Course PDF page 9"><span>Page 9</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-10.jpg" alt="Canva Crash Course PDF page 10"><span>Page 10</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-11.jpg" alt="Canva Crash Course PDF page 11"><span>Page 11</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-12.jpg" alt="Canva Crash Course PDF page 12"><span>Page 12</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-13.jpg" alt="Canva Crash Course PDF page 13"><span>Page 13</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-14.jpg" alt="Canva Crash Course PDF page 14"><span>Page 14</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-15.jpg" alt="Canva Crash Course PDF page 15"><span>Page 15</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-16.jpg" alt="Canva Crash Course PDF page 16"><span>Page 16</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-17.jpg" alt="Canva Crash Course PDF page 17"><span>Page 17</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-18.jpg" alt="Canva Crash Course PDF page 18"><span>Page 18</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-19.jpg" alt="Canva Crash Course PDF page 19"><span>Page 19</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-20.jpg" alt="Canva Crash Course PDF page 20"><span>Page 20</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-21.jpg" alt="Canva Crash Course PDF page 21"><span>Page 21</span></div>
        <div class="pdf-page"><img src="assets/canva-crash-course-pdf/canva-pdf-page-22.jpg" alt="Canva Crash Course PDF page 22"><span>Page 22</span></div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Module Promise</div>
      <h2>What Students Will Learn</h2>
      <div class="grid-3">
        <div class="card">
          <h3>Canva Basics</h3>
          <p>Students learn how to start designs, use templates, edit text, swap images, organize pages, and download files.</p>
        </div>
        <div class="card">
          <h3>Brand Setup</h3>
          <p>Students learn how to choose brand colors, fonts, logos, and repeatable design styles for consistency.</p>
        </div>
        <div class="card">
          <h3>Social Content</h3>
          <p>Students learn how to create posts, carousels, story graphics, YouTube thumbnails, and product promo graphics.</p>
        </div>
        <div class="card">
          <h3>Digital Products</h3>
          <p>Students learn how to create checklists, planners, ebooks, worksheets, prompt packs, and printable resources.</p>
        </div>
        <div class="card">
          <h3>Mockups</h3>
          <p>Students learn how to present digital products visually so buyers understand what they are getting.</p>
        </div>
        <div class="card">
          <h3>Exporting</h3>
          <p>Students learn when to use PNG, JPG, PDF, transparent background, and Canva template links.</p>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Lesson Plan</div>
      <h2>Full Module Outline</h2>
      <div class="grid-2">
        <div class="lesson-card">
          <span class="pill">Lesson 1</span>
          <h3>Canva Basics and Dashboard Tour</h3>
          <p>Students should learn where to start before designing. Canva can feel overwhelming because there are so many templates, tools, and file types. The first goal is confidence.</p>
          <ul>
            <li>Create a design from a template or custom size.</li>
            <li>Understand the editor: pages, toolbar, side panel, elements, uploads, text, and design tabs.</li>
            <li>Use folders to organize brand assets, products, social posts, and client work.</li>
            <li>Rename designs clearly so they are easy to find later.</li>
            <li>Duplicate designs instead of rebuilding from scratch.</li>
          </ul>
          <div class="quote">Student task: create one Instagram post from a template and rename it with a clear file name.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 2</span>
          <h3>Brand Kit and Visual Consistency</h3>
          <p>Canva's Brand Kit helps keep logos, fonts, colors, imagery, and brand assets in one place for consistent designs. Students can also create a manual brand guide if they are using a free account.</p>
          <ul>
            <li>Choose 2 to 4 brand colors.</li>
            <li>Choose 1 headline font and 1 body font.</li>
            <li>Upload logos, icons, photos, and product images.</li>
            <li>Create a simple brand board with colors, font names, and design examples.</li>
            <li>Use the same spacing, buttons, and title styles across content.</li>
          </ul>
          <div class="quote">Design rule: consistency builds trust faster than constantly changing styles.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 3</span>
          <h3>Editing Templates Without Making Them Messy</h3>
          <p>Templates are a shortcut, but students need to edit with intention. A good template can become confusing if too many fonts, colors, stickers, and text blocks are added.</p>
          <ul>
            <li>Start with a template close to the final goal.</li>
            <li>Replace the text before changing decoration.</li>
            <li>Keep margins and spacing clean.</li>
            <li>Use no more than 2 main fonts in one design.</li>
            <li>Use high contrast so text is readable.</li>
            <li>Delete elements that do not support the message.</li>
          </ul>
          <div class="quote">Template rule: customize the message first, then the style.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 4</span>
          <h3>Social Media Graphics</h3>
          <p>Students can use Canva to create feed posts, carousels, quote graphics, story slides, live reminders, promo graphics, and thumbnails. The content should be easy to read on a phone.</p>
          <ul>
            <li>Use large, clear headlines.</li>
            <li>Put one main idea per slide.</li>
            <li>Keep text short for feed posts and story graphics.</li>
            <li>Use carousel slides to teach a step-by-step idea.</li>
            <li>Use brand colors and repeated layouts to batch faster.</li>
            <li>Design with mobile readability first.</li>
          </ul>
          <div class="quote">Student task: create a 5-slide carousel from one tip in your niche.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 5</span>
          <h3>Digital Products and Lead Magnets</h3>
          <p>Canva is useful for creating beginner-friendly digital products. Students can turn their knowledge into simple resources people can download and use.</p>
          <ul>
            <li>Checklists.</li>
            <li>Workbooks.</li>
            <li>Planners.</li>
            <li>Prompt packs.</li>
            <li>Mini ebooks.</li>
            <li>Templates.</li>
            <li>Printable trackers.</li>
          </ul>
          <div class="quote">Product rule: the resource should help the buyer complete one clear task, not overwhelm them with everything you know.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 6</span>
          <h3>Product Covers and Mockups</h3>
          <p>Mockups help buyers understand what the product is. A PDF, checklist, or template pack feels more real when it has a cover, preview image, or product display graphic.</p>
          <ul>
            <li>Create a front cover for guides and workbooks.</li>
            <li>Use mockup frames for phones, laptops, tablets, books, and pages.</li>
            <li>Show what is inside without giving away everything.</li>
            <li>Use mockups on store pages, sales graphics, and promo posts.</li>
            <li>Keep mockups honest: do not make the product look bigger than it is.</li>
          </ul>
          <div class="quote">Student task: create one product cover and one mockup graphic for a digital download.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 7</span>
          <h3>Canva AI and Magic Studio</h3>
          <p>Canva Magic Studio includes AI tools that can help generate designs, images, text, and visual ideas. Students should use AI as a creative assistant, then edit the output to match the brand and message.</p>
          <ul>
            <li>Use AI to brainstorm design ideas.</li>
            <li>Use Magic Write to draft text ideas, captions, and product descriptions.</li>
            <li>Use AI image tools when a unique visual is needed.</li>
            <li>Review every AI-generated design for accuracy and brand fit.</li>
            <li>Do not use AI to create fake proof, fake testimonials, or misleading product examples.</li>
          </ul>
          <div class="quote">AI rule: generate faster, but still edit like a human with taste and honesty.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 8</span>
          <h3>Exporting the Right File Type</h3>
          <p>Students should download the right file for the job. The wrong export can make designs blurry, too large, hard to edit, or unusable for buyers.</p>
          <ul>
            <li>PNG: best for crisp social graphics and images with text.</li>
            <li>JPG: good for photos and smaller image files.</li>
            <li>PDF Standard: good for digital downloads and email delivery.</li>
            <li>PDF Print: better for high-quality print files.</li>
            <li>Transparent PNG: useful for logos, stickers, and overlays when available.</li>
            <li>Canva template link: use when buyers need to edit their own copy.</li>
          </ul>
          <div class="quote">Student task: export the same design as PNG and PDF, then compare when each one should be used.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 9</span>
          <h3>Batch Creating Content</h3>
          <p>Batching helps students create more content in less time. Instead of designing every post from zero, students should build repeatable layouts.</p>
          <ul>
            <li>Create 3 to 5 reusable post templates.</li>
            <li>Create a carousel template.</li>
            <li>Create a product promo template.</li>
            <li>Create a quote or tip graphic template.</li>
            <li>Duplicate, rewrite, and adjust instead of rebuilding every time.</li>
            <li>Save finished graphics in organized folders.</li>
          </ul>
          <div class="quote">Batching system: one hour to create templates, one hour to fill them with weekly content.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 10</span>
          <h3>Design Review Before Publishing</h3>
          <p>Before posting or selling a Canva design, students should check clarity, readability, spelling, spacing, and file type. Small mistakes can make a strong product feel rushed.</p>
          <ul>
            <li>Can the headline be read on a phone?</li>
            <li>Is the text too crowded?</li>
            <li>Are the colors consistent?</li>
            <li>Are there typos?</li>
            <li>Does the design match the offer?</li>
            <li>Is the file exported correctly?</li>
            <li>Did the student test the download link?</li>
          </ul>
          <div class="quote">Final rule: if the buyer cannot understand it in seconds, simplify the design.</div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Design Rules</div>
      <h2>Simple Design Rules for Beginners</h2>
      <table>
        <thead>
          <tr>
            <th>Rule</th>
            <th>Why It Matters</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Use fewer fonts.</td><td>Too many fonts make designs look messy and harder to read.</td></tr>
          <tr><td>Use contrast.</td><td>Text should stand out clearly from the background.</td></tr>
          <tr><td>Leave space.</td><td>White space makes designs feel cleaner and more professional.</td></tr>
          <tr><td>Align elements.</td><td>Aligned text and images make designs feel intentional.</td></tr>
          <tr><td>Repeat styles.</td><td>Repeated colors, fonts, and layouts create brand consistency.</td></tr>
          <tr><td>Design for mobile first.</td><td>Most social content is viewed on small screens.</td></tr>
        </tbody>
      </table>
    </section>

    <section class="section">
      <div class="section-label">Templates</div>
      <h2>Student Project Ideas</h2>
      <div class="grid-3">
        <div class="template-card"><h3>Social Pack</h3><p>Create 10 branded feed posts, 5 story slides, and 3 promo graphics.</p></div>
        <div class="template-card"><h3>Lead Magnet</h3><p>Create a 3-page checklist or mini guide that can be used for email list building.</p></div>
        <div class="template-card"><h3>Digital Product</h3><p>Create a simple workbook, prompt pack, planner, or printable tracker.</p></div>
        <div class="template-card"><h3>Product Mockups</h3><p>Create 3 mockup graphics for a store page and social media promotion.</p></div>
        <div class="template-card"><h3>Brand Board</h3><p>Create one page with colors, fonts, logo, photo style, and sample graphics.</p></div>
        <div class="template-card"><h3>Carousel</h3><p>Create a 5 to 7 slide carousel that teaches one beginner-friendly concept.</p></div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Checklists</div>
      <h2>Student Downloads to Include</h2>
      <div class="grid-2">
        <div class="template-card">
          <h3>Canva Design Checklist</h3>
          <ol>
            <li>Design title is clear.</li>
            <li>Headline is readable on mobile.</li>
            <li>Only 1 to 2 fonts are used.</li>
            <li>Colors match the brand.</li>
            <li>Text has enough contrast.</li>
            <li>Spacing is clean.</li>
            <li>Images are not blurry.</li>
            <li>File type is correct.</li>
            <li>Links and downloads are tested.</li>
          </ol>
        </div>
        <div class="template-card">
          <h3>Digital Product Checklist</h3>
          <ol>
            <li>Product solves one clear problem.</li>
            <li>Cover page is clean and branded.</li>
            <li>Inside pages are easy to read.</li>
            <li>Instructions are clear.</li>
            <li>File is exported as PDF when needed.</li>
            <li>Mockup graphic is created.</li>
            <li>Store image is created.</li>
            <li>Buyer access or template link is tested.</li>
          </ol>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Common Mistakes</div>
      <h2>What Students Should Avoid</h2>
      <div class="grid-3">
        <div class="warning-card">
          <h3>Too Much Text</h3>
          <p>If a social graphic looks like a paragraph, turn it into a carousel or simplify the message.</p>
        </div>
        <div class="warning-card">
          <h3>Unreadable Fonts</h3>
          <p>Pretty fonts are not useful if people cannot read them quickly on a phone.</p>
        </div>
        <div class="warning-card">
          <h3>No Brand Consistency</h3>
          <p>Changing colors and fonts every time makes the brand harder to recognize.</p>
        </div>
        <div class="warning-card">
          <h3>Wrong File Type</h3>
          <p>A buyer who needs an editable template should not receive only a flat PNG or JPG.</p>
        </div>
        <div class="warning-card">
          <h3>Fake Mockups</h3>
          <p>Do not make a product look bigger, deeper, or more complete than it really is.</p>
        </div>
        <div class="warning-card">
          <h3>Not Testing Links</h3>
          <p>Always test PDF links, Canva template links, downloads, and sharing permissions before selling.</p>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Knowledge Check</div>
      <h2>Quick Student Quiz</h2>
      <div class="grid-2">
        <div class="card">
          <h3>Question 1</h3>
          <p>What is the best file type for most social graphics with text?</p>
          <div class="quote">Answer: PNG, because it usually keeps text and graphics crisp.</div>
        </div>
        <div class="card">
          <h3>Question 2</h3>
          <p>What should students use if buyers need to edit the design themselves?</p>
          <div class="quote">Answer: A Canva template link with the correct sharing permissions.</div>
        </div>
        <div class="card">
          <h3>Question 3</h3>
          <p>Why are mockups helpful?</p>
          <div class="quote">Answer: They help buyers understand what the product looks like and what they receive.</div>
        </div>
        <div class="card">
          <h3>Question 4</h3>
          <p>What should students do before posting or selling a design?</p>
          <div class="quote">Answer: Review readability, spelling, spacing, brand consistency, export type, and links.</div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Sources</div>
      <h2>Research Links</h2>
      <p>Use these as platform references when recording walkthroughs or updating student resources.</p>
      <ul>
        <li><a href="https://www.canva.com/learn/how-to-canva-beginners-guide/">Canva: Beginner's Guide</a></li>
        <li><a href="https://www.canva.com/learn/a-step-by-step-guide-to-designing-from-scratch/">Canva: Designing From Scratch</a></li>
        <li><a href="https://www.canva.com/pro/brand-kit/">Canva: Brand Kit</a></li>
        <li><a href="https://www.canva.com/business/features/brand/">Canva: Brand Features</a></li>
        <li><a href="https://www.canva.com/magic/">Canva: Magic Studio</a></li>
        <li><a href="https://www.canva.com/newsroom/news/magic-studio/">Canva: Magic Studio Overview</a></li>
      </ul>
    </section>

    <section class="cta">
      <h2>Create Faster, Design Cleaner</h2>
      <p>Canva helps students turn ideas into real assets. Start with simple layouts, stay consistent, make the message clear, and export the right file for the job.</p>
    </section>
  </div>
</body>
</html>

