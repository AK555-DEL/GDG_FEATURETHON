# FEATURETHON'26

Organised by Google Developer Groups (GDG), Gokaraju Lailavathi Engineering College.

Explore an existing web application, identify a genuine user problem, propose a practical improvement, and implement a meaningful feature or working prototype to demonstrate to the jury. The challenge is to improve the application, not rebuild it from scratch.

## Event format

30 teams take part and are randomly assigned to one of three projects, about 10 teams per project. Teams choose neither their project nor their position in the order. Teams compete only against other teams on the same project. A jury evaluates each project separately; one winner is selected per project, for three winners total.

This is Round 1: [TO BE CONFIRMED: whether there is a later round]. Team size: [TO BE CONFIRMED].

## Projects

Projects are assigned; teams do not choose one.

| Project | Description | Required Node.js | Package Manager | Additional Requirements |
| --- | --- | --- | --- | --- |
| [Simple React Ecommerce](https://github.com/alim1496/simple-react-ecommerce) · [Guide](./simple-react-ecommerce/README.md) | React storefront demo with product browsing, cart, and wishlist. | Vite 5: `^18.0.0` or `>=20.0.0`; Node 24 LTS recommended | npm | Internet for DummyJSON product data |
| [Tripix](https://github.com/MiladJoodi/Tripix) · [Guide](./Tripix/README.md) | Sample travel search and booking app for bus, train, and air. | Next.js 16: `>=20.9.0`; Node 24 LTS recommended | npm | None; sample data included |
| [PancakeMaker](https://github.com/momentmaker/pancakemaker) · [Guide](./pancakemaker/README.md) | Offline-first expense tracker with optional cloud sync. | `>=20`; Node 24 LTS recommended | npm 10.9.0 | Cloudflare and Resend only for optional sync |

A fresh Windows install of Simple React Ecommerce is **NOT TESTED**: a previous attempt did not finish. Check its guide before the event.

## Event rules

- The event starts at 9:00 AM sharp. Registration closes at 9:30 AM.
- Participants should remain at the venue during the event, except for emergencies, medical needs, or short breaks with a coordinator's permission.
- Follow coordinator instructions, maintain discipline, and ensure fair opportunities for all teams.

## Presentation

Each team has 5 minutes to present, followed by 2 minutes for jury questions. Demonstrate the original problem, your proposed solution, the feature or prototype you implemented, and how it benefits users.

## Judging

Each judge scores every team from 1 to 5 in each category, for a maximum of 25 points per judge.

| Category | What is evaluated |
| --- | --- |
| Problem Identification & Purpose | How clearly the team identifies a genuine user problem and explains its importance |
| Innovation & Originality | Creativity and uniqueness of the proposed solution |
| Technical Depth & Implementation | Quality and functionality of the implemented feature or prototype |
| User Experience & Feasibility | Whether the improvement is useful, practical, and easy to use |
| Presentation & Demonstration | How clearly the team explains and demonstrates its solution |

A purely theoretical presentation without a meaningful implementation or prototype should not receive the same implementation credit as a demonstrated solution.

| Score | Description |
| --- | --- |
| 5 | Exceeds one or more brief goals in an innovative way |
| 4 | Moderately exceeds one or more brief goals |
| 3 | Meets one or more brief goals |
| 2 | Nearly meets at least one brief goal |
| 1 | Does not meet any brief goal but receives a participation point |

For each project, calculate each team's average total across all judges evaluating that project. The highest average wins; exactly one winner is selected per project.

Tie-breakers:
1. Higher average Technical Depth & Implementation score.
2. If still tied, higher average Problem Identification & Purpose score.
3. If still tied, the head judge decides.

## Prerequisites

- [Git](https://git-scm.com/install/) is required to clone repositories.
- [Node.js](https://nodejs.org/en/download) 24 LTS is a compatible recommendation for all three projects based on their published engine requirements. Node.js is required at the project-specific versions above; npm comes with it. PancakeMaker requires npm 10.9.0.
- [Visual Studio Code](https://code.visualstudio.com/download) is optional.
- [Google Chrome](https://www.google.com/chrome/) is optional; any modern browser can be used.
- On Windows, use PowerShell. On macOS or Linux, use `npm` instead of `npm.cmd`.

## Participant workflow

1. Check the project assigned to your team.
2. Open its participant setup guide.
3. Install the required software.
4. Clone the original project locally.
5. Install dependencies and start the application.
6. Explore its existing functionality.
7. Identify a genuine problem or missing feature and explain why it matters.
8. Propose a practical, innovative solution and implement a meaningful part of it or develop a working prototype. A production-ready feature is not required; a theoretical presentation alone does not demonstrate implementation.
9. Prepare the demonstration, including how the improved application benefits users.
10. Present your work to the jury.

Each team works on its local clone. Local Git commits are optional; no GitHub code submission is required.

Never commit `.env` files, API keys, passwords, or other secrets.
