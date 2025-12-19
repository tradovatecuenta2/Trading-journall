<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Trading Journal Pro</title>
<style>
/* ========== CSS VARIABLES ========== */
:root {
  --bg-primary: #131722;
  --bg-secondary: #1e222d;
  --bg-card: #1e222d;
  --border: #2a2e39;
  --text-primary: #d1d4dc;
  --text-secondary: #787b86;
  --accent: #2962ff;
  --green: #26a69a;
  --red: #ef5350;
  --yellow: #f7931a;
  --grid: #2a2e39;
}

/* ========== RESET & BASE ========== */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
  background: var(--bg-primary);
  color: var(--text-primary);
  line-height: 1.5;
  min-height: 100vh;
}

/* ========== SCROLLBAR ========== */
::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}
::-webkit-scrollbar-track {
  background: var(--bg-primary);
}
::-webkit-scrollbar-thumb {
  background: var(--border);
  border-radius: 4px;
}
::-webkit-scrollbar-thumb:hover {
  background: var(--text-secondary);
}

/* ========== HEADER ========== */
.header {
  background: var(--bg-secondary);
  border-bottom: 1px solid var(--border);
  padding: 12px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 12px;
  position: sticky;
  top: 0;
  z-index: 100;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 18px;
  font-weight: 700;
  color: #fff;
}

.logo svg {
  width: 28px;
  height: 28px;
  fill: var(--accent);
}

.header-center {
  display: flex;
  gap: 4px;
}

.header-nav-btn {
  padding: 8px 16px;
  background: transparent;
  border: 1px solid transparent;
  border-radius: 6px;
  color: var(--text-secondary);
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  gap: 6px;
}

.header-nav-btn:hover {
  color: var(--text-primary);
  background: rgba(255, 255, 255, 0.05);
}

.header-nav-btn.active {
  color: var(--accent);
  background: rgba(41, 98, 255, 0.1);
  border-color: var(--accent);
}

.header-nav-btn svg {
  width: 16px;
  height: 16px;
  fill: currentColor;
}

.header-status {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  color: var(--text-secondary);
}

.status-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--yellow);
}

.status-dot.active {
  background: var(--green);
}

/* ========== MAIN LAYOUT ========== */
.main-container {
  display: grid;
  grid-template-columns: 320px 1fr;
  gap: 0;
  min-height: calc(100vh - 56px);
}

@media (max-width: 1024px) {
  .main-container {
    grid-template-columns: 1fr;
  }
}

/* ========== VIEW CONTAINERS ========== */
.view-container {
  display: none;
}

.view-container.active {
  display: grid;
  grid-template-columns: 320px 1fr;
  gap: 0;
  min-height: calc(100vh - 56px);
}

.view-container.calendar-view.active {
  display: block;
}

@media (max-width: 1024px) {
  .view-container.active {
    grid-template-columns: 1fr;
  }
}

/* ========== SIDEBAR ========== */
.sidebar {
  background: var(--bg-secondary);
  border-right: 1px solid var(--border);
  padding: 16px;
  overflow-y: auto;
  max-height: calc(100vh - 56px);
}

@media (max-width: 1024px) {
  .sidebar {
    max-height: none;
    border-right: none;
    border-bottom: 1px solid var(--border);
  }
}

.section {
  margin-bottom: 20px;
}

.section-title {
  font-size: 11px;
  font-weight: 600;
  color: var(--text-secondary);
  text-transform: uppercase;
  letter-spacing: 0.5px;
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  gap: 6px;
}

.section-title svg {
  width: 14px;
  height: 14px;
  fill: var(--text-secondary);
}

/* ========== FORM ELEMENTS ========== */
.form-group {
  margin-bottom: 12px;
}

.form-label {
  display: block;
  font-size: 12px;
  color: var(--text-secondary);
  margin-bottom: 4px;
}

.form-input {
  width: 100%;
  padding: 10px 12px;
  background: var(--bg-primary);
  border: 1px solid var(--border);
  border-radius: 6px;
  color: var(--text-primary);
  font-size: 14px;
  transition: border-color 0.2s, box-shadow 0.2s;
}

.form-input:focus {
  outline: none;
  border-color: var(--accent);
  box-shadow: 0 0 0 2px rgba(41, 98, 255, 0.2);
}

.form-input::placeholder {
  color: var(--text-secondary);
}

textarea.form-input {
  resize: vertical;
  min-height: 80px;
  font-family: monospace;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
}

/* ========== FILE INPUT ========== */
.file-input-wrapper {
  position: relative;
  margin-bottom: 8px;
}

.file-input {
  display: none;
}

.file-input-label {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 12px 16px;
  background: var(--bg-primary);
  border: 2px dashed var(--border);
  border-radius: 8px;
  color: var(--text-secondary);
  font-size: 13px;
  cursor: pointer;
  transition: all 0.2s;
}

.file-input-label:hover {
  border-color: var(--accent);
  color: var(--accent);
  background: rgba(41, 98, 255, 0.05);
}

.file-input-label svg {
  width: 20px;
  height: 20px;
  fill: currentColor;
}

.file-name {
  font-size: 12px;
  color: var(--green);
  margin-top: 6px;
  word-break: break-all;
}

/* ========== BUTTONS ========== */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 10px 16px;
  border: none;
  border-radius: 6px;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  width: 100%;
}

.btn svg {
  width: 16px;
  height: 16px;
}

.btn-primary {
  background: var(--accent);
  color: #fff;
}

.btn-primary:hover {
  background: #1e53e4;
}

.btn-success {
  background: var(--green);
  color: #fff;
}

.btn-success:hover {
  background: #1e8e82;
}

.btn-danger {
  background: var(--red);
  color: #fff;
}

.btn-danger:hover {
  background: #d32f2f;
}

.btn-secondary {
  background: var(--border);
  color: var(--text-primary);
}

.btn-secondary:hover {
  background: #3a3f4c;
}

.btn-group {
  display: flex;
  gap: 8px;
  margin-top: 8px;
}

.btn-group .btn {
  flex: 1;
}

/* ========== TOGGLE BUTTONS ========== */
.toggle-group {
  display: flex;
  background: var(--bg-primary);
  border-radius: 6px;
  padding: 3px;
}

.toggle-btn {
  flex: 1;
  padding: 8px 12px;
  border: none;
  background: transparent;
  color: var(--text-secondary);
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  border-radius: 4px;
  transition: all 0.2s;
}

.toggle-btn.active {
  background: var(--accent);
  color: #fff;
}

.toggle-btn.long.active {
  background: var(--green);
}

.toggle-btn.short.active {
  background: var(--red);
}

/* ========== IMPORT INDICATOR ========== */
.import-indicator {
  font-size: 12px;
  color: var(--text-secondary);
  margin-top: 6px;
  min-height: 18px;
}

.import-indicator.has-data {
  color: var(--green);
}

/* ========== CONTENT AREA ========== */
.content {
  padding: 16px;
  overflow-y: auto;
  max-height: calc(100vh - 56px);
}

@media (max-width: 1024px) {
  .content {
    max-height: none;
  }
}

/* ========== METRICS GRID ========== */
.metrics-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 12px;
  margin-bottom: 20px;
}

.metric-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 14px;
}

.metric-label {
  font-size: 11px;
  color: var(--text-secondary);
  text-transform: uppercase;
  letter-spacing: 0.3px;
  margin-bottom: 6px;
  display: flex;
  align-items: center;
  gap: 4px;
}

.metric-value {
  font-size: 20px;
  font-weight: 700;
  color: #fff;
}

.metric-value.positive {
  color: var(--green);
}

.metric-value.negative {
  color: var(--red);
}

.metric-value.large {
  font-size: 26px;
}

.metric-subtext {
  font-size: 11px;
  color: var(--text-secondary);
  margin-top: 4px;
}

/* ========== PROGRESS BAR ========== */
.progress-bar {
  height: 6px;
  background: var(--bg-primary);
  border-radius: 3px;
  margin-top: 8px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: var(--green);
  border-radius: 3px;
  transition: width 0.3s;
}

/* ========== TRADINGVIEW CHART ========== */
.tv-chart-section {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 8px;
  margin-bottom: 20px;
  overflow: hidden;
}

.tv-chart-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 16px;
  border-bottom: 1px solid var(--border);
  background: var(--bg-secondary);
}

.tv-chart-title {
  font-size: 14px;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 8px;
}

.tv-chart-title .symbol {
  color: #fff;
}

.tv-chart-title .price {
  font-size: 13px;
  padding: 2px 8px;
  border-radius: 4px;
}

.tv-chart-title .price.positive {
  background: rgba(38, 166, 154, 0.2);
  color: var(--green);
}

.tv-chart-title .price.negative {
  background: rgba(239, 83, 80, 0.2);
  color: var(--red);
}

.tv-chart-info {
  display: flex;
  gap: 16px;
  font-size: 12px;
  color: var(--text-secondary);
}

.tv-chart-info span {
  display: flex;
  align-items: center;
  gap: 4px;
}

.tv-chart-container {
  position: relative;
  height: 450px;
  background: var(--bg-primary);
}

.tv-chart-canvas {
  position: absolute;
  top: 0;
  left: 0;
}

.tv-y-axis {
  position: absolute;
  top: 0;
  right: 0;
  width: 70px;
  height: calc(100% - 30px);
  background: var(--bg-secondary);
  border-left: 1px solid var(--border);
}

.tv-x-axis {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 70px;
  height: 30px;
  background: var(--bg-secondary);
  border-top: 1px solid var(--border);
}

.tv-price-label {
  position: absolute;
  right: 4px;
  font-size: 10px;
  color: var(--text-secondary);
  transform: translateY(-50%);
  font-family: monospace;
}

.tv-current-price {
  position: absolute;
  right: 0;
  padding: 3px 6px;
  font-size: 11px;
  font-weight: 600;
  color: #fff;
  transform: translateY(-50%);
  z-index: 10;
  font-family: monospace;
}

.tv-current-price.positive {
  background: var(--green);
}

.tv-current-price.negative {
  background: var(--red);
}

.tv-trade-label {
  position: absolute;
  bottom: 8px;
  font-size: 9px;
  color: var(--text-secondary);
  transform: translateX(-50%);
  font-family: monospace;
}

.tv-crosshair-h, .tv-crosshair-v {
  position: absolute;
  pointer-events: none;
  display: none;
}

.tv-crosshair-h {
  height: 1px;
  left: 0;
  right: 70px;
  background: rgba(255, 255, 255, 0.3);
  border-top: 1px dashed rgba(255, 255, 255, 0.3);
}

.tv-crosshair-v {
  width: 1px;
  top: 0;
  bottom: 30px;
  background: rgba(255, 255, 255, 0.3);
  border-left: 1px dashed rgba(255, 255, 255, 0.3);
}

.tv-tooltip {
  position: absolute;
  background: rgba(30, 34, 45, 0.95);
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 10px 14px;
  font-size: 12px;
  pointer-events: none;
  opacity: 0;
  transition: opacity 0.15s;
  z-index: 100;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
  min-width: 160px;
}

.tv-tooltip.visible {
  opacity: 1;
}

.tv-tooltip-row {
  display: flex;
  justify-content: space-between;
  margin-bottom: 4px;
}

.tv-tooltip-row:last-child {
  margin-bottom: 0;
}

.tv-tooltip-label {
  color: var(--text-secondary);
}

.tv-tooltip-value {
  font-weight: 600;
  color: #fff;
  font-family: monospace;
}

.tv-tooltip-value.positive {
  color: var(--green);
}

.tv-tooltip-value.negative {
  color: var(--red);
}

.tv-watermark {
  position: absolute;
  top: 50%;
  left: calc(50% - 35px);
  transform: translate(-50%, -50%);
  font-size: 60px;
  font-weight: 800;
  color: rgba(255, 255, 255, 0.03);
  pointer-events: none;
  user-select: none;
  letter-spacing: 4px;
}

.tv-legend {
  position: absolute;
  top: 10px;
  left: 10px;
  background: rgba(30, 34, 45, 0.8);
  padding: 8px 12px;
  border-radius: 6px;
  font-size: 11px;
  z-index: 50;
}

.tv-legend-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 4px;
}

.tv-legend-row:last-child {
  margin-bottom: 0;
}

.tv-legend-color {
  width: 16px;
  height: 3px;
  border-radius: 2px;
}

.tv-legend-value {
  font-family: monospace;
  font-weight: 600;
}

/* ========== CHART SECTION (Secondary charts) ========== */
.chart-section {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 8px;
  margin-bottom: 20px;
  overflow: hidden;
}

.tabs {
  display: flex;
  border-bottom: 1px solid var(--border);
  padding: 0 16px;
  gap: 4px;
  overflow-x: auto;
  background: var(--bg-secondary);
}

.tab {
  padding: 12px 16px;
  background: none;
  border: none;
  color: var(--text-secondary);
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  position: relative;
  white-space: nowrap;
  transition: color 0.2s;
}

.tab:hover {
  color: var(--text-primary);
}

.tab.active {
  color: var(--accent);
}

.tab.active::after {
  content: '';
  position: absolute;
  bottom: -1px;
  left: 0;
  right: 0;
  height: 2px;
  background: var(--accent);
}

.tab-content {
  display: none;
  padding: 16px;
}

.tab-content.active {
  display: block;
}

.chart-wrapper {
  position: relative;
  height: 280px;
}

.chart-wrapper canvas {
  width: 100% !important;
  height: 100% !important;
}

/* ========== TABLE ========== */
.table-section {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 8px;
  overflow: hidden;
}

.table-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 16px;
  border-bottom: 1px solid var(--border);
  flex-wrap: wrap;
  gap: 10px;
  background: var(--bg-secondary);
}

.table-title {
  font-size: 14px;
  font-weight: 600;
}

.table-filters {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.filter-select {
  padding: 6px 10px;
  background: var(--bg-primary);
  border: 1px solid var(--border);
  border-radius: 4px;
  color: var(--text-primary);
  font-size: 12px;
  cursor: pointer;
}

.table-container {
  overflow-x: auto;
  max-height: 400px;
  overflow-y: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  font-size: 13px;
}

thead {
  position: sticky;
  top: 0;
  background: var(--bg-secondary);
  z-index: 10;
}

th {
  padding: 12px;
  text-align: left;
  font-weight: 600;
  color: var(--text-secondary);
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.3px;
  border-bottom: 1px solid var(--border);
  cursor: pointer;
  user-select: none;
  white-space: nowrap;
}

th:hover {
  color: var(--text-primary);
}

td {
  padding: 12px;
  border-bottom: 1px solid var(--border);
  white-space: nowrap;
}

tr:hover {
  background: rgba(41, 98, 255, 0.05);
}

.pnl-positive {
  color: var(--green);
  font-weight: 600;
}

.pnl-negative {
  color: var(--red);
  font-weight: 600;
}

.direction-long {
  color: var(--green);
}

.direction-short {
  color: var(--red);
}

.action-btn {
  padding: 4px 8px;
  background: transparent;
  border: 1px solid var(--border);
  border-radius: 4px;
  color: var(--text-secondary);
  font-size: 11px;
  cursor: pointer;
  transition: all 0.2s;
  margin-right: 4px;
}

.action-btn:hover {
  border-color: var(--accent);
  color: var(--accent);
}

.action-btn.delete:hover {
  border-color: var(--red);
  color: var(--red);
}

.table-footer {
  padding: 12px 16px;
  background: var(--bg-secondary);
  border-top: 1px solid var(--border);
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 12px;
  color: var(--text-secondary);
}

/* ========== CALENDAR VIEW ========== */
.calendar-content {
  padding: 20px;
  max-width: 1400px;
  margin: 0 auto;
}

.calendar-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
  flex-wrap: wrap;
  gap: 16px;
}

.calendar-nav {
  display: flex;
  align-items: center;
  gap: 12px;
}

.calendar-nav-btn {
  padding: 8px 12px;
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: 6px;
  color: var(--text-primary);
  font-size: 14px;
  cursor: pointer;
  transition: all 0.2s;
}

.calendar-nav-btn:hover {
  background: var(--border);
  border-color: var(--accent);
}

.calendar-month-title {
  font-size: 24px;
  font-weight: 700;
  color: #fff;
  min-width: 200px;
  text-align: center;
}

.calendar-today-btn {
  padding: 8px 16px;
  background: var(--accent);
  border: none;
  border-radius: 6px;
  color: #fff;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
}

.calendar-today-btn:hover {
  background: #1e53e4;
}

/* Calendar Stats */
.calendar-stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 12px;
  margin-bottom: 20px;
}

.calendar-stat-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 14px;
  text-align: center;
}

.calendar-stat-label {
  font-size: 11px;
  color: var(--text-secondary);
  text-transform: uppercase;
  margin-bottom: 4px;
}

.calendar-stat-value {
  font-size: 18px;
  font-weight: 700;
  color: #fff;
}

.calendar-stat-value.positive {
  color: var(--green);
}

.calendar-stat-value.negative {
  color: var(--red);
}

/* Calendar Grid */
.calendar-grid-container {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 12px;
  overflow: hidden;
}

.calendar-weekdays {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  background: var(--bg-secondary);
  border-bottom: 1px solid var(--border);
}

.calendar-weekday {
  padding: 12px;
  text-align: center;
  font-size: 11px;
  font-weight: 600;
  color: var(--text-secondary);
  text-transform: uppercase;
}

.calendar-grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
}

.calendar-day {
  min-height: 100px;
  border-right: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  padding: 8px;
  cursor: pointer;
  transition: all 0.2s;
  position: relative;
}

.calendar-day:nth-child(7n) {
  border-right: none;
}

.calendar-day:hover {
  background: rgba(41, 98, 255, 0.05);
}

.calendar-day.other-month {
  background: rgba(0, 0, 0, 0.2);
}

.calendar-day.other-month .day-number {
  color: var(--text-secondary);
  opacity: 0.5;
}

.calendar-day.today {
  background: rgba(41, 98, 255, 0.1);
}

.calendar-day.today .day-number {
  background: var(--accent);
  color: #fff;
}

.calendar-day.has-trades {
  cursor: pointer;
}

.calendar-day.positive-day {
  background: rgba(38, 166, 154, 0.1);
}

.calendar-day.negative-day {
  background: rgba(239, 83, 80, 0.1);
}

.calendar-day.selected {
  box-shadow: inset 0 0 0 2px var(--accent);
}

.day-number {
  font-size: 14px;
  font-weight: 600;
  color: var(--text-primary);
  width: 28px;
  height: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  margin-bottom: 4px;
}

.day-pnl {
  font-size: 13px;
  font-weight: 700;
  margin-top: 4px;
}

.day-pnl.positive {
  color: var(--green);
}

.day-pnl.negative {
  color: var(--red);
}

.day-trades-count {
  font-size: 10px;
  color: var(--text-secondary);
  margin-top: 2px;
}

.day-bar {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 4px;
}

.day-bar.positive {
  background: var(--green);
}

.day-bar.negative {
  background: var(--red);
}

/* Day Detail Panel */
.day-detail-panel {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 12px;
  margin-top: 20px;
  overflow: hidden;
  display: none;
}

.day-detail-panel.active {
  display: block;
}

.day-detail-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 20px;
  background: var(--bg-secondary);
  border-bottom: 1px solid var(--border);
}

.day-detail-title {
  font-size: 16px;
  font-weight: 600;
}

.day-detail-close {
  background: none;
  border: none;
  color: var(--text-secondary);
  font-size: 24px;
  cursor: pointer;
  line-height: 1;
}

.day-detail-close:hover {
  color: var(--text-primary);
}

.day-detail-content {
  padding: 20px;
}

.day-detail-stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 12px;
  margin-bottom: 20px;
}

.day-detail-stat {
  text-align: center;
  padding: 12px;
  background: var(--bg-primary);
  border-radius: 8px;
}

.day-detail-stat-label {
  font-size: 10px;
  color: var(--text-secondary);
  text-transform: uppercase;
  margin-bottom: 4px;
}

.day-detail-stat-value {
  font-size: 16px;
  font-weight: 700;
  color: #fff;
}

.day-detail-stat-value.positive {
  color: var(--green);
}

.day-detail-stat-value.negative {
  color: var(--red);
}

.day-trades-list {
  max-height: 300px;
  overflow-y: auto;
}

.day-trade-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px;
  background: var(--bg-primary);
  border-radius: 6px;
  margin-bottom: 8px;
}

.day-trade-item:last-child {
  margin-bottom: 0;
}

.day-trade-info {
  display: flex;
  align-items: center;
  gap: 12px;
}

.day-trade-time {
  font-size: 12px;
  color: var(--text-secondary);
  font-family: monospace;
}

.day-trade-symbol {
  font-size: 13px;
  font-weight: 600;
  color: var(--text-primary);
}

.day-trade-direction {
  font-size: 11px;
  padding: 2px 6px;
  border-radius: 4px;
}

.day-trade-direction.long {
  background: rgba(38, 166, 154, 0.2);
  color: var(--green);
}

.day-trade-direction.short {
  background: rgba(239, 83, 80, 0.2);
  color: var(--red);
}

.day-trade-pnl {
  font-size: 14px;
  font-weight: 700;
}

.day-trade-pnl.positive {
  color: var(--green);
}

.day-trade-pnl.negative {
  color: var(--red);
}

/* ========== MODAL ========== */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  opacity: 0;
  visibility: hidden;
  transition: all 0.2s;
}

.modal-overlay.active {
  opacity: 1;
  visibility: visible;
}

.modal {
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: 12px;
  width: 90%;
  max-width: 450px;
  max-height: 90vh;
  overflow-y: auto;
  transform: scale(0.9);
  transition: transform 0.2s;
}

.modal-overlay.active .modal {
  transform: scale(1);
}

.modal-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 20px;
  border-bottom: 1px solid var(--border);
}

.modal-title {
  font-size: 16px;
  font-weight: 600;
}

.modal-close {
  background: none;
  border: none;
  color: var(--text-secondary);
  font-size: 24px;
  cursor: pointer;
  line-height: 1;
}

.modal-close:hover {
  color: var(--text-primary);
}

.modal-body {
  padding: 20px;
}

.modal-footer {
  padding: 16px 20px;
  border-top: 1px solid var(--border);
  display: flex;
  gap: 10px;
  justify-content: flex-end;
}

.modal-footer .btn {
  width: auto;
}

/* ========== TOAST ========== */
.toast-container {
  position: fixed;
  top: 70px;
  right: 20px;
  z-index: 1001;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.toast {
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 12px 16px;
  display: flex;
  align-items: center;
  gap: 10px;
  min-width: 280px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
  animation: slideIn 0.3s ease;
}

@keyframes slideIn {
  from {
    transform: translateX(100%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

.toast.success {
  border-left: 3px solid var(--green);
}

.toast.error {
  border-left: 3px solid var(--red);
}

.toast.warning {
  border-left: 3px solid var(--yellow);
}

.toast-icon {
  font-size: 18px;
}

.toast-message {
  font-size: 13px;
  flex: 1;
}

/* ========== EMPTY STATE ========== */
.empty-state {
  text-align: center;
  padding: 60px 20px;
  color: var(--text-secondary);
}

.empty-state svg {
  width: 64px;
  height: 64px;
  fill: var(--border);
  margin-bottom: 16px;
}

.empty-state h3 {
  font-size: 16px;
  color: var(--text-primary);
  margin-bottom: 8px;
}

.empty-state p {
  font-size: 13px;
}

/* ========== RESPONSIVE ========== */
@media (max-width: 768px) {
  .metrics-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .tv-chart-container {
    height: 350px;
  }
  
  .header {
    padding: 10px 12px;
  }
  
  .sidebar {
    padding: 12px;
  }
  
  .content {
    padding: 12px;
  }
  
  .calendar-day {
    min-height: 70px;
    padding: 4px;
  }
  
  .day-number {
    font-size: 12px;
    width: 24px;
    height: 24px;
  }
  
  .day-pnl {
    font-size: 11px;
  }
  
  .day-trades-count {
    display: none;
  }
  
  .header-center {
    order: 3;
    width: 100%;
    justify-content: center;
  }
}

@media (max-width: 480px) {
  .metrics-grid {
    grid-template-columns: 1fr;
  }
  
  .form-row {
    grid-template-columns: 1fr;
  }
  
  .btn-group {
    flex-direction: column;
  }
  
  .calendar-weekday {
    font-size: 9px;
    padding: 8px 2px;
  }
  
  .calendar-day {
    min-height: 60px;
  }
}
</style>
</head>
<body>

<!-- HEADER -->
<header class="header">
  <div class="logo">
    <svg viewBox="0 0 24 24"><path d="M3.5 18.49l6-6.01 4 4L22 6.92l-1.41-1.41-7.09 7.97-4-4L2 16.99z"/></svg>
    Trading Journal Pro
  </div>
  
  <div class="header-center">
    <button class="header-nav-btn active" data-view="dashboard">
      <svg viewBox="0 0 24 24"><path d="M3 13h8V3H3v10zm0 8h8v-6H3v6zm10 0h8V11h-8v10zm0-18v6h8V3h-8z"/></svg>
      Dashboard
    </button>
    <button class="header-nav-btn" data-view="calendar">
      <svg viewBox="0 0 24 24"><path d="M19 3h-1V1h-2v2H8V1H6v2H5c-1.11 0-1.99.9-1.99 2L3 19c0 1.1.89 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm0 16H5V8h14v11zM9 10H7v2h2v-2zm4 0h-2v2h2v-2zm4 0h-2v2h2v-2zm-8 4H7v2h2v-2zm4 0h-2v2h2v-2zm4 0h-2v2h2v-2z"/></svg>
      Calendario
    </button>
  </div>
  
  <div class="header-status">
    <span class="status-dot" id="statusDot"></span>
    <span id="statusText">Sin datos cargados</span>
  </div>
</header>

<!-- DASHBOARD VIEW -->
<div class="view-container active" id="dashboardView">
  <!-- SIDEBAR -->
  <aside class="sidebar">
    
    <!-- Capital Inicial -->
    <div class="section">
      <div class="section-title">
        <svg viewBox="0 0 24 24"><path d="M11.8 10.9c-2.27-.59-3-1.2-3-2.15 0-1.09 1.01-1.85 2.7-1.85 1.78 0 2.44.85 2.5 2.1h2.21c-.07-1.72-1.12-3.3-3.21-3.81V3h-3v2.16c-1.94.42-3.5 1.68-3.5 3.61 0 2.31 1.91 3.46 4.7 4.13 2.5.6 3 1.48 3 2.41 0 .69-.49 1.79-2.7 1.79-2.06 0-2.87-.92-2.98-2.1h-2.2c.12 2.19 1.76 3.42 3.68 3.83V21h3v-2.15c1.95-.37 3.5-1.5 3.5-3.55 0-2.84-2.43-3.81-4.7-4.4z"/></svg>
        Capital Inicial
      </div>
      <div class="form-group">
        <div class="form-row">
          <input type="number" class="form-input" id="initialCapital" value="50000" placeholder="50000">
          <select class="form-input" id="currency">
            <option value="USD">USD</option>
            <option value="EUR">EUR</option>
            <option value="MXN">MXN</option>
          </select>
        </div>
      </div>
      <button class="btn btn-primary" id="setCapitalBtn">Establecer Capital</button>
    </div>

    <!-- Agregar Operación -->
    <div class="section">
      <div class="section-title">
        <svg viewBox="0 0 24 24"><path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"/></svg>
        Nueva Operación
      </div>
      <div class="form-group">
        <label class="form-label">Fecha y Hora</label>
        <input type="datetime-local" class="form-input" id="tradeDate">
      </div>
      <div class="form-group">
        <label class="form-label">Símbolo</label>
        <input type="text" class="form-input" id="tradeSymbol" placeholder="ES, NQ, EURUSD...">
      </div>
      <div class="form-group">
        <label class="form-label">Dirección</label>
        <div class="toggle-group">
          <button class="toggle-btn long active" data-direction="long">Long</button>
          <button class="toggle-btn short" data-direction="short">Short</button>
        </div>
      </div>
      <div class="form-group">
        <div class="form-row">
          <div>
            <label class="form-label">P&L</label>
            <input type="number" class="form-input" id="tradePnl" placeholder="+/-" step="0.01">
          </div>
          <div>
            <label class="form-label">Comisión</label>
            <input type="number" class="form-input" id="tradeCommission" placeholder="0" value="0" step="0.01">
          </div>
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">Notas (opcional)</label>
        <input type="text" class="form-input" id="tradeNotes" placeholder="Notas sobre el trade...">
      </div>
      <button class="btn btn-success" id="addTradeBtn">Agregar Operación</button>
    </div>

    <!-- Importar Masivo -->
    <div class="section">
      <div class="section-title">
        <svg viewBox="0 0 24 24"><path d="M9 16h6v-6h4l-7-7-7 7h4v6zm-4 2h14v2H5v-2z"/></svg>
        Importar Operaciones
      </div>
      <div class="form-group">
        <textarea class="form-input" id="bulkImport" placeholder="Pegue operaciones separadas por + y -&#10;Ejemplo: +247+264-952+261-948&#10;O: 247, 264, -952, 261"></textarea>
        <div class="import-indicator" id="importIndicator"></div>
      </div>
      <button class="btn btn-primary" id="importBtn">Importar Texto</button>
    </div>

    <!-- Importar CSV -->
    <div class="section">
      <div class="section-title">
        <svg viewBox="0 0 24 24"><path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm4 18H6V4h7v5h5v11zM8 15.01l1.41 1.41L11 14.84V19h2v-4.16l1.59 1.59L16 15.01 12.01 11 8 15.01z"/></svg>
        Importar CSV
      </div>
      <div class="form-group">
        <div class="file-input-wrapper">
          <input type="file" class="file-input" id="csvFileInput" accept=".csv,.txt">
          <label class="file-input-label" for="csvFileInput">
            <svg viewBox="0 0 24 24"><path d="M14 2H6c-1.1 0-1.99.9-1.99 2L4 20c0 1.1.89 2 1.99 2H18c1.1 0 2-.9 2-2V8l-6-6zm4 18H6V4h7v5h5v11zM8 15.01l1.41 1.41L11 14.84V19h2v-4.16l1.59 1.59L16 15.01 12.01 11 8 15.01z"/></svg>
            Seleccionar archivo CSV
          </label>
          <div class="file-name" id="csvFileName"></div>
        </div>
        <div class="import-indicator" id="csvImportIndicator"></div>
      </div>
      <button class="btn btn-success" id="importCsvBtn">Importar CSV</button>
      <p style="font-size: 10px; color: var(--text-secondary); margin-top: 8px;">
        Formato: una columna con valores +/- (ej: +247, -952, 261)
      </p>
    </div>

    <!-- Acciones -->
    <div class="section">
      <div class="section-title">
        <svg viewBox="0 0 24 24"><path d="M19.14 12.94c.04-.31.06-.63.06-.94 0-.31-.02-.63-.06-.94l2.03-1.58c.18-.14.23-.41.12-.61l-1.92-3.32c-.12-.22-.37-.29-.59-.22l-2.39.96c-.5-.38-1.03-.7-1.62-.94l-.36-2.54c-.04-.24-.24-.41-.48-.41h-3.84c-.24 0-.43.17-.47.41l-.36 2.54c-.59.24-1.13.57-1.62.94l-2.39-.96c-.22-.08-.47 0-.59.22L2.74 8.87c-.12.21-.08.47.12.61l2.03 1.58c-.04.31-.06.63-.06.94s.02.63.06.94l-2.03 1.58c-.18.14-.23.41-.12.61l1.92 3.32c.12.22.37.29.59.22l2.39-.96c.5.38 1.03.7 1.62.94l.36 2.54c.05.24.24.41.48.41h3.84c.24 0 .44-.17.47-.41l.36-2.54c.59-.24 1.13-.56 1.62-.94l2.39.96c.22.08.47 0 .59-.22l1.92-3.32c.12-.22.07-.47-.12-.61l-2.01-1.58zM12 15.6c-1.98 0-3.6-1.62-3.6-3.6s1.62-3.6 3.6-3.6 3.6 1.62 3.6 3.6-1.62 3.6-3.6 3.6z"/></svg>
        Acciones
      </div>
      <div class="btn-group">
        <button class="btn btn-secondary" id="exportCsvBtn">CSV</button>
        <button class="btn btn-secondary" id="exportJsonBtn">JSON</button>
      </div>
      <div class="btn-group">
        <button class="btn btn-danger" id="resetBtn">Resetear Todo</button>
      </div>
    </div>
  </aside>

  <!-- CONTENT -->
  <main class="content">
    
    <!-- Metrics Grid -->
    <div class="metrics-grid" id="metricsGrid">
      <div class="metric-card">
        <div class="metric-label">Capital Actual</div>
        <div class="metric-value large" id="metricCapital">$50,000.00</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">P&L Total</div>
        <div class="metric-value" id="metricPnl">$0.00</div>
        <div class="metric-subtext" id="metricPnlPct">0.00%</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Total Trades</div>
        <div class="metric-value" id="metricTrades">0</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Win Rate</div>
        <div class="metric-value" id="metricWinRate">0%</div>
        <div class="progress-bar"><div class="progress-fill" id="winRateBar" style="width: 0%"></div></div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Profit Factor</div>
        <div class="metric-value" id="metricProfitFactor">0.00</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Expectativa</div>
        <div class="metric-value" id="metricExpectancy">$0.00</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Max Drawdown</div>
        <div class="metric-value negative" id="metricMaxDD">$0.00</div>
        <div class="metric-subtext" id="metricMaxDDPct">0.00%</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Mejor Trade</div>
        <div class="metric-value positive" id="metricBestTrade">$0.00</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Peor Trade</div>
        <div class="metric-value negative" id="metricWorstTrade">$0.00</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Promedio Ganador</div>
        <div class="metric-value positive" id="metricAvgWin">$0.00</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Promedio Perdedor</div>
        <div class="metric-value negative" id="metricAvgLoss">$0.00</div>
      </div>
      <div class="metric-card">
        <div class="metric-label">Racha Ganadora</div>
        <div class="metric-value" id="metricWinStreak">0</div>
      </div>
    </div>

    <!-- TradingView Style Chart -->
    <div class="tv-chart-section">
      <div class="tv-chart-header">
        <div class="tv-chart-title">
          <span class="symbol">EQUITY</span>
          <span class="price positive" id="tvCurrentPrice">$50,000.00</span>
        </div>
        <div class="tv-chart-info">
          <span>Capital vs Trades</span>
        </div>
      </div>
      <div class="tv-chart-container" id="tvChartContainer">
        <div class="tv-watermark">EQUITY</div>
        <canvas class="tv-chart-canvas" id="tvChartCanvas"></canvas>
        <div class="tv-y-axis" id="tvYAxis"></div>
        <div class="tv-x-axis" id="tvXAxis"></div>
        <div class="tv-crosshair-h" id="tvCrosshairH"></div>
        <div class="tv-crosshair-v" id="tvCrosshairV"></div>
        <div class="tv-tooltip" id="tvTooltip">
          <div class="tv-tooltip-row">
            <span class="tv-tooltip-label">Trade:</span>
            <span class="tv-tooltip-value" id="ttTrade">#0</span>
          </div>
          <div class="tv-tooltip-row">
            <span class="tv-tooltip-label">Capital:</span>
            <span class="tv-tooltip-value" id="ttCapital">$0</span>
          </div>
          <div class="tv-tooltip-row">
            <span class="tv-tooltip-label">P&L:</span>
            <span class="tv-tooltip-value" id="ttPnl">$0</span>
          </div>
          <div class="tv-tooltip-row">
            <span class="tv-tooltip-label">Cambio:</span>
            <span class="tv-tooltip-value" id="ttChange">0%</span>
          </div>
        </div>
        <div class="tv-legend">
          <div class="tv-legend-row">
            <div class="tv-legend-color" style="background: #2962ff;"></div>
            <span>Capital:</span>
            <span class="tv-legend-value" id="legendCapital">$50,000</span>
          </div>
          <div class="tv-legend-row">
            <div class="tv-legend-color" style="background: rgba(255,193,7,0.5);"></div>
            <span>Inicial:</span>
            <span class="tv-legend-value" id="legendInitial">$50,000</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Secondary Charts Section -->
    <div class="chart-section">
      <div class="tabs">
        <button class="tab active" data-tab="pnl">P&L por Trade</button>
        <button class="tab" data-tab="drawdown">Drawdown</button>
        <button class="tab" data-tab="distribution">Distribución</button>
      </div>
      
      <div class="tab-content active" id="tab-pnl">
        <div class="chart-wrapper">
          <canvas id="pnlChart"></canvas>
        </div>
      </div>
      
      <div class="tab-content" id="tab-drawdown">
        <div class="chart-wrapper">
          <canvas id="drawdownChart"></canvas>
        </div>
      </div>
      
      <div class="tab-content" id="tab-distribution">
        <div class="chart-wrapper">
          <canvas id="distributionChart"></canvas>
        </div>
      </div>
    </div>

    <!-- Trades Table -->
    <div class="table-section">
      <div class="table-header">
        <div class="table-title">Historial de Operaciones</div>
        <div class="table-filters">
          <select class="filter-select" id="filterType">
            <option value="all">Todas</option>
            <option value="winners">Ganadores</option>
            <option value="losers">Perdedores</option>
          </select>
        </div>
      </div>
      <div class="table-container">
        <table id="tradesTable">
          <thead>
            <tr>
              <th>#</th>
              <th>Fecha</th>
              <th>Símbolo</th>
              <th>Dir</th>
              <th>P&L</th>
              <th>Com.</th>
              <th>Neto</th>
              <th>Capital</th>
              <th>Acciones</th>
            </tr>
          </thead>
          <tbody id="tradesTableBody">
          </tbody>
        </table>
        <div class="empty-state" id="emptyState">
          <svg viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/></svg>
          <h3>Sin operaciones</h3>
          <p>Agrega tu primera operación para comenzar el análisis</p>
        </div>
      </div>
      <div class="table-footer" id="tableFooter" style="display: none;">
        <span id="tableStats">0 operaciones</span>
        <span id="tableTotalPnl">Total P&L: $0.00</span>
      </div>
    </div>

  </main>
</div>

<!-- CALENDAR VIEW -->
<div class="view-container calendar-view" id="calendarView">
  <div class="calendar-content">
    <!-- Calendar Header -->
    <div class="calendar-header">
      <div class="calendar-nav">
        <button class="calendar-nav-btn" id="prevMonth">◀</button>
        <div class="calendar-month-title" id="calendarMonthTitle">Diciembre 2024</div>
        <button class="calendar-nav-btn" id="nextMonth">▶</button>
      </div>
      <button class="calendar-today-btn" id="todayBtn">Hoy</button>
    </div>

    <!-- Calendar Stats -->
    <div class="calendar-stats" id="calendarStats">
      <div class="calendar-stat-card">
        <div class="calendar-stat-label">P&L del Mes</div>
        <div class="calendar-stat-value" id="monthPnl">$0.00</div>
      </div>
      <div class="calendar-stat-card">
        <div class="calendar-stat-label">Trades del Mes</div>
        <div class="calendar-stat-value" id="monthTrades">0</div>
      </div>
      <div class="calendar-stat-card">
        <div class="calendar-stat-label">Días Ganadores</div>
        <div class="calendar-stat-value positive" id="monthWinDays">0</div>
      </div>
      <div class="calendar-stat-card">
        <div class="calendar-stat-label">Días Perdedores</div>
        <div class="calendar-stat-value negative" id="monthLoseDays">0</div>
      </div>
      <div class="calendar-stat-card">
        <div class="calendar-stat-label">Mejor Día</div>
        <div class="calendar-stat-value positive" id="monthBestDay">$0.00</div>
      </div>
      <div class="calendar-stat-card">
        <div class="calendar-stat-label">Peor Día</div>
        <div class="calendar-stat-value negative" id="monthWorstDay">$0.00</div>
      </div>
    </div>

    <!-- Calendar Grid -->
    <div class="calendar-grid-container">
      <div class="calendar-weekdays">
        <div class="calendar-weekday">Dom</div>
        <div class="calendar-weekday">Lun</div>
        <div class="calendar-weekday">Mar</div>
        <div class="calendar-weekday">Mié</div>
        <div class="calendar-weekday">Jue</div>
        <div class="calendar-weekday">Vie</div>
        <div class="calendar-weekday">Sáb</div>
      </div>
      <div class="calendar-grid" id="calendarGrid">
        <!-- Days will be generated here -->
      </div>
    </div>

    <!-- Day Detail Panel -->
    <div class="day-detail-panel" id="dayDetailPanel">
      <div class="day-detail-header">
        <div class="day-detail-title" id="dayDetailTitle">Detalle del Día</div>
        <button class="day-detail-close" id="dayDetailClose">&times;</button>
      </div>
      <div class="day-detail-content">
        <div class="day-detail-stats" id="dayDetailStats">
          <!-- Stats will be generated here -->
        </div>
        <div class="day-trades-list" id="dayTradesList">
          <!-- Trades will be generated here -->
        </div>
      </div>
    </div>
  </div>
</div>

<!-- MODAL -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal">
    <div class="modal-header">
      <div class="modal-title" id="modalTitle">Confirmar</div>
      <button class="modal-close" id="modalClose">&times;</button>
    </div>
    <div class="modal-body" id="modalBody">
      ¿Estás seguro?
    </div>
    <div class="modal-footer">
      <button class="btn btn-secondary" id="modalCancel">Cancelar</button>
      <button class="btn btn-danger" id="modalConfirm">Confirmar</button>
    </div>
  </div>
</div>

<!-- TOAST CONTAINER -->
<div class="toast-container" id="toastContainer"></div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
// ========== APP STATE ==========
const state = {
  initialCapital: 50000,
  currency: 'USD',
  capitalLocked: false,
  trades: [],
  direction: 'long',
  csvData: null,
  currentView: 'dashboard',
  calendarDate: new Date(),
  selectedDay: null
};

// ========== DOM ELEMENTS ==========
const elements = {
  initialCapital: document.getElementById('initialCapital'),
  currency: document.getElementById('currency'),
  setCapitalBtn: document.getElementById('setCapitalBtn'),
  tradeDate: document.getElementById('tradeDate'),
  tradeSymbol: document.getElementById('tradeSymbol'),
  tradePnl: document.getElementById('tradePnl'),
  tradeCommission: document.getElementById('tradeCommission'),
  tradeNotes: document.getElementById('tradeNotes'),
  addTradeBtn: document.getElementById('addTradeBtn'),
  bulkImport: document.getElementById('bulkImport'),
  importIndicator: document.getElementById('importIndicator'),
  importBtn: document.getElementById('importBtn'),
  csvFileInput: document.getElementById('csvFileInput'),
  csvFileName: document.getElementById('csvFileName'),
  csvImportIndicator: document.getElementById('csvImportIndicator'),
  importCsvBtn: document.getElementById('importCsvBtn'),
  exportCsvBtn: document.getElementById('exportCsvBtn'),
  exportJsonBtn: document.getElementById('exportJsonBtn'),
  resetBtn: document.getElementById('resetBtn'),
  statusDot: document.getElementById('statusDot'),
  statusText: document.getElementById('statusText'),
  tradesTableBody: document.getElementById('tradesTableBody'),
  emptyState: document.getElementById('emptyState'),
  tableFooter: document.getElementById('tableFooter'),
  filterType: document.getElementById('filterType'),
  modalOverlay: document.getElementById('modalOverlay'),
  toastContainer: document.getElementById('toastContainer'),
  // Calendar elements
  calendarGrid: document.getElementById('calendarGrid'),
  calendarMonthTitle: document.getElementById('calendarMonthTitle'),
  dayDetailPanel: document.getElementById('dayDetailPanel'),
  dayDetailStats: document.getElementById('dayDetailStats'),
  dayTradesList: document.getElementById('dayTradesList'),
  dayDetailTitle: document.getElementById('dayDetailTitle')
};

// ========== CHART INSTANCES ==========
let pnlChart, drawdownChart, distributionChart;
let tvChartData = null;

// ========== UTILITY FUNCTIONS ==========
function formatCurrency(value) {
  if (value === null || value === undefined || isNaN(value)) {
    return '$0.00';
  }
  const sign = value >= 0 ? '' : '-';
  return sign + '$' + Math.abs(value).toLocaleString('en-US', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
}

function formatCurrencyShort(value) {
  if (value === null || value === undefined || isNaN(value)) {
    return '$0';
  }
  if (Math.abs(value) >= 1000000) {
    return '$' + (value / 1000000).toFixed(2) + 'M';
  } else if (Math.abs(value) >= 1000) {
    return '$' + (value / 1000).toFixed(1) + 'K';
  }
  return '$' + value.toFixed(0);
}

function formatPercent(value) {
  if (value === null || value === undefined || isNaN(value)) {
    return '0.00%';
  }
  const sign = value >= 0 ? '+' : '';
  return sign + value.toFixed(2) + '%';
}

function showToast(message, type = 'success') {
  const toast = document.createElement('div');
  toast.className = `toast ${type}`;
  const icons = { success: '✓', error: '✕', warning: '⚠' };
  toast.innerHTML = `
    <span class="toast-icon">${icons[type]}</span>
    <span class="toast-message">${message}</span>
  `;
  elements.toastContainer.appendChild(toast);
  setTimeout(() => toast.remove(), 3000);
}

function showModal(title, body, onConfirm) {
  document.getElementById('modalTitle').textContent = title;
  document.getElementById('modalBody').textContent = body;
  elements.modalOverlay.classList.add('active');
  
  const confirmBtn = document.getElementById('modalConfirm');
  const newConfirmBtn = confirmBtn.cloneNode(true);
  confirmBtn.parentNode.replaceChild(newConfirmBtn, confirmBtn);
  
  newConfirmBtn.addEventListener('click', () => {
    onConfirm();
    elements.modalOverlay.classList.remove('active');
  });
}

function closeModal() {
  elements.modalOverlay.classList.remove('active');
}

function parseBulkTrades(str) {
  let s = str.replace(/\s+/g, '')
             .replace(/\$/g, '')
             .replace(/\(/g, '')
             .replace(/\)/g, '')
             .replace(/,/g, '+')
             .replace(/\+\+/g, '+')
             .replace(/--/g, '+')
             .replace(/-\+/g, '-')
             .replace(/\+-/g, '-');
  
  if (!/^[+-]/.test(s)) s = '+' + s;
  const parts = s.split(/(?=[+-])/).filter(Boolean);
  return parts.map(p => parseFloat(p)).filter(n => !isNaN(n) && n !== 0);
}

// ========== CSV PARSING FUNCTION ==========
function parseCSV(content) {
  const lines = content.split(/\r?\n/).filter(line => line.trim() !== '');
  const trades = [];
  
  for (let i = 0; i < lines.length; i++) {
    const line = lines[i].trim();
    
    if (i === 0 && /[a-zA-Z]{2,}/.test(line) && !/^[+-]?\d/.test(line)) {
      continue;
    }
    
    const cells = line.split(/[,;\t]/);
    
    for (const cell of cells) {
      const cleanValue = cell.trim()
        .replace(/\$/g, '')
        .replace(/\(/g, '-')
        .replace(/\)/g, '')
        .replace(/"/g, '')
        .replace(/'/g, '')
        .replace(/\s+/g, '');
      
      if (cleanValue === '') continue;
      
      const num = parseFloat(cleanValue);
      if (!isNaN(num) && num !== 0) {
        trades.push(num);
      }
    }
  }
  
  return trades;
}

function setDefaultDateTime() {
  const now = new Date();
  now.setMinutes(now.getMinutes() - now.getTimezoneOffset());
  elements.tradeDate.value = now.toISOString().slice(0, 16);
}

// ========== DATE UTILITY FUNCTIONS ==========
function getDateKey(date) {
  const d = new Date(date);
  return `${d.getFullYear()}-${String(d.getMonth() + 1).padStart(2, '0')}-${String(d.getDate()).padStart(2, '0')}`;
}

function formatDateLong(dateKey) {
  // Parse the dateKey (YYYY-MM-DD) manually to avoid timezone issues
  const [year, month, day] = dateKey.split('-').map(Number);
  const date = new Date(year, month - 1, day); // month is 0-indexed
  const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
  return date.toLocaleDateString('es-ES', options);
}

function getMonthName(date) {
  const months = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 
                  'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'];
  return months[date.getMonth()];
}

// ========== CALCULATIONS ==========
function calculateMetrics() {
  const trades = state.trades;
  const initialCapital = state.initialCapital;
  
  if (trades.length === 0) {
    return {
      currentCapital: initialCapital,
      totalPnl: 0,
      totalPnlPct: 0,
      totalTrades: 0,
      winners: 0,
      losers: 0,
      winRate: 0,
      profitFactor: 0,
      expectancy: 0,
      maxDrawdown: 0,
      maxDrawdownPct: 0,
      bestTrade: 0,
      worstTrade: 0,
      avgWin: 0,
      avgLoss: 0,
      winStreak: 0,
      loseStreak: 0,
      equity: [initialCapital],
      drawdowns: [0],
      pnlList: [],
      runningCapitals: [initialCapital]
    };
  }

  let capital = initialCapital;
  let maxCapital = initialCapital;
  let maxDrawdown = 0;
  let maxDrawdownPct = 0;
  const equity = [initialCapital];
  const drawdowns = [0];
  const pnlList = [];
  const runningCapitals = [initialCapital];
  
  let winners = 0, losers = 0;
  let grossProfit = 0, grossLoss = 0;
  let bestTrade = -Infinity, worstTrade = Infinity;
  let currentWinStreak = 0, currentLoseStreak = 0;
  let maxWinStreak = 0, maxLoseStreak = 0;
  
  trades.forEach(trade => {
    const pnl = trade.pnl || 0;
    const commission = trade.commission || 0;
    const net = pnl - commission;
    capital += net;
    equity.push(capital);
    pnlList.push(net);
    runningCapitals.push(capital);
    
    if (capital > maxCapital) maxCapital = capital;
    const dd = maxCapital - capital;
    const ddPct = maxCapital > 0 ? (dd / maxCapital) * 100 : 0;
    drawdowns.push(dd);
    
    if (dd > maxDrawdown) {
      maxDrawdown = dd;
      maxDrawdownPct = ddPct;
    }
    
    if (net > 0) {
      winners++;
      grossProfit += net;
      currentWinStreak++;
      currentLoseStreak = 0;
      if (currentWinStreak > maxWinStreak) maxWinStreak = currentWinStreak;
    } else if (net < 0) {
      losers++;
      grossLoss += Math.abs(net);
      currentLoseStreak++;
      currentWinStreak = 0;
      if (currentLoseStreak > maxLoseStreak) maxLoseStreak = currentLoseStreak;
    }
    
    if (net > bestTrade) bestTrade = net;
    if (net < worstTrade) worstTrade = net;
  });
  
  const totalPnl = capital - initialCapital;
  const totalPnlPct = initialCapital > 0 ? (totalPnl / initialCapital) * 100 : 0;
  const winRate = trades.length > 0 ? (winners / trades.length) * 100 : 0;
  const profitFactor = grossLoss > 0 ? grossProfit / grossLoss : grossProfit > 0 ? Infinity : 0;
  const avgWin = winners > 0 ? grossProfit / winners : 0;
  const avgLoss = losers > 0 ? grossLoss / losers : 0;
  const expectancy = (winRate / 100) * avgWin - ((100 - winRate) / 100) * avgLoss;
  
  return {
    currentCapital: capital,
    totalPnl,
    totalPnlPct,
    totalTrades: trades.length,
    winners,
    losers,
    winRate,
    profitFactor,
    expectancy,
    maxDrawdown,
    maxDrawdownPct,
    bestTrade: bestTrade === -Infinity ? 0 : bestTrade,
    worstTrade: worstTrade === Infinity ? 0 : worstTrade,
    avgWin,
    avgLoss,
    winStreak: maxWinStreak,
    loseStreak: maxLoseStreak,
    equity,
    drawdowns,
    pnlList,
    runningCapitals
  };
}

// ========== CALENDAR CALCULATIONS ==========
function getTradesByDay() {
  const tradesByDay = {};
  
  state.trades.forEach(trade => {
    if (trade.date) {
      const dateKey = getDateKey(trade.date);
      if (!tradesByDay[dateKey]) {
        tradesByDay[dateKey] = [];
      }
      tradesByDay[dateKey].push(trade);
    }
  });
  
  return tradesByDay;
}

function getDayPnl(trades) {
  return trades.reduce((sum, trade) => {
    const pnl = trade.pnl || 0;
    const commission = trade.commission || 0;
    return sum + (pnl - commission);
  }, 0);
}

function getMonthStats(year, month) {
  const tradesByDay = getTradesByDay();
  let monthPnl = 0;
  let monthTrades = 0;
  let winDays = 0;
  let loseDays = 0;
  let bestDay = -Infinity;
  let worstDay = Infinity;
  
  Object.keys(tradesByDay).forEach(dateKey => {
    const [y, m] = dateKey.split('-').map(Number);
    if (y === year && m === month + 1) {
      const dayTrades = tradesByDay[dateKey];
      const dayPnl = getDayPnl(dayTrades);
      
      monthPnl += dayPnl;
      monthTrades += dayTrades.length;
      
      if (dayPnl > 0) winDays++;
      else if (dayPnl < 0) loseDays++;
      
      if (dayPnl > bestDay) bestDay = dayPnl;
      if (dayPnl < worstDay) worstDay = dayPnl;
    }
  });
  
  return {
    monthPnl,
    monthTrades,
    winDays,
    loseDays,
    bestDay: bestDay === -Infinity ? 0 : bestDay,
    worstDay: worstDay === Infinity ? 0 : worstDay
  };
}

// ========== UI UPDATE FUNCTIONS ==========
function updateStatus() {
  const count = state.trades.length;
  if (count === 0) {
    elements.statusDot.classList.remove('active');
    elements.statusText.textContent = 'Sin datos cargados';
  } else {
    elements.statusDot.classList.add('active');
    elements.statusText.textContent = `${count} operacion${count !== 1 ? 'es' : ''} cargada${count !== 1 ? 's' : ''}`;
  }
}

function updateMetricsUI(metrics) {
  document.getElementById('metricCapital').textContent = formatCurrency(metrics.currentCapital);
  document.getElementById('metricCapital').className = 'metric-value large' + (metrics.totalPnl >= 0 ? ' positive' : ' negative');
  
  document.getElementById('metricPnl').textContent = formatCurrency(metrics.totalPnl);
  document.getElementById('metricPnl').className = 'metric-value' + (metrics.totalPnl >= 0 ? ' positive' : ' negative');
  document.getElementById('metricPnlPct').textContent = formatPercent(metrics.totalPnlPct);
  
  document.getElementById('metricTrades').textContent = metrics.totalTrades;
  
  document.getElementById('metricWinRate').textContent = metrics.winRate.toFixed(1) + '%';
  document.getElementById('winRateBar').style.width = metrics.winRate + '%';
  
  document.getElementById('metricProfitFactor').textContent = metrics.profitFactor === Infinity ? '∞' : metrics.profitFactor.toFixed(2);
  document.getElementById('metricProfitFactor').className = 'metric-value' + (metrics.profitFactor >= 1 ? ' positive' : ' negative');
  
  document.getElementById('metricExpectancy').textContent = formatCurrency(metrics.expectancy);
  document.getElementById('metricExpectancy').className = 'metric-value' + (metrics.expectancy >= 0 ? ' positive' : ' negative');
  
  document.getElementById('metricMaxDD').textContent = formatCurrency(-metrics.maxDrawdown);
  document.getElementById('metricMaxDDPct').textContent = '-' + metrics.maxDrawdownPct.toFixed(2) + '%';
  
  document.getElementById('metricBestTrade').textContent = formatCurrency(metrics.bestTrade);
  document.getElementById('metricWorstTrade').textContent = formatCurrency(metrics.worstTrade);
  
  document.getElementById('metricAvgWin').textContent = formatCurrency(metrics.avgWin);
  document.getElementById('metricAvgLoss').textContent = formatCurrency(-metrics.avgLoss);
  
  document.getElementById('metricWinStreak').textContent = metrics.winStreak;
  
  const priceEl = document.getElementById('tvCurrentPrice');
  priceEl.textContent = formatCurrency(metrics.currentCapital);
  priceEl.className = 'price ' + (metrics.totalPnl >= 0 ? 'positive' : 'negative');
  
  document.getElementById('legendCapital').textContent = formatCurrencyShort(metrics.currentCapital);
  document.getElementById('legendInitial').textContent = formatCurrencyShort(state.initialCapital);
}

function updateTable() {
  const filter = elements.filterType.value;
  const tbody = elements.tradesTableBody;
  tbody.innerHTML = '';
  
  const metrics = calculateMetrics();
  const runningCapitals = metrics.runningCapitals;
  
  let filteredTrades = state.trades.map((t, i) => ({ 
    ...t, 
    index: i,
    runningCapital: runningCapitals[i + 1]
  }));
  
  if (filter === 'winners') {
    filteredTrades = filteredTrades.filter(t => ((t.pnl || 0) - (t.commission || 0)) > 0);
  } else if (filter === 'losers') {
    filteredTrades = filteredTrades.filter(t => ((t.pnl || 0) - (t.commission || 0)) < 0);
  }
  
  if (filteredTrades.length === 0) {
    elements.emptyState.style.display = 'block';
    elements.tableFooter.style.display = 'none';
    return;
  }
  
  elements.emptyState.style.display = 'none';
  elements.tableFooter.style.display = 'flex';
  
  let totalPnl = 0;
  
  filteredTrades.forEach(trade => {
    const pnl = trade.pnl || 0;
    const commission = trade.commission || 0;
    const net = pnl - commission;
    totalPnl += net;
    
    const row = document.createElement('tr');
    row.innerHTML = `
      <td>${trade.index + 1}</td>
      <td>${trade.date ? new Date(trade.date).toLocaleDateString('es-ES', { day: '2-digit', month: '2-digit', year: '2-digit', hour: '2-digit', minute: '2-digit' }) : '-'}</td>
      <td>${trade.symbol || '-'}</td>
      <td class="${trade.direction === 'long' ? 'direction-long' : 'direction-short'}">${trade.direction === 'long' ? '↑ L' : '↓ S'}</td>
      <td class="${pnl >= 0 ? 'pnl-positive' : 'pnl-negative'}">${formatCurrency(pnl)}</td>
      <td>${formatCurrency(-commission)}</td>
      <td class="${net >= 0 ? 'pnl-positive' : 'pnl-negative'}">${formatCurrency(net)}</td>
      <td>${formatCurrency(trade.runningCapital)}</td>
      <td>
        <button class="action-btn delete" data-index="${trade.index}" title="Eliminar">✕</button>
      </td>
    `;
    tbody.appendChild(row);
  });
  
  document.getElementById('tableStats').textContent = `${filteredTrades.length} operacion${filteredTrades.length !== 1 ? 'es' : ''}`;
  document.getElementById('tableTotalPnl').textContent = `Total P&L: ${formatCurrency(totalPnl)}`;
  document.getElementById('tableTotalPnl').className = totalPnl >= 0 ? 'pnl-positive' : 'pnl-negative';
}

// ========== CALENDAR RENDERING ==========
function renderCalendar() {
  const year = state.calendarDate.getFullYear();
  const month = state.calendarDate.getMonth();
  
  // Update month title
  elements.calendarMonthTitle.textContent = `${getMonthName(state.calendarDate)} ${year}`;
  
  // Update month stats
  const monthStats = getMonthStats(year, month);
  document.getElementById('monthPnl').textContent = formatCurrency(monthStats.monthPnl);
  document.getElementById('monthPnl').className = 'calendar-stat-value ' + (monthStats.monthPnl >= 0 ? 'positive' : 'negative');
  document.getElementById('monthTrades').textContent = monthStats.monthTrades;
  document.getElementById('monthWinDays').textContent = monthStats.winDays;
  document.getElementById('monthLoseDays').textContent = monthStats.loseDays;
  document.getElementById('monthBestDay').textContent = formatCurrency(monthStats.bestDay);
  document.getElementById('monthWorstDay').textContent = formatCurrency(monthStats.worstDay);
  
  // Get trades by day
  const tradesByDay = getTradesByDay();
  
  // Get first day of month and total days
  const firstDay = new Date(year, month, 1);
  const lastDay = new Date(year, month + 1, 0);
  const daysInMonth = lastDay.getDate();
  const startingDay = firstDay.getDay();
  
  // Get previous month days to fill
  const prevMonthLastDay = new Date(year, month, 0).getDate();
  
  // Clear grid
  elements.calendarGrid.innerHTML = '';
  
  // Today's date for comparison
  const today = new Date();
  const todayKey = getDateKey(today);
  
  // Add previous month days
  for (let i = startingDay - 1; i >= 0; i--) {
    const day = prevMonthLastDay - i;
    const dayEl = createDayElement(year, month - 1, day, tradesByDay, true, todayKey);
    elements.calendarGrid.appendChild(dayEl);
  }
  
  // Add current month days
  for (let day = 1; day <= daysInMonth; day++) {
    const dayEl = createDayElement(year, month, day, tradesByDay, false, todayKey);
    elements.calendarGrid.appendChild(dayEl);
  }
  
  // Add next month days to fill remaining cells
  const totalCells = elements.calendarGrid.children.length;
  const remainingCells = (Math.ceil(totalCells / 7) * 7) - totalCells;
  for (let day = 1; day <= remainingCells; day++) {
    const dayEl = createDayElement(year, month + 1, day, tradesByDay, true, todayKey);
    elements.calendarGrid.appendChild(dayEl);
  }
}

function createDayElement(year, month, day, tradesByDay, isOtherMonth, todayKey) {
  const dayEl = document.createElement('div');
  dayEl.className = 'calendar-day';
  
  // Handle month overflow
  if (month < 0) {
    month = 11;
    year--;
  } else if (month > 11) {
    month = 0;
    year++;
  }
  
  const dateKey = `${year}-${String(month + 1).padStart(2, '0')}-${String(day).padStart(2, '0')}`;
  const dayTrades = tradesByDay[dateKey] || [];
  const dayPnl = getDayPnl(dayTrades);
  
  if (isOtherMonth) {
    dayEl.classList.add('other-month');
  }
  
  if (dateKey === todayKey) {
    dayEl.classList.add('today');
  }
  
  if (dayTrades.length > 0) {
    dayEl.classList.add('has-trades');
    if (dayPnl > 0) {
      dayEl.classList.add('positive-day');
    } else if (dayPnl < 0) {
      dayEl.classList.add('negative-day');
    }
  }
  
  if (state.selectedDay === dateKey) {
    dayEl.classList.add('selected');
  }
  
  dayEl.innerHTML = `
    <div class="day-number">${day}</div>
    ${dayTrades.length > 0 ? `
      <div class="day-pnl ${dayPnl >= 0 ? 'positive' : 'negative'}">${formatCurrencyShort(dayPnl)}</div>
      <div class="day-trades-count">${dayTrades.length} trade${dayTrades.length !== 1 ? 's' : ''}</div>
      <div class="day-bar ${dayPnl >= 0 ? 'positive' : 'negative'}"></div>
    ` : ''}
  `;
  
  dayEl.addEventListener('click', () => {
    if (dayTrades.length > 0) {
      showDayDetail(dateKey, dayTrades, dayPnl);
    }
  });
  
  return dayEl;
}

function showDayDetail(dateKey, trades, totalPnl) {
  state.selectedDay = dateKey;
  renderCalendar(); // Re-render to show selection
  
  elements.dayDetailTitle.textContent = formatDateLong(dateKey);
  
  // Calculate day stats
  const winners = trades.filter(t => (t.pnl || 0) - (t.commission || 0) > 0).length;
  const losers = trades.filter(t => (t.pnl || 0) - (t.commission || 0) < 0).length;
  const winRate = trades.length > 0 ? (winners / trades.length) * 100 : 0;
  
  let grossProfit = 0, grossLoss = 0;
  trades.forEach(t => {
    const net = (t.pnl || 0) - (t.commission || 0);
    if (net > 0) grossProfit += net;
    else grossLoss += Math.abs(net);
  });
  
  const profitFactor = grossLoss > 0 ? grossProfit / grossLoss : grossProfit > 0 ? Infinity : 0;
  
  elements.dayDetailStats.innerHTML = `
    <div class="day-detail-stat">
      <div class="day-detail-stat-label">P&L del Día</div>
      <div class="day-detail-stat-value ${totalPnl >= 0 ? 'positive' : 'negative'}">${formatCurrency(totalPnl)}</div>
    </div>
    <div class="day-detail-stat">
      <div class="day-detail-stat-label">Trades</div>
      <div class="day-detail-stat-value">${trades.length}</div>
    </div>
    <div class="day-detail-stat">
      <div class="day-detail-stat-label">Ganadores</div>
      <div class="day-detail-stat-value positive">${winners}</div>
    </div>
    <div class="day-detail-stat">
      <div class="day-detail-stat-label">Perdedores</div>
      <div class="day-detail-stat-value negative">${losers}</div>
    </div>
    <div class="day-detail-stat">
      <div class="day-detail-stat-label">Win Rate</div>
      <div class="day-detail-stat-value">${winRate.toFixed(1)}%</div>
    </div>
    <div class="day-detail-stat">
      <div class="day-detail-stat-label">Profit Factor</div>
      <div class="day-detail-stat-value">${profitFactor === Infinity ? '∞' : profitFactor.toFixed(2)}</div>
    </div>
  `;
  
  // Render trades list
  elements.dayTradesList.innerHTML = trades.map(trade => {
    const net = (trade.pnl || 0) - (trade.commission || 0);
    const time = trade.date ? new Date(trade.date).toLocaleTimeString('es-ES', { hour: '2-digit', minute: '2-digit' }) : '--:--';
    
    return `
      <div class="day-trade-item">
        <div class="day-trade-info">
          <span class="day-trade-time">${time}</span>
          <span class="day-trade-symbol">${trade.symbol || '-'}</span>
          <span class="day-trade-direction ${trade.direction}">${trade.direction === 'long' ? '↑ LONG' : '↓ SHORT'}</span>
        </div>
        <div class="day-trade-pnl ${net >= 0 ? 'positive' : 'negative'}">${formatCurrency(net)}</div>
      </div>
    `;
  }).join('');
  
  elements.dayDetailPanel.classList.add('active');
}

function closeDayDetail() {
  state.selectedDay = null;
  elements.dayDetailPanel.classList.remove('active');
  renderCalendar();
}

// ========== VIEW SWITCHING ==========
function switchView(viewName) {
  state.currentView = viewName;
  
  // Update nav buttons
  document.querySelectorAll('.header-nav-btn').forEach(btn => {
    btn.classList.toggle('active', btn.dataset.view === viewName);
  });
  
  // Update view containers
  document.querySelectorAll('.view-container').forEach(view => {
    view.classList.remove('active');
  });
  
  if (viewName === 'dashboard') {
    document.getElementById('dashboardView').classList.add('active');
  } else if (viewName === 'calendar') {
    document.getElementById('calendarView').classList.add('active');
    renderCalendar();
  }
}

// ========== TRADINGVIEW STYLE CHART ==========
function drawTVChart(metrics) {
  const container = document.getElementById('tvChartContainer');
  const canvas = document.getElementById('tvChartCanvas');
  const ctx = canvas.getContext('2d');
  const yAxisEl = document.getElementById('tvYAxis');
  const xAxisEl = document.getElementById('tvXAxis');
  
  const rect = container.getBoundingClientRect();
  const dpr = window.devicePixelRatio || 1;
  
  const chartWidth = rect.width - 70;
  const chartHeight = rect.height - 30;
  
  canvas.width = rect.width * dpr;
  canvas.height = rect.height * dpr;
  canvas.style.width = rect.width + 'px';
  canvas.style.height = rect.height + 'px';
  ctx.scale(dpr, dpr);
  
  ctx.clearRect(0, 0, rect.width, rect.height);
  
  const equity = metrics.equity;
  const padding = { top: 30, right: 70, bottom: 30, left: 10 };
  
  const minY = Math.min(...equity) * 0.998;
  const maxY = Math.max(...equity) * 1.002;
  const rangeY = maxY - minY || 1;
  
  const xStep = equity.length > 1 ? (chartWidth - padding.left) / (equity.length - 1) : chartWidth;
  
  function getX(i) { return padding.left + i * xStep; }
  function getY(val) { return padding.top + (1 - (val - minY) / rangeY) * (chartHeight - padding.top); }
  
  ctx.strokeStyle = '#2a2e39';
  ctx.lineWidth = 1;
  const gridLines = 6;
  for (let i = 0; i <= gridLines; i++) {
    const y = padding.top + (i / gridLines) * (chartHeight - padding.top);
    ctx.beginPath();
    ctx.moveTo(padding.left, y);
    ctx.lineTo(chartWidth, y);
    ctx.stroke();
  }
  
  const initialY = getY(state.initialCapital);
  ctx.beginPath();
  ctx.moveTo(padding.left, initialY);
  ctx.lineTo(chartWidth, initialY);
  ctx.strokeStyle = 'rgba(255, 193, 7, 0.4)';
  ctx.lineWidth = 1;
  ctx.setLineDash([5, 5]);
  ctx.stroke();
  ctx.setLineDash([]);
  
  if (equity.length > 1) {
    const gradient = ctx.createLinearGradient(0, padding.top, 0, chartHeight);
    const isPositive = equity[equity.length - 1] >= state.initialCapital;
    
    if (isPositive) {
      gradient.addColorStop(0, 'rgba(41, 98, 255, 0.3)');
      gradient.addColorStop(1, 'rgba(41, 98, 255, 0)');
    } else {
      gradient.addColorStop(0, 'rgba(239, 83, 80, 0.3)');
      gradient.addColorStop(1, 'rgba(239, 83, 80, 0)');
    }
    
    ctx.beginPath();
    ctx.moveTo(getX(0), chartHeight);
    for (let i = 0; i < equity.length; i++) {
      ctx.lineTo(getX(i), getY(equity[i]));
    }
    ctx.lineTo(getX(equity.length - 1), chartHeight);
    ctx.closePath();
    ctx.fillStyle = gradient;
    ctx.fill();
  }
  
  if (equity.length > 1) {
    ctx.beginPath();
    ctx.moveTo(getX(0), getY(equity[0]));
    for (let i = 1; i < equity.length; i++) {
      ctx.lineTo(getX(i), getY(equity[i]));
    }
    
    const isPositive = equity[equity.length - 1] >= state.initialCapital;
    ctx.strokeStyle = isPositive ? '#2962ff' : '#ef5350';
    ctx.lineWidth = 2;
    ctx.stroke();
    
    for (let i = 1; i < equity.length; i++) {
      const pnl = metrics.pnlList[i - 1];
      const threshold = state.initialCapital * 0.01;
      
      if (Math.abs(pnl) > threshold) {
        ctx.beginPath();
        ctx.arc(getX(i), getY(equity[i]), 4, 0, Math.PI * 2);
        ctx.fillStyle = pnl > 0 ? '#26a69a' : '#ef5350';
        ctx.fill();
        ctx.strokeStyle = '#1e222d';
        ctx.lineWidth = 1;
        ctx.stroke();
      }
    }
  } else {
    ctx.beginPath();
    ctx.arc(getX(0), getY(equity[0]), 4, 0, Math.PI * 2);
    ctx.fillStyle = '#2962ff';
    ctx.fill();
  }
  
  yAxisEl.innerHTML = '';
  for (let i = 0; i <= gridLines; i++) {
    const val = maxY - (i / gridLines) * rangeY;
    const y = padding.top + (i / gridLines) * (chartHeight - padding.top);
    const label = document.createElement('div');
    label.className = 'tv-price-label';
    label.style.top = y + 'px';
    label.textContent = formatCurrencyShort(val);
    yAxisEl.appendChild(label);
  }
  
  const currentCapital = equity[equity.length - 1];
  const currentY = getY(currentCapital);
  const currentLabel = document.createElement('div');
  currentLabel.className = 'tv-current-price ' + (currentCapital >= state.initialCapital ? 'positive' : 'negative');
  currentLabel.style.top = Math.max(padding.top, Math.min(chartHeight - 10, currentY)) + 'px';
  currentLabel.textContent = formatCurrencyShort(currentCapital);
  yAxisEl.appendChild(currentLabel);
  
  xAxisEl.innerHTML = '';
  const xLabelStep = Math.max(1, Math.ceil(equity.length / 12));
  for (let i = 0; i < equity.length; i += xLabelStep) {
    const x = getX(i);
    if (x < chartWidth - 30) {
      const label = document.createElement('div');
      label.className = 'tv-trade-label';
      label.style.left = x + 'px';
      label.textContent = i === 0 ? 'Start' : '#' + i;
      xAxisEl.appendChild(label);
    }
  }
  
  tvChartData = {
    equity,
    pnlList: metrics.pnlList,
    getX,
    getY,
    minY,
    maxY,
    chartWidth,
    chartHeight,
    padding
  };
}

// ========== TV CHART INTERACTION ==========
function setupTVChartInteraction() {
  const container = document.getElementById('tvChartContainer');
  const crosshairH = document.getElementById('tvCrosshairH');
  const crosshairV = document.getElementById('tvCrosshairV');
  const tooltip = document.getElementById('tvTooltip');
  
  container.addEventListener('mousemove', function(e) {
    if (!tvChartData || tvChartData.equity.length < 1) return;
    
    const rect = container.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    
    const { equity, pnlList, getX, getY, chartWidth, chartHeight, padding } = tvChartData;
    
    if (x < padding.left || x > chartWidth || y < padding.top || y > chartHeight) {
      tooltip.classList.remove('visible');
      crosshairH.style.display = 'none';
      crosshairV.style.display = 'none';
      return;
    }
    
    const xStep = equity.length > 1 ? (chartWidth - padding.left) / (equity.length - 1) : chartWidth;
    const idx = Math.round((x - padding.left) / xStep);
    const clampedIdx = Math.max(0, Math.min(equity.length - 1, idx));
    
    const pointX = getX(clampedIdx);
    const pointY = getY(equity[clampedIdx]);
    
    crosshairH.style.display = 'block';
    crosshairH.style.top = pointY + 'px';
    crosshairV.style.display = 'block';
    crosshairV.style.left = pointX + 'px';
    
    const pnl = clampedIdx > 0 ? pnlList[clampedIdx - 1] : 0;
    const change = ((equity[clampedIdx] - state.initialCapital) / state.initialCapital) * 100;
    
    document.getElementById('ttTrade').textContent = clampedIdx === 0 ? 'Inicio' : '#' + clampedIdx;
    document.getElementById('ttCapital').textContent = formatCurrency(equity[clampedIdx]);
    
    const ttPnl = document.getElementById('ttPnl');
    ttPnl.textContent = formatCurrency(pnl);
    ttPnl.className = 'tv-tooltip-value ' + (pnl >= 0 ? 'positive' : 'negative');
    
    const ttChange = document.getElementById('ttChange');
    ttChange.textContent = formatPercent(change);
    ttChange.className = 'tv-tooltip-value ' + (change >= 0 ? 'positive' : 'negative');
    
    tooltip.classList.add('visible');
    let tooltipX = pointX + 15;
    let tooltipY = pointY - 60;
    
    if (tooltipX + 170 > chartWidth) tooltipX = pointX - 175;
    if (tooltipY < 10) tooltipY = pointY + 15;
    
    tooltip.style.left = tooltipX + 'px';
    tooltip.style.top = tooltipY + 'px';
    
    document.getElementById('legendCapital').textContent = formatCurrencyShort(equity[clampedIdx]);
  });
  
  container.addEventListener('mouseleave', function() {
    tooltip.classList.remove('visible');
    crosshairH.style.display = 'none';
    crosshairV.style.display = 'none';
    
    const metrics = calculateMetrics();
    document.getElementById('legendCapital').textContent = formatCurrencyShort(metrics.currentCapital);
  });
}

// ========== SECONDARY CHARTS ==========
function updateSecondaryCharts(metrics) {
  const labels = metrics.equity.map((_, i) => i === 0 ? 'Inicio' : `#${i}`);
  
  if (pnlChart) pnlChart.destroy();
  const pnlData = metrics.pnlList;
  const pnlLabels = state.trades.map((_, i) => `#${i + 1}`);
  
  if (pnlData.length > 0) {
    pnlChart = new Chart(document.getElementById('pnlChart'), {
      type: 'bar',
      data: {
        labels: pnlLabels,
        datasets: [{
          label: 'P&L',
          data: pnlData,
          backgroundColor: pnlData.map(v => v >= 0 ? 'rgba(38, 166, 154, 0.8)' : 'rgba(239, 83, 80, 0.8)'),
          borderColor: pnlData.map(v => v >= 0 ? '#26a69a' : '#ef5350'),
          borderWidth: 1
        }]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: { display: false },
          tooltip: {
            backgroundColor: '#1e222d',
            borderColor: '#2a2e39',
            borderWidth: 1,
            callbacks: { label: ctx => `P&L: ${formatCurrency(ctx.parsed.y)}` }
          }
        },
        scales: {
          x: { ticks: { color: '#787b86' }, grid: { color: '#2a2e39' } },
          y: { ticks: { color: '#787b86', callback: v => '$' + v.toLocaleString() }, grid: { color: '#2a2e39' } }
        }
      }
    });
  }

  if (drawdownChart) drawdownChart.destroy();
  const ddCtx = document.getElementById('drawdownChart').getContext('2d');
  const ddGradient = ddCtx.createLinearGradient(0, 0, 0, 280);
  ddGradient.addColorStop(0, 'rgba(239, 83, 80, 0.5)');
  ddGradient.addColorStop(1, 'rgba(239, 83, 80, 0)');
  
  drawdownChart = new Chart(ddCtx, {
    type: 'line',
    data: {
      labels,
      datasets: [{
        label: 'Drawdown',
        data: metrics.drawdowns.map(d => -d),
        borderColor: '#ef5350',
        backgroundColor: ddGradient,
        borderWidth: 2,
        fill: true,
        tension: 0.2,
        pointRadius: 0
      }]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        legend: { display: false },
        tooltip: {
          backgroundColor: '#1e222d',
          borderColor: '#2a2e39',
          borderWidth: 1,
          callbacks: { label: ctx => `Drawdown: ${formatCurrency(ctx.parsed.y)}` }
        }
      },
      scales: {
        x: { ticks: { color: '#787b86' }, grid: { color: '#2a2e39' } },
        y: { ticks: { color: '#787b86', callback: v => '$' + v.toLocaleString() }, grid: { color: '#2a2e39' } }
      }
    }
  });

  if (distributionChart) distributionChart.destroy();
  if (pnlData.length > 0) {
    const bins = Math.min(20, pnlData.length);
    const min = Math.min(...pnlData);
    const max = Math.max(...pnlData);
    const range = max - min || 1;
    const binSize = range / bins;
    const histogram = Array(bins).fill(0);
    
    pnlData.forEach(v => {
      const idx = Math.min(Math.floor((v - min) / binSize), bins - 1);
      histogram[idx]++;
    });
    
    const distLabels = histogram.map((_, i) => formatCurrencyShort(min + i * binSize));
    
    distributionChart = new Chart(document.getElementById('distributionChart'), {
      type: 'bar',
      data: {
        labels: distLabels,
        datasets: [{
          label: 'Frecuencia',
          data: histogram,
          backgroundColor: 'rgba(41, 98, 255, 0.6)',
          borderColor: '#2962ff',
          borderWidth: 1
        }]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: { display: false },
          tooltip: {
            backgroundColor: '#1e222d',
            borderColor: '#2a2e39',
            borderWidth: 1
          }
        },
        scales: {
          x: { ticks: { color: '#787b86', maxRotation: 45 }, grid: { color: '#2a2e39' } },
          y: { ticks: { color: '#787b86' }, grid: { color: '#2a2e39' } }
        }
      }
    });
  }
}

function updateAll() {
  updateStatus();
  const metrics = calculateMetrics();
  updateMetricsUI(metrics);
  updateTable();
  drawTVChart(metrics);
  updateSecondaryCharts(metrics);
  
  // Update calendar if visible
  if (state.currentView === 'calendar') {
    renderCalendar();
  }
}

// ========== EVENT HANDLERS ==========

// View switching
document.querySelectorAll('.header-nav-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    switchView(btn.dataset.view);
  });
});

// Calendar navigation
document.getElementById('prevMonth').addEventListener('click', () => {
  state.calendarDate.setMonth(state.calendarDate.getMonth() - 1);
  closeDayDetail();
  renderCalendar();
});

document.getElementById('nextMonth').addEventListener('click', () => {
  state.calendarDate.setMonth(state.calendarDate.getMonth() + 1);
  closeDayDetail();
  renderCalendar();
});

document.getElementById('todayBtn').addEventListener('click', () => {
  state.calendarDate = new Date();
  closeDayDetail();
  renderCalendar();
});

document.getElementById('dayDetailClose').addEventListener('click', closeDayDetail);

elements.setCapitalBtn.addEventListener('click', () => {
  const value = parseFloat(elements.initialCapital.value);
  if (isNaN(value) || value <= 0) {
    showToast('El capital inicial debe ser mayor a 0', 'error');
    return;
  }
  state.initialCapital = value;
  state.currency = elements.currency.value;
  state.capitalLocked = true;
  elements.initialCapital.disabled = true;
  elements.currency.disabled = true;
  elements.setCapitalBtn.textContent = '✓ Establecido';
  elements.setCapitalBtn.disabled = true;
  showToast(`Capital inicial establecido: ${formatCurrency(value)}`, 'success');
  updateAll();
});

document.querySelectorAll('.toggle-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.toggle-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    state.direction = btn.dataset.direction;
  });
});

elements.addTradeBtn.addEventListener('click', () => {
  const pnl = parseFloat(elements.tradePnl.value);
  if (isNaN(pnl)) {
    showToast('Ingresa un valor de P&L válido', 'error');
    return;
  }
  
  const trade = {
    id: Date.now(),
    date: elements.tradeDate.value || null,
    symbol: elements.tradeSymbol.value.toUpperCase() || null,
    direction: state.direction,
    pnl: pnl,
    commission: parseFloat(elements.tradeCommission.value) || 0,
    notes: elements.tradeNotes.value || null
  };
  
  state.trades.push(trade);
  
  elements.tradePnl.value = '';
  elements.tradeNotes.value = '';
  setDefaultDateTime();
  
  showToast('Operación agregada', 'success');
  updateAll();
});

elements.bulkImport.addEventListener('input', () => {
  const parsed = parseBulkTrades(elements.bulkImport.value);
  if (parsed.length > 0) {
    elements.importIndicator.textContent = `${parsed.length} operaciones detectadas`;
    elements.importIndicator.classList.add('has-data');
  } else {
    elements.importIndicator.textContent = '';
    elements.importIndicator.classList.remove('has-data');
  }
});

elements.importBtn.addEventListener('click', () => {
  const parsed = parseBulkTrades(elements.bulkImport.value);
  if (parsed.length === 0) {
    showToast('No se detectaron operaciones válidas', 'error');
    return;
  }
  
  const now = new Date();
  parsed.forEach((pnl, i) => {
    state.trades.push({
      id: Date.now() + i,
      date: new Date(now.getTime() + i * 60000).toISOString().slice(0, 16),
      symbol: null,
      direction: pnl >= 0 ? 'long' : 'short',
      pnl: pnl,
      commission: 0,
      notes: null
    });
  });
  
  elements.bulkImport.value = '';
  elements.importIndicator.textContent = '';
  elements.importIndicator.classList.remove('has-data');
  
  showToast(`${parsed.length} operaciones importadas`, 'success');
  updateAll();
});

// CSV File Import
elements.csvFileInput.addEventListener('change', (e) => {
  const file = e.target.files[0];
  if (!file) {
    elements.csvFileName.textContent = '';
    elements.csvImportIndicator.textContent = '';
    elements.csvImportIndicator.classList.remove('has-data');
    state.csvData = null;
    return;
  }
  
  elements.csvFileName.textContent = file.name;
  
  const reader = new FileReader();
  reader.onload = function(event) {
    const content = event.target.result;
    const parsed = parseCSV(content);
    
    if (parsed.length > 0) {
      state.csvData = parsed;
      elements.csvImportIndicator.textContent = `${parsed.length} operaciones detectadas en el archivo`;
      elements.csvImportIndicator.classList.add('has-data');
    } else {
      state.csvData = null;
      elements.csvImportIndicator.textContent = 'No se detectaron operaciones válidas';
      elements.csvImportIndicator.classList.remove('has-data');
    }
  };
  
  reader.onerror = function() {
    showToast('Error al leer el archivo', 'error');
    state.csvData = null;
  };
  
  reader.readAsText(file);
});

elements.importCsvBtn.addEventListener('click', () => {
  if (!state.csvData || state.csvData.length === 0) {
    showToast('Selecciona un archivo CSV válido primero', 'error');
    return;
  }
  
  const now = new Date();
  state.csvData.forEach((pnl, i) => {
    state.trades.push({
      id: Date.now() + i,
      date: new Date(now.getTime() + i * 60000).toISOString().slice(0, 16),
      symbol: null,
      direction: pnl >= 0 ? 'long' : 'short',
      pnl: pnl,
      commission: 0,
      notes: 'Importado desde CSV'
    });
  });
  
  const count = state.csvData.length;
  
  elements.csvFileInput.value = '';
  elements.csvFileName.textContent = '';
  elements.csvImportIndicator.textContent = '';
  elements.csvImportIndicator.classList.remove('has-data');
  state.csvData = null;
  
  showToast(`${count} operaciones importadas desde CSV`, 'success');
  updateAll();
});

elements.exportCsvBtn.addEventListener('click', () => {
  if (state.trades.length === 0) {
    showToast('No hay operaciones para exportar', 'warning');
    return;
  }
  
  const header = 'PnL';
  const rows = state.trades.map(t => {
    const net = (t.pnl || 0) - (t.commission || 0);
    return net >= 0 ? '+' + net : String(net);
  });
  
  const csv = [header, ...rows].join('\n');
  const blob = new Blob([csv], { type: 'text/csv' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = `trading-pnl-${new Date().toISOString().slice(0, 10)}.csv`;
  a.click();
  URL.revokeObjectURL(url);
  
  showToast('CSV exportado (solo P&L)', 'success');
});

elements.exportJsonBtn.addEventListener('click', () => {
  if (state.trades.length === 0) {
    showToast('No hay operaciones para exportar', 'warning');
    return;
  }
  
  const data = {
    initialCapital: state.initialCapital,
    currency: state.currency,
    trades: state.trades,
    exportDate: new Date().toISOString()
  };
  
  const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = `trading-journal-${new Date().toISOString().slice(0, 10)}.json`;
  a.click();
  URL.revokeObjectURL(url);
  
  showToast('JSON exportado', 'success');
});

elements.resetBtn.addEventListener('click', () => {
  showModal('Resetear Todo', '¿Estás seguro de que deseas eliminar todas las operaciones? Esta acción no se puede deshacer.', () => {
    state.trades = [];
    state.capitalLocked = false;
    state.csvData = null;
    state.selectedDay = null;
    elements.initialCapital.disabled = false;
    elements.currency.disabled = false;
    elements.setCapitalBtn.textContent = 'Establecer Capital';
    elements.setCapitalBtn.disabled = false;
    elements.csvFileInput.value = '';
    elements.csvFileName.textContent = '';
    elements.csvImportIndicator.textContent = '';
    closeDayDetail();
    showToast('Datos reseteados', 'success');
    updateAll();
  });
});

document.getElementById('modalCancel').addEventListener('click', closeModal);
document.getElementById('modalClose').addEventListener('click', closeModal);
elements.modalOverlay.addEventListener('click', e => {
  if (e.target === elements.modalOverlay) closeModal();
});

elements.filterType.addEventListener('change', updateTable);

document.querySelectorAll('.tab').forEach(tab => {
  tab.addEventListener('click', () => {
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
    tab.classList.add('active');
    document.getElementById(`tab-${tab.dataset.tab}`).classList.add('active');
  });
});

elements.tradesTableBody.addEventListener('click', e => {
  if (e.target.classList.contains('delete')) {
    const idx = parseInt(e.target.dataset.index);
    showModal('Eliminar Operación', `¿Estás seguro de eliminar la operación #${idx + 1}?`, () => {
      state.trades.splice(idx, 1);
      showToast('Operación eliminada', 'success');
      updateAll();
    });
  }
});

// Resize handler
window.addEventListener('resize', () => {
  const metrics = calculateMetrics();
  drawTVChart(metrics);
});

// ========== INITIALIZATION ==========
setDefaultDateTime();
setupTVChartInteraction();
updateAll();
</script>
</body>
</html>
