# Open Spaces: Common Schema & Sandbox

Welcome to the **Open Spaces** repository, maintained by [H-Net:
Humanities and Social Sciences Online](https://networks.h-net.org/).

This project provides a robust, standardized ecosystem for researchers.
It establishes a **common variable schema** inside a no-code database
environment, seamlessly bridging local data collection with powerful,
live Drupal web visualizations.

---

## 🎒 New to Open Spaces or GitHub? Start Here!

Before downloading files or running code, please visit our foundational
onboarding hub on **STEMEd+ Commons**.

* **First-Time Setup Guidance:** If you are new to Git or GitHub, we
have a comprehensive, step-by-step primer on STEMEd+ Commons to guide
you through clone – copying to your own github account - and fork –
downloading to your own computer.

* **Join the Community Group:** Connect with other researchers, share
your progress, and stay updated on upcoming workshops.  Join the
[STEMEd+ Commons Open Spaces Group](https://stemedplus.hcommons.org/).

* **Discussion Forum & Listserv:** Our group features an integrated
discussion forum that functions as an interactive listserv.  Use it to
troubleshoot schema mapping, ask technical questions, or collaborate on
features.

* **Events Calendar:** Check the group calendar for live tutorials, open
hackathons, consultation hours, and governance meetings.

---

## 🚀 Project Overview

Managing and displaying structured research often suffers from software
bottlenecks.  This repository resolves those friction points by
integrating two main tools:

1.  **NocoDB**: A flexible, spreadsheet-like no-code relational database
used to host and structure your datasets via our standardized variable
schema.

2.  **Drupal**: A powerful Content Management System (CMS) that pulls
live data directly from NocoDB to generate dynamic web visualizations.

By downloading this repository, you can deploy a complete, local
developer **sandbox** on your machine to upload your data, test the
common schema, and preview visualizations.  You can keep your data on
your computer forever or you can share it publicly for others to access
and use.

---

## 🛠️ System Prerequisites

Before initializing your sandbox, you must install the core
virtualization dependencies for your operating system.

### 1. Docker

Docker acts as the underlying containerization engine that isolates your
database and CMS environments.

* **Download & Install:** Follow the official guide for [Docker
Desktop](https://docs.docker.com/desktop/).

* **Verification:** Ensure Docker is running in your system tray before
proceeding.

### 2. DDEV

DDEV is an open-source local development tool that significantly
simplifies configuring PHP, MySQL, and Drupal environments via Docker.

* **Download & Install:** Follow the platform-specific instructions on
the [DDEV Installation
Guide](https://docs.ddev.com/en/stable/users/install/ddev-installation/).

* **Verification:** Open your terminal and run `ddev --version` to
ensure it is configured properly.

---

## 📦 Sandbox Setup & Installation

Follow these sequential steps to initialize your local Open Spaces
sandbox:

### Step 1: Clone the Repository

Open your terminal, navigate to your preferred development folder, and
run:

```
git clone https://github.com/H-Net-Humanities/Open-Spaces
cd Open-Spaces

```

### Step 2: Spin Up the DDEV Environment (Drupal & NocoDB)

This repository includes pre-configured DDEV configuration files that
automatically fetch and build containers for both Drupal and NocoDB.
Launch the sandbox by running:

```
ddev start
```

*DDEV will output distinct local URLs once initialization completes
successfully (e.g., `http://container.ddev.site:33000/` for Drupal).*

If you ever need to find the URL(s) for your installation, you can run:

```
ddev describe
```

Next, configure some things about your Drupal installation:

```
ddev composer create-project drupal/recommended-project
ddev composer require drush/drush
ddev drush site:install -y minimal --account-name=admin --account-pass=admin
ddev drush theme:enable -y claro
ddev drush config-set system.theme default claro
ddev launch
```

---

## 💾 Uploading Data & Mapping the Schema

Once your sandbox containers are running, you can upload your existing
data into the pre-configured NocoDB environment.

### 1. Access Your NocoDB Interface

* Open your browser and navigate to the NocoDB container URL specified
by your DDEV startup output (e.g.  `http://container.ddev.site:33000/`).

* Create a local admin account to log into the dashboard.

### 2. Import Your Tables

* Inside your NocoDB dashboard, create a new Project or Base.

* Click **Import Data** and upload your CSV or Excel files.

### 3. Apply the Common Variable Schema

To ensure your data connects flawlessly to the Drupal visualization
templates, map your imported columns to the strict schema standards
included in this repository:

* Review the template file in `Schema/common-variable-schema.json`.

* Adjust your NocoDB column names and field types (e.g.,
`SingleLineText`, `Link`, `Attachment`) to match the required variable
IDs.

---

## 📊 Connecting NocoDB to Drupal Visualizations

With your data structured under the common schema, Drupal can ingest it
natively to output interactive maps, timelines, or charts.

1.  **Log Into Drupal:** Navigate to your local Drupal URL (e.g.,
`https://container.ddev.site:33000/`) and log in using the credentials
provided during environment setup.

2.  **Configure the NocoDB Views API:** Navigate to *Configuration > Web
Services > NocoDB Connect* within your Drupal backend.  Input the
internal Docker network credentials or API token generated by your local
NocoDB instance.

3.  **Generate Visualizations:** Because your tables adhere to the
**Open Spaces Schema**, Drupal's pre-packaged View blocks will
auto-populate with your text data, relationships, and multimedia files.

---

## 🤝 Contributing & Feedback

If you encounter technical bottlenecks during validation, or if you want
to suggest improvements to the core schema properties:

* Post a thread in the **STEMEd+ Commons Open Spaces Discussion Forum**
for peer support.

* Submit a formal bug or feature request via the [Open Spaces GitHub
Issues](https://github.com/H-Net-Humanities/Open-Spaces/issues) tab.

### 📊 Visualization Component Mapping

By adhering to the Open Spaces Common Schema, your NocoDB fields
automatically activate the following interactive outputs inside the
Drupal framework:

* **Geospatial Maps:** Generates dynamic regional overlays from
coordinate or address fields.

* **Interactive Timelines:** Plots chronological data chains using
standardized date strings.

* **Analytical Charts:** Compiles categorical tags into bar charts, pie
graphs, and scatter plots.

* **Searchable Data Tables:** Converts rows into accessible, filterable
public spreadsheets.

### 💾 Exporting and Saving Visualizations

While your dashboards are rendered live using responsive **HTML5** and
**SVG** web components, researchers can extract completed visuals
directly from the interface in the following publication-ready file
formats:

* **Static Images:** Export as high-resolution `.png` or `.jpg` for
slides or digital media.

* **Print Layouts:** Generate vector-sharp `.pdf` documents for
reference materials.

* **Scalable Vectors:** Download raw `.svg` files for post-processing
and custom graphic edits.

### 🤝 Contributing & Feedback

We welcome contributions from the Open Spaces cohort to help expand our
open-source tools, refine data standards, and build richer research
dashboards.

### 🐛 Reporting Issues & Bugs

If you encounter software bottlenecks, installation errors with
Docker/DDEV, or broken API connections inside your local sandbox:

* Check the existing project threads in the **STEMEd+ Commons Open
Spaces Discussion Forum** to see if your issue has a quick fix.

* Open a formal tracker ticket directly on the [Open Spaces GitHub
Issues](https://github.com/H-Net-Humanities/Open-Spaces/issues) page
if you discover a reproducible platform bug.

### 📋 Suggesting Additions to the Common Schema

If your dataset requires specialized fields that are missing from the
current global template rules that you believe other projects would
benefit from:

* Start a topic thread in our community forum detailing your specific
research field and the variables you wish to introduce.

* Submit a **Pull Request (PR)** containing your proposed modifications
directly to our root `Schema/common-variable-schema.json` path using
your **GitHub fork mechanics**.

### 📊 Proposing New Core Visualizations

If your data needs custom dashboard output components that are not
natively supported by our default Drupal templates:

* Outline your specific requirements, preferred JavaScript frontend
libraries (like D3.js or Leaflet plug-ins), and desired data formats in
the community discussion space.

* File a detailed feature request on GitHub Issues outlining exactly
which NocoDB data properties are needed to drive the requested browser
layouts.
