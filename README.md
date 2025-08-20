<img height="100" alt="quick-board-hero" src="https://github.com/user-attachments/assets/75fa5e93-d016-436a-bc47-4b80c2e3bf30" />

## About the project

This is a simple Kanban board built with Vue.js, featuring four lists (To Do, In Progress, Done, Archived) and draggable cards. It was created for learning and portfolio purposes, focusing on Composition API, drag & drop integration, and localStorage persistence.

#### Features

- Four predefined lists (To Do, In Progress, Done, Archived)  
- Add new cards through a modal dialog  
- Drag & drop cards between lists (`vuedraggable`)  
- Expand/collapse list content  
- Automatic saving to `localStorage`  

#### Technologies

- Vue 3 + Vite  
- Tailwind CSS  
- Composition API  
- vuedraggable  

## Main Files

#### Components

- [`List.vue`](src/components/List.vue) – List container with header, collapse toggle, and "Add Card" button  
- [`Card.vue`](src/components/Card.vue) – Individual card with title/description  
- [`ModalDialog.vue`](src/components/ModalDialog.vue) – Modal form to add new cards  
- [`App.vue`](src/App.vue) – Root component with state, persistence, and draggable integration  

#### Core

- [`main.js`](src/main.js) – App entry point  
- [`vite.config.js`](vite.config.js) – Vite configuration  
- [`main.css`](src/main.css) – Global styles (Tailwind)  
- [`index.html`](index.html) – Main HTML file  
