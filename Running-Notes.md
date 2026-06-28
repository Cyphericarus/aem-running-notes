# Local Setup
[05/05/26]

- Run the following command in `cmd` as `admin` after changing directory to `aemInstance` on desktop. 

```bash

mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate -D archetypeGroupId=com.adobe.aem -D archetypeArtifactId=aem-project-archetype -D archetypeVersion=41 -D appTitle="Newsportal" -D appId="newsportal" -D groupId="com.karthik.newsportal"
```

- Output should be like `BUILD SUCCESS`.
- Now, turn on `aemInstance` first, after it is running properly.
- In the `aemInstance`, there should be a new folder called `newsportal`.
- Open `cmd` as non admin in the `newsportal` folder and run the following command.

```bash

mvn clean install -PautoInstallSinglePackage
```

- Output should be like `BUILD SUCCESS`.
- In the `sites` of  `aem GUI` on chrome, the `newsportal` option should be shown.

---

# Syllabus of AEM
[06/05/26]

## 1. Front Modules [No Coding Required] 
✅

1. CMS [Content Management System] - Definition, version, why, tools, uses 
2. Apache Maven - Installation, why
3. AEM Technical Stack & Consoles 
4. AEM Components & Rendering the data of the Web Pages [imp] 
5. AEM Templates 
6. Sling Request Processing 
7. AEM Client - LIBS 
8. Sling Resource Merger 
9. HTL(HTML Templating Language) 
10. Experience Fragment
11. Content Fragment

## 2.  Backend Modules [Coding Required]

1. OSGI [Open Service Gateway Initiative]
2. OSGI Component and Service
3. OSGI Configuration
4. AEM Run Nodes
5. Sling Model [imp]
6. Sling and Node API
7. Sling Servlets
8. Sling Event Handler
9. Sling Schedulers
10. Core Components [Theory]
11. Query Builder [SQL]
12. The Adds-on Concepts
13. Workflows and User Management
14. Dispatcher & AEM Interview Concepts/Questions

---
# Day1 - CMS& AEM
[14/05/26]
## 1. The Problem — Why CMS Exists

Before you understand what a CMS is, understand what happens without one. This is the problem that makes CMS valuable.

### Traditional Web Development — The Old Way

To build a website traditionally (full Java or Python stack), you need a big, expensive team just to do routine things like publish a blog post or update a product image.

| Role | Count | Why Needed |
|---|---|---|
| Java / Python Developers | 50 | Write backend logic |
| Frontend (HTML, CSS, JS / UI-UX) | 15 | Build what users see |
| Testers | 10 | Catch bugs before go-live |
| Team Leads | 5 | Manage developers |
| Project Managers | 2 | Coordinate the whole team |

| Metric | Reality |
|---|---|
| Website delivery (traditional) | 8–10 hours minimum |
| Website delivery (with CMS) | ~20 minutes on average |

> **LOCK IN:** Traditional web development is like handwriting every copy of a newspaper. A CMS is the printing press with same output, a fraction of the effort.

### What Goes Wrong Without a CMS

- A marketing team wants to update a product headline, then they must raise a ticket, wait for a developer, wait for QA, wait for deployment. Days lost.
- The CEO wants to add a press release tonight, then the dev team is offline. It waits till morning.
- The company runs 50 country-specific websites. Every page update requires 50 manual code changes.
- One image upload can trigger a full deployment pipeline.

> **KEY:** Without a CMS, content is locked inside code. Only developers can change it. That is the core problem CMS solves.


## 2. What is a CMS?

A CMS (Content Management System) is a platform that separates content from code. 
It lets non-technical people like marketers, editors, product managers can create, edit, and publish web content directly, without touching a single line of code.

> **🔑 LOCK IN:** Text editors are to IDEs what traditional web development is to CMS. Just as an IDE supercharges a developer's workflow with auto-complete, debugging, and build tools, a CMS supercharges content management for the whole team.

### What a CMS Actually Does

- **Content Creation & Editing:** Lets non-developers create and edit web pages through a visual interface
- **Media Management:** Manages digital assets (Digital Asset Management -DAM) like images, videos, PDFs in one central library
- **User Management:** Controls who can do what like authors write, editors review, admins publish
- **Template Management:** Handles templates so pages stay consistent without coding each one again and again.
- **Zero Downtime:** Runs on servers with zero downtime and changes go live without redeployments
- **Faster Content Publishing:** The content publishing can be made quite quicker.

### CMS vs Traditional Development

| Task | Without CMS | With CMS |
|---|---|---|
| Update page headline | Dev writes code, deploys | Author edits in 30 seconds |
| Upload a new image | Dev adds to codebase, redeploys | Author uploads to DAM library |
| Create a new page | Dev builds template + code | Author picks template, fills content |
| Publish a blog post | Full dev → QA → deploy pipeline | Author clicks Publish |
| Manage 50 country sites | 50 separate codebases | One CMS, 50 content trees |

### Who Actually Uses CMS?

Not just small blogs. The world's biggest companies run CMS platforms at massive scale:

| Company | Why They Use CMS |
|---|---|
| Apple | Manages product pages, launches, and regional content globally |
| Samsung | Runs localised marketing sites across 50+ countries |
| Hyundai | Manages dealer portals, campaign pages, and car configuration tools |
| Airlines, Banks, Retailers | High-volume content teams publishing daily across many channels |

> **📌 NOTE:** The bigger the company, the bigger the content team. And the bigger the content team, the more valuable a CMS becomes. Enterprise CMS is a billion-dollar industry precisely because of this scale.


## 3. The CMS Landscape 

Not all CMS platforms are the same. They fall into categories based on who they serve, what they power, and how they connect to your frontend.

### The Two Types of CMS

#### Traditional (Coupled) CMS

The CMS controls both the content AND how it looks on screen. It renders HTML directly. Simple, fast to start with, but harder to push content to mobile apps or multiple channels.

#### Headless CMS

The CMS stores and manages content but has NO opinion about how it looks. It exposes content through an API. Your frontend (React, mobile app, anything) fetches and renders it however it wants. `Contentful` and `Amplience` work this way.

> **🔑 LOCK IN:** Traditional CMS is a restaurant that cooks AND serves the food on their plates. Headless CMS is a cloud kitchen — it prepares the food (content) and delivers it to any restaurant, food truck, or delivery app that requests it via API.

### Popular CMS Platforms 

| Tool | Type | Best For |
|---|---|---|
| WordPress | Traditional (Open Source) | Blogs, SMB websites — most widely used CMS on earth |
| Joomla | Traditional (Open Source) | Community sites, flexible content models |
| Drupal | Traditional (Open Source) | Developer-heavy enterprise sites, complex data models |
| SiteCore | Traditional (Enterprise) | Large enterprises on Microsoft/.NET stack |
| Contentful | Headless (SaaS) | Multi-channel content delivery via API |
| Amplience | Headless (SaaS) | E-commerce focused, commerce + content together |
| OpenText | Enterprise ECM | Document management, compliance, records |
| **AEM** | **Enterprise (Adobe)** | **Marketing-led enterprise sites with full digital experience stack** |

> **📌 NOTE:** AEM stands apart from the others because it is not just a CMS, it is an entire Digital Experience Platform (DXP). It manages content AND analytics AND marketing campaigns AND assets AND personalization, all inside one suite.


## 4. Adobe Experience Cloud 

AEM does not stand alone. It is one product inside Adobe Experience Cloud — a full suite of enterprise marketing and analytics tools. Understanding this context explains why AEM is the CMS of choice for marketing-led enterprises.

> **🔑 LOCK IN:** Adobe Experience Cloud is like a city infrastructure. AEM (Experience Manager) is the roads — it connects everything. Analytics is the city's data centre tracking traffic. Campaign is the billboard network running ads. Target is the GPS that gives each driver a personalized route. They all work together, but you can also use any one of them independently.

| Adobe Product                | What It Does                                                                               |
| ---------------------------- | ------------------------------------------------------------------------------------------ |
| **Experience Manager (AEM)** | The core CMS which builds and manages the website and its content                          |
| Adobe Analytics              | Tracks how users behave, what they click, where they drop off, what converts               |
| Audience Manager             | Identifies and segments users, who is your audience, what do they want                     |
| Adobe Campaign               | Sends targeted marketing campaigns like email, SMS, push notifications                     |
| Adobe Target                 | A/B testing and personalisation, shows different content to different users                |
| Adobe Social                 | Manages marketing and promotions across social media channels                              |
| Adobe Primetime              | Handles extreme traffic spikes, keeps the server stable when millions hit the site at once |

### Why Adobe Primetime Exists — The Traffic Spike Problem

Imagine Apple launches a new iPhone. The second Tim Cook says "And one more thing..." — millions of people hit apple.com simultaneously. A normal server crashes under that load.

Adobe Primetime is the layer that sits between the incoming traffic storm and your server. It manages the queue, distributes load, and ensures the site stays up even during peak spikes. This is why Primetime matters specifically for companies running major product launches, ticket sales, or live events.

> **KEY:** Adobe Target does personalisation — every user gets a version of the page tailored to them (based on location, past behaviour, segment). This is different from Audience Manager, which simply identifies and groups users. Target acts on that data.


## 5. AEM - What It Actually Is

AEM (Adobe Experience Manager) is the enterprise CMS for companies where marketing, sales, and audience engagement are the core business. 

It is not just a tool for publishing blog posts, it is the backbone of how large companies build, manage, and personalize digital experiences at scale.

Under the hood, AEM is a Java-based platform. This is why you are learning Java alongside AEM, your backend logic is written in Java, Maven builds and deploys it, and AEM runs it.

> **🔑 LOCK IN:** AEM is like a five-star hotel management system. The guests (end users) see beautiful rooms and seamless service. Behind the scenes, there is a full operation like kitchen (Java backend), housekeeping (content management), concierge (personalization), all coordinated by one system. WordPress is a guest house. AEM is the Ritz.

### AEM's Five Core Modules

AEM is not one monolithic tool. It is a platform made up of five specialised modules. Enterprises buy the ones they need.

| AEM Module        | What It Manages                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------ |
| **AEM Sites**     | Website development and management, namely pages, templates, components, content authoring |
| **AEM Assets**    | Digital Asset Management (DAM) that stores and serves images, videos, PDFs, documents      |
| **AEM Forms**     | Registration and data collection forms like complex, multi-step enterprise forms           |
| **AEM Mobile**    | Mobile application content management  that push content to iOS and Android apps           |
| **AEM Community** | Forums, community groups, user-generated content, developer channels                       |

### AEM Sites

As a Java developer learning AEM, your primary focus is AEM Sites. This is where websites are built and managed. Here is what AEM Sites makes possible:

- Content authors create and edit pages through a visual drag-and-drop interface — no code required
- Developers build reusable components (banner, nav, card) that authors can configure through dialog popups
- Templates define the skeleton of every page — zones, allowed components, and page structure
- Pages are stored as nodes in JCR (AEM's content database) — everything is queryable
- Multi-site management — one AEM instance can run 50 country websites with shared components
- Author-Publish architecture — authors work on a private instance (4502), end users see the published instance (4503)

### AEM Assets

AEM Assets is the DAM (Digital Asset Manager) — the central library for every image, video, PDF, and document used across all AEM Sites. Instead of embedding images directly in page code, authors upload to DAM once and reference assets across any number of pages.

> **🔑 LOCK IN:** AEM Assets is like a corporate stock photo library. Designers upload the master images once. Every website, every campaign, every page just picks from the library. Change the asset in one place, and it updates everywhere it is referenced.

### Author vs Publish 

This is one of the most important AEM concepts to lock in early.

| Instance | Port | What Happens Here |
|---|---|---|
| **Author** | 4502 | Developers build. Authors create and edit content. Nothing here is live yet. |
| **Publish** | 4503 | What end users see. Content is pushed here when authors click Publish. |
| Dispatcher | 80/443 | Sits in front of Publish. Handles caching and load balancing. (Learn later.) |

> **🔑 LOCK IN:** Author is the backstage of a theatre. Publish is the stage. The audience (end users) only ever sees the stage. Everything — rehearsals, set design, lighting tests — happens backstage first. Only when the director (author) approves does the curtain go up.


## 6. When to Use AEM vs Other CMS

AEM is powerful but expensive. Knowing when it is the right tool (and when it is overkill) is important context for your career.

| Scenario | Right CMS | Why |
|---|---|---|
| Personal blog or small business | WordPress | Fast, free, easy. AEM would cost more than the business. |
| Mid-size company, 5–20 pages | Drupal or Joomla | More control than WordPress, far cheaper than AEM. |
| Multi-channel startup | Contentful (Headless) | API-first, push content to web + mobile + anything. |
| **Global enterprise, marketing-driven** | **AEM** | **Multi-site, personalisation, DAM, analytics — all in one. Justified at scale.** |
| E-commerce + content hybrid | Amplience or AEM | Commerce-aware content management at scale. |

> **📌 NOTE:** AEM licenses cost six to seven figures per year. Companies like Apple, Samsung, Hyundai, and airlines pay this because the ROI at their scale — managing hundreds of websites, millions of assets, and personalised campaigns for millions of users — justifies it completely.

> **⚠️ KEY:** As an AEM developer, you are not building small websites. You are building infrastructure for marketing teams at companies where the website IS the business. That is the professional context you are entering.

## 7. How Everything Connects — Your Learning Path

Everything you learn over the coming weeks connects into a single pipeline. Here is how it all fits:

| What You Learn | Where It Goes in AEM |
|---|---|
| Java | Backend logic — Sling Models, Servlets, OSGi Services (all inside AEM's core module) |
| Maven | Build and deploy tool — compiles your Java, packages everything, installs into AEM |
| HTML / CSS / JS | Component markup — written in HTL (AEM's templating language built on HTML) |
| AEM Sites | Where your components, templates, and pages live — the output users see |
| AEM Assets (DAM) | Where all images and media are stored — referenced by your pages |
| JCR | AEM's internal database — everything (pages, components, configs) stored as nodes |

### The Full Flow — End to End

```
You write Java (core/) + HTML/CSS (ui.frontend/)
         ↓
Maven compiles + packages → .zip (all module)
         ↓
AEM Author (localhost:4502) installs the package
         ↓
Content authors build pages using your components
         ↓
Authors click Publish → AEM Publish (localhost:4503)
         ↓
End users visit the live website
```

> **🔑 LOCK IN:** Think of it as a factory production line. You are the engineer who designs the machines (Java components). Maven is the assembly line that builds and installs them. AEM is the factory floor. Content authors are the operators who run the machines. The Publish instance is the warehouse where finished products go. End users are the customers receiving them.


## 8. Terms to Lock In — Day 1 Glossary

| Term | One-Line Lock-In |
|---|---|
| CMS | A platform that lets non-developers create and manage web content without code |
| AEM | Adobe's enterprise CMS — built on Java, powers marketing-led enterprise websites |
| Adobe Experience Cloud | The full suite of Adobe products (CMS + analytics + campaigns + more) |
| AEM Sites | The AEM module for website development — where you will spend most of your time |
| AEM Assets / DAM | AEM's digital library — central storage for all images, videos, and documents |
| AEM Forms | Enterprise form builder — registration, applications, data collection |
| Author Instance (4502) | Private AEM instance — where developers and authors work. Not public. |
| Publish Instance (4503) | Public AEM instance — what end users see. The live website. |
| Dispatcher | Caching + load balancing layer in front of Publish (learn in depth later) |
| JCR | AEM's internal content database — stores everything as a tree of nodes |
| Headless CMS | CMS that stores content and delivers it via API — no opinion on how it renders |
| Adobe Primetime | Adobe's traffic spike management — keeps sites alive during massive concurrent hits |
| Adobe Target | Personalisation tool — different content for different users based on data |
| Editable Template | The skeleton of a page — defines zones and which components are allowed where |
| Component | Reusable UI block (banner, nav, card) — built once by devs, used everywhere by authors |



___

# Day2 - Apache Maven - Installation, Purpose& Project Setup
[15/05/26]


## 1. The Problem Maven Solves

Before understanding Maven, understand the problem it solves.

When you write Java code, three things need to happen before it can run anywhere:

1. **Compile** — Convert `.java` files into `.class` files the JVM can run
2. **Package** — Bundle everything into a deployable file (`.jar` or `.zip`)
3. **Manage Libraries** — Your code needs external libraries (like importing `ArrayList` but for much bigger things)

Without Maven, a developer would:
- Manually download every library their project needs
- Manually compile the code
- Manually package it
- Manually upload it to the server

**Maven automates all of this** through a single config file called `pom.xml`.

> **Analogy:** Think of Maven as a personal assistant. You write the instruction file (`pom.xml`) once — telling it what libraries you need, how to build, and where to deploy. After that, one command and Maven handles everything while you focus on writing code.


## 2. Why Maven is used for AEM?

**AEM (Adobe Experience Manager)** is a Java-based CMS (Content Management System) used by large companies to build websites, portals, and digital experiences.

Since AEM runs on Java internally:
- Your backend logic is written in Java
- Maven is the standard tool to build and deploy AEM projects

You will be writing Java code → Maven builds it → AEM runs it.

> **Analogy:** AEM is like a factory building. Your Java code is the machinery inside. Maven is the construction crew that installs and updates the machinery whenever you make changes.


## 3. What is Maven?

**Apache Maven** is a build automation and project management tool for Java projects.

- Manage dependencies
- Organize project structure
- Build the project
- Package the code
- Deploy the application into AEM

| Task | Without Maven | With Maven |
|------|--------------|------------|
| Libraries | Download manually | Auto-downloaded via `pom.xml` |
| Compiling | Run `javac` manually | `mvn install` |
| Packaging | Zip files manually | Done automatically |
| Deploying to AEM | Upload manually | `mvn clean install -PautoInstallSinglePackage` |


## 4. Key Reasons Maven is Used in AEM

### 1. Standardized Project Structure
Maven enforces a consistent, industry-standard folder layout for every AEM project using the **AEM Project Archetype**. Instead of every developer organizing files differently, Maven generates the same predictable structure every time — `core`, `ui.apps`, `ui.content`, `ui.config`, `all` — making projects easy to navigate, maintain, and hand off to other developers.

> **Analogy:** Like a franchise restaurant — every McDonald's branch looks the same inside. A new employee walking into any branch knows exactly where the kitchen, counter, and storage are. AEM projects work the same way — any AEM developer can jump into any AEM project and immediately know where everything is.

### 2. Dependency Management
AEM projects rely on many external libraries — AEM APIs, Apache Sling libraries, OSGi APIs, logging frameworks, and more. Instead of downloading `.jar` files manually and worrying about version conflicts, you declare what you need inside `pom.xml` and Maven resolves, downloads, and links everything automatically.

```xml
<!-- Declare it once in pom.xml — Maven handles the rest -->
<dependency>
    <groupId>org.apache.sling</groupId>
    <artifactId>org.apache.sling.api</artifactId>
    <scope>provided</scope>
</dependency>
```

> **Analogy:** Like a grocery delivery app. Instead of going to multiple stores to find ingredients, you just write a shopping list (`pom.xml`) and everything gets delivered to your door automatically.

### 3. Build & Deployment Automation
Maven compiles your Java code, packages all modules, and deploys directly into a running AEM instance with a single command:

```bash
mvn clean install -PautoInstallSinglePackage
```

No manual steps. No uploading packages through the AEM UI. One command does everything.

> **Analogy:** Like a pizza oven with a conveyor belt. You put the raw pizza (your code) in one end, and a fully cooked, boxed, delivered pizza (deployed AEM package) comes out the other end automatically.

### 4. Multi-Module Project Support
A real AEM project is not a single Java file — it's a collection of interconnected modules (Java backend, frontend components, content, configs). Maven's **multi-module project structure** lets you manage all of them from a single root `pom.xml`, build them in the correct order, and package them together for deployment.

```
newsportal/          ← root pom.xml manages everything
├── core/            ← own pom.xml (inherits from root)
├── ui.apps/         ← own pom.xml (inherits from root)
├── ui.content/      ← own pom.xml (inherits from root)
└── all/             ← own pom.xml (inherits from root)
```

> **Analogy:** Think of the root `pom.xml` as a company HR policy document. Every department (module) automatically follows those base rules. But each department can also have its own extra rules on top. The `<parent>` tag in each child `pom.xml` is literally saying "I inherit from the company policy."

### 5. Plugin Support
Maven's functionality is extended through **plugins** — tools that hook into the build process to perform AEM-specific tasks.

| Plugin | What it does |
|--------|-------------|
| **Content Package Maven Plugin** (`filevault-package-maven-plugin`) | Packages and deploys AEM content packages (`.zip`) to AEM |
| **Maven Bundle Plugin** (`maven-bundle-plugin`) | Compiles Java code into OSGi bundles (`.jar`) that AEM can run |
| **AEM Analyzer Plugin** | Validates your package before deployment — catches errors early |
| **Maven Archetype Plugin** | Generates the initial AEM project from the archetype template |

Plugins are declared in `pom.xml` under `<build><plugins>` and run automatically during the Maven build lifecycle.

> **Analogy:** Plugins are like attachments for a power drill. The drill (Maven) is the core tool, but you attach different bits (plugins) depending on the job — one bit for drilling, one for screwing, one for sanding.



## 5. The Most Important File — `pom.xml`

`pom.xml` stands for **Project Object Model**.

pom.xml is the main configuration file used by Maven.

It contains:
- Project information
- Dependencies
- Plugins
- Build instructions
- Deployment configurations

In AEM projects, the root pom.xml acts like a parent configuration file, and each module can also have its own pom.xml that inherits settings from the parent.

It is an XML file — and since you already know HTML, reading XML will feel very familiar. It uses the same tag-based structure.

```xml
<!-- HTML you already know -->
<div class="container">
  <p>Hello</p>
</div>

<!-- pom.xml uses the same idea — just different tags -->
<project>
  <groupId>com.karthik.newsportal</groupId>
  <artifactId>newsportal</artifactId>
  <version>1.0.0</version>
</project>
```

### What `pom.xml` contains

| Section | Purpose |
|---------|---------|
| `<groupId>` | Your organization/project namespace (like a Java package name) |
| `<artifactId>` | The name of this specific module |
| `<version>` | Project version |
| `<dependencies>` | External libraries your project needs |
| `<plugins>` | Tools that extend Maven's build process |
| `<modules>` | Links to sub-projects (in multi-module projects) |
| `<profiles>` | Environment-specific settings (e.g. local vs production) |

### Adding a dependency in `pom.xml`

```xml
<dependencies>
  <dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>aem-sdk-api</artifactId>
    <scope>provided</scope>
    <!-- Maven downloads this automatically -->
  </dependency>
</dependencies>
```

### `scope: provided` — Why AEM Libraries Are Special

You'll notice AEM and Sling dependencies use `<scope>provided</scope>`. This means:

> *"I need this library to compile my code, but don't bundle it into my package — AEM already has it running on the server."*

| Scope | Meaning |
|-------|---------|
| `provided` | AEM already has this — don't bundle it. Used for AEM/Sling/OSGi APIs |
| `compile` | Bundle this into my package — the server won't have it. Used for third-party utilities |

> **Analogy:** If you're moving into a furnished apartment (AEM), you don't bring your own sofa (AEM APIs) — it's already there (`provided`). But you do bring your personal laptop (your own third-party libraries) because the apartment doesn't have one (`compile`).

> **Every module in an AEM project has its own `pom.xml`.** The root `pom.xml` acts as the parent that links and controls all of them.

---

## 6. Key Maven Terms

| Term | Plain English Meaning |
|------|-----------------------|
| **Dependency** | An external library your code needs (like importing a Java class, but bigger) |
| **Build** | Compile + package your source code into a deployable file |
| **Artifact** | The output file Maven creates — a `.jar` (Java library) or `.zip` (AEM package) |
| **Plugin** | An add-on tool that gives Maven extra abilities during build |
| **Archetype** | A starter template that generates a full project structure automatically |
| **Module** | A sub-project inside a larger Maven project |
| **Profile** | A named set of build settings you activate with `-P` (e.g. `-PautoInstallSinglePackage`) |
| **Repository** | An online storage where Maven downloads dependencies from (Maven Central) |
| **`-B` flag** | Batch mode — runs Maven without pausing to ask questions. Used in scripts and automation |
| **`-D` flag** | Define — passes a `key=value` property into Maven from the command line |

---

## 7. AEM Multi-Module Project Structure

When Maven generates an AEM project using the AEM Archetype, it creates this structure:

```
newsportal/
│
├── ui.frontend/    ← Raw CSS / SCSS / JS / TypeScript source files
├── core/           ← Java backend code
├── ui.apps/        ← AEM components, clientlibs, OSGi configs
├── ui.content/     ← Page structure, editable templates, DAM folders, tags
├── ui.config/      ← Environment-specific OSGi configurations
├── all/            ← Final combined package — deployed to AEM
└── pom.xml         ← Root Maven config (parent of all modules)
```

![[media_1db0c52bb9ac29f2386578641738a68655dbe9542.png 1.webp]]
### The City Analogy — lock this in

|Module|City Equivalent|
|---|---|
|ui.frontend|The design studio — architects draw plans here|
|core|The engineering department — all technical systems (plumbing, electricity)|
|ui.apps|Construction blueprints — standardized reusable building designs|
|ui.content|The actual city — real buildings, roads, and parks that exist|
|ui.config|City regulations file — rules about how services run|
|all|The entire city packaged and handed over to AEM to run|


## 8. Understanding Each Module in Detail

### `ui.frontend/` — Raw Frontend Source

Where you write modern CSS, SCSS, TypeScript, and JavaScript **before** they get compiled.

Contains: `.scss`, `.css`, `.ts`, `.js`, Webpack config

This module **compiles down into clientlibs** which are then placed into `ui.apps`. You write here, the output goes there.

> **Analogy:** `ui.frontend` is the kitchen where food is cooked. `ui.apps` is the plate it gets served on. You work in the kitchen, but the customer (AEM/browser) sees only the plate.



### `core/` — Your Java Code

This is where you will spend most of your time as a Java developer.

Contains:
- Java classes and business logic
- **Sling Models** — Java classes that map AEM content nodes to Java objects
- **Sling Servlets** — Java classes that handle HTTP requests inside AEM
- **OSGi Services** — background services running inside AEM
- Unit tests

```
core/src/main/java/com/karthik/newsportal/
├── models/         ← Sling Models
├── servlets/       ← Sling Servlets
└── services/       ← OSGi Services
```

> **Analogy:** `core` is the engine room of a ship. Passengers (content authors) never see it, but nothing moves without it.



### `ui.apps/` — Application Code Layer

Contains the AEM application definitions — reusable pieces that developers build once and authors use everywhere.

Contains:
- **Components** — Reusable UI blocks (banner, card, navigation, footer)
- **Clientlibs** — Compiled CSS and JS output (from `ui.frontend`)
- **OSGi Configs** — Some environment configs
- **Dialogs** — Component configuration popups for content authors

> **Analogy:** `ui.apps` is IKEA's product catalog — standardized, reusable furniture designs. Each component is like an IKEA product: designed once, assembled anywhere, by anyone.



### `ui.content/` — The Actual Content

Contains the real content stored in AEM's repository (JCR). This is what authors interact with.

Contains:
- **Page Structure** — Actual pages (`/content/newsportal/home`, `/content/newsportal/about`)
- **Editable Templates** — Modern AEM templates that define page skeletons (live under `/conf/`)
- **DAM Folders** — Digital Asset Management folders (where images/videos are stored)
- **Tags** — Taxonomy and metadata tags used across the site

```
ui.content/
├── content/
│   └── newsportal/
│       ├── home/          ← Home page (actual page)
│       ├── about/         ← About page (actual page)
│       └── news/          ← News listing page (actual page)
└── conf/
    └── newsportal/
        └── settings/wcm/
            └── templates/ ← Editable Templates live here
```

> **Analogy:** If `ui.apps` is IKEA's catalog, then `ui.content` is **your actual home** — the real rooms you built using IKEA furniture. Every page is a real room. Templates are the floor plans you followed to build it.



### `ui.config/` — OSGi Configurations

Environment-specific settings for AEM services — different values for local, staging, and production.

> **Analogy:** Like a `.env` file in web development — same app, different config per environment.




### `all/` — The Final Deployable Package

Bundles every module (`core`, `ui.apps`, `ui.content`, `ui.config`) into one single `.zip` package that gets installed into AEM.

> **Analogy:** `all` is the moving truck. It picks up everything from every department and delivers it all to AEM in one trip.



## 9. Components vs Templates vs Page Structure — Cleared Up Permanently

This is the most confusing part for beginners. Here it is locked in.

### The House-Building Analogy

| House | AEM Equivalent | Lives In |
|-------|---------------|----------|
| LEGO bricks | **Components** | `ui.apps` |
| Blueprint / floor plan | **Editable Template** | `ui.content` → `/conf/` |
| The actual built house | **Page Structure** | `ui.content` → `/content/` |



### Components (`ui.apps`)

A **component** is a reusable UI block — the smallest building piece in AEM.

Examples: Button, Banner, Navigation bar, News card, Image with caption

- Built **once** by a developer
- Used **anywhere**, on any page, multiple times
- Has a **Dialog** — popup so authors can configure it (change text, image, etc.)
- Has a **Sling Model** — Java class that feeds data into it
- Rendered using **HTL** — AEM's HTML-like templating language

> **Lock-in:** Components are LEGO bricks. One brick design, infinite uses. You design it once, snap it in anywhere.



### Editable Templates (`ui.content` → `/conf/`)

A **template** defines the **skeleton of a page** — which regions exist and what components are allowed where.

```
┌─────────────────────────┐
│         Header          │  ← fixed zone, always there
├─────────────────────────┤
│    Hero Banner Area     │  ← only 'banner' component allowed
├─────────────────────────┤
│   Main Content Area     │  ← newscard, image, text allowed
├─────────────────────────┤
│         Footer          │  ← fixed zone, always there
└─────────────────────────┘
```

> **Important clarification:** In **modern AEM**, templates are **Editable Templates** and they live in `ui.content` under `/conf/`. Older AEM used "Static Templates" which lived in `ui.apps`. The Adobe diagram shows the modern structure — always go with editable templates.

> **Lock-in:** Template is a floor plan from an architect. It defines where the bedroom, kitchen, and bathroom go. It doesn't have actual furniture yet — just zones and rules for what's allowed where.



### Page Structure (`ui.content` → `/content/`)

This is where **actual pages** live — real instances created by authors using a template.

When a content author opens AEM, picks a template, and creates a page — that page gets saved as a node in the JCR content repository under `/content/`.

> **Lock-in:** Page structure is the actual house built from the blueprint. The blueprint (template) told you where rooms go. Now you have real walls, real furniture (components), real content inside.



### How All Three Work Together — Real Example

**Scenario: Building a News Article page for Newsportal**

1. **Developer builds a `NewsCard` component** → `ui.apps`
   - HTL renders the HTML structure
   - Dialog lets authors set title, image, description
   - Sling Model reads the data from JCR and passes it to HTL

2. **Developer creates an `Article Page` template** → `ui.content/conf/`
   - Header zone (fixed)
   - Content zone (NewsCard allowed here)
   - Footer zone (fixed)

3. **Content author opens AEM, creates a new page** → `ui.content/content/`
   - Picks the `Article Page` template
   - Drags `NewsCard` into the content zone
   - Fills in title and image
   - Saves → page now exists as a real node under `/content/newsportal/news/article-1`

```
Component (LEGO brick — built by dev)
        +
Template (floor plan — built by dev)
        +
Author places components + fills in real content
        =
Page in ui.content/content/ (what users actually see)
```



## 10. Important AEM-Specific Terms

| Term | What it is |
|------|-----------|
| **Component** | A reusable UI block in AEM (banner, card, nav) |
| **Editable Template** | Modern template defining page skeleton — lives in `ui.content/conf/` |
| **Dialog** | A popup that lets content authors configure a component |
| **HTL** | HTML Template Language — AEM's server-side templating syntax (like HTML with AEM expressions) |
| **Sling Model** | A Java class annotated with `@Model` that maps AEM content nodes to Java objects |
| **Servlet** | A Java class that handles HTTP requests inside AEM |
| **OSGi** | AEM's internal module system — how AEM loads and runs Java services |
| **JCR** | Java Content Repository — AEM's internal database; all content stored as a tree of nodes |
| **DAM** | Digital Asset Manager — where images, videos, and PDFs are stored in AEM |
| **Clientlib** | Compiled CSS/JS files packaged for the browser — output of `ui.frontend` going into `ui.apps` |
| **Package** | A `.zip` file containing code/content that gets installed into AEM |
| **Author (4502)** | AEM instance where developers and content authors work |
| **Publish (4503)** | AEM instance that end-users (public) see — the live website |
| **Dispatcher** | AEM's caching and load-balancing layer — sits in front of Publish (learn this later) |



## 11. Essential Maven Commands

### Check your setup
```bash
# Verify Java is installed
java -version

# Verify Maven is installed
mvn -version
```
Both must return version numbers, not errors. If either fails, install before proceeding.

### Build without deploying
```bash
mvn clean install
```
Compiles and packages but does NOT deploy to AEM. Useful for checking if code compiles cleanly.

### Build and deploy to AEM (most used command)
```bash
mvn clean install -PautoInstallSinglePackage
```

| Part | What it does |
|------|-------------|
| `mvn` | Runs Maven |
| `clean` | Deletes the `/target` folder (previous build output) |
| `install` | Compiles, tests, and packages all modules |
| `-P` | Activates a Maven Profile |
| `autoInstallSinglePackage` | Profile that deploys the `all` package to AEM Author (4502) |

This one command replaces: compile → package → open AEM → upload package → install.

### Other useful commands
```bash
# Deploy to AEM Publish instance (port 4503)
mvn clean install -PautoInstallSinglePackagePublish

# See all dependencies and their resolved versions
mvn dependency:tree

# See the fully resolved pom.xml (useful for debugging)
mvn help:effective-pom
```



## 12. Things That Will Catch You Off Guard

### The First Build is Always Slow
The very first `mvn clean install` feels like it's frozen — it's not. Maven is downloading every dependency into your local cache folder:

```
C:\Users\gnikh\.m2\repository\
```

Every build after that is fast because Maven reuses this local cache instead of re-downloading.

> **Analogy:** Like installing an app for the first time vs opening it after. First install downloads everything. After that it just opens instantly.

### The `.m2` Folder — Maven's Personal Warehouse
This folder on your computer is Maven's local library. When you declare a dependency in `pom.xml`, Maven checks here first before going online. If already downloaded, it uses the local copy instantly.

> **Analogy:** Like your browser cache — websites load faster on the second visit because assets are already saved locally.

### The `target/` Folder — Never Touch It
Every module gets a `target/` folder after a build. This is where Maven puts compiled `.class` files and the final packaged output. You never touch this manually — Maven owns it. That's why `clean` deletes it — to wipe previous build output so nothing stale carries over.

### Author vs Publish — Two Separate AEM Instances

AEM runs as **two separate instances**:

| Instance | Port | Who uses it |
|----------|------|-------------|
| **Author** | `4502` | Developers & content authors — where you build and edit |
| **Publish** | `4503` | End users — the live public-facing website |

`-PautoInstallSinglePackage` deploys to **Author (4502)** only. That's intentional — you always develop on Author, never directly on Publish.

### The Archetype Command — Run Only Once
The long `mvn -B org.apache.maven.plugins...` command is a **one-time project generator**. You run it once to create the project, and never again. From that point on, your daily command is only:

```bash
mvn clean install -PautoInstallSinglePackage
```

> **Analogy:** The archetype command is like scaffolding on a construction site — used once during initial setup, then removed. The building (your project) stands on its own after that.

### `groupId` is Just Your Java Package Name
`com.karthik.newsportal` follows the exact same reverse-domain naming convention as Java packages. If you've written `package com.karthik.newsportal.models;` in Java — this is the same idea. It uniquely identifies your project globally so no two projects clash with each other.



## 13. How Everything Connects — The Full Flow

```
Developer writes Java code in core/
Developer writes CSS/JS in ui.frontend/
                ↓
mvn clean install -PautoInstallSinglePackage
                ↓
Maven compiles Java → OSGi bundle (.jar)
Maven compiles frontend → clientlibs in ui.apps
Maven packages all modules → .zip (the 'all' package)
                ↓
Maven uploads .zip to AEM Author (localhost:4502)
                ↓
AEM installs it:
  - Components & clientlibs available (from ui.apps)
  - Pages & templates available (from ui.content)
  - Java logic running (from core)
                ↓
Content authors use components to build and edit pages
                ↓
Pages published from Author → AEM Publish (localhost:4503)
                ↓
End users visit the live website
```


## 14. Project Setup — Step by Step

### Prerequisites
- Java JDK 11+ installed
- Apache Maven 3.6+ installed and added to PATH
- AEM SDK downloaded and running locally

### Step 1 — Open Command Prompt as Administrator
Search **Command Prompt** → Right-click → **Run as Administrator**

> Running as admin prevents permission errors when Maven writes files to your system.

### Step 2 — Navigate to Your Working Folder
```bash
cd C:\Users\raju\OneDrive\Desktop\AEMInstance
```

### Step 3 — Generate the AEM Project Using Maven Archetype

```bash
mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
-D archetypeGroupId=com.adobe.aem ^
-D archetypeArtifactId=aem-project-archetype ^
-D archetypeVersion=41 ^
-D appTitle="Newsportal" ^
-D appId="newsportal" ^
-D groupId="com.karthik.newsportal"
```

- **`-B`** — Batch mode: don't pause and ask questions, just run straight through
- **`-D`** — Define: pass a `key=value` property into Maven
- **`^`** — Windows CMD line continuation: it's one single command split across lines for readability

**What each parameter means:**

| Parameter | Your Value | What it means |
|-----------|-----------|---------------|
| `archetypeGroupId` | `com.adobe.aem` | The company that made this template (Adobe) |
| `archetypeArtifactId` | `aem-project-archetype` | The name of the template |
| `archetypeVersion` | `41` | Version of the AEM project template to use |
| `appTitle` | `Newsportal` | Human-readable display name of your project |
| `appId` | `newsportal` | Short ID — becomes the generated folder name and used in paths |
| `groupId` | `com.karthik.newsportal` | Java package naming (reverse domain convention) |

**What happens after this runs:**
Maven downloads the AEM archetype template and generates a complete `newsportal/` folder at your current location — with all modules, Java structure, and config files ready to go.

### Step 4 — Start AEM and Log In
1. Start your local AEM instance (run the AEM SDK jar)
2. Open browser → `http://localhost:4502`
3. Log in (`admin` / `admin` for local development only)
4. Wait for AEM to fully load — the home screen must be visible before next step

### Step 5 — Navigate Into the Generated Project
```bash
cd newsportal
```

### Step 6 — Build and Deploy
```bash
mvn clean install -PautoInstallSinglePackage
```
Maven compiles all Java, packages all modules, and installs everything into your running AEM instance. **First build is slow** — Maven is downloading all dependencies into `.m2`. Every subsequent build is fast.


## 15. Recommended Tools

| Tool              | Purpose                  | Notes                                     |
| ----------------- | ------------------------ | ----------------------------------------- |
| Java JDK 11+      | Compile and run Java/AEM | AEM 6.5 uses Java 11                      |
| Apache Maven 3.6+ | Build and deploy         | Install and add to system PATH            |
| AEM SDK           | Local AEM instance       | Download from Adobe                       |
| IntelliJ IDEA     | Best Java IDE for AEM    | Community edition is free                 |
| VS Code           | Lightweight editor       | Good for `ui.apps` and `ui.frontend` work |
| Git               | Version control          | Standard in all AEM projects              |


## Quick Reference

### Commands
| Command | Purpose |
|---------|---------|
| `java -version` | Check Java install |
| `mvn -version` | Check Maven install |
| `mvn clean install` | Build all modules without deploying |
| `mvn clean install -PautoInstallSinglePackage` | Build + deploy to Author (4502) |
| `mvn clean install -PautoInstallSinglePackagePublish` | Build + deploy to Publish (4503) |
| `mvn dependency:tree` | View all dependencies and versions |
| `mvn help:effective-pom` | View fully resolved pom.xml |

### Module Summary
| Module | Contains | Lock-in Analogy |
|--------|---------|----------------|
| `ui.frontend` | Raw CSS, SCSS, JS, TS | Design studio — work happens here |
| `core` | Java, Sling Models, Servlets, OSGi Services | Engine room — powers everything |
| `ui.apps` | Components, Clientlibs, Dialogs, OSGi configs | IKEA catalog — reusable designs |
| `ui.content` | Pages, Editable Templates, DAM, Tags | The actual city — real things that exist |
| `ui.config` | Environment-specific OSGi configs | `.env` file — different per environment |
| `all` | Bundles everything for deployment | Moving truck — delivers it all at once |

### Concepts
| Concept           | One-Line Definition                                            |
| ----------------- | -------------------------------------------------------------- |
| Maven             | Automates compiling, packaging, and deploying Java projects    |
| AEM               | Java-based CMS for building enterprise websites                |
| `pom.xml`         | XML instruction file that controls everything Maven does       |
| Dependency        | External library Maven downloads automatically                 |
| `scope: provided` | Don't bundle — AEM already has this on the server              |
| `scope: compile`  | Bundle this — the server won't have it                         |
| Archetype         | One-time project starter template — run once, never again      |
| `.m2` folder      | Maven's local library cache — lives on your computer           |
| `target/` folder  | Maven's build output — never touch manually                    |
| Component         | Reusable UI brick — built once, used everywhere                |
| Editable Template | Floor plan — defines page skeleton and allowed components      |
| Page Structure    | The actual built page — real content, real authors, real users |
| Author (4502)     | AEM instance where developers and authors work                 |
| Publish (4503)    | AEM instance that end-users see — the live site                |
| HTL               | AEM's HTML-based templating language                           |
| Sling Model       | Java class that maps AEM content nodes to Java objects         |
| OSGi              | AEM's internal module system for running Java services         |
| JCR               | AEM's content database — stores everything as a tree of nodes  |
| DAM               | AEM's media library — images, videos, PDFs                     |
| Clientlib         | Compiled CSS/JS ready for the browser                          |
| `-B` flag         | Batch mode — no interactive prompts, just run                  |
| `-D` flag         | Define — pass key=value into Maven from command line           |

## Reference

[Adobe AEM WKND Tutorial — Project Setup](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/project-setup)

---

# Day3 - AEM Technical Stack & Consoles
[18-05-2026]

### Overview

The AEM technical foundation is primarily built on three important stacks:

1. **JCR** (Java Content Repository)
2. **Apache Sling**
3. **OSGi** (Open Services Gateway initiative)


## 1. JCR (Java Content Repository)

The Java Content Repository is the database layer of AEM. It is the hierarchical location where all content, code, configurations, and data are stored and managed.

### CRXDE Lite (Content Repository Extreme Development Environment)

CRXDE Lite is the web-based IDE and interface used to interact with the JCR.

- **Purpose:** It provides the tools to view, edit, and manage the storage (JCR).
- **Structure:** The repository is **Tree-Structured** (hierarchical).

#### Repository Structure: Tree vs. Unstructured

- **Tree-Structured:** The data is organized hierarchically, similar to a file system.
    - _Analogy:_ Think of a natural tree with branches and leaves. Just as you cannot predict exactly how many branches a tree will grow, the JCR is flexible and scalable, allowing for an unpredictable number of branches (folders) and modules.
- **Unstructured:** The repository also supports unstructured data, meaning it can store different types of content without a rigid pre-defined schema.

> **Console URL:** `http://localhost:4502/crx/de/index.jsp`

### How to Access CRXDE Lite

There are two ways to open the CRXDE Lite console:

1. **Direct URL:** Enter `http://localhost:4502/crx/de/index.jsp` in your browser after the AEM instance has started.
2. **Via AEM Navigation:**
    - Open the AEM Start screen (`http://localhost:4502`).
    - Navigate to the **Tools** tab.
    - Select **General**.
    - Click on **CRXDE Lite**.

### Key Terminology: Node

- **Node:** Every branch, folder, or file visible inside the CRXDE tree structure is referred to as a **Node**.


## 2. Apache Sling

### Overview
**Apache Sling** is the **web framework** and **request processing engine** at the core of Adobe Experience Manager (AEM).

It is a **resource-oriented**, **RESTful** framework that handles all incoming HTTP requests and generates responses.

### Core Purpose
- Processes every **Request** and returns an appropriate **Response**.
- Treats **everything as a Resource** (pages, components, assets, metadata, etc.).
- **Decouples** the URL from the actual content storage location.

### Request Processing Flow

**Example URL:**  
`http://localhost:8080/content/Test/sample.html`

**Step-by-step Flow:**
1. Request arrives at the AEM server.
2. **Apache Sling** receives and processes the request.
3. Sling performs **Resource Resolution** (maps the URL to a JCR node).
4. Locates the resource in the **JCR Repository** (CRX).
5. Selects the appropriate script, servlet, or model based on the resource.
6. Renders the content and sends back the **Response**.

**Simplified Flow:**  
**Request → Apache Sling → Resource Resolution → JCR Repository (CRX) → Response**

> **Important Note**:  
> **Apache Jackrabbit** is the default **JCR (Java Content Repository)** backend implementation used by Apache Sling.

### Key Sling Concepts

#### 1. Resource Resolution
Sling resolves a URL using this order:
- Resource Path
- Selectors (e.g., `.print`, `.feed`)
- Extension (e.g., `.html`, `.json`)
- Suffix

#### 2. Selectors & Extensions
- **Extension**: Defines the output format (`.html`, `.json`, `.xml`, etc.).
- **Selectors**: Used to create variations of the same resource.  
  Example: `/content/Test/sample.print.html` → applies “print” variation.

#### 3. Sling Servlets
- Custom Java servlets registered in OSGi.
- Can be bound to a `sling:resourceType`, path, extension, or selector.
- Ideal for APIs, AJAX calls, JSON exports, and backend logic.

#### 4. Scripting Engines Supported
- **HTL (HTML Template Language)** — Recommended and default in modern AEM.
- JSP
- Java Servlets
- Others (Groovy, Ruby, etc.)

### Most Important Feature: URL Decoupling

[[apache-sling-analogy]]

This is achieved using:
- **Sling Resource Resolver**
- **Sling Mappings** (`/etc/map`)

#### How It Works in Practice: Complete Flow

Here's the complete journey when a user visits your website:

##### 1. User Request

```
User types in browser: https://www.example1.com/products
```

#####  2. Apache Dispatcher Processing

```
Dispatcher intercepts requestChecks cache (if available)If not cached, passes to AEM Publish instanceAdds full content path: /content/wknd/us/products.html
```

#####  3. Sling Request Processing

```
Request arrives at AEM:   Path: /products  Host: www.example1.com  Protocol: https
```

#####  4. Resource Resolver Forward Mapping

```
Sling queries /etc/map/https/ for matching rulesFinds: /etc/map/https/www.example1.com/redirect/Matches regex: (.+)$ against "products"Applies sling:internalRedirect: /content/wknd/us/$1Result: /content/wknd/us/products
```

#####  5. Resource Located

```
Resource Resolver finds:  /content/wknd/us/products (with .html extension)Passes to Sling rendering pipelineHTL template processes the page
```

#####  6. Link Generation (Reverse Mapping)

```
Inside HTL template:<a href="${ model.path @ context='uri' }">Products</a>
model.path = /content/wknd/us/products.html
Resource Resolver reverse mapping applied:  sling:match: "$1/"  sling:internalRedirect: "/content/wknd/us/(.*).html"  Output URL: /products/
```

#####  7. HTML Response

```
<a href="/products/">Products</a>Sent back to DispatcherDispatcher caches the page
```

#####  8. Browser Receives

```
HTML: <a href="/products/">Products</a>User sees link: https://www.example1.com/products/
```

#####  9. Link Clicked (Cycle Repeats)

```
User clicks link → /products/Goes back to step 2Resource Resolver again maps to /content/wknd/us/productsContent is served
```
### URL Decoupling: Complete Explanation

URL Decoupling is an architectural pattern that separates the external URL structure (what users see in browsers) from the internal content repository structure (where content is stored in AEM). This decoupling allows you to change internal content organization without affecting user-facing URLs, and vice versa.
#### The Core Problem Without Decoupling

##### Tightly Coupled Scenario

In a tightly coupled system, the internal JCR path directly maps to the public URL:

|Internal Path|External URL|Problem|
|---|---|---|
|`/content/wknd/en/products.html`|`www.example.com/content/wknd/en/products.html`|Ugly, exposes structure|
|`/content/wknd/en/blog/article-1.html`|`www.example.com/content/wknd/en/blog/article-1.html`|Long, not SEO-friendly|
|`/content/wknd/en/about.html`|`www.example.com/content/wknd/en/about.html`|Not memorable|

Consequences of tight coupling:

- Users see internal structure in URLs
- Restructuring content requires URL changes (breaks bookmarks, SEO rankings)
- No flexibility in content organization
- SEO penalties for long, non-semantic URLs
- Security concerns (exposes system architecture)


#### URL Decoupling Solution

With URL Decoupling, internal structure is hidden behind clean, user-friendly URLs:

|Internal Path|External URL|Benefits|
|---|---|---|
|`/content/wknd/en/products.html`|`www.example.com/products`|Clean, memorable|
|`/content/wknd/en/blog/article-1.html`|`www.example.com/insights/article-1`|Semantic, SEO-friendly|
|`/content/wknd/en/about.html`|`www.example.com/about`|Short, brandable|

Result:

- External URLs are user-friendly and don't change
- Internal content can be reorganized without affecting URLs
- Better SEO with semantic URLs
- Improved security by hiding system structure
#### Benefits of URL Decoupling

| Aspect                      | Traditional Web Apps    | Apache Sling (AEM)              |
| ---------------------------- | ----------------------- | ------------------- |
| URL vs Content Location    | Tightly coupled         | Fully decoupled                 |
| Moving/Restructuring Content | Breaks existing URLs    | No impact on URLs               |
| SEO & Vanity URLs          | Difficult               | Easy and flexible               |
| Multiple URLs for one page | Hard                    | Naturally supported             |
| Clean URL support          | Requires extra config[] | Built-in                        |

**Simple Analogy**:  
Traditional = Fixed library shelves (URL = exact shelf address).  
Sling = Smart librarian who can deliver any book using any name you request.

### Key Takeaways

- Apache Sling is **resource-centric** — every URL resolves to a JCR resource.
- It is highly flexible due to selectors, extensions, servlets, and mappings.
- URL decoupling gives massive freedom for content management, SEO, and marketing needs.
- Everything in AEM (pages, assets, components) is treated as a **Resource** by Sling.


## 3. OSGi - Open Service Gateway Initiative

### Overview
**OSGi** (Open Service Gateway Initiative) is a **modular architecture** for Java. 

It forms the foundation of Adobe Experience Manager (AEM), enabling large applications to be built as small, independent, reusable **bundles** (modules).

### Core Philosophy
- Break the application into independent **bundles**.
- Bundles can be developed, tested, deployed, started, stopped, and updated **independently** at runtime.
- Promotes **loose coupling** between modules through services.

### Analogy: Car Manufacturing
A car is built from many independent parts (engine, wheels, transmission, seats, etc.):
- Different teams can work on different parts **in parallel**.
- If one part fails, only that part is repaired or replaced — the entire car doesn’t need to be rebuilt.

**In AEM**: The whole project is divided into multiple bundles that work together via services.

### Bundle Lifecycle States

OSGi bundles transition through several states:

| State          | Description |
|----------------|-----------|
| **INSTALLED**  | Bundle is installed in the framework but dependencies not yet resolved. |
| **RESOLVED**   | All dependencies are satisfied; bundle is ready to start. |
| **STARTING**   | `BundleActivator.start()` is executing. |
| **ACTIVE**     | Bundle is fully running and providing services. |
| **STOPPING**   | `BundleActivator.stop()` is executing. |
| **UNINSTALLED**| Bundle has been removed from the framework. |

OSGi supports **hot deployment** — bundles can be updated without restarting the server.

### OSGi Service Lifecycle (Declarative Services)

Modern AEM heavily uses **Declarative Services (DS)** for components and services. The lifecycle is managed by the Service Component Runtime (SCR).

#### Key Lifecycle Methods

| Method         | When Called                           | Purpose                                                |
| -------------- | ------------------------------------- | ------------------------------------------------------ |
| **Activate**   | After dependencies are injected       | Initialize resources, connections, and start logic.    |
| **Modified**   | When configuration changes at runtime | Handle dynamic config updates without restart.         |
| **Deactivate** | Before component/bundle is stopped    | Clean up resources, close connections, release memory. |

#### Service Flow
1. Bundle starts → Component is activated.
2. Service is registered in the **OSGi Service Registry**.
3. Other components reference it using `@Reference`.
4. Services can appear/disappear dynamically at runtime.


### Key Benefits

| Benefit               | Description |
|-----------------------|-----------|
| Modularity            | Application built as independent, reusable bundles |
| Parallel Development  | Multiple teams can work on different bundles simultaneously |
| Dynamic Updates       | Install/start/stop/update bundles at runtime |
| Loose Coupling        | Components communicate via service interfaces |
| Fault Isolation       | Failure in one bundle/service has limited impact |
| Versioning            | Multiple versions of same bundle/service can coexist |
| Hot Deployment        | No server restart required for most changes |


### Key Takeaways
- OSGi is the **modularity layer** of AEM.
- Almost everything in AEM (Servlets, Sling Models, Workflows, custom services, etc.) runs as OSGi bundles.
- Enables scalable, maintainable, and highly dynamic enterprise applications.
- Supports **zero-downtime** deployments through dynamic bundle and service management.

These notes are now complete, consistent, and ready for revision. Let me know if you want to move to the next topic.


## 4. Local Server Setup - Author & Publish

### Overview
Adobe Experience Manager (AEM) runs in two main modes on local machines:

### 1. Author Instance
- **Purpose**: Development, content authoring, testing, and administration.
- **Users**: Developers, Administrators, Content Authors, Testers.
- **Default Port**: 4502
- **Jar File**: `aem-author-p4502.jar`

### 2. Publish Instance
- **Purpose**: Final delivery of content to end users (view-only).
- **Users**: Clients / End users (public website).
- **Default Port**: 4503
- **Jar File**: `aem-publish-p4503.jar`

### System Requirements

- **Minimum RAM**: 8 GB (Recommended: 16 GB or more)
- **JDK**: Version 11 (JDK 8 for older AEM versions)
- Valid Adobe credentials to download AEM Quickstart JAR.


### How to Run Publish Instance Locally

1. Create a new folder named `publish` inside your AEM directory.
2. Copy the `aem-publish-p4503.jar` file into the `publish` folder.
3. Open Command Prompt / Terminal inside the `publish` folder.
4. Run the following command:  
   ```bash
   java -jar aem-publish-p4503.jar -gui
   ```

> **Best Practice**: Do **not** run Author and Publish instances simultaneously on the same machine unless you have sufficient RAM (16GB+), as it consumes high system resources.


### Connecting Author and Publish

- **Replication Agent** is used to replicate (publish) content from Author to Publish instance.
- Replication pushes content, assets, and configurations from Author → Publish.


### Project Structure - Maven

**Project Name Example**: `newsportal`

AEM projects are typically built using **Apache Maven** and divided into two main types of modules:

#### Frontend Modules (Package Type: `content-package` - .zip files)
These are deployed via **Package Manager**.

| Module     | Purpose |
|------------|-------|
| **apps**   | Contains components, templates, clientlibs, and UI code |
| **config** | OSGi configurations and runmode-specific settings |
| **content** | Site content, pages, and structure |
| **frontend**| Frontend assets (optional, for modern frontend build) |
| **all**    | Aggregator package that includes all other modules |

**Access URL**:  
`http://localhost:4502/crx/packmgr/index.jsp`

#### Backend Modules (Package Type: `bundle` - .jar files)
These are OSGi bundles deployed via **Felix Web Console**.

| Module   | Purpose |
|----------|-------|
| **core** | Contains all Java code: Sling Models, Servlets, Services, Workflows, Utilities, etc. |

**Access URL**:  
`http://localhost:4502/system/console/bundles`

### Key Takeaways
- **Author** = Content creation & management environment.
- **Publish** = Live environment for end users.
- Always develop on **Author** and replicate content to **Publish**.
- Use **Maven** multi-module structure to keep frontend and backend code organized.
- Monitor both **Package Manager** and **OSGi Bundles** console regularly.



## 5. Important Maven Commands & Useful Consoles

### Maven Commands for Deployment

These commands are used to build and automatically deploy AEM code from your local Maven project to the running AEM instance.

| Command                                         | Purpose                                                                            |
| ----------------------------------------------- | ---------------------------------------------------------------------------------- |
| `mvn clean install -PautoInstallSinglePackage`  | Builds and deploys **only the current module** (recommended for most development). |
| `mvn clean install -PautoInstallPackage`        | Builds and installs the complete content package to Author instance.               |
| `mvn clean install -PautoInstallBundle`         | Builds and deploys **only the core bundle** (backend Java code).                   |
| `mvn clean install -PautoInstallPackagePublish` | Builds and installs the package to the **Publish** instance.                       |


### Most Commonly Used Commands

- **During active development** → `mvn clean install -PautoInstallSinglePackage`
- **Backend only changes** → `mvn clean install -PautoInstallBundle`
- **Deploy to Publish** → `mvn clean install -PautoInstallPackagePublish`

> **Tip**: Always run `clean install` to ensure old compiled files are removed before building.


### Important AEM Consoles & URLs

|Console|URL|Description|
|---|---|---|
|**AEM Welcome / Start Page**|`http://localhost:4502/aem/start.html`|AEM Home / Welcome screen with quick links to major consoles|
|**Sites Console**|`http://localhost:4502/sites.html/content`|Manage site hierarchy, pages, and content structure|
|**CRXDE Lite**|`http://localhost:4502/crx/de/index.jsp`|Repository browser and development tool (JCR editor)|
|**OSGi Web Console**|`http://localhost:4502/system/console`|View and manage OSGi bundles, components, configurations, and services|
|**Package Manager**|`http://localhost:4502/crx/packmgr/index.jsp`|Upload, install, build, and manage content packages (.zip)|
|**Error Log**|`http://localhost:4502/system/console/slinglog`|View real-time AEM error and debug logs|
|**User Management**|`http://localhost:4502/libs/granite/security/content/admin.html`|Manage users and groups|
|**Assets Console**|`http://localhost:4502/assets.html/content/dam`|Digital Asset Management (DAM) console|

### Key Takeaways
- Use appropriate Maven profiles (`-P`) based on what you want to deploy (single module, full package, bundle, or publish).
- Master the five consoles above — they are used daily during AEM development.
- `CRXDE Lite` → for repository exploration and quick changes.
- `Bundles Console` → for checking OSGi bundle status.
- `Package Manager` → for installing frontend/content packages.

## 6. Assignment

1. `newsportal` in CRXDE
2. Open Package Manger and check all frontend modules
3. Open bundles for core folder 

Take Screenshots of all

---

# Day4 - AEM Components & Rendering the data of the Web-Pages  [imp]
[19-05-2026]


1. What is Component
2. How to create a component
3. Component structure
4. component properties
5. Component Types
6. OOTB Component - Out of the box Component or Core components or existing or inbuilt components
7. Parsys/container Component.

## 1. Component

- A containers which store some info/data like images, text, videos etc.
- There are reusable.

**Ex:** An image component can be used multiple times 

### How to create a sample page

Project -> select ->


For Rendering the data on the Web-Pages, each and every components are developed by by using HTL (HTML Template Language)

## 2. How to create a component

Each and everything in JCR or CRXDE is a node.

### Properties of Nodes

`jcr:primaryType`: Each and every node has a node type under this property.

#### Node name 


## 3. Component structure

![[image-6 2.png]]


These two are the must(mandatory properties) in every component structure.

1. componentGroup 
2. jcr:title

#### Touch UI Dialog
This dialog is used to set the content to the component.

Allows to store the data in the content  node.

##### The dialog implementation is basically of 2 types

1. Granite UI: Collection of components 
	1. Granite Components
	2. Granite Form Components

All the below paths are the in built components path

###### 1. Granite Components

cq/gui/components/authoring/dialog
granite/ui/components/coral/foundation/container
granite/ui/components/coral/foundation/fixedcolumns
cq/gui/components/authoring/dialog/richtext
granite/ui/components/coral/foundation/include
granite/ui/components/coral/foundation/tabs
cq/gui/components/coral/common/form/tagfield
granite/ui/components/coral/foundation/form/autocomplete
granite/ui/components/coral/foundation/form/fileupload
cq/gui/components/common/tagspicker
	
###### 2. Granite form components :-

granite/ui/components/coral/foundation/form/textfield
granite/ui/components/coral/foundation/form/textarea
granite/ui/components/coral/foundation/form/pathfield
granite/ui/components/coral/foundation/form/pathbrowser
granite/ui/components/coral/foundation/form/checkbox
granite/ui/components/coral/foundation/form/select
granite/ui/components/coral/foundation/form/numberfield
granite/ui/components/coral/foundation/form/datepicker
granite/ui/components/coral/foundation/form/multifield


tabs = fixedcolumns = select = container  ==> for all these mandatory child node is `items`


2. Coral UI: Based on CSS/JS frameworks


#### multifield [imp]

1. Multifield
2. Composite Multifield

For multifield node, the mandatory child node is `field`

##### Dialog structure

cq:dialog
jcr:primaryType --> nt:unstructured

Mandatory properties:
1. sling:resourceType  -> String -> Granite
2. jcr:title 

- content
- items

another propery-> sling:resourceType --> String  --> Granite components


###### `sling:resourceType`
Its a component to content

## Assignment 

Create own component
Structure 
5 components
	1. textfield
	2. textarea
	3. pathfield
	4. datepicker
	5. numberfield



---

# Day5  - Components  Continuation
[20-05-2026]


### `sling:resourceSuperType`

If we want to inherit a parent component properties, we use the above property



----

# Day6 - AEM Templates
[22-05-2026]

## AEM Templates

Snapchat --> Filters --> Templates

**Def:** Blueprint of the webpages.

### Types of Templates

1. **Static:** fixed templates
	- Not recommended in `AEMaaCS` these days
2. **Dynamic** - editable or modifiable
	- Other name is `editable` templates

## Editable(Dynamic) Templates

### Steps to Create a Editable Template

1. Open CRXDE
2. The `projectname` here is `newsportal`.
3. Open `/apps/projectname/components/` for the predefined `page` component
4. Copy the `page` component and paste it in the same`/apps/projectname/components/` again.
5. Rename the node to any other name. Let's say here `anon`
6. Change the `jcr:title`  of `anon` to any other. Here, say `Anon Page`.
7. Then Open `/conf/projectname/wcm/settings/template-types/`
8. Another `page` component will be found here.  Copy it and paste it again into the same `template-types` component. 
9. Rename the node to any other name. Let's say here `anon`.
10. There will be 5 nodes exist inside the `anon` node in `template-types`.
11. Change the `jcr:title` of `jcr:content` in `anon` to any other. Here, say `Anon Page`.
12.  In `anon` component, among the 5 nodes, there will be a node called `initial`, and inside this `initial` node, there is a node called `jcr:content`, open it, and change the `sling:resourceType` to `projectname/components/anon`, which is the copy of the `page` component in the `components` node.
13. And change the `sling:resourceType` to `projectname/components/anon` again for the  `jcr:content` inside the `structure` node which is one of the nodes among the 5 nodes in the `anon` in `conf` node.
14. Open AEM start page, then open `tools` tab,  then open `Templates`(4th option from start)  in `General` tab.
15. Open the `projectname` folder, which is `Newsportal` will be found here.
16. There are 2 pre-existing templates will be found, `Content Page` and `Web Variation`.
17. Now, click on `create` button to create a new template, you will be directed to `Pick a Template Type`, besides with the pre-existing pages, you will find `Anon Page` which is created by us.
18. Select it and click on the `Next`, and give `Template Title`, say  `Anon Template` here, and click on `Create`.
19. Then `Anon Template` template will be created successfully, then click on `Done`.
20. Initially, the `Anon Template` will be in `Draft` mode by default.
21. Hover to that template, you will see 3 dots on the right top of the template, click that and click `Enable` to enable the template.
22. Once it is `Enabled`,  select that template and `edit` it.
23. While editing the template, one must have to aware of the type of editing a template: ![[Running-Notes#Edit modes in Template Editing]]
24. By default, the every new template is in the `Structure` mode.
25. Then, add any components and render the data on the web page of the template.
26. Now create a new page in `sites` using `Create` button.
		Create > Page > select `Anon Template` > `Next` > Give `Title` (say `page2` here) > `Create` > `Open`. 
27. Now by default the `Anon Template` template will be rendered on the page.
28. We can't edit that content/component on this page, because it is from the  template level not from the page level.
29. If we modify anything from the `Anon Template`, then it will be reflected in the `page2` also in the real time.


### Edit modes in Template Editing

When editing a template, choose the correct mode:

- **Structure mode**  
  Edits apply to existing and future pages.  
  Example: Template is applied to 100 pages and has a property "customer support number". After applying the template to 50 more pages and changing the property, the change appears on all 150 pages.

- **Initial mode**  
  Edits apply only to future pages. Existing pages keep their previous values.  
  Example: Template is applied to 100 pages and has a property "customer support number". After applying the template to 50 more pages and changing the property, only the new 50 pages receive the change.


## `sling:resourceType` vs `sling:resourceSuperType`


`sling:resourceType` : Component to Content.

`sling:resourceSuperType` : Component to Component like parent to child.

![[resourceType vs resourceSuperType]]


---


# Day7 - AEM Client - LIBS
[25-05-2026]

## Client LIBS

It's like a `Folder`.

### Creation of Client LIBS folder

1. Create a Node (Not Folder)
2. Set `jcr:primaryType` is `cq:ClientLibraryFolder`

#### Mandatory  Properties

>`categories`  -> String[] -->`newsportal.employee`
>`allowProxy` --> Boolean --> true

`dependencies` and `embed` --> multi value

#### Mandatory child Nodes of `clientlibs`
1. css.txt
2. js.txt

**`css.text`**

1. First and Recommended approach

```
#base=css
employee.css
```

2. Second approach 

```
css/employee.css
css/employee1.css
css/employee2.css
```


In sites -> select any page with custom template:

1. Page info
2. Edit template
3. In template, page info
4. Page policy
5. Find `Client Libraries`
6. Add `newsportal.employee`
7. Add privacy title, say`emp` here.
8. click `Done`


---


# Day8 - Sling Request Processing
[26-05-2026]

## Sling Request Processing

Sample Link:

http://localhost:4502/editor.html/content/newsportal/us/en/may-aem/page1.html

### Step 1. Entire URL is split into parts
1. Protocol: http / https
2. Host: localhost
3. Port: 4502
4. Content path: /content/newsportal/us/en/may-aem/page1
5. Selector: print
6. Extension: .html
7. Method: GET

### Step 2. Content Path

**Content path:**` /content/newsportal/us/en/may-aem/page1`

The page(resource) is checked, if the page is not found at the path and JCR location, it results in 404resource not found error, otherwise it will be generated as response


### Step 3. Get Resource Type

- Each and every node inside the CRXDE is treated as a `Resource` by Sling.

- `jcr:content` is the mandatory child node for the all the pages in CRXDE.

- Node type or `jcr:primaryType` of `jcr:content` must be `cq:PageContent`.

- `sling:resourceType` is the mandatory property for every `jcr:content` node.

### Step 4. Script Location

The value which is passed to the `sling:resourceType` can be either an **absolute** or a **relative** path.

#### Absolute Path

`/content/newsportal/us/en/may-aem/page1`

#### Relative Path

Adding `/libs/` or `/apps/` in front of the path.

### Step 5. Sling has a Priority

##### The Priority Order of Executing a Component or a Page
1. Selector + Extension
2. Selector
3. Extension
4. Method
5. Default (ComponentName.html)
6. Parent Component Script File


---

# Day9 - Sling Resource Merger
[27-05-2026]

## Sling Resource Merger

- Each and every node in the CRXDE is treated as a **Resource** by Sling.

### Sling Properties

1. `sling:hideResource` : Boolean --> True 
 Hides the entire component/resource  from rendering into the Webpage
 
**Ex:** Node `name`
```
sling:hideResource  |  Boolean  |  true
```
	
2. `sling:hideChildren` :  String\[\]  --> names of the child nodes
 Hides the multiple tabs only where the `sling:resourceSuperType` is used.

3. `sling:orderBefore` :  String --> name of the node/component
Changes the order of the tabs.

**Ex:** Node:`dob` 
```
sling:orderBefore  |  String |  name
```


4. `sling:hideProperties` : String\[\] --> name of the properties/nodes
Hides the properties or nodes in component.

**Ex:** Node: `cq:dialog`
```
sling:hideProperties  |  String[]  |  jcr:title
```


### Core `page` component

- `/apps/newsportal/components/page` : Child Component

- `/libs/core/wcm/components/page/v3/page` : Father Component
	- This `page` component has 3 tabs
		1. basic
		2. thumbnail
		3. pwa
   
- `/libs/wcm/foundation/components/basicpage/v1/basicpage`  : Grand Father Component
	- This `page` component has 3 tabs
		1. basic
		2. advanced
		3. thumbnail
		4. personalization
		5. permission
		6. cloudservice

---

# Day10 - HTL
[02-06-2026]

## HTL - HTML Templating Language

Also called as `Sightly`

Used to store and render the data on the Web Pages.

Follows `MVC` pattern -> **Model View Controller**

**Model:** For implementing Java Backend Language

**View:** For viewing the HTML/HTL file in CRXDE

**Controller:** We can control the authoring content from the Both pages and using content node in CRXDE.


### Advantages of HTL

1. Provides Security
2. Development Efficiency
3. Reduces the Cost 
4. No Java knowledge is required.

### Expressions / Syntax

`${}` -- inside the tags

`<h1>${properties.text}</h1>`


-- >Variables
-- > Literals
-- > Strings, Boolean , Numeric
-- >Operators :- Logical Operators {!, &&, ||}
-- >Ternary operator {condition?truevalue: falseValue}
-- >Comparison :- { == , != , > , < , >= , <= }
-- >Grouping paranthesis :- {()}
-- >Relational Operator :- `in`

**Ex:** 

```HTL
${'a' in 'abc'} //  true

arr = {100, 200, 300}

${100 in arr} // true

```

## HTL Format

### Date Format to render on Web Pages

`${'YYYY-MM-DD' @format=properties.dob}`

`${'DD-MM-YYYY' @format=properties.dob}`


## HTL Global Objects



**1. `properties`** - Used to call/get the values from the `cq:dialog`

Ex: `<h1>${properties.text}</h1>`


**2. `currentStyle`** - `cq:designdialog`

Ex: `<h1>${currentStyle.text}</h1>`


```
properties
pageproperties
currentStyle
currentPage
resourcePage
Component -- >com.day.cq.wcm.api.components-components
CompentContext -- >com.day.cq.wcm.api.components-componentContext
currentDesign and resourceDesign
designer
editcontext
resolver
resourceDesign
response
request
sling
currentNode
WCMmode
currentsession
log
out
reader
slytWCMhelper
XSSAPI
```


## Block Statements

**Customized Attributes:**  `data-sly` is a common prefix.

```HTL
data-sly-use
data-sly-include
data-sly-resource
data-sly-list
data-sly-test
data-sly-repeat
data-sly-template
data-sly-call
data-sly-unwrap
data-sly-text
data-sly-attribute
data-sly-element
data-sly-set
```

### 1. `data-sly-use`

Used to use the files

**Ex:**
##### `Test.class` in `package com`

`Test t = new Test();`
`t.add();`

```HTL
<div data-sly-use.t = "com.anon.Test">
<h1>${t.add}</h1>
```

For  `"com.anon.Test"`, no need to use the extension after class name(`Test`) for Java files only.
And for the rest of the file types, extension is required.


### 2. `data-sly-test`

Used to test a condition like conditional statements.

>[!NOTE]
>In side a tag, double quotes are required. Where as, in bw the tags, no double quotes are required.
>
>`<div "$ {} ">`
>`<div>$ {}</div>`

```
<div data-sly-use.design = "com.anon.Test :
<div data-sly-test = "$ {design. examPassed} ">
	// true
</div>
```

### 3. `data-sly-list`

Used for looping the content

It was repetition of the content of the host element for each enumerable property in provided object.

`labels` --> String[] -> {English, Telugu, Hindi}

```HTL
<ul data-sly-list="${properties.labels}">
	<li>${items}</li>
</ul>
```

**OP:** 
```
<li>English</li>
<li>Telugu</li>
<li>Hindi</li>
```

### 4. `data-sly-repeat`

The host element and the child elements are repeated, where as in `list`, only the child elements are looped.

**Ex:**

`labels` --> String[] -> {English, Telugu, Hindi}

```HTL
<ul data-sly-repeat="${properties.labels}">
	<li>${items}</li>
</ul>
```

**OP:** 
```
<ul><li>English</li></ul>
<ul><li>Telugu</li></ul>
<ul><li>Hindi</li></ul>
```

**We can also assign variable here:**
```HTL
<ul data-sly-repeatbooks="${properties.labels}">
	<li>${books.count}</li>
</ul>
```


### 5. `data-sly-resource`

Used to define the existing data.

**Ex:**
```
<div data-sly-resource = "${'button-1' @resourceType='/apps/newsportal/components/button'}"></div>
```


### 6. `data-sly-include`

Used to include another script file into the present file.

**Ex:**

```
<div data-sly-include="footer.html"></div>
```


### 7. `data-sly-template` & `data-sly-call`

Static and Dynamic

##### Used to initialize a template

Say name of the template is `writerInfo`:

```HTL
<div data-sly-template.writerInfo>
	<h1>First Name: Anon</h1>
	<h1>Last Name: ymous</h1>
</div>
```

```HTL
<div data-sly-call = "${writerInfo}"></div>
```

Using `data-sly-call`is the best practice to initialize a template.


```HTL
<div data-sly-template.writerInfo = "${@ firstName, lastName}">
	<h1>First Name: ${firstName}</h1>
	<h1>Last Name: ${lastName}</h1>
</div>
```

```HTL
<div data-sly-call = "${writerInfo @ firstName = 'Saloman', lastName = 'Raju'}">
</div>
```


```HTL
<div data-sly-use.raju = "writerInfo.html"></div>
<div data-sly-call = "${raju.writerInfo}"></div>
```

### 9. `data-sly-element`

```HTL
<div data-sly-element = "${properties.titleType}">${properties.text}</div>
```

### 10. `data-sly-text`

```HTL
<p data-sly-text = "${properties.jcr:description}">Enter description</p>
```

### 11. `data-sly-attribute`

```HTL
<div title="FirstName" data-sly-attribute.title="${properties.fieldLabel}"></div>
```

### 12. `data-sly-set`

Use to define a variable

```
<sly data-sly-set.title = "${properties.dob}">
```


>[!NOTE]
>Just like `div` tag in HTML, the same functionality is possessed by `sly` tag in HTL

### 13. `data-sly-unwrap`

Used to remove the host tag from the markup.

## Comments

```
<! -- this line is comment which is same as in HTML -- >
```

---

# Day11 - Experience Fragment
[03-06-2026]

## Experience Fragment

Shortcut is `XF`

Its a page whose primary type is `cq:Page`

All the content is stored at `/content/experience-fragments`

If any content that was injected in the template level each and every page with the template the content is rendering.

### Analogy 

template - a -- 100pages
template - b -- 75pages
template - c -- 50pages
template - d -- 25
template - e -- 10


### Variation

Default variation is `master` Variation

**Variation:** Have to build it from scratch 

**Variation as a Live Copy:** Same as master variation



### Uses


## Assignment 

Create a XF, connect to page

Page level
Template Level


----

# Day12 - Content Fragment
[04-06-2026]

Shortcut: `CF`

CF is an `Asset`, where as XF is a `page`

CF is a type of `dam:Asset`
XF: `cq:Page`

CF stores under: `/content/dam`
XF: `/content/experience-fragments`

-> Author Instance
-> Publish Instance

CF is not for regular development purpose, but for Headless CMS tool.

For a single time, it can only accepts 5000 requests.
5 Publish Instances

For large scale applications, running 100 publish instances at peak time is not possible.

Only ~75 publish instances got the pages.

##### **The Solution is:** 

>Headless CMS

**JSON:** Java Script Object Notation
**API:** Application Programming Interface

**Format:**

`{key: value}`

```JSON
{name: 'aem',
 type: 'cms'}
```


After a CF Model is created and saved, navigate to: `localhost:4502/assets.html/content/dam`

There are two approaches for converting CF into JSON format

1. **HttpAssetsAPI** :  `localhost:4502/api/assets/newsportal/cf/rajumodel.json` [localhost:4502/api/assets/project/folder/contentfragmentmodel.json]

2. **GraphQL** : -- needs proper Credentials 


---
---
---


# Day13 - OSGI (Open Service Gateway Initiative)
[08-06-2026]

`OSGI` stands for `Open Service Gateway Initiative`

- Introduced in 1991
- Developed initially for the embedded systems.
- Modular based Java Framework
- Used to divide the entire project into multiple small, independent, reusable parts and develop them by multiple requirements.

## Analogy

**Car Manufacturing** <--> **Newsportal(AEM) Project**
Contractor        <-->          department-1
Plumber    <-->    department-2
Electrician    <-->    department-3
Paint    <-->    department-4
Interior     <-->   department-5


## Advantages

1. **Fast Development:** OSGI maintains the list of all classes and provides the required bundles which provides the fast development.
2. **Reduce Complexity:** Multiple bundles reduce the complexity.
3. **Reusability:** We can use a single same class/model for multiple times.
4. **Dynamic Updates:** OSGI allows modifications/updates without restarting the server.
5. **Easy Deployment:** The deployment can be done without restarting the server.
6. **Secure:** Provides both the Authentication and Authorization.


## Archetypes of different Modules

**Frontend Modules:** --> `.zip` files
**Backend Modules:** --> `.jar` files


## Bundle Life Cycle

Each bundle undergoes into the following **Six Steps:**

1. Installed
2. Resolved
3. Started (optional)
4. Active
5. Stopped (optional)
6. Uninstalled

### Analogy

**Bike:**

1. Installing the Keys  --`Installed`
2. Checking the Petrol, Air pressure, Bike Condition -- `Resolved`
3. Starting the Bike, we cant see how it is going to start -- `Started`
4. Bike provides services so that we can use it to travel -- `Active`
5. After our need is satisfied, we stop the bike -- `Stopped`
6. Removing the keys -- `Unistalled`


## OSGI Architecture

1. **Module Layer:** Managing the bundles
2. **Life Cycle Layer:** The above life cycle is done here.
3. **Security Layer:** The Authorization and Authentication is provided here.
4. **Execution Layer:** All OSGI executions/implementation is happened here.
5. **Service Layer:** 


---

# Day14 - OSGI Component and Service
[09-06-2026]

These both are the java classes and the only difference is that it will listen to the life cycle of the bundle.

1. Installed
2. Resolved
3. Started
4. Active
5. Stopped
6. Uninstalled

### The 3 events of the bundle life cycle

1. Activate
2. De-activate
3. Modified

## OSGI R7 Annotations

Every annotation requires import statements:

```java
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Deactivate;
import org.osgi.service.component.annotations.MOdified;
```

1. @Component
2. @Activate
3. @Deactivate
4. @Modified
5. `@Reference` = Used to inject one OSGI component to another OSGI component


### `Logger` and `Loggerfactory` import statements

```java
import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Deactivate;
import org.osgi.service.component.annotations.Modified;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
```


```java

@Component(immediate = true, service = Demo.class)
//try to build it immediately without depending on any other models
public class TestDemo {
	private static final Logger log = LoggerFactory.getLogger(TestDemo.class);
	
	@Activate
	public void active() {
		//executes when budle is in Activte state
		log.info("Bundle -- Activated -- Test");
	}
	
	@Deactivate
	public void deactive() {
		//executes when budle is in Activte state
		log.info("Bundle -- De-activated -- Test");
	}
	
	@Modified
	public void update() {
		//executes when budle is in Activte state
		log.info("Bundle -- Updated -- Test");
	}
}
```

All the `@Component` classes are by default `singleton` classes.

In order to use them in another component classes, we have to use `@Refernece` and `service` parameter as  

```java
public class Demo {
	@Refernce 
	TestDemo td;
}
```


---

# Day15 - OSGi Configuration
[10-06-2026]

Many bundles are trained to get the data from external sources like APIs, Authentication Keys, Limits etc.
Instead of hardcoding the data, we use **OSGi Configuration** to use them.

**Example:**

`https://gorest.co.in/public/v2/posts`

If we wanna use the above source in our model, then we hardcoded that resource and deploy into AEM, then modification of the resource should be followed by the Deployment again. 

That's why the OSGi Configuration is introduced. Through them, we can deploy once and do modifications multiple times in the AEM itself, without re-deploying it for multiple times.

## OSGi R7 Annotations

1. @Component
2. @Activate
3. @Deactivate
4. @Modified
5. @Reference

- @ObjectClassDefintion
- @AttributeDefintion 
- @Designate

```java
public class Test implements Test1{}
// instead of implements, we use @Designate
```


```java
package com.karthik.newsportal.core.services;

import org.osgi.service.metatype.annotations.AttributeDefinition;
import org.osgi.service.metatype.annotations.ObjectClassDefinition;

@ObjectClassDefinition
public @interface AdithyaConfiguration {
	
	@AttributeDefinition(name = "Adithya URL Path", description ="This is a sample URL path" )
	public String restAPIurl() default "https://gorest.co.in/public/v2/posts";

}
```




```java
package com.karthik.newsportal.core.services;

import java.io.IOException;

import org.apache.http.HttpEntity;
import org.apache.http.client.methods.CloseableHttpResponse;
import org.apache.http.client.methods.HttpGet;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.util.EntityUtils;
import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Modified;
import org.osgi.service.metatype.annotations.Designate;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

@Component(service = KarthikService.class, immediate = true)
@Designate(ocd = AdithyaConfiguration.class)
public class KarthikService {
	
	private static final Logger Log = LoggerFactory.getLogger(KarthikService.class);
	
	private String articleRestUrl;
	
//	private Boolean status;
	
	@Activate
	public void activate(AdithyaConfiguration config){
		Log.info("KarthikService -- Inside the Activated Method");
		this.articleRestUrl = config.restAPIurl();
		
	}
	
	@Modified
	public void update(AdithyaConfiguration config){
		Log.info("KarthikService -- Inside the update Method");
		this.articleRestUrl = config.restAPIurl();
		
	}
	
	public String getarticle() {
		CloseableHttpClient httpclient = HttpClients.createDefault();
		HttpGet Request = new HttpGet(articleRestUrl);
		String result = null;
		try {
			CloseableHttpResponse response = httpclient.execute(Request);
			HttpEntity entity = response.getEntity();
			if(entity!=null) {
				
				result = EntityUtils.toString(entity);
			}
		}
			catch(IOException e) {
				e.printStackTrace();
			}
		
		return result;
		
	}

}
```



```java
package com.karthik.newsportal.core.services;

import org.osgi.service.component.annotations.Activate;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Deactivate;
import org.osgi.service.component.annotations.Modified;
import org.osgi.service.component.annotations.Reference;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

@Component(immediate = true)

public class PreereleaseService {
	
	private static final Logger Log = LoggerFactory.getLogger(PreereleaseService.class);
	
	@Reference
	KarthikService service;
	
	@Activate
	public void activate(){
		String ar = service.getarticle();
		Log.info("PreereleaseService -- Inside the Activated Method");
		Log.info("Response --{}",ar);
		
	}
	
	@Deactivate
	public void deactivate(){
		Log.info("PreereleaseService -- Inside the DeActivated Method");
		
	}
	
	@Modified
	public void update(){
		Log.info("PreereleaseService -- Inside the update Method");
		
	}
}
```


Two ways to open OSGi configurations:

1. In `configMgr`, find PID of our file.
2. `config` node in `/apps/newsportal/osgiconfig/`in CRXDE, create a json file in the following format.
	- `PID.cfg.json` 

#### 1. The resource URL`https://gorest.co.in/public/v2/posts` is hardcoded in the `RajuConfiguration` config file.
#### 2. We use `@Designate` to tell OSGi which configuration applies to this Component  and used that component in another component using `service` and `@Reference`. Then deployed it into AEM using Maven command `mvn clean install -PautoInstallBundle`

#### 3. The response for the URL is shown inside the `error.log` file

#### 4. The config file is show in `configMgr` of AEM

#### 5. The config file can also be updated by creating a `PID.cfg.json` file in `/apps/newsportal/osgiconfig/config` and modifying here

#### 6. The URL modification can be done at any two places, either in `configMgr` or in CRXDE, where the changes at one place can be reflected at another place.


----


# Day16 - Sling Model
[12-06-2026]

Used to apply a Business logic for a component where applying it through the HTL is not possible.


`MenuItemsModel.java`

```java
package com.karthik.newsportal.core.models;

import java.util.Date;
import java.util.List;

import javax.annotation.PostConstruct;

import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.models.annotations.DefaultInjectionStrategy;
import org.apache.sling.models.annotations.Exporter;
import org.apache.sling.models.annotations.Model;
import org.apache.sling.models.annotations.injectorspecific.ChildResource;
import org.apache.sling.models.annotations.injectorspecific.ValueMapValue;


@Model(adaptables = {Resource.class, SlingHttpServletRequest.class}, 
resourceType = "newsportal/components/raju", 
defaultInjectionStrategy = DefaultInjectionStrategy.OPTIONAL)

@Exporter(extensions = "json" , name = "jackson")

public class MenuItemsModel {

    @ValueMapValue
    public String text;

    @ValueMapValue
    public String desc;

	@ValueMapValue
    public Date expireDate;

	public String getText() {
		return text;
	}

	public String getDesc() {
		return desc;
	}

	public Date getExpireDate() {
		return expireDate;
	}

	public boolean articleExpired = false;

    public boolean isArticleExpired() {
		return articleExpired;
	}
    
    public List<RelatedMenuItemsModel> getMenu() {
		return menu;
	}
	
	@ChildResource
    private List<RelatedMenuItemsModel> menu;

	@PostConstruct
    public void init() {
    	Date today = new Date();
    	if(expireDate != null && expireDate.compareTo(today)<0) {
    		articleExpired = true;
    	}
    }
    
}

```


`RelatedMenuItemsModel.java`

```java
package com.karthik.newsportal.core.models;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.models.annotations.Model;
import org.apache.sling.models.annotations.injectorspecific.ValueMapValue;

@Model(adaptables = {Resource.class})
public class RelatedMenuItemsModel {

    @ValueMapValue
    public String menuText;

    @ValueMapValue
    public String menuLink;
    
    public String getMenuText() {
        return menuText;
    }

    public String getMenuLink() {
        return menuLink;
    }   
}
```


1. @Required
2. @Optional
#### 3. @Named and @Default

We cant use `sling:resourceType` as a variable directly in java

```java
@ValueMapValue(name = "sling:resourceType")
@Named
@Default("/apps/newsportal/components/panCard/cq:dialog/content/items/panNum")
public string slingresourceType;
```

#### 4. @Exporter
Used to create a JSON Object

#### 5. @OSGIService 
To inject an OSGI service into a Sling model

#### 6. @Self
To inject one Sling model into another Sling model

#### 7. @Reference
To inject one OSGI service into another OSGI service

#### 8. @ChildResource
To use multifield items in sling model from crxde

```java
@ChildResource
List<Resource> items;
// field -> name property = ./items in crxde
```

---
# Day17 - Sling Servlets
[15-06-2026]


## Steps to follow to create a Sling Servlet

1. Need to extend two  classes:
	1. `SlingAllMethodsServlet` --> get, post, put, delete
	2. `SlingSafeMethodsServlet` --> get
2. Need to register a class as a OSGi Service using `@Component(service = Servlet.class, immediate = true)`
3. `@SlingServletPaths (value = {"/bin/newsgortal/raju/service"} )`. We can use the url instead of direct path: `/bin/newsgortal/raju/service`. `/bin/` must be used at the front of the url.



```java
@Component(service = Servlet.class, immediate = true)
public class Test extends SlingAllMethodsServlet {

	public void doGet (SlingHttpServletRequest request , SlingHttpServletResponse response) throws ServletException, IOException{
		//stmts
	}
}
```


```java
@Component(service = Servlet.class , immediate = true)
@SlingServletPaths(value = {"/bin/newsportal/service/Sample"})
public class SampleServlet extends SlingAllMethodsServlet{

@Override
protected void doGet(SlingHttpServletRequest request, SlingHttpServletResponse response)
throws ServletException, IOException {
response.getWriter().write("Response from Resource SampleServlet -- GET");

}

@Override
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response)
throws ServletException, IOException {
response.getWriter().write("Response from Resource SampleServlet -- POST");

@Override
protected void doPut(SlingHttpServletRequest request, SlingHttpServletResponse response)
throws ServletException, IOException {
response.getWriter().write("Response from Resource SampleServlet -- PUT");

I

@Override
protected void doDelete(SlingHttpServletRequest request, SlingHttpServletResponse response)
throws ServletException, IOException {
response.getWriter().write("Response from Resource SampleServlet -- DELETE");
```


## `@SlingServletResourceTypes`

```java
@SlingServletResourceTypes (resourceTypes = {"newsportal/raju/karthik"})
```

Using this, we can use any url, without using `bin` at the front.

A custom node in `content` folder with `nt:Unstructured` and 
`sling:resourceType`: `newsportal/service/Sample`

Using postman to get all the outputs/responses.

---

# Day18 - Sling Node APIs
[17-06-2026]

Each and Everything in CRXDE is treated as a `Node`.

Without opening a CRXDE, we can do CRUD ops of `nodes` in CRXDE  with the help of `Sling Node APIs`.

## Predefined Classes of Sling Node APIs

1. `ResourceResolver`- Main class to perform the CRUD ops.
2. `Resource`
3. `ValueMap` - Used to inject values
4. `ModifiableValueMap` - Used to modify the values


### 1. `ResourceResolver`

Two ways

1. `request.getResourceResolver();`
2. System user

```java
@SlingServletPaths(value = {""})
```

```java
package com.karthik.newsportal.core.servlets;

import java.io.IOException;
import java.util.Iterator;
import java.util.*;
import javax.json.Json;
import javax.json.JsonArrayBuilder;
import javax.json.JsonObjectBuilder;
import javax.servlet.Servlet;
import javax.servlet.ServletException;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.resource.ModifiableValueMap;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ValueMap;
import org.apache.sling.api.servlets.SlingAllMethodsServlet;
import org.apache.sling.servlets.annotations.SlingServletPaths;
import org.osgi.service.component.annotations.Component;

@Component(service = Servlet.class, immediate = true)
@SlingServletPaths(value = {"/bin/newsportal/recent/articleServlet"})
public class RecentArticleServlet  extends SlingAllMethodsServlet{
	
	@Override
	protected void doGet(SlingHttpServletRequest request,SlingHttpServletResponse response)
			throws ServletException, IOException {
		
		ResourceResolver resolver = request.getResourceResolver(); //
        Resource userResource = resolver.getResource("/content/users");  //		
        
        if(userResource != null) {
        	 Iterator<Resource> userChildList = userResource.listChildren();
        	 JsonArrayBuilder userJsonList = Json.createArrayBuilder();
        	 
        	 while (userChildList.hasNext()) {
				Resource childUserResource = (Resource) userChildList.next(); //
				
				ValueMap properties = childUserResource.getValueMap();
				String firstName = properties.get("firstName", String.class);
				String lastName = properties.get("lastName", String.class);
				String email = properties.get("email", String.class);
				String phone = properties.get("phone", String.class);
				
				JsonObjectBuilder userJson = Json.createObjectBuilder();
				
				userJson.add("firstName", firstName);
				userJson.add("lastName", lastName);
				userJson.add("email", email);
				userJson.add("phone", phone);
				userJsonList.add(userJson);
			}
        	
        	 response.getWriter().write(userJsonList.build().toString());
        }		
	}

	@Override
	protected void doPost(SlingHttpServletRequest request,SlingHttpServletResponse response)
			throws ServletException, IOException {
		
		ResourceResolver resolver = request.getResourceResolver();
        Resource userResource = resolver.getResource("/content/users");  
        
        String userID = request.getParameter("userID");
        
        Map<String, Object > properties = new HashMap();
        properties.put("firstName", request.getParameter("firstName"));
        properties.put("lastName", request.getParameter("lastName"));
        properties.put("email", request.getParameter("email"));
        properties.put("phone", request.getParameter("phone"));
        
        resolver.create(userResource, userID, properties); 
        resolver.commit();
		response.getWriter().write("User ID successfully Created " + userID);
	}
	
	@Override
	protected void doPut(SlingHttpServletRequest request,SlingHttpServletResponse response)
			throws ServletException, IOException {
		
        String userID = request.getParameter("userID");
		
		ResourceResolver resolver = request.getResourceResolver();
        Resource userResource = resolver.getResource("/content/users/" + userID);  
        
        if(userResource != null) {
        	
        	ModifiableValueMap mProp = userResource.adaptTo(ModifiableValueMap.class);
        	
        	String firstName = request.getParameter("firstName");
			String lastName = request.getParameter("lastName");
			String email = request.getParameter("email");
			String phone = request.getParameter("phone");
			
			if(firstName != null) {
				
				mProp.put("firstName", firstName);
			}
            if(lastName != null) {
				
				mProp.put("lastName", lastName);
			}
            if(email != null) {
	
	            mProp.put("email", email);
                                  }
            if(phone != null) {
	
	            mProp.put("phone", phone);
                                   }
        	resolver.commit();
        	response.getWriter().write("UserID successfully Updated " + userID);
        }else {
        
		response.getWriter().write("UserID not found..");
        }
	} 
	
	@Override
	protected void doDelete(SlingHttpServletRequest request,SlingHttpServletResponse response)
			throws ServletException, IOException {
	
		String userID = request.getParameter("userID");
		
		ResourceResolver resolver = request.getResourceResolver();
        Resource userResource = resolver.getResource("/content/users/" + userID);  
        resolver.delete(userResource);
        resolver.commit();
        
        
		response.getWriter().write("UserID successfully Deleted " + userID);
	}
}
```


---
# Day19 - Sling Event Handler
[18-06-2026]

It is the way to listen and responds to the event that was occurred in cling framework or CRXDE.

**Example:**
1. Page Events - - create, delete, modify
2. Asset Events
3. Replication Events -- Activate and Deactivate
4. MSM (Multi Site Management)
5. Workflow
6. OSGI
7. Service Events
8. Resource -- adding, deleting, updating nodes/resources


## Replication

Establishing the connection bw the Author instance and the Publish instance through Replication Agent.

[One Time Set Up]
1. Copy AEM instance's `.jar` file
2. Create a folder named `publush` and paste into it.
3. `aem-author-p4502.jar` --> `aem-publish-p4503.jar`
4. Run `java -jar aem-publish-p4503.jar -gui`
5. URL will be like: `localhost:4503`
6. Open `http://localhost:4502/miscadmin`
7. Under `Replication` folder, `Agents on Author`, then `Default Agent` will be found.
8. Double click on the `Default Agent`.
9. Beside settings, there is `edit`.
10. Check connection test, when the publish instance is running
11. `Replication Test Succeed`


## Event Handler Creation

1. Java class should implement `EventHandler`
2. Convert it into OSGI Component and `Service = EventHandler.class`
3. Implement the unimplemented methods like:
	```java
	public void handleEvent(Event event);
	```


## Code

```java
package com.karthik.newsportal.core.listeners;

import org.osgi.service.component.annotations.Component;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventConstants;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.replication.ReplicationAction;

@Component(service = EventHandler.class,
          property = {EventConstants.EVENT_TOPIC+"="+ReplicationAction.EVENT_TOPIC,
          EventConstants.EVENT_FILTER+"(&(type=ACTIVATE)(path=/content/newsportal/us/en/article-details/*))"
}
		)

public class ArticleEventHandler implements EventHandler{

	private static final Logger LOG = LoggerFactory.getLogger(ArticleEventHandler.class);
	@Override
	public void handleEvent(Event event) {
		LOG.info("Inside the ArticleEventHandlerKarthik........");
		String[] Properties = event.getPropertyNames();
		for(String Property : Properties) {
			LOG.info("PropertyName -{} , PropertyValue - {}", Property,event.getProperty(Property));
		}
	}
}
```


## 

1. Save the Program and deploy it into AEM
2. Open `error.log` file and clear all the data inside it.
3. Go to `sites` and activate/publish the page.
4. Now, see the updated logs in the `error.log` file.


---
# Day20 - Sling Schedulers
[23-06-2026]

It's a background service which let's you run a piece of code automatically at a specific intervals of the time.


### Schedule:
Setting up a specific time for an event to be happened automatically.

**Example:**
1. Publishing a Republic day banner on the Jan 26th at 12:00 AM.

## Uses/Purpose:

- Automatically publishing / Unpublishing content at specific Time.
- Cleaning the old Workflows
- Sending daily reports
- Syncing data from an external API's.

## Cron Expression

Its a string that defines when and how often should a Scheduled Job should run.

Its a time-based job trigger.

### Format

``` text
* * * * * * *
```

#### Each Above Star Represents
```
* -- Seconds - (0 - 59)
* -- Minutes - (0 - 59)
* -- Hours - (0 - 23)
* -- Day of the Month  - (1 - 31)
* -- Month - (1 - 12)
* -- Day Of the week - (1 - 7)
* -- Year 
```

## Scenarios

### 1. A sling model should be run everyday at 12:00 AM

```text
0 0 0 * * *
```


### 2. If job should be run by every 5 mins

```text
* */5 * * * * 
```

### 3. If job should be run every 5 mins in a specific months on a specific days

```text
* */5 * * JAN, MAR, NOV MON, TUE, SAT
```

### `?` Symbol

Used when a a time event is OPTIONAL

```text
* */5 * ? * * -- > Optional
```

## How to create a Sling Scheduler

Step 1: Existing package called **schedulers**.

Step 2: Create a class

Step 3: Convert a class into OSGI component & service.

Step 4: You must have to implement the **Runnable** interface

Step 5: Must implement all unimplemented methods.


### How to use `ResourceResolver` 

1. Using `request.getResourceResolver()
2. System User

#### Creating `System User`

Step 1:- `localhost:4502/crx/explorer`

Step 2:- Login 

Step 3:- User Administration 

Step 4:- System User 

Step 5:- Create a User ID 

Step 6:- `localhost:4502/useradmin`

Step 7:- Update the User mapper Configuration 

http://localhost:4502/system/console/configMgr

Step 8:- user mapper

Apache Sling Service User Mapper Service Amendment

Step 9:- Open that tab:-

`newsportal.core:subservicename=servicename`-->user


## Program for System User

```java
package com.karthik.newsportal.core.servicesImp;

import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import java.util.*;

@Component(service = KarthikRes.class)
public class KarthikRes {
	
	@Reference
	ResourceResolverFactory factory;
	
	public ResourceResolver getResourceResolver() {
		ResourceResolver resolver = null;
		
		try {
			
			Map<String,Object> prop = new HashMap();
			prop.put(ResourceResolverFactory.SUBSERVICE, "eHandler");
			resolver = factory.getServiceResourceResolver(prop);
		}
		catch(org.apache.sling.api.resource.LoginException e) {
			e.printStackTrace();
			
		}
		
		
		return resolver;
	}

}
```



## Program on Sling Schedulers


```Java
package com.karthik.newsportal.core.schedulers;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ValueMap;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.replication.ReplicationActionType;
import com.day.cq.replication.ReplicationException;
import com.day.cq.replication.Replicator;
import com.day.cq.wcm.api.Page;
import com.day.cq.wcm.api.PageManager;
import com.karthik.newsportal.core.servicesImp.KarthikRes;

import java.util.Date;
import java.util.Iterator;

import javax.jcr.Session;

@Component(immediate = true, service = Runnable.class, property = { "scheduler.expression = */30 * * ? * * " })
public class Test implements Runnable {

    private static final Logger log = LoggerFactory.getLogger(Test.class);

    @Reference
    KarthikRes karthik;

    @Reference
    Replicator replicator;

    @Override
    public void run() {
        log.info("I am Inside the Sling schedulers...--RajuScheduler");

        try (ResourceResolver resolver = karthik.getResourceResolver()) {
            PageManager pagemanager = resolver.adaptTo(PageManager.class);
            Page articlepage = pagemanager.getPage("/content/newsportal/us/en/article-details");
            Iterator<Page> childpages = articlepage.listChildren();
            while (childpages.hasNext()) {
                Page page = (Page) childpages.next();
                Resource contentResource = page.getContentResource();
                ValueMap properties = contentResource.getValueMap();
                Date articleExpiry = properties.get("articleExpiry", Date.class);
                Date today = new Date();
                if (articleExpiry != null && articleExpiry.compareTo(today) < 0) {
                    Session session = resolver.adaptTo(Session.class);
                    replicator.replicate(session, ReplicationActionType.DEACTIVATE, page.getPath());
                } 

            } 
        }

        catch (ReplicationException e) {
            e.printStackTrace();
        } 
    }

}
```



Step1:- Write a program
Step 2:- Deploy the program
Step 3:- CRXDE --> /content/newsportal/us/en/article-details -->jcr:content 
Step 4:- Add the property --> `articleExpiry` -->Date --> Yesterday
Step 5:- Error.log and erase the log and reopen the file.

---

# Day21 - Query Builder
[24-06-2026]

Used to filter the JCR repository 

1. **x-path** - Uses the query builder for the implementation. (older approach)
2. **SQL-2** - Used to search and filter the content in the JCR. (latest approach)

**URL:** `localhost:4502/libs/cq/search/content/querydebug.html/`

- `predicates`  means `condition`

## Examples using `x-path` 

1. `type = cq:Page` - Used to search all the pages in the AEM.
2. Used to get all the paths of the above pages:
```
type = cq:Page
p.limt = -1
```

3. Used to get 30 pages
```
type = cq:Page
p.limt = 30
```

4. Used to get the pages from 31 to 40 pages
```
type = cq:Page
p.offset = 30
p.limt = 10
```

5. Get pages in all pages with paths in `/content/newsportal`
```
type = cq:Page
path=/content/newsportal
p.limit = -1
```

6. Get a particular page with a particular template
```
type = cq:Page
path = /content/newsportal
property = jcr:content/cq:template
property.value = /conf/newsportal/settings/wcm/templates/raju
p.limit = -1
```

7. Get by order
```
...
orderby=@jcr:content/jcr:created
// orderby.sort = desc
..
```

8. Get date range
```
daterange.property = jcr:content/jcr:jcr:created
daterange.lowerbound = 2026-06-15T12:19:25.641+05:30
daterange.upperbound = 2026-06-18T12:19:25.641+05:30
```

**Date format:** `2026-06-18T12:19:25.641+05:30`

9.  Get any node or resource that contains `raju` from JCR
```
type=cq:Page
fulltext=raju
p.limit=-1
```

### Predicates used so far

```
type
path
p.limit
p.offset
property
property.value
orderby
orderby.sort 
daterange.property
daterange.lowerbound
daterange.upperbound
fulltext

```

### Grouping

**Ex:**
```
group. 1_property=
group. 1_property. value=
group. 2_property=
group. 2_property. value=
```

## SQL-2


SQL-2 -> X-path ->

SELECT * FROM [cq:Page] AS s WHERE ISDESCENDANTNODE([/content/newsportal])

![ssx](https://iili.io/CA3RiKP.png)




---

# Day22 - AEM Run Modes
[25-06-2026]

There are separate modes to run instance with different credentials like developer, publisher etc.

### There are **two** types of run modes:

## 1. Installation Run Mode : --> Standard / Primary / Installation / OOTB Run Mode

- author Instance
- publish instance
- samplecontent
- nosamplecontent
- AEM 6.5 -- WKND
- AEMaaCS

#### Four Combinations

1. author, samplecontent
2. author, nosamplecontent
3. publish, samplecontent
4. publish, nosamplecontent

**Command:** 

```bash
java -jar aem-author-p4502.jar -r samplecontent
```


## 2. Custom Run Modes

1. dev
2. qa
3. stage
4. prod
5. preprod
6. uat
7. sit
8. live

### Developer Combinations

1. author, dev
2. publish, dev
3. ....
4. author, qa
5. publish, qa

### Environments

```
config.author.dev
config.publish.dev
config.dev
config
config.author
config.publish
```

It follows a specific priority order to fetch a particular API URL:

For `author`:
1. First, it checks in `config.author.dev`
2. It's not there then, it checks in  `config.author`
3. Likewise, `config.dev`
4. Then, `config`
5. Finally, default values.

For `publiish`:
1. First, it checks in `config.publish.dev`
2. It's not there then, it checks in  `config.publish
3. Likewise, `config.dev`
4. Then, `config`
5. Finally, default values.

#### Commands

**Approach 1:**

```bash
-Dsling.run.modes=dev

java -jar aem-author-p4502.jar -Dsling.run.modes=dev
```

**Approach 2:**

```

crx-quickstart -> conf -> sling.properties -> add `sling.run.modes=dev` in the sling.properties file -> save
```

**Approach 3:** 

```bash
java -jar aem-author-p4502.jar -r dev
```

##### Testing Purpose

```bash
java -jar aem-author-p4502.jar -Dsling.run.modes=dev

```

After running above command, then check in `sling settings` in `cfgMgr`,  **dev** will be found there.

---

# Day23 - Core Components & Style System
**[26-06-2026]**

## Core Components

Core Components are Adobe's **pre-built reusable components**.

They follow AEM best practices and are recommended for new projects.

Examples

- Title
    
- Text
    
- Image
    
- Button
    
- List
    
- Carousel
    
- Teaser
    
- Accordion
    

Instead of creating these components from scratch, we can reuse and customize them.



### OOTB (Out Of The Box) Components

OOTB Components are the components provided by Adobe by default.

No need to create them manually.


### Component Evolution

#### 1. Foundation Components

**Path**

```text
/libs/foundation/components
```

**Technology**

- JSP
    
- Classic Dialog
    
- WCMUsePojo
    

> Older implementation. Not recommended for new development.



#### 2. WCM Foundation Components

**Path**

```text
/libs/wcm/foundation/components
```

**Technology**

- HTL
    
- Classic UI / Touch UI Dialog
    
- WCMUsePojo
    

> Better than Foundation Components, but still considered legacy.


#### 3. Core Components

**Path**

```text
/libs/core/wcm/components
```

This is the standard path used in **AEM as a Cloud Service (AEMaaCS).**

**Technology**

- HTL
    
- Sling Models
    
- Touch UI
    
- Style System
    
- Editable Templates
    

> This is the recommended approach for modern AEM projects.


### Coral UI Components

Coral UI provides ready-made UI elements used inside AEM dialogs.

Example Path

```text
/libs/coral/foundation/ui/
```

Example

```text
/libs/granite/ui/components/coral/foundation/form/textfield
```

This represents a **Text Field** used in Touch UI dialogs.



### Component Comparison

|Foundation|WCM Foundation|Core Components|
|---|---|---|
|JSP|HTL|HTL|
|Classic Dialog|Classic + Touch UI|Touch UI|
|WCMUsePojo|WCMUsePojo|Sling Models|
|Legacy|Legacy|Recommended|



#### Classic UI vs Touch UI

#### Classic UI

- Old User Interface
    
- ExtJS based
    
- Used in older AEM versions
    
- Not recommended
    



#### Touch UI

- Modern UI
    
- Coral UI based
    
- Responsive
    
- Used in AEM 6.x and AEMaaCS
    

> Modern AEM development uses **Touch UI**.



## Style System

Style System allows Authors to apply different CSS styles **without changing the component code.**

One component can have multiple visual appearances.


### Example

Title Component

Author can choose

- Red
    
- Green
    
- Blue
    
- Orange
    

without creating multiple Title components.


### Enabling Style System
### Step 1

Copy

```text
cq:design_dialog
```

from

```text
/libs/core/wcm/components/title/v3/title
```

Paste it into your custom component.



#### Step 2

Open

**Template Editor**

↓

Select your component

↓

Open **Policies**

↓

Configure the available styles.


#### CSS Example

```css
.redd{
    color:red;
    text-align:center;
    background:black;
}

.greenn{
    color:green;
    text-align:center;
    background:black;
}

.bluee{
    color:blue;
    text-align:center;
    background:black;
}

.yelloww{
    color:yellow;
    text-align:center;
    background:black;
}

.pinkk{
    color:pink;
    text-align:center;
    background:black;
}

.orangee{
    color:orange;
    text-align:center;
    background:black;
}
```

Each CSS class becomes a selectable style inside the Style System.



### Useful URL

AEM Core Components Playground

```text
https://www.aemcomponents.dev/
```

Use this website to

- Explore Core Components
    
- View component examples
    
- Check dialogs
    
- Understand authoring behavior
    
- Learn recommended implementation
    
---

# Day24 - User Management, Workflow & Dispatcher

**[26-06-2026]**

## 1. User Management

User Management is used to create and manage:

- Users
    
- Groups
    
- Permissions
    
- Roles
    

### Example

Suppose a company has **30 employees** working in AEM.

```
2  -> Admins
18 -> AEM Developers
5  -> QA(Testers)
5  -> Content Authors
```

Instead of assigning permissions to every user individually, we create **Groups**.

Example:

```
Admin Group
 ├── User 1
 └── User 2

Developer Group 1
 ├── 9 Users

Developer Group 2
 ├── 9 Users

QA Group
 ├── 5 Users

Content Group
 ├── 5 Users
```

Then permissions are assigned to the **Group**, not to individual users.

If a new developer joins,

Just add the user to the Developer Group.

No need to assign permissions again.

### Access User Management

```
http://localhost:4502/useradmin
```

### Common Roles

```
Admin
↓

Team Lead
↓

Developers
↓

Content Authors
↓

QA(Testers)
```


## 2. Workflow

Workflow means

> **A step-by-step process to complete a task automatically or with approvals.**


### Real-life Example

Chocolate Manufacturing

```
Collect Seeds
      ↓
Prepare Chocolate
      ↓
Packing
      ↓
Transport
      ↓
Delivered to Vendors
```

Every step must be completed before moving to the next step.


### AEM Workflow Example

Publishing a Page

```
Developer
↓
UI / Frontend Team
↓
QA Testing
↓
Pre-Production Team
↓
Production
↓
Page Published
```

### Explanation

**Step 1**

Developers check

- Components
    
- Backend Logic
    
- Functionality
    

↓

**Step 2**

Frontend Team checks

- HTML
    
- CSS
    
- JavaScript
    
- Responsive Design
    

↓

**Step 3**

QA Team

- Testing
    
- Bug Verification
    

↓

**Step 4**

Pre-Production

Final verification before going live.

↓

**Step 5**

Production

Page is published to Live Server.


### Typical Workflow Stages

```
Start
↓

Review
↓

Approve
↓

Activation (Publish)
↓

End
```


### Workflow Uses

- Content Approval
    
- Page Publishing
    
- Asset Approval
    
- Automatic Notifications
    
- Business Approval Process
    


## 3. Dispatcher

Dispatcher is a combination of

- Load Balancer
    
- Cache
    
- Security Layer
    

It sits between

```
Client

↓

Dispatcher

↓

AEM Publish Instance
```

Instead of every request going to AEM,

Dispatcher serves cached content whenever possible.

This makes the website much faster.


### Request Flow

```
Browser

↓

DNS
(Domain Name Server)

↓

CDN
(Content Delivery Network)

↓

Dispatcher

↓

AEM Publish Server

↓

Response
```

### Example

User opens

```
www.flipkart.com
```

Flow becomes

```
Browser

↓

DNS

↓

CDN

↓

Dispatcher

↓

AEM Publish

↓

Page Returned
```


### Real-life Example

#### Movie Theatre

Whether your ticket costs

```
₹100

or

₹1000
```

Everyone watches the same movie.

Similarly,

When many users open the same page,

Dispatcher serves the same cached page instead of asking AEM repeatedly.


#### Another Example

Buying a Flat

```
Customer

↓

Broker

↓

Owner
```

Mapping in AEM

```
Client

↓

Dispatcher (Broker)

↓

AEM Publish Server (Owner)
```

Dispatcher communicates with AEM and returns the response to users.


### Advantages of Dispatcher

#### 1. Content Caching

Frequently requested pages are stored in cache.

Result

- Faster page loading
    
- Reduced server load
    

#### 2. Security

Dispatcher can

- Allow requests
    
- Deny requests
    
- Block unwanted URLs
    

It protects the Publish instance from direct access.

#### 3. Load Balancing

If multiple Publish servers exist,

Dispatcher distributes requests among them.

This improves

- Performance
    
- High Availability
    

### Dispatcher Configuration

Common configuration files

```
conf/

dispatcher.d/

dispatcher.any
```


### Allow and Deny Rules

Example

```
deny

/content/newsportal
```

Blocks access.

Example

```
allow

/content/newsportal/us/en/march-aem/page-1.html
```

Allows only that page.


### Tools Used for Dispatcher

- Docker
    
- Fiddler Classic
    
----

