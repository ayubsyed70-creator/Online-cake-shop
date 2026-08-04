# Online Cake Shop — BA Assignment

This repository contains the Business Analyst deliverables for the
**Online Cake Shop** assignment (Checkmate IT Training Institute,
Assignment 5 — BPMN & User Stories).

## What's here

```
online-cake-shop/
├── README.md
├── requirements/
│   └── cake-shop-modules-requirements.md   Module-wise functional requirements
├── diagrams/
│   ├── cake-shop-process.bpmn              BPMN 2.0 process diagram (editable source)
│   ├── cake-shop-process.png               Exported PNG of the process diagram
│   ├── cake-shop-use-case.puml             UML use case diagram (editable source, PlantUML)
│   └── cake-shop-use-case.png              Exported PNG of the use case diagram
└── user-stories/
    └── user-stories.md                     User stories, INVEST notes, Gherkin acceptance criteria
```

## Process overview

The order-to-delivery process has three pools:
- **Customer** — browses, customizes, checks out, receives, and reviews the cake
- **Online Cake Shop** — two lanes, **System** (payment, order, delivery status) and
  **Bakery Staff** (prepare, quality check, package)
- **Delivery Partner** — pickup and delivery, handed off via message flows

## Tools used

- **BPMN diagram:** modeled to BPMN 2.0 spec, importable into Camunda Modeler / bpmn.io
- **Use case diagram:** PlantUML syntax, renderable via plantuml.com, the PlantUML VS Code
  extension, or draw.io's PlantUML plugin
- **Requirements & user stories:** Markdown

## How to view/edit the diagrams

- Open `diagrams/cake-shop-process.bpmn` in [Camunda Modeler](https://camunda.com/download/modeler/)
  or [bpmn.io](https://bpmn.io) to view or edit the process diagram.
- Paste `diagrams/cake-shop-use-case.puml` into the
  [PlantUML online editor](https://www.plantuml.com/plantuml/uml/) to view or edit the use case diagram.

## Status

- [x] Module-wise requirements
- [x] BPMN process diagram
- [x] UML use case diagram
- [x] User stories with INVEST + Gherkin acceptance criteria
- [ ] Backlog loaded into OpenProject/Taiga with story-point estimates
