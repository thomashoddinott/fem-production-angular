### Tips of Managing Complexity

**Managing complexity** is the hardest thing about developing software

**Code complexity** scales with **code volume**, often in a non-linear fashion

This is most commonly due to poor state management 

==> There is no silver bullet: no framework, programming language, etc. that solves this problem completely 

Remember this rule:

1. Make it **work **
2. Make it **known** (get feedback ASAP - check it's what you need)

3. Make it **right**

4. Make it **fast**

**Tips:**

Code should be fine grained === Code (functions) should do one thing

Code should be self documenting

Favour pure, immutable functions - reduces state management complexity

Abstractions should reduce complexity

Abstractions should increase cohesion 

Refactor through promotion

Composition over inheritance (inheritance = coupling)

Do not confuse convention for repetition

Well-structured code will naturally have a larger surface area**

Use a [style guide](https://angular.io/guide/styleguide) until it doesn't make sense for your situation

**Rules for managing complexity:**

Eliminate hidden state in functions

Eliminate nested logic in functions

Do not break the Single Responsibility Principle

==> Extracting to a method is one of the most effective refactoring strategies available

If you need to clarify your code with comments then it is probably too complex

It is impossible to write good tests for bad code

### Managing Complexity in Angular

Your routing table will generally describe your features

==> A feature will generally get a route ==> A route will navigate to a container component ==> Everything inside that container component should be a presentation component 

A component should only ever do 2 things:

1. Consume just enough data to satisfy its templates
2. Capture user events and delegate them upwards

==> Components should:

- be as thin as possible
- satisfy inputs using the async pipe
- be oblivious to business logic
- be oblivious to server communication  
- be oblivious to application state

Facades (services) are an effective delegation layer between components and the rest of the app

Facades are for delegation only

Facades hide all of the implementation details from the producer to the consumer

Server communication and state management should be decoupled

Data models should be decoupled especially inside of a monorepo with client and API projects

Do not unnecessarily optimise until you have a good reason to do so. e.g. a component should not become a lib until it's going to be used in more than one app ==> Refactor through promotion

### Complexity Resources and Q&A

Clean Code - Martin

Refactoring - Fowler

What to do if you *inherit* a real mess of a code base? ==> Slowly, piece by piece:

- You need tests

- Refactor through promotion

- Extract to method

- Get rid of hidden state ==> dependency injection 

- Decouple code into the proper extraction level

Start with these questions:

1. Can I test it?
2. Can I move it?

If you can't ==> refactor!

Team style guides trump community style guides. If it works for your team, go for it.

### Data Modelling

**You need to understand the data model for the domain you are working in**

When you have the data model down, you can already infer what the UI will be 

... and you can already see what the RestAPI is going to look like

... and you know what services you're going to need

**When you understand the data model, you understand the shape of the app**

Where is the complexity in an app?

- UI
- Business logic

^ 95% of your time should be spent finishing that last 5% of your app

### Nx Workspaces & Angular CLI

https://nx.dev/

Follows the concept of a **monorepo**

`nx` generates apps (angular, react, node, ... ) side-by-side

e.g. Angular + Node

==> think of it as an extension of the AngularCLI, allowing you to further manage complexity

```
npx create-nx-workspace@10.3.2 fem-production-angular --appName=dashboard --preset=angular-nest --npmS cope-fem --linter=tslint --style=scss --nx-cloud=false
```

 ### Nx & Monorepo Setup

`nx` separates apps from libs

Only have related technology stacks in a monorepo

Increases build complexity, but improves developer ergonomics massively

### Adding Angular Material

Using the CLI we generate the majority of our app

`core-data` - communicates with server ==> moves data from server into the client

==> `widgets.service.ts`, etc.

`core-state` - manages state of the app

### App Boilerplate & Components Overview

Thin components which don't do very much :heavy_check_mark:

==> Very portable

