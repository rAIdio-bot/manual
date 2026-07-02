# Privacy Policy

**Last updated: July 2, 2026**

We are pro-privacy. rAIdio.bot collects no information about you for analytics, tracking, advertising, or profiling — none. This policy exists to tell you exactly what that means and to document the narrow cases where third-party infrastructure is involved.

The Software runs locally and does not transmit your audio, prompts, or generated content — ever. There is one required exception: **license activation**, which transmits your order ID and a machine identifier to enforce the license terms (see Section 6). Your purchase itself is handled by our e-commerce provider, LemonSqueezy, who is the data controller for that transaction.

We will never collect audio, prompts, or generated content.

## 1. Local-First Design

rAIdio.bot is designed to run entirely on your local machine. All audio generation, voice processing, mixing, and file management happens locally. No audio, text prompts, generated content, or usage data is transmitted to us or any server we operate. The sole exception is license activation (Section 6), which transmits your order ID and a machine identifier solely to enforce the license terms — never your content.

## 2. Data We Do Not Collect

We do not collect:

- Your audio files or generated content
- Your text prompts or lyrics
- Your voice recordings or training data
- Usage analytics or telemetry of any kind
- Crash reports or diagnostic data
- Device identifiers, IP addresses, or location data for analytics, profiling, or tracking (the sole exception is the machine identifier used for license activation — see Section 6)
- Cookies or tracking identifiers of any kind

Beyond the order ID and machine identifier used for license activation (Section 6), there is no database of users, no user account system, and no analytics dashboard. We do not build a profile of you, and we have designed the Software so that we cannot.

## 3. Data Stored Locally

The Software stores the following data on your machine only. It does not leave your machine unless you choose to share the files yourself:

- Your preferences and settings (via local application storage)
- Creator identity fields you enter (name, email, URL) for C2PA signing
- Generated audio files and metadata sidecars in your Documents folder
- AI model files in the application directory

## 4. C2PA Content Credentials

When C2PA signing is enabled, creator identity fields you provide (name, email, URL) are embedded in the cryptographic signature attached to your output files. This information becomes part of the file itself and will be visible to anyone who inspects the C2PA manifest. You control what identity information you enter. You may leave those fields blank or use a pseudonym. We do not receive or store this information.

## 5. Updates

The Software receives updates as signed installers published to our public release repository on GitHub. In all cases we receive only what is described below and nothing more.

**Direct download (GitHub)**
When the Software checks for or downloads an update, it requests a public release file from GitHub and sends no account, license, or identifying information to do so; we do not log who downloads updates. If you file a support issue or pull request on GitHub, we receive your GitHub username and the content of your submission, which we use solely to respond. GitHub's own privacy policy governs their platform.

**Hugging Face**
Model files and updates obtained via Hugging Face are accessed anonymously where Hugging Face permits anonymous access. We do not require you to authenticate with us to obtain these files. Hugging Face's own privacy policy governs their platform.

## 6. License Activation and Purchases

When you purchase rAIdio.bot, the purchase is processed by our e-commerce provider, **LemonSqueezy** (Lemon Squeezy, LLC), acting as merchant of record and as the **data controller** for your purchase. The name, email, and payment details you enter at checkout are held by LemonSqueezy under their privacy policy; we do not receive or store your payment details.

To run a licensed copy, the Software must activate. Activation transmits your **license key** and a **machine identifier** (a value identifying your machine) to enforce the license terms and detect abuse such as unauthorized sharing of your license (see the EULA, Section 2.3). From this, **we retain only your order ID and your machine identifier**, used solely for license enforcement. We do not retain your name, email, or payment information, and no audio, prompts, projects, or generated content is transmitted at any point. After activation, normal use of the Software is offline and does not contact the licensing service.

## 7. Support

We provide community support via a Discord server. We do not log Discord conversations, do not retain transcripts of support interactions, and do not use Discord to collect data about you. Discord's own privacy policy governs the Discord platform. You are not required to use your real name or provide identifying information to participate.

We also provide support via a GitHub issue tracker. If you file a support ticket there, we receive your GitHub username and the content of your submission. We use that solely to respond to your request. GitHub's own privacy policy governs the GitHub platform.

If you contact us by email at info@rAIdio.bot, we receive only what you send and use it solely to respond to you.

## 8. Third-Party Services During Normal Operation

During normal use the Software communicates only between its components running on your local machine, specifically between the application and its local backend on localhost. No network requests are made to external services during audio generation, mixing, voice processing, or file management.

## 9. Children

The Software is not directed at children under 16 (or the applicable age of digital consent in your jurisdiction). We do not knowingly collect information from children. Aside from the license activation data described in Section 6, we collect no information from anyone.

## 10. Your Rights

The only personal data we retain is your order ID and machine identifier, used to enforce license activation (Section 6). You may request access to, or deletion of, that data by emailing info@rAIdio.bot with your order ID; note that deleting your activation data may require you to re-activate the Software. Your purchase data (name, email, payment) is controlled by LemonSqueezy — direct those requests to them under their privacy policy. We hold no other personal data.

Users in the European Economic Area, United Kingdom, and other jurisdictions with data protection law retain all statutory rights under those laws. We will respond to any formal request.

## 11. Changes to This Policy

If we change this policy in a way that involves collecting data we do not currently collect, we will notify you through the Software before the change takes effect and obtain your consent where required by law. Routine clarifications will be distributed with Software updates and noted in the changelog.

---

© 2026 Creative Mayhem UG (haftungsbeschränkt). rAIdio.bot® is a registered trademark of Creative Mayhem UG. All other trademarks are property of their respective owners.
