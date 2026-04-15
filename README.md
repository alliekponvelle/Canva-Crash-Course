

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Business Backend and Store Setup</title>
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
      --gold-deep: #9b7427;
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
      max-width: 12ch;
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
    .grid-4 {
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
    .platform-card {
      background: var(--panel-soft);
      border: 1px solid var(--line);
      border-radius: 22px;
      padding: 18px;
    }

    .lesson-card,
    .platform-card {
      border-top: 4px solid var(--purple);
    }

    .warning-card {
      border-top: 4px solid var(--red);
    }

    .template-card {
      border-top: 4px solid var(--green);
    }

    .card h3,
    .lesson-card h3,
    .template-card h3,
    .warning-card h3,
    .platform-card h3 {
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
      .grid-4 {
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
      <span class="eyebrow">Module 4</span>
      <h1>Business Backend and Store Setup</h1>
      <p>Build a creator store that is simple on the outside and organized behind the scenes. Learn how to choose a platform, set up payments, add offers, deliver products, connect social traffic, and track what is working.</p>
      <div class="hero-grid">
        <div class="hero-stat">
          <strong>Set Up</strong>
          <span>Create the store, bio, products, links, payments, and support path</span>
        </div>
        <div class="hero-stat">
          <strong>Choose</strong>
          <span>Know when to use Stan, Beacons, Shopify, or a simple link hub</span>
        </div>
        <div class="hero-stat">
          <strong>Deliver</strong>
          <span>Make sure buyers receive files, links, confirmation emails, and next steps</span>
        </div>
        <div class="hero-stat">
          <strong>Improve</strong>
          <span>Use clicks, views, sales, and placement tests to increase conversions</span>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Beginner Basics</div>
      <h2>Setting Up Your Creator Store</h2>
      <p>Every creator store needs a few basic things. Your store should be easy to understand in seconds.</p>
      <div class="grid-2">
        <div class="template-card">
          <h3>Quick Store Setup Checklist</h3>
          <ol>
            <li>Create your account.</li>
            <li>Write a clear bio.</li>
            <li>Add your first offer.</li>
            <li>Connect payments.</li>
            <li>Add your store link to your social bio.</li>
            <li>Mention your store in your content.</li>
            <li>Keep the layout simple.</li>
          </ol>
        </div>
        <div class="card">
          <h3>Store Rule</h3>
          <p>People should instantly understand who the store is for, what the main offer is, and what action to take next.</p>
          <div class="quote">Simple stores usually convert better than cluttered stores because buyers do not have to think so hard.</div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Module Promise</div>
      <h2>What Students Will Learn</h2>
      <div class="grid-3">
        <div class="card">
          <h3>Platform Choice</h3>
          <p>Students learn how to choose between Stan, Beacons, Shopify, and a link-in-bio setup based on their offer type.</p>
        </div>
        <div class="card">
          <h3>Payment Setup</h3>
          <p>Students learn how Stripe, PayPal, bank accounts, payouts, currency, and payment options fit into the backend.</p>
        </div>
        <div class="card">
          <h3>Product Pages</h3>
          <p>Students learn how to write clear titles, descriptions, prices, calls-to-action, and post-purchase instructions.</p>
        </div>
        <div class="card">
          <h3>Delivery Flow</h3>
          <p>Students learn how buyers access files, links, courses, coaching, custom products, and confirmation emails.</p>
        </div>
        <div class="card">
          <h3>Store Organization</h3>
          <p>Students learn how to put the main offer first, avoid too many options, and create a clean buying path.</p>
        </div>
        <div class="card">
          <h3>Performance Tracking</h3>
          <p>Students learn how to watch clicks, views, sales, placement, price, and description changes.</p>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Lesson Plan</div>
      <h2>Full Module Outline</h2>
      <div class="grid-2">
        <div class="lesson-card">
          <span class="pill">Lesson 1</span>
          <h3>The Creator Store Backend</h3>
          <p>The front of the store should look simple, but the backend needs structure. Students should know where the buyer goes, how the payment is processed, how the product is delivered, and how support is handled.</p>
          <p>Think of the backend as the invisible system that keeps the business from feeling messy. A buyer should never have to wonder if the payment worked, where the product is, who to contact, or what happens next.</p>
          <ul>
            <li>Store page or link-in-bio page.</li>
            <li>Offer page or checkout page.</li>
            <li>Payment processor.</li>
            <li>Delivery method.</li>
            <li>Support email or contact path.</li>
            <li>Analytics and sales tracking.</li>
          </ul>
          <div class="quote">Student task: draw your buyer path from social post to store click, product page, checkout, delivery email, and support contact.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 2</span>
          <h3>Choosing the Right Store Platform</h3>
          <p>Students should choose a platform based on what they are selling, not just what is trending.</p>
          <p>A beginner selling one digital guide does not need the same setup as someone selling 30 physical products. The best platform is the one that makes the next sale easier without adding unnecessary work.</p>
          <ul>
            <li>Use Stan for direct-selling digital products, coaching, courses, and services.</li>
            <li>Use Beacons when you need a simple bio hub with links, resources, affiliate links, and digital offers.</li>
            <li>Use Shopify when you need a fuller ecommerce store with collections, products, shipping, and more store control.</li>
            <li>Use a link hub only when the buyer needs simple navigation, not a full sales funnel.</li>
          </ul>
          <div class="quote">Decision shortcut: if your store needs checkout plus a simple offer page, start with Stan or Beacons. If you need product collections, shipping, inventory, and a full storefront, consider Shopify.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 3</span>
          <h3>Adding Products to Your Store</h3>
          <p>Every offer should be clear. People should understand what they are buying before they click checkout.</p>
          <p>The product page should answer the buyer's silent questions: What is this? Is it for me? What do I get? How fast do I get it? What do I do after purchase?</p>
          <ul>
            <li>Clear title.</li>
            <li>Short description.</li>
            <li>Visible price.</li>
            <li>Simple call-to-action.</li>
            <li>Product image or thumbnail.</li>
            <li>What is included.</li>
            <li>How it is delivered.</li>
          </ul>
          <div class="quote">Example: "Creator Bio Template Pack" is clearer than "Glow Up Your Page." Creative names can work, but the buyer still needs to understand the offer fast.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 4</span>
          <h3>Connecting Payments</h3>
          <p>Payments are not just a button. Students need to know what processor they are using, how payouts happen, and what customers will see at checkout.</p>
          <p>Before promoting, students should confirm that payments are connected, account verification is complete, payout details are correct, and the checkout page actually lets a buyer complete the order.</p>
          <ul>
            <li>Stripe usually handles credit cards, debit cards, Apple Pay, and Google Pay where available.</li>
            <li>PayPal allows customers to pay with PayPal and may support Pay Later options where available.</li>
            <li>Stan supports Stripe and PayPal, but Stan's Stripe setup uses a Stan-managed custom Stripe flow.</li>
            <li>Beacons supports Stripe and PayPal for store payments.</li>
            <li>Students should verify their account, bank details, business details, and support contact information.</li>
          </ul>
          <div class="quote">Student task: complete a test purchase or checkout preview before announcing the store publicly.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 5</span>
          <h3>Digital Product Delivery</h3>
          <p>Students need a reliable delivery process so buyers get what they paid for and support issues stay low.</p>
          <p>Delivery is part of the customer experience. If the buyer pays and cannot find the file, the seller may get DMs, refund requests, bad reviews, or chargebacks. The smoother the delivery, the more professional the store feels.</p>
          <ul>
            <li>Stan buyers can access digital products from the confirmation page and confirmation email.</li>
            <li>Beacons buyers can access digital products from the success screen and confirmation email.</li>
            <li>Beacons says access links are active for 7 days after purchase, so creators may need to resend order emails when needed.</li>
            <li>Students should test checkout, delivery email, download links, and support links before launching.</li>
          </ul>
          <div class="quote">Best practice: keep a backup folder with product files, sales page screenshots, refund policy, and buyer support instructions.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 6</span>
          <h3>Selling Custom AI Content</h3>
          <p>Custom AI content can be sold through a creator store, but the offer needs clear expectations.</p>
          <p>This type of offer should be treated like a service, not just a download. Students need an intake process, turnaround time, revision rules, and delivery instructions so buyers know exactly what happens after checkout.</p>
          <ul>
            <li>AI portraits.</li>
            <li>AI scene images.</li>
            <li>Custom AI videos.</li>
            <li>Personalized creative content.</li>
            <li>State turnaround time, revision limit, what the buyer must submit, and delivery method.</li>
          </ul>
          <div class="quote">Example intake fields: name, email, reference photo, preferred style, colors, text to include, usage goal, and any details to avoid.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 7</span>
          <h3>Connecting Your Store to Social Media</h3>
          <p>Content should send people to the store naturally. The store is where attention turns into action.</p>
          <p>The content should create the reason to click. A store link by itself does not sell much if the content never explains the problem, the outcome, or the next step.</p>
          <ul>
            <li>Add the store link in your bio.</li>
            <li>Mention the offer in videos.</li>
            <li>Mention the store during live streams.</li>
            <li>Use clear calls-to-action like: "Link in my bio if you want the full guide."</li>
            <li>Match the product at the top of the store to the content you are promoting that week.</li>
          </ul>
          <div class="quote">Content formula: teach one useful thing, name the bigger problem, then invite viewers to the store for the full resource.</div>
        </div>

        <div class="lesson-card">
          <span class="pill">Lesson 8</span>
          <h3>Tracking and Improving Store Performance</h3>
          <p>Students should pay attention to their data and make small improvements instead of rebuilding everything at once.</p>
          <p>Store data tells students where the problem might be. If views are low, the content may not be sending enough traffic. If clicks are high but sales are low, the product page, price, offer, or trust signals may need work.</p>
          <ul>
            <li>Track clicks.</li>
            <li>Track views.</li>
            <li>Track sales.</li>
            <li>Move the main offer higher if it gets attention but not clicks.</li>
            <li>Change the title or description if people do not understand the offer.</li>
            <li>Adjust the price or bonus if clicks are strong but sales are low.</li>
          </ul>
          <div class="quote">Simple test: change one thing at a time, then watch what happens for 7 days before making another change.</div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Platform Deep Dive</div>
      <h2>Stan vs. Beacons vs. Shopify</h2>
      <table>
        <thead>
          <tr>
            <th>Platform</th>
            <th>Best For</th>
            <th>Watch For</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Stan Store</td>
            <td>Digital products, coaching, courses, services, funnels, and clean sales pages.</td>
            <td>Requires payment processor setup. At least one product/service and a social link or contact info may be needed before processor verification.</td>
          </tr>
          <tr>
            <td>Beacons</td>
            <td>Bio link hub, resource lists, affiliate links, digital offers, and fast creator storefronts.</td>
            <td>Beacons is strong for link-in-bio simplicity. For direct product sales, students still need product files/links, payment setup, and clear checkout settings.</td>
          </tr>
          <tr>
            <td>Shopify</td>
            <td>Full ecommerce stores, physical products, product collections, shipping workflows, and brand storefronts.</td>
            <td>More powerful, but more setup. Students need product descriptions, pricing, policies, payments, taxes, shipping, and theme organization.</td>
          </tr>
        </tbody>
      </table>
    </section>

    <section class="section">
      <div class="section-label">Stan Store</div>
      <h2>Stan Store Setup Notes</h2>
      <div class="grid-2">
        <div class="platform-card">
          <h3>When to Use Stan</h3>
          <p>Stan Store works well for direct selling.</p>
          <ul>
            <li>Digital products.</li>
            <li>Coaching.</li>
            <li>Courses.</li>
            <li>Services.</li>
            <li>Clean sales pages.</li>
          </ul>
        </div>
        <div class="platform-card">
          <h3>Setup Reminders</h3>
          <ul>
            <li>Stan supports Stripe and PayPal.</li>
            <li>Stan's Stripe setup creates a Stan-managed custom Stripe account.</li>
            <li>Stan says PayPal setup requires a PayPal Business account.</li>
            <li>If PayPal and Stripe are both connected, customers can see both checkout options.</li>
            <li>If the store says "Sold Out," Stan says the creator may need to connect a payment processor.</li>
          </ul>
        </div>
      </div>
      <div class="quote">Your existing resource: <a href="https://youtu.be/aS11ZfwG5Wk?si=kq9hDNkSYEHYl04W">How to set up a Stan Store</a> and affiliate link: <a href="https://join.stan.store/AlliePonvelle">join.stan.store/AlliePonvelle</a></div>
    </section>

    <section class="section">
      <div class="section-label">Beacons Store</div>
      <h2>Beacons Store Setup Notes</h2>
      <div class="grid-2">
        <div class="platform-card">
          <h3>When to Use Beacons</h3>
          <p>Beacons works great as a bio link hub and simple creator storefront.</p>
          <ul>
            <li>Resource lists.</li>
            <li>Affiliate links.</li>
            <li>Digital offers.</li>
            <li>Quick access pages.</li>
            <li>Simple creator setups.</li>
          </ul>
        </div>
        <div class="platform-card">
          <h3>Setup Reminders</h3>
          <ul>
            <li>Beacons supports Stripe and PayPal for store payments.</li>
            <li>Stripe can support cards, Apple Pay, and Google Pay where available.</li>
            <li>Beacons product access can happen through the success screen and confirmation email.</li>
            <li>Beacons says digital product access links are active for 7 days after purchase.</li>
            <li>Beacons allows digital product files or URL delivery.</li>
          </ul>
        </div>
      </div>
      <div class="quote">Your existing resource: <a href="https://youtube.com/playlist?list=PLdMWlA48UlTQn156o6czhjIGzPH8lMVPu&si=LGWvPPLyBfKfIkPu">Beacons setup playlist</a> and affiliate link: <a href="https://beacons.ai/signup?c=allieponvelle">beacons.ai/signup?c=allieponvelle</a></div>
    </section>

    <section class="section">
      <div class="section-label">Store Layout</div>
      <h2>Organizing Your Store</h2>
      <div class="grid-2">
        <div class="template-card">
          <h3>Best Layout</h3>
          <ol>
            <li>Main offer first.</li>
            <li>Most important products at the top.</li>
            <li>Free lead magnet or starter resource near the top if list building matters.</li>
            <li>Affiliate links below core offers.</li>
            <li>Do not overload the page.</li>
          </ol>
        </div>
        <div class="card">
          <h3>Decision Rule</h3>
          <p>If the buyer has to scroll through too many unrelated offers, they may leave without buying. Keep the page focused on the next action you want them to take.</p>
          <div class="quote">Too many options can confuse buyers. A clear first offer creates a cleaner path to the sale.</div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Promotion</div>
      <h2>Promoting Your Store Through Content</h2>
      <p>Your content should naturally lead to your store. Give value first, then invite viewers to the next step.</p>
      <div class="grid-3">
        <div class="template-card">
          <h3>Simple CTA</h3>
          <pre>Link in my bio if you want the full guide.</pre>
        </div>
        <div class="template-card">
          <h3>Problem-Solution CTA</h3>
          <pre>If this is what you are stuck on, I made a step-by-step resource for you. It is linked in my store.</pre>
        </div>
        <div class="template-card">
          <h3>Live Stream CTA</h3>
          <pre>If you want the checklist I am talking about, go to the link in my bio and tap the first product.</pre>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Backend Trust</div>
      <h2>Before You Launch Checklist</h2>
      <div class="grid-2">
        <div class="template-card">
          <h3>Store Trust Checklist</h3>
          <ol>
            <li>Clear bio or store intro.</li>
            <li>At least one support contact method.</li>
            <li>Payment processor connected and verified.</li>
            <li>Main offer tested from checkout to delivery.</li>
            <li>Refund policy visible before purchase.</li>
            <li>Product delivery email checked.</li>
            <li>Store link added to social bio.</li>
            <li>Product title and button text are easy to understand.</li>
          </ol>
        </div>
        <div class="template-card">
          <h3>Product Page Checklist</h3>
          <ol>
            <li>Title says what the product is.</li>
            <li>Description explains who it helps.</li>
            <li>Price is visible.</li>
            <li>CTA tells the buyer what to do.</li>
            <li>Includes what the buyer receives.</li>
            <li>Includes how and when they receive it.</li>
            <li>Includes refund/access notes.</li>
            <li>Includes support contact.</li>
          </ol>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Templates</div>
      <h2>Copy and Paste Swipe File</h2>
      <div class="grid-2">
        <div class="template-card">
          <h3>Store Bio</h3>
          <pre>I help [audience] [result] with simple digital tools, creator resources, and step-by-step guides.</pre>
        </div>
        <div class="template-card">
          <h3>Digital Product Description</h3>
          <pre>This [guide/template/checklist] helps you [specific result]. Inside, you will get [main items included]. It is best for [audience] who want [clear outcome].</pre>
        </div>
        <div class="template-card">
          <h3>Custom AI Content Offer</h3>
          <pre>Get a custom [AI portrait / AI scene / AI video] created for your brand. After purchase, you will receive instructions for submitting your details. Delivery time: [timeframe]. Includes [number] revision.</pre>
        </div>
        <div class="template-card">
          <h3>Post-Purchase Email</h3>
          <pre>Thank you for your purchase. Your access link is below. Please save this email. If you have trouble accessing your product, contact [support email] and include your order email.</pre>
        </div>
        <div class="template-card">
          <h3>Refund Policy</h3>
          <pre>Because this is a digital product with instant access, all sales are final once the product has been delivered or accessed. If you have trouble accessing your purchase, contact [support email] within 7 days.</pre>
        </div>
        <div class="template-card">
          <h3>Store Link CTA</h3>
          <pre>Go to the link in my bio and tap [product name] if you want the full step-by-step resource.</pre>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Common Mistakes</div>
      <h2>What Students Should Avoid</h2>
      <div class="grid-3">
        <div class="warning-card">
          <h3>Too Many Offers</h3>
          <p>New buyers should not have to sort through everything. Put the main offer first and keep the page focused.</p>
        </div>
        <div class="warning-card">
          <h3>Payments Not Verified</h3>
          <p>A store is not ready if the payment processor is incomplete, unverified, or not connected.</p>
        </div>
        <div class="warning-card">
          <h3>No Delivery Test</h3>
          <p>Students should test the buying process before sending traffic. Broken access links create refunds and disputes.</p>
        </div>
        <div class="warning-card">
          <h3>No Support Contact</h3>
          <p>If buyers cannot get help, they may ask their bank or payment processor instead.</p>
        </div>
        <div class="warning-card">
          <h3>Vague Product Titles</h3>
          <p>Creative titles are fine, but buyers should still know what they are getting.</p>
        </div>
        <div class="warning-card">
          <h3>Ignoring Analytics</h3>
          <p>If people click but do not buy, the offer page, price, product placement, or description may need work.</p>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Knowledge Check</div>
      <h2>Quick Student Quiz</h2>
      <div class="grid-2">
        <div class="card">
          <h3>Question 1</h3>
          <p>What should go first on a creator store?</p>
          <div class="quote">Answer: The main offer or the most important action you want visitors to take.</div>
        </div>
        <div class="card">
          <h3>Question 2</h3>
          <p>What should every product page include?</p>
          <div class="quote">Answer: Clear title, short description, visible price, simple CTA, what is included, delivery method, and support path.</div>
        </div>
        <div class="card">
          <h3>Question 3</h3>
          <p>Why should students test checkout before promoting?</p>
          <div class="quote">Answer: To make sure payment, delivery, confirmation emails, and product access work before buyers arrive.</div>
        </div>
        <div class="card">
          <h3>Question 4</h3>
          <p>When should a student consider Shopify instead of a simple creator store?</p>
          <div class="quote">Answer: When they need a fuller ecommerce setup with product collections, shipping, inventory, and more store control.</div>
        </div>
      </div>
    </section>

    <section class="section">
      <div class="section-label">Sources</div>
      <h2>Research Links</h2>
      <p>Use these as platform references when recording walkthroughs or updating student resources.</p>
      <ul>
        <li><a href="https://help.stan.store/article/258-how-to-integrate-stan-with-stripe-or-paypal">Stan Store: Integrate Stan with Stripe or PayPal</a></li>
        <li><a href="https://help.stan.store/article/7-how-to-connect-stan-with-stripe">Stan Store: Connect Stan with Stripe</a></li>
        <li><a href="https://help.stan.store/article/53-how-to-connect-stan-with-paypal">Stan Store: Connect Stan with PayPal</a></li>
        <li><a href="https://help.stan.store/article/14-sell-a-digital-download-product">Stan Store: Sell a Digital Download Product</a></li>
        <li><a href="https://help.stan.store/article/74-how-will-my-customer-download-my-digital-product">Stan Store: How Customers Access Digital Products</a></li>
        <li><a href="https://help.beacons.ai/en/articles/4699009">Beacons: Store Overview</a></li>
        <li><a href="https://help.beacons.ai/en/articles/4698049">Beacons: Setting Up Payments and Payouts</a></li>
        <li><a href="https://help.beacons.ai/en/articles/4699393">Beacons: Set Up Your Store in Minutes</a></li>
        <li><a href="https://help.beacons.ai/en/articles/4699713">Beacons: How Customers Access Digital Products</a></li>
        <li><a href="https://help.shopify.com/en/manual/products">Shopify: Products Help Center</a></li>
      </ul>
    </section>

    <section class="cta">
      <h2>Simple Store, Strong Backend</h2>
      <p>Your creator store should feel simple to buyers, but the backend should be clear, tested, and ready before traffic starts coming in.</p>
    </section>
  </div>
</body>
</html>
