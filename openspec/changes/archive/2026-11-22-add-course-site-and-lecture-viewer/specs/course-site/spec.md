# Spec Delta

## Purpose

The course site gives learners a clear course introduction and a direct way to browse and view the existing HTML lecture decks. It provides a simple static experience that can grow as more lecture files are added.

## ADDED Requirements

### Requirement: Course landing page
The site SHALL present the course identity and a concise course overview on its home page, with a visible link to the lecture viewer.

#### Scenario: Learner opens the home page
- **WHEN** a learner opens `index.html`
- **THEN** the page presents the course and provides a link to `lectures.html`

### Requirement: Lecture viewer lists and displays lecture decks
The viewer SHALL present a hardcoded list of available lecture decks and display the selected deck in a frame beside that list.

#### Scenario: Viewer opens without a selected lecture
- **WHEN** a learner opens `lectures.html` without a lecture fragment
- **THEN** the first listed lecture is selected and displayed in the frame

#### Scenario: Learner selects a lecture
- **WHEN** a learner selects a lecture from the list
- **THEN** that lecture's HTML file under `lecs/` is displayed in the frame and the selected item is visibly identified

### Requirement: Lecture selection is addressable
The viewer SHALL represent the selected lecture in the URL and restore the selection when a valid lecture fragment is opened directly or through browser history navigation.

#### Scenario: Open a lecture link directly
- **WHEN** a learner opens a viewer URL containing a fragment for a listed lecture
- **THEN** the corresponding lecture is selected and displayed

#### Scenario: Navigate lecture history
- **WHEN** a learner uses browser back or forward after changing lectures
- **THEN** the selection and displayed deck follow the URL fragment

### Requirement: Lecture viewer adapts to narrow screens
The viewer SHALL keep lecture selection and deck access usable on narrow screens.

#### Scenario: Viewer opens on a narrow screen
- **WHEN** a learner opens the viewer on a narrow viewport
- **THEN** the lecture list and deck area are arranged so both remain accessible without requiring a wide desktop layout
