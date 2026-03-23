# new.drupal.org Header Navigation Reference

Source: `https://new.drupal.org/home` (fetched 2026-03-23)

---

## Clean Summary

### Overall Structure

The header (`<header id="header" class="header l-section-container">`) contains:

1. **Search button** (mobile) - `header-search-button header__mobile-search-button`
2. **Logo** - Drupal SVG logo linking to `/`
3. **Hamburger menu toggle** (mobile) - `🍔-menu-toggle`
4. **Main navigation** (`<nav id="block-bluecheese-mainmenu">`) - 5 dropdown menus + User Menu + Get Started CTA
5. **Search drawer** (`<search>` element) - desktop search button + form posting to `/home` with `drupalorg_search_form`
6. **User menu** (`<nav class="header-user-menu">`) - user icon button with Log in / Create account
7. **Secondary menu** (`<nav id="block-bluecheese-secondarymenu">`) - "Get Started" CTA button with dropdown

---

### Logo

- **Element:** `<a class="drupal-logo drupal-navy" href="/" title="Drupal.org">`
- Contains inline SVG (185x67)

---

### Main Navigation (5 dropdowns + User Menu + Get Started)

Each top-level item is a `<button>` (not a link) with `aria-expanded="false"` that toggles a `menu-main__submenu-wrapper` containing level-2 links. Each level-2 link has an optional `<span class="menu-main__description">` with descriptive text.

#### 1. Discover Drupal

| Link Text | URL | Description |
|---|---|---|
| Drupal Core | `https://www.drupal.org/about/overview/technical` | The open source framework behind millions of websites |
| Drupal CMS | `/drupal-cms` | Drupal CMS puts the power of Drupal into the hands of marketers, designers and content creators |
| Drupal AI | `/ai` | Open limitless possibilities with Drupal AI |
| Case Studies | `https://www.drupal.org/case-studies` | Powerful stories that show Drupal solutions in the real world |
| Drupal for Government | `https://www.drupal.org/industries/government` | Drupal is the open-source CMS that enables digital transformation of government and increases citizen engagement |
| Drupal for Higher Education | `https://www.drupal.org/industries/education` | See why 70% of the world's leading universities chose Drupal |
| Drupal for Nonprofit | `https://www.drupal.org/industries/nonprofit` | See why Drupal is the open-source CMS choice for some of the world's most influential nonprofits |
| Drupal for eCommerce | `https://www.drupal.org/industries/ecommerce` | Natively integrate content and commerce |
| Drupal for FinTech | `https://www.drupal.org/industries/fintech` | Secure and trustworthy FinTech infrastructure |
| Drupal for Healthcare | `https://www.drupal.org/industries/healthcare` | Drupal powers systems that are secure, patient-centric and engaging |
| Drupal for Enterprise | `/industries/enterprise` | Why enterprise organizations choose Drupal for multi-brand governance and global scale. |
| Drupal for Retail | `/industries/retail` | See how Drupal delivers retail experiences across every channel and touchpoint. |
| Drupal for Travel & Tourism | `/industries/travel` | Discover how Drupal powers travel across websites, mobile, and onboard experiences. |

#### 2. Build with Drupal

| Link Text | URL | Description |
|---|---|---|
| Download Drupal | `https://www.drupal.org/download` | Download Drupal and the extensions you need |
| Documentation | `https://www.drupal.org/documentation` | Full knowledgebase including Drupal 7 resources |
| Getting Started | `https://www.drupal.org/docs/getting-started` | Guide to installing Drupal on a server |
| Local Development Guide | `https://www.drupal.org/docs/official_docs/local-development-guide` | Guide to installing Drupal locally with Docker and DDEV |
| Developer Resources | `https://www.drupal.org/docs/develop` | Step-by-step guide for learning Drupal |
| Drupal User Guide | `https://www.drupal.org/docs/user_guide/en/index.html` | Learn to build with Drupal |
| API | `https://api.drupal.org/` | Complete documentation of Drupal Core APIs |
| Modules | `https://www.drupal.org/project/modules` | Extend your project's functionality |
| Themes | `https://www.drupal.org/project/themes` | Change your project's look and feel |
| Distributions | `https://www.drupal.org/project/distributions` | Jumpstart your project with a pre-configured install |
| Issues Queue | `https://www.drupal.org/project/issues` | Report issues and contribute improvements |
| Security Advisories | `https://www.drupal.org/security` | Stay on top of the latest security alerts and updates |

#### 3. Partners & Services

| Link Text | URL | Description |
|---|---|---|
| Find a Drupal Certified Partner | `https://www.drupal.org/drupal-services` | Connect with the best Drupal agencies around the world |
| Become a Drupal Certified Partner | `https://new.drupal.org/association/become-a-drupal-certified-partner` | Join an elite network of agencies committed to Drupal excellence and innovation |
| Find a Hosting Provider | `https://www.drupal.org/hosting` | Find a hosting provider for your Drupal project |
| Find a Migration Partner | `https://www.drupal.org/about/drupal-7/d7eol/migration-resource-center/enterprise` | Get help with your migration to the latest version of Drupal |
| Find Training | `https://www.drupal.org/training` | Upskill your Drupal team |
| Drupal Steward | `https://www.drupal.org/steward` | Ensure your website is protected with Drupal Steward |

#### 4. Community

| Link Text | URL | Description |
|---|---|---|
| About the Community | `https://www.drupal.org/community` | Come for the code, stay for the community |
| How to Contribute | `/community/contributor-guide` | Get involved in growing and evolving Drupal |
| DrupalCon | `https://events.drupal.org/` | DrupalCon unites experts from around the globe who create ambitious digital experiences. Network, learn, and be inspired |
| Events | `https://www.drupal.org/community/events` | Discover local events, meet-ups, and training |
| Jobs / Careers | `https://jobs.drupal.org/home` | Find opportunities to work in Drupal |
| News & Blogs | `https://www.drupal.org/blog` | News and stories about Drupal |
| Forum | `https://www.drupal.org/forum` | Got a question about Drupal? Find answers on the Drupal forums |
| Slack | `https://www.drupal.org/slack` | Get support and communicate with the global Drupal community |
| Newsletters | `https://www.drupal.org/subscribe` | Sign up for Drupal news and manage your subscriptions |
| Drupal Swag Shop | `https://www.drupal.org/swag` | Get your Drupal branded merch! |

#### 5. Support Drupal

Top-level button has extra class: `support-drupal`

| Link Text | URL | Description |
|---|---|---|
| The Drupal Association | `https://www.drupal.org/association` | Learn how we support Drupal's growth and innovation - and how you can help |
| Become a Member | `https://www.drupal.org/association/RippleMakers` | Become a Ripplemaker and support the Drupal Association |
| Become a Drupal Certified Partner | `https://www.drupal.org/association/become-a-drupal-certified-partner` | Join an elite network of agencies committed to Drupal excellence and innovation |
| Donate | `https://www.drupal.org/association/donate` | Make a donation to the nonprofit that supports Drupal |

#### 6. User Menu (inside main nav)

| Link Text | URL |
|---|---|
| Log in | `/user/login/keycloak` |
| Create account | `https://www.drupal.org/user/register` |

#### 7. Get Started (CTA button inside main nav)

Button class: `button button--primary icon-arrow-right`

| Link Text | URL |
|---|---|
| Try Drupal CMS | `/drupal-cms/trial` |
| Try hosting | `/try-hosting` |

---

### Search Drawer

- `<search data-component-id="bluecheese:header-search">`
- Desktop button: `header-search-button header-search__desktop-button`
- Form: `POST /home`, form_id: `drupalorg_search_form`
- Input: `name="query"`, placeholder "What are you searching for..."

---

### User Menu (standalone nav)

- `<nav data-component-id="bluecheese:header-user-menu" class="header-user-menu">`
- User icon: `/themes/contrib/bluecheese/images/user.svg`
- Links: Log in (`/user/login`) and Create account (`https://www.drupal.org/user/register`)

---

### Secondary Menu

- `<nav id="block-bluecheese-secondarymenu">`
- "Get Started" button (same CTA style: `button button--primary icon-arrow-right`)
  - Try Drupal CMS: `/drupal-cms/trial`
  - Try Hosting: `/try-hosting`

---

## Key CSS Classes

- Header wrapper: `header l-section-container`
- Nav section: `header__nav-section`
- Main nav block: `block block-system main-navigation`
- Menu levels: `menu-main--level-1`, `menu-main--level-2`
- Menu items: `menu-main__item--level-1`, `menu-main__item--level-2`
- Expanded items: `menu-main__item--expanded`
- Link buttons (dropdowns): `menu-main__link--button menu-main__link--has-children`
- Link anchors: `menu-main__link--link`
- Submenu wrapper: `menu-main__submenu-wrapper`
- Descriptions: `menu-main__description`
- CTA button: `button button--primary icon-arrow-right`
- Support Drupal special class: `support-drupal`
- Search component: `search-drawer`
- User menu: `header-user-menu`
- Logo: `header-logo` > `drupal-logo drupal-navy`
- Mobile hamburger: `🍔-menu-toggle`

---

## Raw HTML

```html
<header id="header" class="header l-section-container">
    <div class="header__nav-section">
      <button data-component-id="bluecheese:header-search-button" class="header-search-button header__mobile-search-button" aria-expanded="false" aria-controls="">
  <span class="visually-hidden">Search</span>
  <span class="header-search-button__icon"></span>
</button>

      <div data-component-id="bluecheese:header-logo" class="header-logo">
    <a class="drupal-logo drupal-navy" href="/" title="Drupal.org">
    <span class="element-focusable">Drupal.org</span>
    <!-- SVG logo omitted for brevity -->
  </a>
</div>

      <button class="🍔-menu-toggle">
  <span class="visually-hidden">Menu</span>
  <span class="🍔-menu-toggle__icon">
    <span class="🍔-menu-toggle__line-1"></span>
    <span class="🍔-menu-toggle__line-2"></span>
    <span class="🍔-menu-toggle__line-3"></span>
  </span>
</button>

      <nav id="block-bluecheese-mainmenu" class="block block-system main-navigation" aria-labelledby="block-bluecheese-mainmenu-menu">
          <h2 class="visually-hidden" id="block-bluecheese-mainmenu-menu">Main menu</h2>
          <ul class="menu-main menu-main--level-1">

        <!-- 1. Discover Drupal -->
        <li class="menu-main__item menu-main__item--level-1 menu-main__item--expanded">
          <button aria-expanded="false" class="menu-main__link menu-main__link--button menu-main__link--level-1 menu-main__link--has-children" type="button">Discover Drupal</button>
          <div class="menu-main__submenu-wrapper">
            <ul class="menu-main menu-main--level-2">
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/about/overview/technical" title="The open source framework behind millions of websites" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal Core</a>
                <span class="menu-main__description">The open source framework behind millions of websites</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/drupal-cms" title="Drupal CMS puts the power of Drupal into the hands of marketers, designers and content creators" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal CMS</a>
                <span class="menu-main__description">Drupal CMS puts the power of Drupal into the hands of marketers, designers and content creators</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/ai" title="Open limitless possibilities with Drupal AI" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal AI</a>
                <span class="menu-main__description">Open limitless possibilities with Drupal AI</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/case-studies" title="Powerful stories that show Drupal solutions in the real world" class="menu-main__link menu-main__link--link menu-main__link--level-2">Case Studies</a>
                <span class="menu-main__description">Powerful stories that show Drupal solutions in the real world</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/industries/government" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for Government</a>
                <span class="menu-main__description">Drupal is the open-source CMS that enables digital transformation of government and increases citizen engagement</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/industries/education" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for Higher Education</a>
                <span class="menu-main__description">See why 70% of the world's leading universities chose Drupal</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/industries/nonprofit" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for Nonprofit</a>
                <span class="menu-main__description">See why Drupal is the open-source CMS choice for some of the world's most influential nonprofits</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/industries/ecommerce" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for eCommerce</a>
                <span class="menu-main__description">Natively integrate content and commerce</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/industries/fintech" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for FinTech</a>
                <span class="menu-main__description">Secure and trustworthy FinTech infrastructure</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/industries/healthcare" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for Healthcare</a>
                <span class="menu-main__description">Drupal powers systems that are secure, patient-centric and engaging</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/industries/enterprise" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for Enterprise</a>
                <span class="menu-main__description">Why enterprise organizations choose Drupal for multi-brand governance and global scale.</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/industries/retail" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for Retail</a>
                <span class="menu-main__description">See how Drupal delivers retail experiences across every channel and touchpoint.</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/industries/travel" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal for Travel &amp; Tourism</a>
                <span class="menu-main__description">Discover how Drupal powers travel across websites, mobile, and onboard experiences.</span>
              </li>
            </ul>
          </div>
        </li>

        <!-- 2. Build with Drupal -->
        <li class="menu-main__item menu-main__item--level-1 menu-main__item--expanded">
          <button aria-expanded="false" class="menu-main__link menu-main__link--button menu-main__link--level-1 menu-main__link--has-children" type="button">Build with Drupal</button>
          <div class="menu-main__submenu-wrapper">
            <ul class="menu-main menu-main--level-2">
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/download" class="menu-main__link menu-main__link--link menu-main__link--level-2">Download Drupal</a>
                <span class="menu-main__description">Download Drupal and the extensions you need</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/documentation" class="menu-main__link menu-main__link--link menu-main__link--level-2">Documentation</a>
                <span class="menu-main__description">Full knowledgebase including Drupal 7 resources</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/docs/getting-started" class="menu-main__link menu-main__link--link menu-main__link--level-2">Getting Started</a>
                <span class="menu-main__description">Guide to installing Drupal on a server</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/docs/official_docs/local-development-guide" class="menu-main__link menu-main__link--link menu-main__link--level-2">Local Development Guide</a>
                <span class="menu-main__description">Guide to installing Drupal locally with Docker and DDEV</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/docs/develop" class="menu-main__link menu-main__link--link menu-main__link--level-2">Developer Resources</a>
                <span class="menu-main__description">Step-by-step guide for learning Drupal</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/docs/user_guide/en/index.html" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal User Guide</a>
                <span class="menu-main__description">Learn to build with Drupal</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://api.drupal.org/" class="menu-main__link menu-main__link--link menu-main__link--level-2">API</a>
                <span class="menu-main__description">Complete documentation of Drupal Core APIs</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/project/modules" class="menu-main__link menu-main__link--link menu-main__link--level-2">Modules</a>
                <span class="menu-main__description">Extend your project's functionality</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/project/themes" class="menu-main__link menu-main__link--link menu-main__link--level-2">Themes</a>
                <span class="menu-main__description">Change your project's look and feel</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/project/distributions" class="menu-main__link menu-main__link--link menu-main__link--level-2">Distributions</a>
                <span class="menu-main__description">Jumpstart your project with a pre-configured install</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/project/issues" class="menu-main__link menu-main__link--link menu-main__link--level-2">Issues Queue</a>
                <span class="menu-main__description">Report issues and contribute improvements</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/security" class="menu-main__link menu-main__link--link menu-main__link--level-2">Security Advisories</a>
                <span class="menu-main__description">Stay on top of the latest security alerts and updates</span>
              </li>
            </ul>
          </div>
        </li>

        <!-- 3. Partners & Services -->
        <li class="menu-main__item menu-main__item--level-1 menu-main__item--expanded">
          <button aria-expanded="false" class="menu-main__link menu-main__link--button menu-main__link--level-1 menu-main__link--has-children" type="button">Partners &amp; Services</button>
          <div class="menu-main__submenu-wrapper">
            <ul class="menu-main menu-main--level-2">
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/drupal-services" class="menu-main__link menu-main__link--link menu-main__link--level-2">Find a Drupal Certified Partner</a>
                <span class="menu-main__description">Connect with the best Drupal agencies around the world</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://new.drupal.org/association/become-a-drupal-certified-partner" class="menu-main__link menu-main__link--link menu-main__link--level-2">Become a Drupal Certified Partner</a>
                <span class="menu-main__description">Join an elite network of agencies committed to Drupal excellence and innovation</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/hosting" class="menu-main__link menu-main__link--link menu-main__link--level-2">Find a Hosting Provider</a>
                <span class="menu-main__description">Find a hosting provider for your Drupal project</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/about/drupal-7/d7eol/migration-resource-center/enterprise" class="menu-main__link menu-main__link--link menu-main__link--level-2">Find a Migration Partner</a>
                <span class="menu-main__description">Get help with your migration to the latest version of Drupal</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/training" class="menu-main__link menu-main__link--link menu-main__link--level-2">Find Training</a>
                <span class="menu-main__description">Upskill your Drupal team</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/steward" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal Steward</a>
                <span class="menu-main__description">Ensure your website is protected with Drupal Steward</span>
              </li>
            </ul>
          </div>
        </li>

        <!-- 4. Community -->
        <li class="menu-main__item menu-main__item--level-1 menu-main__item--expanded">
          <button aria-expanded="false" class="menu-main__link menu-main__link--button menu-main__link--level-1 menu-main__link--has-children" type="button">Community</button>
          <div class="menu-main__submenu-wrapper">
            <ul class="menu-main menu-main--level-2">
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/community" class="menu-main__link menu-main__link--link menu-main__link--level-2">About the Community</a>
                <span class="menu-main__description">Come for the code, stay for the community</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/community/contributor-guide" class="menu-main__link menu-main__link--link menu-main__link--level-2">How to Contribute</a>
                <span class="menu-main__description">Get involved in growing and evolving Drupal</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://events.drupal.org/" class="menu-main__link menu-main__link--link menu-main__link--level-2">DrupalCon</a>
                <span class="menu-main__description">DrupalCon unites experts from around the globe who create ambitious digital experiences. Network, learn, and be inspired</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/community/events" class="menu-main__link menu-main__link--link menu-main__link--level-2">Events</a>
                <span class="menu-main__description">Discover local events, meet-ups, and training</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://jobs.drupal.org/home" class="menu-main__link menu-main__link--link menu-main__link--level-2">Jobs / Careers</a>
                <span class="menu-main__description">Find opportunities to work in Drupal</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/blog" class="menu-main__link menu-main__link--link menu-main__link--level-2">News &amp; Blogs</a>
                <span class="menu-main__description">News and stories about Drupal</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/forum" class="menu-main__link menu-main__link--link menu-main__link--level-2">Forum</a>
                <span class="menu-main__description">Got a question about Drupal? Find answers on the Drupal forums</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/slack" class="menu-main__link menu-main__link--link menu-main__link--level-2">Slack</a>
                <span class="menu-main__description">Get support and communicate with the global Drupal community</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/subscribe" class="menu-main__link menu-main__link--link menu-main__link--level-2">Newsletters</a>
                <span class="menu-main__description">Sign up for Drupal news and manage your subscriptions</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/swag" class="menu-main__link menu-main__link--link menu-main__link--level-2">Drupal Swag Shop</a>
                <span class="menu-main__description">Get your Drupal branded merch!</span>
              </li>
            </ul>
          </div>
        </li>

        <!-- 5. Support Drupal -->
        <li class="menu-main__item menu-main__item--level-1 menu-main__item--expanded">
          <button aria-expanded="false" class="menu-main__link menu-main__link--button menu-main__link--level-1 menu-main__link--has-children support-drupal" type="button">Support Drupal</button>
          <div class="menu-main__submenu-wrapper">
            <ul class="menu-main menu-main--level-2">
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/association" class="menu-main__link menu-main__link--link menu-main__link--level-2">The Drupal Association</a>
                <span class="menu-main__description">Learn how we support Drupal's growth and innovation - and how you can help</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/association/RippleMakers" class="menu-main__link menu-main__link--link menu-main__link--level-2">Become a Member</a>
                <span class="menu-main__description">Become a Ripplemaker and support the Drupal Association</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/association/become-a-drupal-certified-partner" class="menu-main__link menu-main__link--link menu-main__link--level-2">Become a Drupal Certified Partner</a>
                <span class="menu-main__description">Join an elite network of agencies committed to Drupal excellence and innovation</span>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/association/donate" class="menu-main__link menu-main__link--link menu-main__link--level-2">Donate</a>
                <span class="menu-main__description">Make a donation to the nonprofit that supports Drupal</span>
              </li>
            </ul>
          </div>
        </li>

        <!-- 6. User Menu (inside main nav for mobile) -->
        <li class="menu-main__item menu-main__item--level-1 menu-main__item--expanded">
          <button aria-expanded="false" class="menu-main__link menu-main__link--button menu-main__link--level-1 menu-main__link--has-children" type="button">User Menu</button>
          <div class="menu-main__submenu-wrapper">
            <ul class="menu-main menu-main--level-2">
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/user/login/keycloak" class="menu-main__link menu-main__link--link menu-main__link--level-2">Log in</a>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="https://www.drupal.org/user/register" class="menu-main__link menu-main__link--link menu-main__link--level-2">Create account</a>
              </li>
            </ul>
          </div>
        </li>

        <!-- 7. Get Started CTA (inside main nav) -->
        <li class="menu-main__item menu-main__item--level-1 menu-main__item--expanded">
          <button class="button button--primary icon-arrow-right menu-main__link menu-main__link--button menu-main__link--level-1 menu-main__link--has-children" aria-expanded="false" type="button">Get Started</button>
          <div class="menu-main__submenu-wrapper">
            <ul class="menu-main menu-main--level-2">
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/drupal-cms/trial" class="menu-main__link menu-main__link--link menu-main__link--level-2">Try Drupal CMS</a>
              </li>
              <li class="menu-main__item menu-main__item--level-2">
                <a href="/try-hosting" class="menu-main__link menu-main__link--link menu-main__link--level-2">Try hosting</a>
              </li>
            </ul>
          </div>
        </li>

          </ul>
      </nav>

      <!-- Search Drawer -->
      <search data-component-id="bluecheese:header-search" class="search-drawer">
        <button data-component-id="bluecheese:header-search-button" class="header-search-button header-search__desktop-button" aria-expanded="false" aria-controls="">
          <span class="visually-hidden">Search</span>
          <span class="header-search-button__icon"></span>
        </button>
        <div class="header-search__drawer">
          <div class="header-search__inner">
            <div class="drupalorg-search-form global-text--form block block-drupalorg-crosssite">
              <div class="block-inner">
                <div class="content">
                  <form action="/home" method="post" id="drupalorg-search-form" accept-charset="UTF-8">
                    <div class="js-form-item form-item js-form-type-textfield form-type--textfield js-form-item-query form-item--query">
                      <label for="edit-query" class="form-item__label">Search</label>
                      <input placeholder="What are you searching for..." type="text" id="edit-query" name="query" value="" size="60" maxlength="128" class="form-text form-element form-element--type-text form-element--api-textfield"/>
                    </div>
                    <input type="submit" id="edit-submit" name="op" value="Search" class="button js-form-submit form-submit"/>
                    <input type="hidden" name="form_id" value="drupalorg_search_form"/>
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </search>

      <!-- User Menu (desktop) -->
      <nav data-component-id="bluecheese:header-user-menu" class="header-user-menu" aria-labelledby="user-menu">
        <h2 id="user-menu" class="visually-hidden">User menu</h2>
        <button class="header-user-menu__button" aria-expanded="false" aria-labelledby="user-menu">
          <img class="header-user-menu__picture" src="/themes/contrib/bluecheese/images/user.svg" alt>
        </button>
        <ul class="menu menu--level-1">
          <li class="menu__item menu__item--level-1">
            <a href="/user/login" class="menu__link menu__link--link menu__link--level-1">Log in</a>
          </li>
          <li class="menu__item menu__item--level-1">
            <a href="https://www.drupal.org/user/register" class="menu__link menu__link--link menu__link--level-1">Create account</a>
          </li>
        </ul>
      </nav>

      <!-- Secondary Menu (Get Started CTA - desktop) -->
      <nav id="block-bluecheese-secondarymenu" class="block block-system block-bluecheese-secondarymenu" aria-labelledby="block-bluecheese-secondarymenu-menu">
        <h2 class="visually-hidden" id="block-bluecheese-secondarymenu-menu">Secondary menu</h2>
        <ul class="menu menu--level-1">
          <li class="menu__item menu__item--level-1 menu__item--has-children">
            <button class="button button--primary icon-arrow-right menu__link menu__link--button menu__link--level-1 menu__link--has-children" type="button">Get Started</button>
            <ul class="menu menu--level-2">
              <li class="menu__item menu__item--level-2">
                <a href="/drupal-cms/trial" class="menu__link menu__link--link menu__link--level-2">Try Drupal CMS</a>
              </li>
              <li class="menu__item menu__item--level-2">
                <a href="/try-hosting" class="menu__link menu__link--link menu__link--level-2">Try Hosting</a>
              </li>
            </ul>
          </li>
        </ul>
      </nav>

    </div>
</header>
```
