# LoreFlow Architecture Documentation

## Overview

LoreFlow is a desktop application for structured world-building, built using Wails (Go) + React. The application follows a file-based approach using TOML for both template definitions (.ltt) and lore entries (.ltf).

## Core Architecture Decisions

### 1. Tech Stack

- **Frontend**: React + Zustand + Tailwind CSS
  - React for component-based UI development
  - Zustand for lightweight state management
  - Tailwind CSS for utility-first styling
- **Backend**: Go with Wails framework
  - Native performance
  - Direct frontend-backend communication
  - Cross-platform compatibility
- **Data Storage**: File-based using TOML
  - No database required
  - Portable and lightweight
  - Human-readable format

### 2. File Format Specifications

#### Lore Template Type (.ltt)
```toml
[header]
name = "template_name"    # Required: Unique template identifier
version = "1.0"          # Required: Template version for future compatibility

[fields.{section_name}]   # Grouped fields by section
keys = [
    {
        key = "field_name",           # Required: Unique field identifier
        type = "string|number|...",   # Required: Data type
        ui_component = "text|...",    # Required: UI component type
        required = true|false,        # Optional: Field requirement
        options = ["opt1", "opt2"],   # Optional: For dropdowns/selects
        validation = {                # Optional: Validation rules
            min = 0,
            max = 100,
            pattern = "regex"
        }
    }
]
```

#### Lore File (.ltf)
```toml
[header]
ltt = "template_name"              # Required: Reference to .ltt template
uuid = "unique-identifier"         # Required: UUID for relationships
created = "2025-01-29T12:34:56Z"  # Required: Creation timestamp
modified = "2025-01-29T12:34:56Z" # Required: Last modified timestamp

[data.{section_name}]              # Data grouped by template sections
field_name = "value"              # Field values matching template
```

### 3. Component Architecture

```
frontend/
├── components/
│   ├── template/              # Template management
│   │   ├── TemplateEditor    # .ltt file editor
│   │   └── TemplateList      # Template browser
│   ├── lore/                 # Lore entry management
│   │   ├── LoreEditor       # .ltf file editor
│   │   └── LoreList         # Entry browser
│   ├── common/              # Shared components
│   │   ├── FormFields      # Dynamic form fields
│   │   └── FileDialog      # Native file dialogs
│   └── layout/              # Layout components
├── stores/                  # Zustand stores
│   ├── templateStore       # Template state management
│   └── loreStore          # Lore entries state
└── utils/                  # Utility functions
    ├── toml               # TOML parsing/writing
    └── validation        # Form validation
```

### 4. State Management

Using Zustand for state management with the following stores:

```typescript
// Template Store
interface TemplateStore {
  templates: Map<string, Template>;
  activeTemplate: Template | null;
  loadTemplate: (path: string) => void;
  saveTemplate: (template: Template) => void;
}

// Lore Store
interface LoreStore {
  entries: Map<string, LoreEntry>;
  activeEntry: LoreEntry | null;
  loadEntry: (path: string) => void;
  saveEntry: (entry: LoreEntry) => void;
  relationships: Map<string, string[]>;
}
```

### 5. Data Flow

1. **Template Management**
   - Templates (.ltt) are loaded on demand
   - Template store maintains active template state
   - Changes trigger validation before saving

2. **Lore Entry Management**
   - Entries (.ltf) are loaded when opened
   - Entry editor dynamically renders based on template
   - Auto-save functionality with file watchers

3. **Relationship Handling**
   - UUID-based linking between entries
   - Relationship store tracks connections
   - Bi-directional updates on changes

### 6. File System Integration

Using Wails native capabilities for:
- File dialogs (open/save)
- Directory watching
- File system operations

### 7. Error Handling

1. **Validation Errors**
   - Template validation
   - Entry data validation
   - Relationship integrity

2. **File System Errors**
   - File not found
   - Permission issues
   - Concurrent access

3. **Recovery Strategies**
   - Auto-save backups
   - Validation before save
   - Error boundary components

## Development Phases

### Phase 1: Core Infrastructure
- Template system implementation
- File handling (read/write TOML)
- Basic UI components

### Phase 2: Core Features
- Template editor
- Entry editor
- File dialog integration
- Basic search

### Phase 3: Advanced Features
- Relationship management
- Export functionality
- Auto-save
- File watching

## Security Considerations

1. **File System**
   - Sanitize file paths
   - Validate file contents
   - Handle permissions appropriately

2. **Data Validation**
   - Validate all user inputs
   - Sanitize template definitions
   - Verify relationship integrity

## Performance Considerations

1. **File Loading**
   - Lazy loading of entries
   - Caching frequently used templates
   - Efficient TOML parsing

2. **UI Performance**
   - Virtual lists for large collections
   - Debounced auto-save
   - Optimized re-renders

## Testing Strategy

1. **Unit Tests**
   - Template validation
   - TOML parsing/writing
   - Store operations

2. **Integration Tests**
   - File system operations
   - Template-entry relationships
   - UI interactions

3. **End-to-End Tests**
   - Complete workflows
   - Cross-platform verification
   - File handling scenarios