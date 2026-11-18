# FEATURETHON'26

Organised by Google Developer Groups (GDG), Gokaraju Lailavathi Engineering College.

Explore an existing web application, identify a genuine user problem, propose an innovative improvement, and implement a meaningful feature or working prototype to demonstrate to the jury. The challenge is to improve the application, not rebuild it from scratch.

## Event format

30 participants take part and are randomly assigned to one of three projects, about 10 participants per project. Participants choose neither their project nor their presentation order. They compete only against others assigned to the same project. One winner is selected from each project, for three winners total.

## Projects

Projects are assigned; participants do not choose one.

| Project | Description | Required Node.js | Package Manager | Additional Requirements |
| --- | --- | --- | --- | --- |
| [Simple React Ecommerce](https://github.com/alim1496/simple-react-ecommerce) · [Guide](./simple-react-ecommerce/README.md) | Ecommerce storefront with product browsing, categories, search, and shopping cart. | Vite 5: `^18.0.0` or `>=20.0.0`; Node 24 LTS recommended | npm | Internet for DummyJSON product data |
| [Tripix](https://github.com/MiladJoodi/Tripix) · [Guide](./Tripix/README.md) | Sample travel search and booking app for bus, train, and air. | Next.js 16: `>=20.9.0`; Node 24 LTS recommended | npm | None; sample data included |
| [PancakeMaker](https://github.com/momentmaker/pancakemaker) · [Guide](./pancakemaker/README.md) | Offline-first expense tracker with optional cloud sync. | `>=20`; Node 24 LTS recommended | npm 10.9.0 | Cloudflare and Resend only for optional sync |

A fresh Windows install of Simple React Ecommerce is **NOT TESTED**: a previous attempt did not finish. Check its guide before the event.

## Event rules

- The event starts at **9:00 AM sharp**. Registration closes at **9:30 AM**.
- Participants must remain at the venue except for emergencies, medical needs, or short breaks with a coordinator's permission.
- Follow coordinator instructions throughout the event.
- Maintain discipline and ensure fair opportunities for everyone.

## What you will do

1. Explore your assigned application and understand its existing functionality.
2. Identify gaps, limitations, and problems affecting the user experience.
3. Brainstorm innovative and practical improvements.
4. Develop a meaningful feature or working prototype.
5. Demonstrate your implementation and explain how it improves the application.

You do not need to rebuild the application. A production-ready implementation is not required, but your work should demonstrate a meaningful improvement.

## Presentation

You have **5 minutes** for your project presentation and demonstration, followed by **2 minutes** for questions from the jury. Cover:

- The problem you identified.
- Your proposed solution.
- The feature or prototype you implemented.
- How your improvement benefits users.

## Judging criteria

Each judge scores every participant from 1 to 5 in each category, for a maximum of 25 points per judge.

| Category | What is evaluated |
| --- | --- |
| Problem Identification & Purpose | How clearly the participant identifies a genuine user problem and explains its importance |
| Innovation & Originality | Creativity and uniqueness of the proposed solution |
| Technical Depth & Implementation | Quality and functionality of the implemented feature or prototype |
| User Experience & Feasibility | Whether the improvement is useful, practical, and easy to use |
| Presentation & Demonstration | How clearly the participant explains and demonstrates their solution |

| Score | Description |
| --- | --- |
| 5 | Exceeds one or more brief goals in an innovative way |
| 4 | Moderately exceeds one or more brief goals |
| 3 | Meets one or more brief goals |
| 2 | Nearly meets at least one brief goal |
| 1 | Does not meet any brief goal but receives a participation point |

Each project is evaluated separately. The participant with the highest average total score across all judges evaluating that project wins. Exactly one winner is selected per project.

Tie-breakers:
1. Higher average Technical Depth & Implementation score.
2. If still tied, higher average Problem Identification & Purpose score.
3. If still tied, the head judge makes the final decision.

## Prerequisites

- [Git](https://git-scm.com/install/) is required to clone repositories.
- [Node.js](https://nodejs.org/en/download) 24 LTS is a compatible recommendation for all three projects based on their published engine requirements. Node.js is required at the project-specific versions above; npm comes with it. PancakeMaker requires npm 10.9.0.
- [Visual Studio Code](https://code.visualstudio.com/download) is optional.
- [Google Chrome](https://www.google.com/chrome/) is optional; any modern browser can be used.
- On Windows, use PowerShell. On macOS or Linux, use `npm` instead of `npm.cmd`.

## Participant workflow

1. Check your assigned project.
2. Open its participant setup guide.
3. Install the required software.
4. Clone the original GitHub repository locally.
5. Install dependencies and start the application.
6. Explore its existing functionality.
7. Identify a genuine problem or missing feature.
8. Develop your proposed improvement or working prototype.
9. Prepare your presentation and demonstration.
10. Present your work to the jury.

Each participant works on their own local clone of the assigned project. GitHub submission is not required. Local Git commits are optional.

Never commit `.env` files, API keys, passwords, or other secrets.
