---
layout: post
title: "Why I Built a React Native Starter That AI Agents Can't Break"
date: 2026-03-25
tags: reactnative, typescript, mobile, ai, architecture
published: true
---
I didn’t write this post to chase trends. I wrote it to make sense of the noise, especially all the AI hype, and get back to what actually helps. Boilerplates still matter. They just need to be built with more care for the realities of modern development.

* we do need boilerplates
* but we need better ones

# The 2026 React Native Blueprint

At first, it felt fine. It helped us move quickly, and early on, that was exactly what we needed.

As data has grown exponentially — driven by IoT — thousands of events, heavier logging, deeper syncing, more real-world complexity — that early convenience started to show its limits..
The app felt sluggish, and dependencies upgrades became something to approach carefully rather than casually.

Around that same time, I had a couple of months to step back and rethink what I wanted from a modern mobile stack. I explored newer tools, like **Biome** for a more unified code-quality setup. And because my access to the database and cloud code was limited, I had to be more creative — which is what pushed me toward **TanStack Query** and its built-in caching, background refetching, persistence support, and offline-friendly patterns.

Eventually, I came to a simple conclusion:

I didn’t want to keep extending an old foundation.  
I wanted to build one that reflected how I want to develop now.

That’s why I built [react-native-bare-starter](https://github.com/maximcoding/react-native-bare-starter).

---

## The Storage Shift: MMKV over AsyncStorage

Storage is one of those things users never think about — until they feel it.

If saving a preference causes a small pause, or if reading persisted data slows down the experience, the app starts to feel less polished than it should.

That’s why I moved to **MMKV** as it's widely known for being significantly faster than AsyncStorage, and more importantly, it feels better in the places that matter: startup time, persistence, reads, and those tiny moments where responsiveness shapes trust.

I also wasn’t trying to build around the most experimental path possible. I chose a version that works well, with a setup that feels practical and stable.

Because a starter should not be a demo. 
It should be a dependable base.

---

## Agnostic by Design, Flexible on Purpose

Most apps begin with one backend, but very few stay that simple forever.

Maybe the first version uses **Firebase**.  
Maybe the company already has a **REST API**.  
Maybe the team prefers **GraphQL**.

Over time, needs change. Teams evolve. Infrastructure shifts.

And when that happens, I don’t want the UI layer to absorb the cost.

So this starter is built around an **agnostic transport layer**. The goal is straightforward: feature logic should not care where data comes from.

By using adapters, the app stays flexible without becoming chaotic.

- **Decoupled logic** keeps features independent from the underlying transport.
- **Swappable adapters** make it easier to move between Firebase, REST, GraphQL, WebSockets, or mock services.
- **Minimal UI impact** means backend changes don’t force a rewrite of every screen.

It’s a way to build for the backend you have today without overcommitting the product to it forever.

---

## Server State and Offline-First Thinking

Offline support is easy to postpone when everything works nicely on stable Wi-Fi.

But mobile apps don’t live in perfect conditions. People use them in elevators, on trains, in parking garages, and in places where connectivity is inconsistent at best.

So in this starter, **offline-first thinking is part of the foundation**.

By combining **TanStack Query**, **MMKV persistence**, and **queue/replay logic**, the app is designed to handle temporary network loss with more grace.

That matters because reliability on mobile is not just about features.  
It’s about behavior when conditions are less than ideal.

---

## Permission Mapping, So You Spend Less Time Hunting Docs (A Gift file)

I also included a pre-mapped catalog of native permissions for Bare React Native.

It’s a small addition, but it saves real time — especially when switching contexts between JavaScript and native configuration, check [**repo doc](https://github.com/maximcoding/react-native-bare-starter/blob/master/docs/permissions-bare-rn.md)

---

## Under the Hood (v1.0.2)

This starter currently includes:

- **Bare React Native 0.82.1** — full native control means full!
- **React Navigation 7.x** — stacks, tabs, and modals already wired
- **Zustand 5.x** — lightweight global state
- **MMKV Storage** — `react-native-mmkv` via Nitro Modules
- **🔌 Pluggable transport** — adapters for REST, GraphQL, WebSocket, and Firebase, so you can change backend strategy without rewiring the app
- **SVG automation** — scripted icon generation with `npm run gen:icons`
- **Biome 2.x** — a single source of truth for formatting and linting
- **Theming** - system / light / dark
- **i18next 25.x** — typed translations with a custom `useT()` hook
- **BootSplash 6.x** — native splash screen setup

As i mentioned above: the goal wasn’t to chase trends.

It was to assemble a stack that feels durable, understandable, and easier to maintain as the app becomes more complex.

---

## Get the Code

[**maximcoding/react-native-bare-starter**](https://github.com/maximcoding/react-native-bare-starter)

This starter is still being pressure-tested in real work, and I’m planning to carry it into my next few ideas as well. If you’d like to jump in, contribute, and help shape where it goes next, you’re more than welcome.
