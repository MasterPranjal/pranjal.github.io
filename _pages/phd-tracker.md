---
layout: page
permalink: /phd-tracker/
title: PhD Journey
nav: true
nav_order: 6
description: Interactive progress tracker for doctoral research
---

<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
.phd-wrapper { max-width: 1200px; margin: 20px auto; padding: 0 20px; }
.phd-nav { background: white; border: 1px solid #dee2e6; border-radius: 8px; padding: 15px; margin-bottom: 30px; }
.phd-nav-container { display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; }
.phd-nav-btn { padding: 12px 20px; border: 2px solid #dee2e6; background: white; cursor: pointer; font-size: 0.9em; border-radius: 6px; transition: all 0.3s; font-family: inherit; }
.phd-nav-btn:hover { background: #f8f9fa; }
.phd-nav-btn.active { background: var(--global-theme-color, #7c4dff); color: white; border-color: var(--global-theme-color, #7c4dff); }
.phd-section { display: none; background: white; padding: 30px; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.05); margin-bottom: 30px; }
.phd-section.active { display: block; animation: fadeIn 0.4s; }
@keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
.form-group { margin-bottom: 20px; }
label { display: block; margin-bottom: 8px; font-weight: 600; color: #495057; }
input, textarea, select { width: 100%; padding: 12px; border: 1px solid #ced4da; border-radius: 4px; font-family: inherit; font-size: 0.95em; }
textarea { min-height: 120px; resize: vertical; }
.btn { padding: 12px 30px; border: none; border-radius: 4px; cursor: pointer; font-size: 1em; transition: all 0.3s; font-weight: 600; }
.btn-primary { background: var(--global-theme-color, #7c4dff); color: white; }
.btn-primary:hover { opacity: 0.9; }
.btn-danger { background: #dc3545; color: white; padding: 8px 15px; font-size: 0.85em; }
.btn-danger:hover { background: #c82333; }
.category-selector { display: flex; gap: 10px; flex-wrap: wrap; }
.category-chip { padding: 8px 20px; border: 2px solid var(--global-theme-color, #7c4dff); border-radius: 20px; cursor: pointer; transition: all 0.3s; background: white; font-size: 0.9em; }
.category-chip.selected { background: var(--global-theme-color, #7c4dff); color: white; }
.tree-item { background: #f8f9fa; padding: 20px; margin: 15px 0; border-radius: 8px; border-left: 4px solid var(--global-theme-color, #7c4dff); }
.tree-item-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; flex-wrap: wrap; gap: 10px; }
.tree-item-title { font-weight: 600; color: #212529; }
.tree-item-date { color: #6c757d; font-size: 0.9em; }
.stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin: 30px 0; }
.stat-card { background: var(--global-theme-color, #7c4dff); color: white; padding: 30px; border-radius: 8px; text-align: center; }
.stat-number { font-size: 3em; font-weight: 700; margin-bottom: 10px; }
.stat-label { font-size: 0.9em; opacity: 0.9; }
.empty-state { text-align: center; padding: 60px; color: #6c757d; }
.view-toggle { display: flex; gap: 10px; margin: 20px 0; }
.view-btn { padding: 10px 20px; border: 2px solid #6c757d; background: white; cursor: pointer; border-radius: 4px; transition: all 0.3s; }
.view-btn.active { background: #6c757d; color: white; }
table { width: 100%; border-collapse: collapse; margin: 20px 0; }
th, td { padding: 12px; text-align: left; border-bottom: 1px solid #dee2e6; }
th { background: #f8f9fa; font-weight: 600; }
tr:hover { background: #f8f9fa; }
.progress-bar-container { background: #e9ecef; border-radius: 10px; height: 20px; margin: 10px 0; overflow: hidden; }
.progress-bar { height: 100%; background: var(--global-theme-color, #7c4dff); transition: width 0.3s; display: flex; align-items: center; justify-content: center; color: white; font-size: 0.85em; font-weight: 600; }
.timeline-item { position: relative; padding: 20px; background: white; border: 2px solid #e9ecef; border-radius: 8px; margin: 20px 0 20px 40px; }
.timeline-item::before { content: ''; position: absolute; left: -40px; top: 50%; transform: translateY(-50%); width: 15px; height: 15px; border-radius: 50%; background: var(--global-theme-color, #7c4dff); border: 3px solid white; box-shadow: 0 0 0 2px var(--global-theme-color, #7c4dff); }
.timeline-item.current::before { background: #e74c3c; box-shadow: 0 0 0 2px #e74c3c; animation: pulse 2s infinite; }
@keyframes pulse { 0%, 100% { transform: translateY(-50%) scale(1); } 50% { transform: translateY(-50%) scale(1.2); } }
.form-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin: 20px 0; }
@media (max-width: 768px) { .phd-nav-container { flex-direction: column; } .stats-grid { grid-template-columns: 1fr; } .form-grid { grid-template-columns: 1fr; } }
</style>

<div class="phd-wrapper">
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
        <p style="margin-bottom: 20px; color: #6c757d;">Document critical decisions shaping your thesis direction</p>
        
        <div class="form-group">
            <label>Date</label>
            <input type="date" id="decision-date">
        </div>
        
        <div class="form-group">
            <label>Decision Context</label>
            <input type="text" id="decision-title" placeholder="What decision did you make?">
        </div>
        
        <div class="form-group">
            <label>Rationale & Implications</label>
            <textarea id="decision-rationale" placeholder="Why? What are the implications for your research?"></textarea>
        </div>
        
        <div class="form-group">
            <label>Related Categories</label>
            <div class="category-selector">
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

    <!-- Work Categories -->
    <div id="categories" class="phd-section">
        <h2>🎯 Work Categories Progress</h2>
        
        <div class="view-toggle">
            <button class="view-btn active" onclick="switchPhdView('tree')">Decision Tree View</button>
            <button class="view-btn" onclick="switchPhdView('table')">Table View</button>
        </div>
        
        <div id="tree-view">
            <h3>Thesis Writing</h3>
            <div id="tree-thesis"></div>
            
            <h3>Field Work</h3>
            <div id="tree-fieldwork"></div>
            
            <h3>Data Analysis</h3>
            <div id="tree-analysis"></div>
            
            <h3>Paper Writing</h3>
            <div id="tree-paper"></div>
            
            <h3>Reading</h3>
            <div id="tree-reading"></div>
        </div>
        
        <div id="table-view" style="display: none;">
            <table>
                <thead>
                    <tr>
                        <th>Date</th>
                        <th>Category</th>
                        <th>Decision</th>
                        <th>Action</th>
                    </tr>
                </thead>
                <tbody id="table-body"></tbody>
            </table>
        </div>
    </div>

    <!-- 90-Day Timeline -->
    <div id="timeline" class="phd-section">
        <h2>📅 90-Day Progress Timeline</h2>
        
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-number" id="days-completed">0</div>
                <div class="stat-label">Days Completed</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="days-remaining">90</div>
                <div class="stat-label">Days Remaining</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="total-weeks">0</div>
                <div class="stat-label">Weeks Logged</div>
            </div>
        </div>
        
        <div class="form-grid">
            <div class="form-group">
                <label>Week Number (1-13)</label>
                <input type="number" id="week-num" min="1" max="13" placeholder="e.g., 1">
            </div>
            <div class="form-group">
                <label>Focus Area</label>
                <input type="text" id="week-focus" placeholder="Main focus this week">
            </div>
        </div>
        
        <div class="form-group">
            <label>Progress Notes</label>
            <textarea id="week-notes" placeholder="What did you accomplish? Challenges? Insights?"></textarea>
        </div>
        
        <button class="btn btn-primary" onclick="savePhdWeekProgress()">Save Week Progress</button>
        <div id="timeline-display" style="margin-top: 30px;"></div>
    </div>

    <!-- Field Work -->
    <div id="fieldwork" class="phd-section">
        <h2>🔬 Field Work Tracker</h2>
        
        <div class="form-grid">
            <div class="form-group">
                <label>Date</label>
                <input type="date" id="field-date">
            </div>
            <div class="form-group">
                <label>Location</label>
                <input type="text" id="field-location" placeholder="Repair café, workshop, etc.">
            </div>
        </div>
        
        <div class="form-group">
            <label>Type of Activity</label>
            <select id="field-type">
                <option>Observation</option>
                <option>Participant Observation</option>
                <option>Interview</option>
                <option>Co-design Session</option>
                <option>Data Collection</option>
                <option>Other</option>
            </select>
        </div>
        
        <div class="form-group">
            <label>Field Notes</label>
            <textarea id="field-notes" placeholder="Detailed observations, interactions, what happened..."></textarea>
        </div>
        
        <div class="form-group">
            <label>Key Insights</label>
            <textarea id="field-insights" placeholder="What tacit knowledge emerged? What surprised you?"></textarea>
        </div>
        
        <button class="btn btn-primary" onclick="savePhdFieldWork()">Save Field Work</button>
        <div id="fieldwork-list" style="margin-top: 30px;"></div>
    </div>

    <!-- Writing Goals -->
    <div id="writing" class="phd-section">
        <h2>✍️ Writing Goals Tracker</h2>
        
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-number" id="thesis-words-total">0</div>
                <div class="stat-label">Thesis Words Written</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="paper-words-total">0</div>
                <div class="stat-label">Paper Words Written</div>
            </div>
        </div>
        
        <h3>Thesis Writing</h3>
        <div class="form-group">
            <label>Daily Goal: 300 words</label>
            <div class="progress-bar-container">
                <div class="progress-bar" id="thesis-progress" style="width: 0%">0%</div>
            </div>
            <input type="number" id="thesis-words-input" placeholder="Words written today">
        </div>
        
        <div class="form-group">
            <label>Chapter/Section</label>
            <input type="text" id="thesis-section" placeholder="e.g., Introduction, Literature Review">
        </div>
        
        <button class="btn btn-primary" onclick="savePhdThesisProgress()">Log Thesis Progress</button>
        
        <h3 style="margin-top: 40px;">Paper Writing</h3>
        <div class="form-group">
            <label>Daily Goal: 400 words</label>
            <div class="progress-bar-container">
                <div class="progress-bar" id="paper-progress" style="width: 0%">0%</div>
            </div>
            <input type="number" id="paper-words-input" placeholder="Words written today">
        </div>
        
        <div class="form-group">
            <label>Paper Name</label>
            <input type="text" id="paper-name" placeholder="e.g., CHI Paper 1, DIS Submission">
        </div>
        
        <button class="btn btn-primary" onclick="savePhdPaperProgress()">Log Paper Progress</button>
        <div id="writing-history" style="margin-top: 30px;"></div>
    </div>

    <!-- Overview -->
    <div id="overview" class="phd-section">
        <h2>📊 Research Overview</h2>
        
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-number" id="total-decisions">0</div>
                <div class="stat-label">Decisions Logged</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="fieldwork-sessions">0</div>
                <div class="stat-label">Field Work Sessions</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="total-words">0</div>
                <div class="stat-label">Total Words Written</div>
            </div>
            <div class="stat-card">
                <div class="stat-number" id="active-categories">0</div>
                <div class="stat-label">Active Categories</div>
            </div>
        </div>
        
        <h3>Export Data</h3>
        <div style="text-align: center; margin: 30px 0;">
            <button class="btn btn-primary" onclick="exportPhdData('json')">Export as JSON</button>
            <button class="btn btn-primary" style="margin-left: 10px;" onclick="exportPhdData('markdown')">Export as Markdown</button>
            <button class="btn btn-danger" style="margin-left: 20px;" onclick="clearPhdData()">Clear All Data</button>
        </div>
    </div>
</div>

<script>
let selectedCategories = [];

document.addEventListener('DOMContentLoaded', function() {
    document.getElementById('decision-date').valueAsDate = new Date();
    document.getElementById('field-date').valueAsDate = new Date();
    loadAllPhdData();
});

function showPhdSection(sectionId) {
    document.querySelectorAll('.phd-section').forEach(s => s.classList.remove('active'));
    document.querySelectorAll('.phd-nav-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(sectionId).classList.add('active');
    event.target.classList.add('active');
    
    if (sectionId === 'categories') renderPhdCategoryViews();
    if (sectionId === 'timeline') renderPhdTimeline();
    if (sectionId === 'fieldwork') renderPhdFieldWork();
    if (sectionId === 'writing') renderPhdWritingHistory();
    if (sectionId === 'overview') updatePhdOverview();
}

function togglePhdCategory(element, category) {
    element.classList.toggle('selected');
    const index = selectedCategories.indexOf(category);
    if (index > -1) selectedCategories.splice(index, 1);
    else selectedCategories.push(category);
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
    
    renderPhdDecisions();
    alert('Decision logged successfully!');
}

function renderPhdDecisions() {
    const decisions = JSON.parse(localStorage.getItem('phd-decisions') || '[]');
    const container = document.getElementById('decisions-list');
    
    if (decisions.length === 0) {
        container.innerHTML = '<div class="empty-state"><p>No decisions logged yet</p></div>';
        return;
    }
    
    container.innerHTML = '<h3>Recent Decisions</h3>' + decisions.slice(0, 10).map(d => `
        <div class="tree-item">
            <div class="tree-item-header">
                <span class="tree-item-title">${d.title}</span>
                <span class="tree-item-date">${new Date(d.date).toLocaleDateString()}</span>
            </div>
            <p>${d.rationale}</p>
            <div style="margin-top: 10px;">
                ${d.categories.map(c => `<span class="category-chip selected" style="pointer-events: none;">${c}</span>`).join('')}
            </div>
            <button class="btn btn-danger" style="margin-top: 10px;" onclick="deletePhdItem('phd-decisions', ${d.id})">Delete</button>
        </div>
    `).join('');
}

function switchPhdView(view) {
    document.querySelectorAll('.view-btn').forEach(b => b.classList.remove('active'));
    event.target.classList.add('active');
    
    if (view === 'tree') {
        document.getElementById('tree-view').style.display = 'block';
        document.getElementById('table-view').style.display = 'none';
    } else {
        document.getElementById('tree-view').style.display = 'none';
        document.getElementById('table-view').style.display = 'block';
    }
}

function renderPhdCategoryViews() {
    const decisions = JSON.parse(localStorage.getItem('phd-decisions') || '[]');
    const categories = ['thesis', 'fieldwork', 'analysis', 'paper', 'reading'];
    
    categories.forEach(cat => {
        const filtered = decisions.filter(d => d.categories.includes(cat));
        const container = document.getElementById(`tree-${cat}`);
        
        if (filtered.length === 0) {
            container.innerHTML = '<p style="color: #6c757d; padding: 15px;">No entries yet</p>';
        } else {
            container.innerHTML = filtered.map(d => `
                <div class="tree-item">
                    <div class="tree-item-header">
                        <span class="tree-item-title">${d.title}</span>
                        <span class="tree-item-date">${new Date(d.date).toLocaleDateString()}</span>
                    </div>
                    <p>${d.rationale}</p>
                </div>
            `).join('');
        }
    });
    
    const tableBody = document.getElementById('table-body');
    if (decisions.length === 0) {
        tableBody.innerHTML = '<tr><td colspan="4" style="text-align: center; color: #6c757d;">No data</td></tr>';
    } else {
        tableBody.innerHTML = decisions.map(d => `
            <tr>
                <td>${new Date(d.date).toLocaleDateString()}</td>
                <td>${d.categories.join(', ')}</td>
                <td>${d.title}</td>
                <td><button class="btn btn-danger" onclick="deletePhdItem('phd-decisions', ${d.id})">Delete</button></td>
            </tr>
        `).join('');
    }
}

function savePhdWeekProgress() {
    const progress = {
        id: Date.now(),
        week: document.getElementById('week-num').value,
        focus: document.getElementById('week-focus').value,
        notes: document.getElementById('week-notes').value,
        date: new Date().toISOString()
    };
    
    if (!progress.week || !progress.focus || !progress.notes) {
        alert('Please fill all fields');
        return;
    }
    
    const timeline = JSON.parse(localStorage.getItem('phd-timeline') || '[]');
    timeline.push(progress);
    localStorage.setItem('phd-timeline', JSON.stringify(timeline));
    
    document.getElementById('week-num').value = '';
    document.getElementById('week-focus').value = '';
    document.getElementById('week-notes').value = '';
    
    renderPhdTimeline();
    alert('Week progress saved!');
}

function renderPhdTimeline() {
    const timeline = JSON.parse(localStorage.getItem('phd-timeline') || '[]').sort((a, b) => a.week - b.week);
    const container = document.getElementById('timeline-display');
    
    document.getElementById('days-completed').textContent = timeline.length * 7;
    document.getElementById('days-remaining').textContent = 90 - (timeline.length * 7);
    document.getElementById('total-weeks').textContent = timeline.length;
    
    if (timeline.length === 0) {
        container.innerHTML = '<div class="empty-state"><p>No timeline entries yet</p></div>';
        return;
    }
    
    const currentWeek = Math.max(...timeline.map(t => parseInt(t.week)));
    
    container.innerHTML = timeline.map(t => `
        <div class="timeline-item ${parseInt(t.week) === currentWeek ? 'current' : ''}">
            <h3>Week ${t.week}: ${t.focus}</h3>
            <p style="color: #6c757d; margin: 10px 0;">${new Date(t.date).toLocaleDateString()}</p>
            <p>${t.notes}</p>
            <button class="btn btn-danger" style="margin-top: 10px;" onclick="deletePhdItem('phd-timeline', ${t.id})">Delete</button>
        </div>
    `).join('');
}

function savePhdFieldWork() {
    const fieldwork = {
        id: Date.now(),
        date: document.getElementById('field-date').value,
        location: document.getElementById('field-location').value,
        type: document.getElementById('field-type').value,
        notes: document.getElementById('field-notes').value,
        insights: document.getElementById('field-insights').value
    };
    
    if (!fieldwork.date || !fieldwork.location || !fieldwork.notes) {
        alert('Please fill required fields');
        return;
    }
    
    const fieldworks = JSON.parse(localStorage.getItem('phd-fieldwork') || '[]');
    fieldworks.unshift(fieldwork);
    localStorage.setItem('phd-fieldwork', JSON.stringify(fieldworks));
    
    document.getElementById('field-location').value = '';
    document.getElementById('field-notes').value = '';
    document.getElementById('field-insights').value = '';
    
    renderPhdFieldWork();
    alert('Field work saved!');
}

function renderPhdFieldWork() {
    const fieldworks = JSON.parse(localStorage.getItem('phd-fieldwork') || '[]');
    const container = document.getElementById('fieldwork-list');
    
    if (fieldworks.length === 0) {
        container.innerHTML = '<div class="empty-state"><p>No field work logged yet</p></div>';
        return;
    }
    
    container.innerHTML = '<h3>Field Work Sessions</h3>' + fieldworks.map(f => `
        <div class="tree-item">
            <div class="tree-item-header">
                <span class="tree-item-title">${f.location} - ${f.type}</span>
                <span class="tree-item-date">${new Date(f.date).toLocaleDateString()}</span>
            </div>
            <p><strong>Notes:</strong> ${f.notes}</p>
            ${f.insights ? `<p><strong>Insights:</strong> ${f.insights}</p>` : ''}
            <button class="btn btn-danger" style="margin-top: 10px;" onclick="deletePhdItem('phd-fieldwork', ${f.id})">Delete</button>
        </div>
    `).join('');
}

function savePhdThesisProgress() {
    const words = parseInt(document.getElementById('thesis-words-input').value);
    const section = document.getElementById('thesis-section').value;
    
    if (!words || !section) {
        alert('Please fill all fields');
        return;
    }
    
    const progress = {
        id: Date.now(),
        type: 'thesis',
        words: words,
        section: section,
        date: new Date().toISOString()
    };
    
    const writing = JSON.parse(localStorage.getItem('phd-writing') || '[]');
    writing.unshift(progress);
    localStorage.setItem('phd-writing', JSON.stringify(writing));
    
    document.getElementById('thesis-words-input').value = '';
    document.getElementById('thesis-section').value = '';
    
    updatePhdWritingStats();
    renderPhdWritingHistory();
    alert('Thesis progress logged!');
}

function savePhdPaperProgress() {
    const words = parseInt(document.getElementById('paper-words-input').value);
    const paper = document.getElementById('paper-name').value;
    
    if (!words || !paper) {
        alert('Please fill all fields');
        return;
    }
    
    const progress = {
        id: Date.now(),
        type: 'paper',
        words: words,
        paper: paper,
        date: new Date().toISOString()
    };
    
    const writing = JSON.parse(localStorage.getItem('phd-writing') || '[]');
    writing.unshift(progress);
    localStorage.setItem('phd-writing', JSON.stringify(writing));
    
    document.getElementById('paper-words-input').value = '';
    document.getElementById('paper-name').value = '';
    
    updatePhdWritingStats();
    renderPhdWritingHistory();
    alert('Paper progress logged!');
}

function updatePhdWritingStats() {
    const writing = JSON.parse(localStorage.getItem('phd-writing') || '[]');
    const today = new Date().toDateString();
    
    const thesisToday = writing
        .filter(w => w.type === 'thesis' && new Date(w.date).toDateString() === today)
        .reduce((sum, w) => sum + w.words, 0);
    
    const paperToday = writing
        .filter(w => w.type === 'paper' && new Date(w.date).toDateString() === today)
        .reduce((sum, w) => sum + w.words, 0);
    
    const thesisTotal = writing
        .filter(w => w.type === 'thesis')
        .reduce((sum, w) => sum + w.words, 0);
    
    const paperTotal = writing
        .filter(w => w.type === 'paper')
        .reduce((sum, w) => sum + w.words, 0);
    
    document.getElementById('thesis-words-total').textContent = thesisTotal;
    document.getElementById('paper-words-total').textContent = paperTotal;
    
    const thesisPercent = Math.min((thesisToday / 300) * 100, 100);
    const paperPercent = Math.min((paperToday / 400) * 100, 100);
    
    document.getElementById('thesis-progress').style.width = thesisPercent + '%';
    document.getElementById('thesis-progress').textContent = Math.round(thesisPercent) + '%';
    
    document.getElementById('paper-progress').style.width = paperPercent + '%';
    document.getElementById('paper-progress').textContent = Math.round(paperPercent) + '%';
}

function renderPhdWritingHistory() {
    const writing = JSON.parse(localStorage.getItem('phd-writing') || '[]');
    const container = document.getElementById('writing-history');
    
    if (writing.length === 0) {
        container.innerHTML = '';
        return;
    }
    
    container.innerHTML = '<h3 style="margin-top: 40px;">Recent Writing Sessions</h3>' + writing.slice(0, 10).map(w => `
        <div class="tree-item">
            <div class="tree-item-header">
                <span class="tree-item-title">${w.type === 'thesis' ? w.section : w.paper}</span>
                <span class="tree-item-date">${new Date(w.date).toLocaleDateString()}</span>
            </div>
            <p>${w.words} words written</p>
            <button class="btn btn-danger" style="margin-top: 10px;" onclick="deletePhdItem('phd-writing', ${w.id})">Delete</button>
        </div>
    `).join('');
}

function updatePhdOverview() {
    const decisions = JSON.parse(localStorage.getItem('phd-decisions') || '[]');
    const fieldwork = JSON.parse(localStorage.getItem('phd-fieldwork') || '[]');
    const writing = JSON.parse(localStorage.getItem('phd-writing') || '[]');
    
    const totalWords = writing.reduce((sum, w) => sum + w.words, 0);
    const activeCategories = new Set();
    decisions.forEach(d => d.categories.forEach(c => activeCategories.add(c)));
    
    document.getElementById('total-decisions').textContent = decisions.length;
    document.getElementById('fieldwork-sessions').textContent = fieldwork.length;
    document.getElementById('total-words').textContent = totalWords;
    document.getElementById('active-categories').textContent = activeCategories.size;
}

function deletePhdItem(storageKey, id) {
    if (!confirm('Delete this entry?')) return;
    
    const items = JSON.parse(localStorage.getItem(storageKey) || '[]');
    const filtered = items.filter(i => i.id !== id);
    localStorage.setItem(storageKey, JSON.stringify(filtered));
    
    loadAllPhdData();
}

function loadAllPhdData() {
    renderPhdDecisions();
    renderPhdCategoryViews();
    renderPhdTimeline();
    renderPhdFieldWork();
    updatePhdWritingStats();
    renderPhdWritingHistory();
    updatePhdOverview();
}

function exportPhdData(format) {
    const allData = {
        decisions: JSON.parse(localStorage.getItem('phd-decisions') || '[]'),
        timeline: JSON.parse(localStorage.getItem('phd-timeline') || '[]'),
        fieldwork: JSON.parse(localStorage.getItem('phd-fieldwork') || '[]'),
        writing: JSON.parse(localStorage.getItem('phd-writing') || '[]')
    };
    
    let content, filename, type;
    
    if (format === 'json') {
        content = JSON.stringify(allData, null, 2);
        filename = 'phd-progress-complete.json';
        type = 'application/json';
    } else {
        content = '# PhD Progress - Pranjal Jain\n\n';
        content += `Generated on ${new Date().toLocaleDateString()}\n\n---\n\n`;
        
        content += `## Decisions (${allData.decisions.length})\n\n`;
        allData.decisions.forEach(d => {
            content += `### ${d.title}\n`;
            content += `**Date:** ${d.date} | **Categories:** ${d.categories.join(', ')}\n\n`;
            content += `${d.rationale}\n\n---\n\n`;
        });
        
        content += `## Field Work (${allData.fieldwork.length})\n\n`;
        allData.fieldwork.forEach(f => {
            content += `### ${f.location} - ${f.type}\n`;
            content += `**Date:** ${f.date}\n\n`;
            content += `${f.notes}\n\n`;
            if (f.insights) content += `**Insights:** ${f.insights}\n\n`;
            content += `---\n\n`;
        });
        
        filename = 'phd-progress-complete.md';
        type = 'text/markdown';
    }
    
    const blob = new Blob([content], { type });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = filename;
    a.click();
    URL.revokeObjectURL(url);
}

function clearPhdData() {
    if (!confirm('Delete ALL data? This cannot be undone!')) return;
    
    localStorage.removeItem('phd-decisions');
    localStorage.removeItem('phd-timeline');
    localStorage.removeItem('phd-fieldwork');
    localStorage.removeItem('phd-writing');
    loadAllPhdData();
    alert('All data cleared');
}
</script>
