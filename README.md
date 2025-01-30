# **LoreFlow – Effortless, Structured World-Building**  

### **🔹 What is LoreFlow?**  
LoreFlow is a **structured, intuitive world-building tool** that helps **writers, RPG game masters, and creatives** seamlessly organize their worlds.  

Managing lore—characters, locations, artifacts—can be **overwhelming**. Existing tools lack structure or are difficult to navigate. LoreFlow solves this with a **template-driven system** that lets you **define, edit, and manage world-building elements effortlessly.**  

---

## **🔹 Key Features**
✅ **Template-Driven System** – Define and customize structured **Lore Template Types (`.ltt`)** to ensure consistency across world-building elements.  
✅ **Easy-to-Use Interface** – No coding required—just **intuitive form-based input** for creating and editing **Lore Files (`.ltf`)**.  
✅ **File-Based Organization** – Use your **native file system** to categorize lore entries, keeping everything **local, portable, and flexible**.  
✅ **Linked Data & Relationships** – Connect characters, locations, and items through **UUID-based references**, ensuring seamless navigation.  
✅ **Powerful Search & Indexing** – Quickly find any **NPC, artifact, or setting** in your world-building archive.  
✅ **Offline & Private** – No cloud dependency—**your world, your data**.  

### **Why LoreFlow?**  
Because **world-building should be structured, intuitive, and frictionless**—so your creativity can flow.  

---

## **🔹 Current Status of the Project**
📌 **LoreFlow is in early development.**  

We are currently **defining the foundation**—**Lore Template Types (`.ltt`)**, **Lore Files (`.ltf`)**, and the **file-based approach**. With the tech stack finalized, we are preparing to **build the first version** of the software.

---

## **🔹 Roadmap & Development Plan**
LoreFlow is being developed in **phases**, focusing on **functionality first, then UI refinements**.  

### **🛠 Phase 1: Core Infrastructure**
✅ **Define File Formats** – `.ltt` for templates, `.ltf` for data entries. (Done)  
✅ **Select Tech Stack** – Go (Wails) + React + Zustand + Tailwind. (Done)  
🟡 **Initialize Codebase** – Set up Wails project and GitHub repo.  
🟡 **Implement File Handling** – Read/write `.ltt` and `.ltf` files.  
🟡 **Build Template Editor** – UI for creating and managing `.ltt` templates.  

---

### **🎨 Phase 2: Core UI & Editing Features**
🟡 **Lore Entry Editor** – Form-based UI for creating and editing `.ltf` files.  
🟡 **File Dialog Integration** – Open/save files via Wails native dialogs.  
🟡 **UUID-Based Linking** – Allow linking entries (e.g., NPCs to locations).  
🟡 **Basic Search & Filtering** – Quickly find lore entries via tags.  

---

### **🚀 Phase 3: Refinements & Advanced Features**
🟡 **Polish UI & Styling** – Improve user experience with Tailwind CSS.  
🟡 **Auto-Saving & File Watcher** – Keep files updated in real time.  
🟡 **Export & Sharing** – Markdown/PDF export for sharing lore.  
🟡 **Testing & User Feedback** – Refine usability based on early testers.  

---

## **🔹 Tech Stack**
✅ **Frontend:** **React + Zustand + Tailwind CSS** (Modern, responsive UI).  
✅ **Backend:** **Go (Wails framework)** (Native speed, direct bindings).  
✅ **Data Storage:** **Flat Files (`.ltf/.ltt`)**, No Database (Portable, lightweight).  
✅ **File Handling:** **Wails File Dialogs** (Native OS integration for opening/saving).  

📌 **Why Wails?**  
- **Lightweight & Fast** – Unlike Electron, Wails **doesn’t bundle Chromium**, keeping the app small (~10MB).  
- **Cross-Platform** – Works on **Windows, macOS, and Linux** as a **single `.exe/.app`** without cloud dependencies.  
- **Direct Integration** – **No need for REST APIs**—the frontend directly communicates with Go functions.  

---

## **🔹 Who Is This For?**
✅ **RPG Game Masters** – Organize structured campaign notes.  
✅ **Writers & Authors** – Manage world-building details easily.  
✅ **Game Developers** – Store structured lore for in-game use.  
✅ **Creatives** – Keep track of **characters, locations, and artifacts** without clutter.  

---

## **🔹 Next Development Milestones**
Since LoreFlow is in early development, we are focusing on **building the foundation first.**  

🔹 **Initialize the GitHub Repo & Codebase** – Set up the Wails project.  
🔹 **Build the `.ltt` Template Editor** – First working feature.  
🔹 **Implement `.ltf` File Handling** – Creating & saving lore entries.  
🔹 **Release an Early Prototype** – Gather feedback from early testers.  

With **LoreFlow**, your world-building stays **structured, intuitive, and frictionless**—so your creativity can **flow**. 🚀 
