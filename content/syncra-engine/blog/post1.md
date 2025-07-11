+++
date = '2025-07-11T01:26:53+01:00'
draft = true
title = 'Syncra Devlog #1: Foundations and Frameworks'
+++

Welcome to the first devlog for Syncra, our ambitious project to create a Rhythm Game Level Development Toolkit that can be applied to most engines and existing games. In this post, we’ll outline the foundational work we’ve done so far and the frameworks we’re using to bring Syncra to life.

## TL;DR

We've been laying the foundation of Syncra’s architecture — including a robust data model, essential libraries, and initial project structure — while beginning implementation of the first core features.

For the Syncra Editor, we’ve chosen Godot as our primary platform. Its flexibility, scripting power, and strong OS integration make it ideal for building a toolkit that supports cross-engine workflows and features like Git and file management.

On the engine side, we're evaluating options to make Syncra easily integrable into existing projects. At its core will be a Common Library written in C or Rust — designed to be lightweight, efficient, and portable. Built on top of that will be modular Runtime Libraries offering high-level abstractions tailored to Syncra’s functionality.

We're now focusing on support for Godot, Unity, and Unreal Engine. By supporting multiple platforms, we hope to reach a wider audience and provide a flexible, powerful toolset for developers of all kinds.

When it comes to exporting for existing games, we're now evaluating which titles should be our first integration targets. We want to ensure that Syncra can integrate seamlessly with popular engines and games, such as osu!, Friday Night Funkin, and others that have a strong modding community. (This requires a bit of research, specifically for osu! as it has a unique file structure not well documented.)

As for actual progress on the Editor, we've made significant strides in the past few weeks. We have a partially working prototype that allows users to place notes on a timeline and adjust their properties. The UI is still rough around the edges, but it’s functional enough to start testing the core concepts. Saving and Loading projects is non-functional; we have the UI in place, but the backend logic is still being developed.

## Planning Foundations

Before diving into implementation, we spent a lot of time planning the architecture and design of Syncra. This involved defining the core data structures, workflows, and user interactions that would form the backbone of the toolkit.

We started by identifying the key parts of Syncra:
- **Data Model**: The structure that defines how levels, notes, and other entities are represented.
- **Editor**: The user interface for creating and editing levels, including timelines, note placement, and property adjustments.
- **Runtime Libraries**: The libraries that will handle the playback and interaction logic for levels created with Syncra.
- **Export Mechanism**: The system that will convert Syncra projects into formats compatible with various game engines and existing games.

We also established a set of principles to guide our development:
- **Modularity**: Syncra should be built in a way that allows for easy extension and integration with other tools and engines.
- **Cross-Platform Compatibility**: The toolkit should work seamlessly across different operating systems and game engines.
- **User-Centric Design**: The editor should be intuitive and easy to use, allowing developers to focus on creativity rather than technical hurdles.
- **Performance**: Syncra should be efficient in memory and processing, ensuring smooth operation even with complex levels.

### Data Model

Syncra's Data Model is designed to be flexible and easily modifiable. It is primarily a ZIP-Based Format built on top of a JSON structure, allowing for easy serialization and deserialization. This format will enable us to store levels, notes, and other entities in a way that is both human-readable and machine-friendly.

The core components of the Data Model include:
- **Level**: Represents a complete rhythm game level, including metadata, timing information, and a collection of notes.
- **Note**: Represents an individual note in the level, including its position, timing, type, and any additional properties.
- **Timing**: Represents the timing information for the level, including BPM (Beats Per Minute), offsets, and any tempo changes.
- **Metadata**: Contains information about the level, such as title, artist, difficulty, and any custom properties defined by the user.

### Editor Framework
The Syncra Editor is being built using Godot, leveraging its powerful scene system and scripting capabilities. The editor will provide a timeline-based interface for creating and editing levels, allowing users to place notes, adjust their properties, and visualize the timing of the level.

The core features of the Syncra Editor include:
- **Timeline View**: A visual representation of the level's timing, allowing users to see the placement of notes relative to the music.
- **Note Placement**: A system for placing notes on the timeline, with support for different note types and properties.
- **Property Editor**: A panel for adjusting the properties of selected notes, including position, timing, and custom attributes.
- **Project Management**: A system for creating, saving, and loading Syncra projects, allowing users to manage their levels and assets easily.

### Core Libraries
To support the Syncra Editor and Runtime Libraries, we are developing a core library that will provide essential functionality and abstractions. This library will be written in C or Rust, ensuring that it is lightweight, efficient, and portable across different platforms.

The core components of the library include:
- **Data Serialization**: Functions for serializing and deserializing the Syncra Data Model
- **Timing Calculations**: Utilities for calculating timing information, including BPM conversions, offsets, and tempo changes.
- **Note Management**: Functions for creating, modifying, and deleting notes, as well as handling their properties and interactions.
- **File Management**: Functions for reading and writing Syncra project files, including support for ZIP-based formats.
- **Cross-Platform Compatibility**: Ensuring that the library can be used across different operating systems and game engines, with minimal dependencies.


### Runtime Libraries

The Runtime Libraries will provide higher-level abstractions for integrating Syncra levels into game engines and existing games. These libraries will be built on top of the core library and will include engine-specific implementations for handling playback, input, and visual effects.

The core components of the Runtime Libraries include:
- **Playback Engine**: The core engine that handles the timing and playback of notes, ensuring that they are triggered at the correct times and with the appropriate effects.
- **Input Handling**: A system for capturing user input, allowing players to interact with the level and trigger notes in real-time. (engine specific)
- **Visual Effects**: A set of visual effects that can be applied to notes and the level, enhancing the overall experience and providing feedback to the player. (engine specific)
- **Audio Integration**: A system for integrating audio playback with the level, ensuring that notes are synchronized with the music. (engine specific, considering FMOD compatibility)

### Export/Import Mechanism
The export mechanism will allow users to convert Syncra projects into formats compatible with various game engines and existing games. This will involve creating a set of export plugins for each target engine, ensuring that the exported levels retain their timing, note properties, and other essential information.

The import mechanism will allow users to bring existing levels from other formats into Syncra, enabling them to take advantage of the toolkit's features and workflows. This will involve creating import plugins for popular formats used in rhythm games, such as osu! Beatmaps and FNF levels.

