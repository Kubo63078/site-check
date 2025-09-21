# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Reactor Installation Survey System** (원세이버스 리액터 설치 통합 조사 시스템) - a specialized electrical engineering application for surveying and analyzing power systems to determine optimal reactor installations. The application is built as a single-page HTML application with embedded CSS and JavaScript.

## Architecture

**Single-File Application Structure:**
- **Frontend**: Self-contained HTML file with embedded CSS styling and JavaScript functionality
- **Data Model**: In-memory JavaScript objects representing electrical power system hierarchy
- **UI Components**: Dynamic tree visualization with modal-based editing
- **Export/Import**: JSON-based data persistence

**Core Data Model Hierarchy:**
```
KEPCO (한전 수전) → Transformers (변압기) → Panels (배전반/MCC) → Loads (부하)
```

The application manages a hierarchical electrical system where:
- KEPCO represents the main power reception from Korea Electric Power Corporation
- Transformers step down voltage levels
- Panels (MCCs - Motor Control Centers) distribute power
- Loads represent end-use electrical equipment

## Key Features

**Dynamic Tree Management:**
- Visual tree structure showing electrical system hierarchy
- Drag-and-drop node management with real-time updates
- Color-coded status indicators (완료/incomplete/empty)
- Interactive node editing with specialized forms for each component type

**Electrical Calculations:**
- Automatic power factor and reactor calculation
- Real-time capacity summation across system levels
- Progress tracking for survey completion
- Comprehensive electrical load analysis

**Data Management:**
- JSON export/import functionality for survey data persistence
- Automated report generation with electrical specifications
- Reset and initialization capabilities
- Cross-session data continuity

## Common Development Tasks

**Testing the Application:**
```bash
# Open in web browser (no build process required)
# For local development with file:// protocol
start reactor_survey_dynamic_tree.html

# For web server testing
python -m http.server 8000
# Then open http://localhost:8000/reactor_survey_dynamic_tree.html
```

**Data Structure Validation:**
The application maintains electrical system data in `systemData` object with these key components:
- `kepco`: Main power reception data (voltage, contract power, reception type)
- `transformers`: Transformer specifications (capacity, voltage levels, types)
- `panels`: Distribution panels and MCCs (rated current, panel types)
- `loads`: End-use loads (power, type, installation location)
- `connections`: Hierarchical relationships between components

**Key Electrical Engineering Constants:**
- Default reception voltage: 22.9kV
- Transformer types: 몰드형, 유입형, 건식
- Panel types: 일반형, 인출형, 고정형
- Load categories with specific power factor calculations

## File Structure

**Single File Application:**
- `reactor_survey_dynamic_tree.html` - Complete application (1,817 lines)
  - Lines 1-860: HTML structure and CSS styling
  - Lines 861-1817: JavaScript application logic
  - Embedded SVG for connection visualization
  - Modal dialogs for component editing

**Supporting Files:**
- `.claude/settings.local.json` - Claude Code permissions configuration

## Electrical Engineering Domain Knowledge

**Power System Calculations:**
- Power factor correction calculations for reactive power compensation
- Load diversity factors for different electrical equipment types
- Transformer sizing based on connected load analysis
- Reactor sizing recommendations based on system harmonics and power factor

**Korean Electrical Standards:**
- Compliance with Korean electrical codes and KEPCO requirements
- Voltage class specifications (22.9kV, 380V, 220V)
- Electrical equipment naming conventions in Korean
- Standard electrical symbols and representations

## Browser Compatibility

**Target Environment:**
- Modern browsers with ES6+ support
- Local file system operation capability
- SVG rendering support for electrical diagrams
- JSON data handling for import/export

**No Build Process Required:**
- Direct browser execution
- No package management or bundling
- Self-contained dependencies
- Immediate development iteration capability