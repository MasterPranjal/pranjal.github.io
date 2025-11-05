---
layout: page
permalink: /phd-tracker/
title: PhD Journey
description: Documenting my doctoral research progress
nav: true
nav_order: 5
---

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.phd-container {
    max-width: 1200px;
    margin: 40px auto;
    padding: 0 20px;
}

.phd-section {
    display: none;
    background: white;
    padding: 40px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.05);
    margin-bottom: 30px;
}

.phd-section.active {
    display: block;
    animation: fadeIn 0.4s;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

.phd-nav {
    background: white;
    border: 1px solid #dee2e6;
    border-radius: 8px;
    padding: 10px;
    margin-bottom: 30px;
}

.phd-nav-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
}

.phd-nav-btn {
    padding: 12px 20px;
    border: 2px solid transparent;
    background: #f8f9fa;
    cursor: pointer;
    font-size: 0.95em;
    border-radius: 6px;
    transition: all 0.3s;
}

.phd-nav-btn:hover {
    background: #e9ecef;
}

.phd-nav-btn.active {
    border-color: var(--global-theme-color);
    background: var(--global-theme-color);
    color: white;
}

.form-group {
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 8px;
    font-weight: 600;
}

input, textarea, select {
    width: 100%;
    padding: 12px;
    border: 1px solid #ced4da;
    border-radius: 4px;
    font-family: inherit;
    font-size: 0.95em;
}

textarea {
    min-height: 120px;
    resize: vertical;
}

.btn {
    padding: 12px 30px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1em;
    transition: all 0.3s;
    font-weight: 600;
}

.btn-primary {
    background: var(--global-theme-color);
    color: white;
}

.btn-primary:hover {
    opacity: 0.9;
}

.category-chip {
    display: inline-block;
    padding: 8px 20px;
    border: 2px solid var(--global-theme-color);
    border-radius: 20px;
    cursor: pointer;
    transition: all 0.3s;
    background: white;
    margin: 5px;
}

.category-chip.selected {
    background: var(--global-theme-color);
    color: white;
}

.tree-item {
    background: white;
    padding: 15px;
    margin: 10px 0;
    border-radius: 4px;
    border-left: 4px solid var(--global-theme-color);
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

.tree-item-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
}

.empty-state {
    text-align: center;
    padding: 60px;
    color: #6c757d;
}

.stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin: 30px 0;
}

.stat-card {
    background: var(--global-theme-color);
    color: white;
    padding: 30px;
    border-radius: 8px;
    text-align: center;
}

.stat-number {
    font-size: 3em;
    font-weight: 700;
    margin-bottom: 10px;
}

@media (max-width: 768px) {
    .phd-nav-container {
        flex-direction: column;
    }
    .stats-grid {
        grid-template-columns: 1fr;
    }
}
</style>

<div class="phd-container">
    <div class="phd-nav">
        <div class="phd-nav-container">
            <button class="phd-nav-btn active" onclick="showPhdSection('decisions')">Decision Log</button>
            <button class="phd-nav-btn" onclick="showPhdSection('categories')">Work Categories</button>
            <button class="phd-nav-btn" onclick="showPhdSection('timeline')">90-Day Timeline</button>
            <button class="phd-nav-btn" onclick="showPhdSection('fieldwork')">Field Work</button>
            <button class="phd-nav-btn" onclick="showPhdSection('writing')">Writing Goals</button>
            <button class="phd-nav-btn" onclick="showPhdSection('overview')">Overview</button>
        </div>
    </div>

    <!-- Decision Log -->
    <div id="decisions" class="phd-section active">
        <h2>📝 Daily Decision Log</h2>
        <p style="margin-bottom: 20px; color: #6c757d;">Document critical decisions shaping your thesis</p>
        
        <div class="form-group">
            <label>Date</label>
            <input type="date" id="decision-date" />
        </div>
        
        <div class="form-group">
            <label>Decision Context</label>
            <input type="text" id="decision-title" placeholder="What decision did you make?" />
        </div>
        
        <div class="form-group">
            <label>Rationale & Implications</label>
            <textarea id="decision-rationale" placeholder="Why? What are the implications?"></textarea>
        </div>
        
        <div class="form-group">
            <label>Categories</label>
            <div id="category-selector">
                <span class="category-chip" onclick="togglePhdCategory(this, 'thesis')">Thesis Writing</span>
                <span class="category-chip" onclick="togglePhdCategory(this, 'fieldwork')">Field Work</span>
                <span class="category-chip" onclick="togglePhdCategory(this, 'analysis')">Data Analysis</span>
                <span class="category-chip" onclick="togglePhdCategory(this, 'paper')">Paper Writing</span>
                <span class="category-chip" onclick="togglePhdCategory(this, 'reading')">Reading</span>
            </div>
        </div>
        
        <button class="btn btn-primary" onclick="savePhdDecision()">Log Decision</button>
        <div id="decisions-list" style="margin-top: 30px;"></div>
    </div>

    <!-- Other sections... -->
    <div id="categories" class="phd-section">
        <h2>Work Categories Progress</h2>
        <div id="categories-content"></div>
    </div>

    <div id="timeline" class="phd-section">
        <h2>90-Day Timeline</h2>
        <div id="timeline-content"></div>
    </div>

    <div id="fieldwork" class="phd-section">
        <h2>Field Work Tracker</h2>
        <div id="fieldwork-content"></div>
    </div>

    <div id="writing" class="phd-section">
        <h2>Writing Goals</h2>
        <div id="writing-content"></div>
    </div>

    <div id="overview" class="phd-section">
        <h2>Overview</h2>
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-number" id="total-decisions">0</div>
                <div class="stat-label">Decisions Logged</div>
            </div>
        </div>
    </div>
</div>

<script>
let selectedCategories = [];

document.addEventListener('DOMContentLoaded', function() {
    document.getElementById('decision-date').valueAsDate = new Date();
    loadPhdData();
});

function showPhdSection(sectionId) {
    document.querySelectorAll('.phd-section').forEach(s => s.classList.remove('active'));
    document.querySelectorAll('.phd-nav-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(sectionId).classList.add('active');
    event.target.classList.add('active');
}

function togglePhdCategory(element, category) {
    element.classList.toggle('selected');
    const index = selectedCategories.indexOf(category);
    if (index > -1) {
        selectedCategories.splice(index, 1);
    } else {
        selectedCategories.push(category);
    }
}

function savePhdDecision() {
    const decision = {
        id: Date.now(),
        date: document.getElementById('decision-date').value,
        title: document.getElementById('decision-title').value,
        rationale: document.getElementById('decision-rationale').value,
        categories: [...selectedCategories],
        timestamp: new Date().toISOString()
    };
    
    if (!decision.date || !decision.title || !decision.rationale) {
        alert('Please fill all fields');
        return;
    }
    
    const decisions = JSON.parse(localStorage.getItem('phd-decisions') || '[]');
    decisions.unshift(decision);
    localStorage.setItem('phd-decisions', JSON.stringify(decisions));
    
    document.getElementById('decision-title').value = '';
    document.getElementById('decision-rationale').value = '';
    selectedCategories = [];
    document.querySelectorAll('.category-chip').forEach(c => c.classList.remove('selected'));
    
    loadPhdData();
    alert('Decision logged!');
}

function loadPhdData() {
    const decisions = JSON.parse(localStorage.getItem('phd-decisions') || '[]');
    const container = document.getElementById('decisions-list');
    
    if (decisions.length === 0) {
        container.innerHTML = '<div class="empty-state"><p>No decisions yet</p></div>';
        return;
    }
    
    container.innerHTML = '<h3>Recent Decisions</h3>' + decisions.slice(0, 10).map(d => `
        <div class="tree-item">
            <div class="tree-item-header">
                <strong>${d.title}</strong>
                <span>${new Date(d.date).toLocaleDateString()}</span>
            </div>
            <p>${d.rationale}</p>
            <div style="margin-top: 10px;">
                ${d.categories.map(c => `<span class="category-chip selected">${c}</span>`).join('')}
            </div>
        </div>
    `).join('');
    
    document.getElementById('total-decisions').textContent = decisions.length;
}
</script>
