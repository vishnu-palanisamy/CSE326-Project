<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>PlayLeague — Sports League Management</title>

  <!-- Google Font: Plus Jakarta Sans -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">

  <style>
    /* 1. Global Reset & Styles */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, sans-serif;
      background-color: #f8fafc;
      color: #0f172a;
      line-height: 1.5;
      -webkit-font-smoothing: antialiased;
    }

    /* 2. Professional Top Navigation */
    header {
      background-color: #0f172a;
      border-bottom: 1px solid #1e293b;
      padding: 14px 28px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 10px;
      color: #ffffff;
      font-size: 18px;
      font-weight: 700;
      letter-spacing: -0.3px;
    }

    .brand-badge {
      background: linear-gradient(135deg, #6366f1, #3b82f6);
      color: #ffffff;
      font-size: 11px;
      font-weight: 800;
      letter-spacing: 0.5px;
      padding: 5px 8px;
      border-radius: 6px;
    }

    nav {
      display: flex;
      gap: 6px;
      flex: 1;
      margin-left: 24px;
    }

    .nav-btn {
      background: transparent;
      border: none;
      color: #94a3b8;
      padding: 8px 16px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 13px;
      font-weight: 600;
      font-family: inherit;
      transition: all 0.15s ease;
    }

    .nav-btn:hover {
      color: #ffffff;
      background-color: #1e293b;
    }

    .nav-btn.active {
      background-color: #4f46e5;
      color: #ffffff;
    }

    .sport-group-head {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 14px;
    }

    .sport-group-head .card-title {
      margin-bottom: 0;
    }

    .sport-count {
      font-size: 12px;
      font-weight: 600;
      color: #64748b;
    }

    .team-subgroup {
      margin-top: 18px;
      padding-top: 16px;
      border-top: 1px dashed #e2e8f0;
    }

    .team-subgroup:first-of-type {
      margin-top: 0;
      padding-top: 0;
      border-top: none;
    }

    .team-subhead {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      cursor: pointer;
      list-style: none;
      padding: 10px 12px;
      border: 1px solid #e2e8f0;
      border-radius: 8px;
      background-color: #f8fafc;
      user-select: none;
    }

    .team-subhead::-webkit-details-marker {
      display: none;
    }

    .team-subhead:hover {
      background-color: #f1f5f9;
    }

    .team-subhead-left {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .chevron {
      display: inline-block;
      width: 8px;
      height: 8px;
      border-right: 2px solid #64748b;
      border-bottom: 2px solid #64748b;
      transform: rotate(-45deg);
      transition: transform 0.15s ease;
      margin-right: 2px;
    }

    details[open] > .team-subhead .chevron {
      transform: rotate(45deg);
    }

    details[open] > .team-subhead {
      margin-bottom: 10px;
    }

    .team-subhead-name {
      font-size: 14px;
      font-weight: 700;
      color: #0f172a;
    }

    .date-filter {
      display: flex;
      align-items: center;
      gap: 6px;
      flex-wrap: wrap;
    }

    .date-filter input[type="date"] {
      padding: 7px 10px;
      border: 1px solid #e2e8f0;
      border-radius: 8px;
      font-family: inherit;
      font-size: 13px;
      color: #0f172a;
      background-color: #ffffff;
    }

    .btn-day {
      background-color: #ffffff;
      border: 1px solid #e2e8f0;
      border-radius: 8px;
      padding: 6px 11px;
      font-family: inherit;
      font-size: 14px;
      font-weight: 700;
      color: #475569;
      cursor: pointer;
    }

    .btn-day:hover { background-color: #f1f5f9; }
    .btn-today { font-size: 12px; color: #4f46e5; }

    /* Points table */
    .points-table th.num,
    .points-table td.num {
      text-align: center;
      white-space: nowrap;
    }

    .points-table .pos {
      width: 44px;
      text-align: center;
      font-weight: 700;
      color: #64748b;
    }

    .points-table .pts {
      font-weight: 800;
      color: #0f172a;
    }

    .points-table tr.leader td {
      background-color: #f0fdf4;
    }

    .points-table tr.leader .pos {
      color: #047857;
    }

    .vs-cell {
      display: flex;
      align-items: center;
      gap: 10px;
      flex-wrap: wrap;
    }

    .vs-cell .vs {
      font-size: 11px;
      font-weight: 800;
      color: #94a3b8;
      letter-spacing: 0.5px;
      text-transform: uppercase;
    }

    .side-tag {
      display: inline-block;
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 0.4px;
      text-transform: uppercase;
      padding: 2px 7px;
      border-radius: 999px;
      margin-left: 8px;
      vertical-align: middle;
    }

    .side-home { background-color: #eef2ff; color: #3730a3; }
    .side-away { background-color: #f1f5f9; color: #475569; }

    .team-subhead-right {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .empty-row td {
      color: #94a3b8;
      font-size: 13px;
      text-align: center;
      padding: 18px;
    }

    /* View Switcher (Organiser / Player) */
    .header-right {
      margin-left: auto;
      display: flex;
      align-items: center;
      gap: 14px;
      flex-wrap: wrap;
    }

    .view-switch {
      display: flex;
      background-color: #1e293b;
      border-radius: 8px;
      padding: 3px;
      gap: 2px;
    }

    .view-btn {
      background: transparent;
      border: none;
      color: #94a3b8;
      padding: 6px 12px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 12px;
      font-weight: 700;
      font-family: inherit;
      transition: all 0.15s ease;
    }

    .view-btn:hover {
      color: #ffffff;
    }

    .view-btn.active {
      background-color: #ffffff;
      color: #0f172a;
    }

    .readonly-badge {
      display: none;
      background-color: #fef3c7;
      color: #92400e;
      font-size: 11px;
      font-weight: 700;
      padding: 4px 10px;
      border-radius: 999px;
    }

    /* Player view = read-only: hide everything that edits data */
    body.player-view .org-only {
      display: none !important;
    }

    body.player-view .readonly-badge {
      display: inline-block;
    }

    /* 3. Container */
    .container {
      max-width: 1040px;
      margin: 28px auto;
      padding: 0 20px;
    }

    .tab-content {
      display: none;
    }

    .tab-content.active {
      display: block;
    }

    .page-title {
      font-size: 24px;
      font-weight: 800;
      color: #0f172a;
      letter-spacing: -0.5px;
      margin-bottom: 4px;
    }

    .subtitle {
      color: #64748b;
      font-size: 14px;
      margin-bottom: 24px;
    }

    /* 4. Professional Hero Stadium Banner */
    .hero-banner {
      position: relative;
      border-radius: 12px;
      overflow: hidden;
      background: url('https://images.unsplash.com/photo-1508098682722-e99c43a406b2?auto=format&fit=crop&w=1200&q=80') center/cover no-repeat;
      min-height: 190px;
      display: flex;
      align-items: center;
      padding: 30px;
      margin-bottom: 24px;
      color: #ffffff;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
    }

    .hero-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(90deg, rgba(15, 23, 42, 0.92) 0%, rgba(15, 23, 42, 0.45) 100%);
    }

    .hero-content {
      position: relative;
      z-index: 1;
      max-width: 580px;
    }

    .hero-tag {
      display: inline-block;
      background: #4f46e5;
      color: #ffffff;
      font-size: 11px;
      font-weight: 700;
      padding: 4px 10px;
      border-radius: 20px;
      text-transform: uppercase;
      letter-spacing: 0.8px;
      margin-bottom: 10px;
    }

    .hero-content h2 {
      font-size: 22px;
      font-weight: 800;
      margin-bottom: 6px;
      letter-spacing: -0.3px;
    }

    .hero-content p {
      font-size: 13px;
      color: #cbd5e1;
      line-height: 1.5;
    }

    /* 5. Sports Category Cards */
    .sports-gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
      gap: 16px;
      margin-bottom: 24px;
    }

    .sport-card {
      position: relative;
      height: 110px;
      border-radius: 10px;
      overflow: hidden;
      display: flex;
      align-items: flex-end;
      padding: 14px;
      text-decoration: none;
      color: #ffffff;
      background-size: cover;
      background-position: center;
      box-shadow: 0 2px 6px rgba(0,0,0,0.06);
    }

    .sport-card::after {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, rgba(15, 23, 42, 0.85) 0%, rgba(15, 23, 42, 0.15) 100%);
    }

    .cricket-card {
      background-size: cover;
      background-position: center 60%;
    }

    .sport-card span {
      position: relative;
      z-index: 1;
      font-weight: 700;
      font-size: 15px;
      letter-spacing: -0.2px;
    }

    /* 6. Metric Cards */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 16px;
      margin-bottom: 24px;
    }

    .stat-card {
      background: #ffffff;
      border: 1px solid #e2e8f0;
      border-radius: 12px;
      padding: 20px;
      box-shadow: 0 1px 3px rgba(15, 23, 42, 0.04);
      position: relative;
      overflow: hidden;
    }

    .stat-card::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 3px;
    }

    .stat-teams::before { background-color: #6366f1; }
    .stat-players::before { background-color: #10b981; }
    .stat-matches::before { background-color: #f59e0b; }

    .stat-label {
      font-size: 11px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.8px;
      color: #64748b;
      margin-bottom: 8px;
    }

    .stat-number {
      font-size: 32px;
      font-weight: 800;
      letter-spacing: -1px;
    }

    .stat-teams .stat-number { color: #4338ca; }
    .stat-players .stat-number { color: #047857; }
    .stat-matches .stat-number { color: #b45309; }

    /* 7. Surface Cards & Tables */
    .card {
      background: #ffffff;
      border: 1px solid #e2e8f0;
      border-radius: 12px;
      padding: 24px;
      margin-bottom: 24px;
      box-shadow: 0 1px 3px rgba(15, 23, 42, 0.04);
    }

    .card-title {
      font-size: 16px;
      font-weight: 700;
      color: #0f172a;
      letter-spacing: -0.3px;
      margin-bottom: 16px;
    }

    .table-container {
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
    }

    th {
      background-color: #f8fafc;
      color: #475569;
      font-size: 11px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.6px;
      padding: 12px 16px;
      border-bottom: 1px solid #e2e8f0;
    }

    td {
      padding: 14px 16px;
      border-bottom: 1px solid #f1f5f9;
      font-size: 13px;
      color: #334155;
    }

    tr:last-child td {
      border-bottom: none;
    }

    tr:hover td {
      background-color: #f8fafc;
    }

    /* 8. Entity Photo Cells */
    .item-cell {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    /* 9. Forms & Inputs */
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 16px;
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    label {
      font-size: 12px;
      font-weight: 600;
      color: #334155;
    }

    input, select {
      font-family: inherit;
      padding: 9px 12px;
      border: 1px solid #cbd5e1;
      border-radius: 8px;
      font-size: 14px;
      color: #0f172a;
      background-color: #ffffff;
      transition: all 0.15s ease;
    }

    input:focus, select:focus {
      outline: none;
      border-color: #6366f1;
      box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.15);
    }

    /* 10. Buttons */
    .btn {
      font-family: inherit;
      padding: 9px 16px;
      border: none;
      border-radius: 8px;
      font-size: 13px;
      font-weight: 600;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      transition: all 0.15s ease;
    }

    .btn-primary {
      background-color: #4f46e5;
      color: #ffffff;
    }

    .btn-primary:hover {
      background-color: #4338ca;
    }

    .btn-delete {
      background-color: #fef2f2;
      color: #dc2626;
      border: 1px solid #fecaca;
      padding: 5px 10px;
      font-size: 12px;
      font-weight: 600;
      border-radius: 6px;
    }

    .btn-delete:hover {
      background-color: #dc2626;
      color: #ffffff;
      border-color: #dc2626;
    }

    /* 11. Indicator Badges */
    .badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 3px 9px;
      border-radius: 12px;
      font-size: 12px;
      font-weight: 600;
    }

    .dot {
      width: 6px;
      height: 6px;
      border-radius: 50%;
    }

    .badge-football { background-color: #ecfdf5; color: #065f46; border: 1px solid #a7f3d0; }
    .badge-football .dot { background-color: #10b981; }

    .badge-basketball { background-color: #fff7ed; color: #9a3412; border: 1px solid #fed7aa; }
    .badge-basketball .dot { background-color: #f97316; }

    .badge-cricket { background-color: #eff6ff; color: #1e40af; border: 1px solid #bfdbfe; }
    .badge-cricket .dot { background-color: #3b82f6; }

    .badge-badminton { background-color: #fdf4ff; color: #86198f; border: 1px solid #f5d0fe; }
    .badge-badminton .dot { background-color: #d946ef; }

    .badge-default { background-color: #f1f5f9; color: #475569; border: 1px solid #e2e8f0; }
    .badge-default .dot { background-color: #64748b; }

    .status-completed { background-color: #ecfdf5; color: #047857; border: 1px solid #a7f3d0; }
    .status-completed .dot { background-color: #10b981; }

    .status-pending { background-color: #fffbeb; color: #b45309; border: 1px solid #fde68a; }
    .status-pending .dot { background-color: #f59e0b; }
  </style>
</head>
<body>

  <!-- Top Navigation Bar -->
  <header>
    <div class="brand">
      <span class="brand-badge">PL</span>
      <span>PlayLeague</span>
    </div>
    <nav>
      <button class="nav-btn active" id="btn-dashboard" onclick="showTab('dashboard')">Dashboard</button>
      <button class="nav-btn" id="btn-teams" onclick="showTab('teams')">Teams</button>
      <button class="nav-btn" id="btn-players" onclick="showTab('players')">Players</button>
      <button class="nav-btn" id="btn-matches" onclick="showTab('matches')">Matches</button>
      <button class="nav-btn" id="btn-points" onclick="showTab('points')">Points Table</button>
    </nav>
    <div class="header-right">
      <span class="readonly-badge">Read-only</span>
      <div class="view-switch" role="group" aria-label="Switch view">
        <button class="view-btn active" id="view-organiser" onclick="setView('organiser')">Organiser View</button>
        <button class="view-btn" id="view-player" onclick="setView('player')">Player View</button>
      </div>
    </div>
  </header>

  <div class="container">

    <!-- 1. DASHBOARD TAB -->
    <section id="dashboard" class="tab-content active">

      <!-- Stadium Hero Banner -->
      <div class="hero-banner">
        <div class="hero-overlay"></div>
        <div class="hero-content">
          <span class="hero-tag">Season 2026 Championship</span>
          <h2>Professional League Operations</h2>
          <p>Real-time tournament tracking, team schedules, and athlete directory management all in one place.</p>
        </div>
      </div>

      <!-- Sports Category Visual Cards -->
      <div class="sports-gallery">
        <div class="sport-card" style="background-image: url('https://images.unsplash.com/photo-1579952363873-27f3bade9f55?auto=format&fit=crop&w=500&q=80');">
          <span>Football Division</span>
        </div>
        <div class="sport-card" style="background-image: url('https://images.unsplash.com/photo-1546519638-68e109498ffc?auto=format&fit=crop&w=500&q=80');">
          <span>Basketball League</span>
        </div>
        <div class="sport-card cricket-card" style="background-image: url('data:image/jpeg;base64,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');">
          <span>Cricket Series</span>
        </div>
        <div class="sport-card" style="background-image: url('https://images.unsplash.com/photo-1626224583764-f87db24ac4ea?auto=format&fit=crop&w=500&q=80');">
          <span>Badminton Open</span>
        </div>
      </div>

      <!-- Live Counters -->
      <div class="stats-grid">
        <div class="stat-card stat-teams">
          <div class="stat-label">Total Teams</div>
          <div class="stat-number" id="stat-teams">0</div>
        </div>
        <div class="stat-card stat-players">
          <div class="stat-label">Active Players</div>
          <div class="stat-number" id="stat-players">0</div>
        </div>
        <div class="stat-card stat-matches">
          <div class="stat-label">Recorded Matches</div>
          <div class="stat-number" id="stat-matches">0</div>
        </div>
      </div>

      <!-- Recent Fixtures Table -->
      <div class="card">
        <div class="sport-group-head">
          <div class="card-title">Fixtures</div>
          <div class="date-filter">
            <button type="button" class="btn-day" onclick="shiftDashboardDate(-1)" title="Previous day">&#8249;</button>
            <input type="date" id="dashboard-date" onchange="setDashboardDate(this.value)" />
            <button type="button" class="btn-day" onclick="shiftDashboardDate(1)" title="Next day">&#8250;</button>
            <button type="button" class="btn-day btn-today" onclick="setDashboardDate(todayString())">Today</button>
          </div>
        </div>
        <div class="table-container">
          <table>
            <thead>
              <tr>
                <th>Sport</th>
                <th>Home Team</th>
                <th>Away Team</th>
                <th>Date</th>
                <th>Status / Result</th>
              </tr>
            </thead>
            <tbody id="dashboard-matches-body">
              <!-- Populated by JS -->
            </tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- 2. TEAMS TAB -->
    <section id="teams" class="tab-content">
      <h1 class="page-title">Teams Management</h1>
      <p class="subtitle" data-org="Register team profiles and track squad captains." data-player="Browse team profiles and squad captains.">Register team profiles and track squad captains.</p>

      <!-- Add Team Form -->
      <div class="card org-only">
        <div class="card-title">Register New Team</div>
        <form id="team-form" onsubmit="addTeam(event)">
          <div class="form-grid">
            <div class="form-group">
              <label>Team Name</label>
              <input type="text" id="team-name" placeholder="e.g. River Hawks" required />
            </div>
            <div class="form-group">
              <label>Sport</label>
              <select id="team-sport">
                <option value="Football">Football</option>
                <option value="Basketball">Basketball</option>
                <option value="Cricket">Cricket</option>
                <option value="Badminton">Badminton</option>
              </select>
            </div>
            <div class="form-group">
              <label>Team Captain</label>
              <input type="text" id="team-captain" placeholder="Captain name" required />
            </div>
            <div class="form-group">
              <label>Roster Size</label>
              <input type="number" id="team-players" value="11" min="1" required />
            </div>
          </div>
          <div style="margin-top: 18px;">
            <button type="submit" class="btn btn-primary">Save Team</button>
          </div>
        </form>
      </div>

      <!-- Teams grouped by sport (populated by JS) -->
      <div id="teams-groups"></div>
    </section>

    <!-- 3. PLAYERS TAB -->
    <section id="players" class="tab-content">
      <h1 class="page-title">Player Directory</h1>
      <p class="subtitle" data-org="Maintain active player profiles." data-player="Browse the player directory.">Maintain active player profiles.</p>

      <!-- Add Player Form -->
      <div class="card org-only">
        <div class="card-title">Register New Player</div>
        <form id="player-form" onsubmit="addPlayer(event)">
          <div class="form-grid">
            <div class="form-group">
              <label>Full Name</label>
              <input type="text" id="player-name" placeholder="Player name" required />
            </div>
            <div class="form-group">
              <label>Assigned Team</label>
              <input type="text" id="player-team" placeholder="Team name" required />
            </div>
            <div class="form-group">
              <label>Sport</label>
              <select id="player-sport">
                <option value="Football">Football</option>
                <option value="Basketball">Basketball</option>
                <option value="Cricket">Cricket</option>
                <option value="Badminton">Badminton</option>
              </select>
            </div>
            <div class="form-group">
              <label>Email Address</label>
              <input type="email" id="player-email" placeholder="name@domain.com" required />
            </div>
          </div>
          <div style="margin-top: 18px;">
            <button type="submit" class="btn btn-primary">Save Player</button>
          </div>
        </form>
      </div>

      <!-- Players grouped by sport, then by team (populated by JS) -->
      <div id="players-groups"></div>
    </section>

    <!-- 4. MATCHES TAB -->
    <section id="matches" class="tab-content">
      <h1 class="page-title">Match Schedules</h1>
      <p class="subtitle" data-org="Coordinate fixtures and record final results." data-player="View fixtures and final results.">Coordinate fixtures and record final results.</p>

      <!-- Schedule Match Form -->
      <div class="card org-only">
        <div class="card-title">Schedule New Fixture</div>
        <form id="match-form" onsubmit="addMatch(event)">
          <div class="form-grid">
            <div class="form-group">
              <label>Sport</label>
              <select id="match-sport">
                <option value="Football">Football</option>
                <option value="Basketball">Basketball</option>
                <option value="Cricket">Cricket</option>
                <option value="Badminton">Badminton</option>
              </select>
            </div>
            <div class="form-group">
              <label>Home Team</label>
              <input type="text" id="match-home" placeholder="Home team" required />
            </div>
            <div class="form-group">
              <label>Away Team</label>
              <input type="text" id="match-away" placeholder="Away team" required />
            </div>
            <div class="form-group">
              <label>Match Date</label>
              <input type="date" id="match-date" required />
            </div>
            <div class="form-group">
              <label>Score or Status</label>
              <input type="text" id="match-score" value="Pending" required />
            </div>
          </div>
          <div style="margin-top: 18px;">
            <button type="submit" class="btn btn-primary">Schedule Fixture</button>
          </div>
        </form>
      </div>

      <!-- Matches grouped by sport, then by team (populated by JS) -->
      <div id="matches-groups"></div>
    </section>

    <!-- 5. POINTS TABLE TAB -->
    <section id="points" class="tab-content">
      <h1 class="page-title">Points Table</h1>
      <p class="subtitle">Standings by sport, worked out from recorded match results. Win = 2 pts, Draw = 1 pt, Loss = 0 pts. Matches marked Pending are not counted.</p>

      <div id="points-groups"></div>
    </section>

  </div>

  <!-- JavaScript -->
  <script>
    // 1. Initial State Data
    let teams = [
      { name: "River Hawks", sport: "Football", captain: "Aarav Mehta", players: 15 },
      { name: "City Strikers", sport: "Football", captain: "Darsh Kapoor", players: 15 },
      { name: "Eastside Rovers", sport: "Football", captain: "Kunal Bose", players: 15 },
      { name: "Capital Warriors", sport: "Football", captain: "Om Nair", players: 15 },
      { name: "Lakeside Lions", sport: "Football", captain: "Neel Mann", players: 15 },
      { name: "Mumbai Mavericks", sport: "Cricket", captain: "Vihaan Sandhu", players: 15 },
      { name: "Delhi Dynamos", sport: "Cricket", captain: "Ayush Mann", players: 15 },
      { name: "Punjab Panthers", sport: "Cricket", captain: "Rajat Reddy", players: 15 },
      { name: "Bengal Blazers", sport: "Cricket", captain: "Kunal Chopra", players: 15 },
      { name: "Jaipur Jaguars", sport: "Cricket", captain: "Vihaan Desai", players: 15 },
      { name: "Northside Bulls", sport: "Basketball", captain: "Kabir Singh", players: 11 },
      { name: "Metro Hoopers", sport: "Basketball", captain: "Omkar Bhatia", players: 11 },
      { name: "Downtown Dunkers", sport: "Basketball", captain: "Tanish Kulkarni", players: 11 },
      { name: "Harbor Hornets", sport: "Basketball", captain: "Aarush Iyer", players: 11 },
      { name: "Skyline Kings", sport: "Basketball", captain: "Parth Sandhu", players: 11 },
      { name: "Smash Squad", sport: "Badminton", captain: "Farhan Rao", players: 2 },
      { name: "Ace Racquets", sport: "Badminton", captain: "Vikram Rathore", players: 2 },
      { name: "Shuttle Stars", sport: "Badminton", captain: "Aditya Joshi", players: 2 },
      { name: "Net Ninjas", sport: "Badminton", captain: "Govind Bose", players: 2 }
    ];

    let players = [
      { name: "Aarav Mehta", team: "River Hawks", sport: "Football", email: "aarav.mehta@domain.com" },
      { name: "Rohan Sharma", team: "River Hawks", sport: "Football", email: "rohan.sharma@domain.com" },
      { name: "Yash Kulkarni", team: "River Hawks", sport: "Football", email: "yash.kulkarni@domain.com" },
      { name: "Rudra Yadav", team: "River Hawks", sport: "Football", email: "rudra.yadav@domain.com" },
      { name: "Aarush Sandhu", team: "River Hawks", sport: "Football", email: "aarush.sandhu@domain.com" },
      { name: "Atharv Reddy", team: "River Hawks", sport: "Football", email: "atharv.reddy@domain.com" },
      { name: "Advait Saxena", team: "River Hawks", sport: "Football", email: "advait.saxena@domain.com" },
      { name: "Gaurav Ghosh", team: "River Hawks", sport: "Football", email: "gaurav.ghosh@domain.com" },
      { name: "Kabir Sidhu", team: "River Hawks", sport: "Football", email: "kabir.sidhu@domain.com" },
      { name: "Omkar Bansal", team: "River Hawks", sport: "Football", email: "omkar.bansal@domain.com" },
      { name: "Dev Khanna", team: "River Hawks", sport: "Football", email: "dev.khanna@domain.com" },
      { name: "Reyansh Thakur", team: "River Hawks", sport: "Football", email: "reyansh.thakur@domain.com" },
      { name: "Nikhil Verma", team: "River Hawks", sport: "Football", email: "nikhil.verma@domain.com" },
      { name: "Ayaan Iyer", team: "River Hawks", sport: "Football", email: "ayaan.iyer@domain.com" },
      { name: "Bhavesh Chauhan", team: "River Hawks", sport: "Football", email: "bhavesh.chauhan@domain.com" },
      { name: "Darsh Kapoor", team: "City Strikers", sport: "Football", email: "darsh.kapoor@domain.com" },
      { name: "Eshan Dhillon", team: "City Strikers", sport: "Football", email: "eshan.dhillon@domain.com" },
      { name: "Varun Patel", team: "City Strikers", sport: "Football", email: "varun.patel@domain.com" },
      { name: "Tushar Kapoor", team: "City Strikers", sport: "Football", email: "tushar.kapoor@domain.com" },
      { name: "Pavan Das", team: "City Strikers", sport: "Football", email: "pavan.das@domain.com" },
      { name: "Ishaan Mann", team: "City Strikers", sport: "Football", email: "ishaan.mann@domain.com" },
      { name: "Tanish Chopra", team: "City Strikers", sport: "Football", email: "tanish.chopra@domain.com" },
      { name: "Farhan Mishra", team: "City Strikers", sport: "Football", email: "farhan.mishra@domain.com" },
      { name: "Govind Bajwa", team: "City Strikers", sport: "Football", email: "govind.bajwa@domain.com" },
      { name: "Hrithik Gupta", team: "City Strikers", sport: "Football", email: "hrithik.gupta@domain.com" },
      { name: "Lakshay Menon", team: "City Strikers", sport: "Football", email: "lakshay.menon@domain.com" },
      { name: "Jatin Rathore", team: "City Strikers", sport: "Football", email: "jatin.rathore@domain.com" },
      { name: "Zayan Grewal", team: "City Strikers", sport: "Football", email: "zayan.grewal@domain.com" },
      { name: "Arjun Joshi", team: "City Strikers", sport: "Football", email: "arjun.joshi@domain.com" },
      { name: "Siddharth Sethi", team: "City Strikers", sport: "Football", email: "siddharth.sethi@domain.com" },
      { name: "Kunal Bose", team: "Eastside Rovers", sport: "Football", email: "kunal.bose@domain.com" },
      { name: "Jayesh Brar", team: "Eastside Rovers", sport: "Football", email: "jayesh.brar@domain.com" },
      { name: "Krish Bhatia", team: "Eastside Rovers", sport: "Football", email: "krish.bhatia@domain.com" },
      { name: "Laksh Pandey", team: "Eastside Rovers", sport: "Football", email: "laksh.pandey@domain.com" },
      { name: "Sahil Gill", team: "Eastside Rovers", sport: "Football", email: "sahil.gill@domain.com" },
      { name: "Raghav Nair", team: "Eastside Rovers", sport: "Football", email: "raghav.nair@domain.com" },
      { name: "Chirag Desai", team: "Eastside Rovers", sport: "Football", email: "chirag.desai@domain.com" },
      { name: "Neel Tiwari", team: "Eastside Rovers", sport: "Football", email: "neel.tiwari@domain.com" },
      { name: "Manav Randhawa", team: "Eastside Rovers", sport: "Football", email: "manav.randhawa@domain.com" },
      { name: "Rahul Malhotra", team: "Eastside Rovers", sport: "Football", email: "rahul.malhotra@domain.com" },
      { name: "Madhav Arora", team: "Eastside Rovers", sport: "Football", email: "madhav.arora@domain.com" },
      { name: "Nakul Sen", team: "Eastside Rovers", sport: "Football", email: "nakul.sen@domain.com" },
      { name: "Armaan Sharma", team: "Eastside Rovers", sport: "Football", email: "armaan.sharma@domain.com" },
      { name: "Dhruv Kulkarni", team: "Eastside Rovers", sport: "Football", email: "dhruv.kulkarni@domain.com" },
      { name: "Vikram Yadav", team: "Eastside Rovers", sport: "Football", email: "vikram.yadav@domain.com" },
      { name: "Om Nair", team: "Capital Warriors", sport: "Football", email: "om.nair@domain.com" },
      { name: "Pratik Kapoor", team: "Capital Warriors", sport: "Football", email: "pratik.kapoor@domain.com" },
      { name: "Rishi Sen", team: "Capital Warriors", sport: "Football", email: "rishi.sen@domain.com" },
      { name: "Lakshay Gupta", team: "Capital Warriors", sport: "Football", email: "lakshay.gupta@domain.com" },
      { name: "Jatin Saxena", team: "Capital Warriors", sport: "Football", email: "jatin.saxena@domain.com" },
      { name: "Zayan Bose", team: "Capital Warriors", sport: "Football", email: "zayan.bose@domain.com" },
      { name: "Arjun Verma", team: "Capital Warriors", sport: "Football", email: "arjun.verma@domain.com" },
      { name: "Siddharth Desai", team: "Capital Warriors", sport: "Football", email: "siddharth.desai@domain.com" },
      { name: "Kunal Das", team: "Capital Warriors", sport: "Football", email: "kunal.das@domain.com" },
      { name: "Sameer Sharma", team: "Capital Warriors", sport: "Football", email: "sameer.sharma@domain.com" },
      { name: "Tarun Menon", team: "Capital Warriors", sport: "Football", email: "tarun.menon@domain.com" },
      { name: "Utkarsh Ghosh", team: "Capital Warriors", sport: "Football", email: "utkarsh.ghosh@domain.com" },
      { name: "Sahil Brar", team: "Capital Warriors", sport: "Football", email: "sahil.brar@domain.com" },
      { name: "Raghav Iyer", team: "Capital Warriors", sport: "Football", email: "raghav.iyer@domain.com" },
      { name: "Chirag Tiwari", team: "Capital Warriors", sport: "Football", email: "chirag.tiwari@domain.com" },
      { name: "Neel Mann", team: "Lakeside Lions", sport: "Football", email: "neel.mann@domain.com" },
      { name: "Manav Kulkarni", team: "Lakeside Lions", sport: "Football", email: "manav.kulkarni@domain.com" },
      { name: "Rahul Rathore", team: "Lakeside Lions", sport: "Football", email: "rahul.rathore@domain.com" },
      { name: "Vivaan Sidhu", team: "Lakeside Lions", sport: "Football", email: "vivaan.sidhu@domain.com" },
      { name: "Yuvraj Menon", team: "Lakeside Lions", sport: "Football", email: "yuvraj.menon@domain.com" },
      { name: "Armaan Chauhan", team: "Lakeside Lions", sport: "Football", email: "armaan.chauhan@domain.com" },
      { name: "Dhruv Randhawa", team: "Lakeside Lions", sport: "Football", email: "dhruv.randhawa@domain.com" },
      { name: "Vikram Chopra", team: "Lakeside Lions", sport: "Football", email: "vikram.chopra@domain.com" },
      { name: "Vihaan Yadav", team: "Lakeside Lions", sport: "Football", email: "vihaan.yadav@domain.com" },
      { name: "Aditya Grewal", team: "Lakeside Lions", sport: "Football", email: "aditya.grewal@domain.com" },
      { name: "Veer Bansal", team: "Lakeside Lions", sport: "Football", email: "veer.bansal@domain.com" },
      { name: "Abhay Pandey", team: "Lakeside Lions", sport: "Football", email: "abhay.pandey@domain.com" },
      { name: "Bharat Dhillon", team: "Lakeside Lions", sport: "Football", email: "bharat.dhillon@domain.com" },
      { name: "Chetan Malhotra", team: "Lakeside Lions", sport: "Football", email: "chetan.malhotra@domain.com" },
      { name: "Mohit Mishra", team: "Lakeside Lions", sport: "Football", email: "mohit.mishra@domain.com" },
      { name: "Vihaan Sandhu", team: "Mumbai Mavericks", sport: "Cricket", email: "vihaan.sandhu@domain.com" },
      { name: "Aditya Reddy", team: "Mumbai Mavericks", sport: "Cricket", email: "aditya.reddy@domain.com" },
      { name: "Veer Saxena", team: "Mumbai Mavericks", sport: "Cricket", email: "veer.saxena@domain.com" },
      { name: "Deepak Ghosh", team: "Mumbai Mavericks", sport: "Cricket", email: "deepak.ghosh@domain.com" },
      { name: "Gopal Sidhu", team: "Mumbai Mavericks", sport: "Cricket", email: "gopal.sidhu@domain.com" },
      { name: "Himanshu Bansal", team: "Mumbai Mavericks", sport: "Cricket", email: "himanshu.bansal@domain.com" },
      { name: "Mohit Khanna", team: "Mumbai Mavericks", sport: "Cricket", email: "mohit.khanna@domain.com" },
      { name: "Parth Thakur", team: "Mumbai Mavericks", sport: "Cricket", email: "parth.thakur@domain.com" },
      { name: "Hemant Verma", team: "Mumbai Mavericks", sport: "Cricket", email: "hemant.verma@domain.com" },
      { name: "Karan Iyer", team: "Mumbai Mavericks", sport: "Cricket", email: "karan.iyer@domain.com" },
      { name: "Harsh Chauhan", team: "Mumbai Mavericks", sport: "Cricket", email: "harsh.chauhan@domain.com" },
      { name: "Pranav Dhillon", team: "Mumbai Mavericks", sport: "Cricket", email: "pranav.dhillon@domain.com" },
      { name: "Jai Patel", team: "Mumbai Mavericks", sport: "Cricket", email: "jai.patel@domain.com" },
      { name: "Kartik Kapoor", team: "Mumbai Mavericks", sport: "Cricket", email: "kartik.kapoor@domain.com" },
      { name: "Lalit Das", team: "Mumbai Mavericks", sport: "Cricket", email: "lalit.das@domain.com" },
      { name: "Ayush Mann", team: "Delhi Dynamos", sport: "Cricket", email: "ayush.mann@domain.com" },
      { name: "Uday Chopra", team: "Delhi Dynamos", sport: "Cricket", email: "uday.chopra@domain.com" },
      { name: "Rohan Pandey", team: "Delhi Dynamos", sport: "Cricket", email: "rohan.pandey@domain.com" },
      { name: "Yash Gill", team: "Delhi Dynamos", sport: "Cricket", email: "yash.gill@domain.com" },
      { name: "Rudra Nair", team: "Delhi Dynamos", sport: "Cricket", email: "rudra.nair@domain.com" },
      { name: "Mayank Desai", team: "Delhi Dynamos", sport: "Cricket", email: "mayank.desai@domain.com" },
      { name: "Naveen Tiwari", team: "Delhi Dynamos", sport: "Cricket", email: "naveen.tiwari@domain.com" },
      { name: "Ojas Randhawa", team: "Delhi Dynamos", sport: "Cricket", email: "ojas.randhawa@domain.com" },
      { name: "Gaurav Malhotra", team: "Delhi Dynamos", sport: "Cricket", email: "gaurav.malhotra@domain.com" },
      { name: "Kabir Arora", team: "Delhi Dynamos", sport: "Cricket", email: "kabir.arora@domain.com" },
      { name: "Omkar Sen", team: "Delhi Dynamos", sport: "Cricket", email: "omkar.sen@domain.com" },
      { name: "Dev Sharma", team: "Delhi Dynamos", sport: "Cricket", email: "dev.sharma@domain.com" },
      { name: "Reyansh Kulkarni", team: "Delhi Dynamos", sport: "Cricket", email: "reyansh.kulkarni@domain.com" },
      { name: "Nikhil Yadav", team: "Delhi Dynamos", sport: "Cricket", email: "nikhil.yadav@domain.com" },
      { name: "Piyush Sandhu", team: "Delhi Dynamos", sport: "Cricket", email: "piyush.sandhu@domain.com" },
      { name: "Rajat Reddy", team: "Punjab Panthers", sport: "Cricket", email: "rajat.reddy@domain.com" },
      { name: "Sanjay Saxena", team: "Punjab Panthers", sport: "Cricket", email: "sanjay.saxena@domain.com" },
      { name: "Varun Ghosh", team: "Punjab Panthers", sport: "Cricket", email: "varun.ghosh@domain.com" },
      { name: "Tushar Sidhu", team: "Punjab Panthers", sport: "Cricket", email: "tushar.sidhu@domain.com" },
      { name: "Pavan Bansal", team: "Punjab Panthers", sport: "Cricket", email: "pavan.bansal@domain.com" },
      { name: "Ishaan Khanna", team: "Punjab Panthers", sport: "Cricket", email: "ishaan.khanna@domain.com" },
      { name: "Tanish Thakur", team: "Punjab Panthers", sport: "Cricket", email: "tanish.thakur@domain.com" },
      { name: "Tejas Verma", team: "Punjab Panthers", sport: "Cricket", email: "tejas.verma@domain.com" },
      { name: "Vinay Iyer", team: "Punjab Panthers", sport: "Cricket", email: "vinay.iyer@domain.com" },
      { name: "Yogesh Chauhan", team: "Punjab Panthers", sport: "Cricket", email: "yogesh.chauhan@domain.com" },
      { name: "Lakshay Dhillon", team: "Punjab Panthers", sport: "Cricket", email: "lakshay.dhillon@domain.com" },
      { name: "Jatin Patel", team: "Punjab Panthers", sport: "Cricket", email: "jatin.patel@domain.com" },
      { name: "Zayan Kapoor", team: "Punjab Panthers", sport: "Cricket", email: "zayan.kapoor@domain.com" },
      { name: "Arjun Das", team: "Punjab Panthers", sport: "Cricket", email: "arjun.das@domain.com" },
      { name: "Siddharth Mann", team: "Punjab Panthers", sport: "Cricket", email: "siddharth.mann@domain.com" },
      { name: "Kunal Chopra", team: "Bengal Blazers", sport: "Cricket", email: "kunal.chopra@domain.com" },
      { name: "Akash Mishra", team: "Bengal Blazers", sport: "Cricket", email: "akash.mishra@domain.com" },
      { name: "Anuj Bajwa", team: "Bengal Blazers", sport: "Cricket", email: "anuj.bajwa@domain.com" },
      { name: "Bhuvan Gupta", team: "Bengal Blazers", sport: "Cricket", email: "bhuvan.gupta@domain.com" },
      { name: "Sahil Menon", team: "Bengal Blazers", sport: "Cricket", email: "sahil.menon@domain.com" },
      { name: "Raghav Rathore", team: "Bengal Blazers", sport: "Cricket", email: "raghav.rathore@domain.com" },
      { name: "Chirag Grewal", team: "Bengal Blazers", sport: "Cricket", email: "chirag.grewal@domain.com" },
      { name: "Neel Joshi", team: "Bengal Blazers", sport: "Cricket", email: "neel.joshi@domain.com" },
      { name: "Manav Sethi", team: "Bengal Blazers", sport: "Cricket", email: "manav.sethi@domain.com" },
      { name: "Rahul Bose", team: "Bengal Blazers", sport: "Cricket", email: "rahul.bose@domain.com" },
      { name: "Chaitanya Brar", team: "Bengal Blazers", sport: "Cricket", email: "chaitanya.brar@domain.com" },
      { name: "Devansh Bhatia", team: "Bengal Blazers", sport: "Cricket", email: "devansh.bhatia@domain.com" },
      { name: "Armaan Pandey", team: "Bengal Blazers", sport: "Cricket", email: "armaan.pandey@domain.com" },
      { name: "Dhruv Gill", team: "Bengal Blazers", sport: "Cricket", email: "dhruv.gill@domain.com" },
      { name: "Vikram Nair", team: "Bengal Blazers", sport: "Cricket", email: "vikram.nair@domain.com" },
      { name: "Vihaan Desai", team: "Jaipur Jaguars", sport: "Cricket", email: "vihaan.desai@domain.com" },
      { name: "Aditya Tiwari", team: "Jaipur Jaguars", sport: "Cricket", email: "aditya.tiwari@domain.com" },
      { name: "Veer Randhawa", team: "Jaipur Jaguars", sport: "Cricket", email: "veer.randhawa@domain.com" },
      { name: "Ekansh Malhotra", team: "Jaipur Jaguars", sport: "Cricket", email: "ekansh.malhotra@domain.com" },
      { name: "Fahad Arora", team: "Jaipur Jaguars", sport: "Cricket", email: "fahad.arora@domain.com" },
      { name: "Gautam Sen", team: "Jaipur Jaguars", sport: "Cricket", email: "gautam.sen@domain.com" },
      { name: "Mohit Sharma", team: "Jaipur Jaguars", sport: "Cricket", email: "mohit.sharma@domain.com" },
      { name: "Parth Kulkarni", team: "Jaipur Jaguars", sport: "Cricket", email: "parth.kulkarni@domain.com" },
      { name: "Hemant Yadav", team: "Jaipur Jaguars", sport: "Cricket", email: "hemant.yadav@domain.com" },
      { name: "Karan Sandhu", team: "Jaipur Jaguars", sport: "Cricket", email: "karan.sandhu@domain.com" },
      { name: "Harsh Reddy", team: "Jaipur Jaguars", sport: "Cricket", email: "harsh.reddy@domain.com" },
      { name: "Pranav Saxena", team: "Jaipur Jaguars", sport: "Cricket", email: "pranav.saxena@domain.com" },
      { name: "Hardik Ghosh", team: "Jaipur Jaguars", sport: "Cricket", email: "hardik.ghosh@domain.com" },
      { name: "Indrajit Sidhu", team: "Jaipur Jaguars", sport: "Cricket", email: "indrajit.sidhu@domain.com" },
      { name: "Jayant Bansal", team: "Jaipur Jaguars", sport: "Cricket", email: "jayant.bansal@domain.com" },
      { name: "Kabir Singh", team: "Northside Bulls", sport: "Basketball", email: "kabir.singh@domain.com" },
      { name: "Ayush Khanna", team: "Northside Bulls", sport: "Basketball", email: "ayush.khanna@domain.com" },
      { name: "Uday Thakur", team: "Northside Bulls", sport: "Basketball", email: "uday.thakur@domain.com" },
      { name: "Rohan Gupta", team: "Northside Bulls", sport: "Basketball", email: "rohan.gupta@domain.com" },
      { name: "Yash Menon", team: "Northside Bulls", sport: "Basketball", email: "yash.menon@domain.com" },
      { name: "Rudra Rathore", team: "Northside Bulls", sport: "Basketball", email: "rudra.rathore@domain.com" },
      { name: "Keshav Grewal", team: "Northside Bulls", sport: "Basketball", email: "keshav.grewal@domain.com" },
      { name: "Lokesh Joshi", team: "Northside Bulls", sport: "Basketball", email: "lokesh.joshi@domain.com" },
      { name: "Mukesh Sethi", team: "Northside Bulls", sport: "Basketball", email: "mukesh.sethi@domain.com" },
      { name: "Gaurav Bose", team: "Northside Bulls", sport: "Basketball", email: "gaurav.bose@domain.com" },
      { name: "Kabir Brar", team: "Northside Bulls", sport: "Basketball", email: "kabir.brar@domain.com" },
      { name: "Omkar Bhatia", team: "Metro Hoopers", sport: "Basketball", email: "omkar.bhatia@domain.com" },
      { name: "Dev Pandey", team: "Metro Hoopers", sport: "Basketball", email: "dev.pandey@domain.com" },
      { name: "Reyansh Gill", team: "Metro Hoopers", sport: "Basketball", email: "reyansh.gill@domain.com" },
      { name: "Nikhil Nair", team: "Metro Hoopers", sport: "Basketball", email: "nikhil.nair@domain.com" },
      { name: "Nitin Desai", team: "Metro Hoopers", sport: "Basketball", email: "nitin.desai@domain.com" },
      { name: "Prakash Tiwari", team: "Metro Hoopers", sport: "Basketball", email: "prakash.tiwari@domain.com" },
      { name: "Ramesh Randhawa", team: "Metro Hoopers", sport: "Basketball", email: "ramesh.randhawa@domain.com" },
      { name: "Varun Malhotra", team: "Metro Hoopers", sport: "Basketball", email: "varun.malhotra@domain.com" },
      { name: "Tushar Arora", team: "Metro Hoopers", sport: "Basketball", email: "tushar.arora@domain.com" },
      { name: "Pavan Sen", team: "Metro Hoopers", sport: "Basketball", email: "pavan.sen@domain.com" },
      { name: "Ishaan Sharma", team: "Metro Hoopers", sport: "Basketball", email: "ishaan.sharma@domain.com" },
      { name: "Tanish Kulkarni", team: "Downtown Dunkers", sport: "Basketball", email: "tanish.kulkarni@domain.com" },
      { name: "Suresh Yadav", team: "Downtown Dunkers", sport: "Basketball", email: "suresh.yadav@domain.com" },
      { name: "Tilak Sandhu", team: "Downtown Dunkers", sport: "Basketball", email: "tilak.sandhu@domain.com" },
      { name: "Umesh Reddy", team: "Downtown Dunkers", sport: "Basketball", email: "umesh.reddy@domain.com" },
      { name: "Lakshay Saxena", team: "Downtown Dunkers", sport: "Basketball", email: "lakshay.saxena@domain.com" },
      { name: "Jatin Ghosh", team: "Downtown Dunkers", sport: "Basketball", email: "jatin.ghosh@domain.com" },
      { name: "Zayan Sidhu", team: "Downtown Dunkers", sport: "Basketball", email: "zayan.sidhu@domain.com" },
      { name: "Arjun Bansal", team: "Downtown Dunkers", sport: "Basketball", email: "arjun.bansal@domain.com" },
      { name: "Siddharth Khanna", team: "Downtown Dunkers", sport: "Basketball", email: "siddharth.khanna@domain.com" },
      { name: "Kunal Thakur", team: "Downtown Dunkers", sport: "Basketball", email: "kunal.thakur@domain.com" },
      { name: "Vishal Verma", team: "Downtown Dunkers", sport: "Basketball", email: "vishal.verma@domain.com" },
      { name: "Aarush Iyer", team: "Harbor Hornets", sport: "Basketball", email: "aarush.iyer@domain.com" },
      { name: "Atharv Chauhan", team: "Harbor Hornets", sport: "Basketball", email: "atharv.chauhan@domain.com" },
      { name: "Sahil Dhillon", team: "Harbor Hornets", sport: "Basketball", email: "sahil.dhillon@domain.com" },
      { name: "Raghav Patel", team: "Harbor Hornets", sport: "Basketball", email: "raghav.patel@domain.com" },
      { name: "Chirag Kapoor", team: "Harbor Hornets", sport: "Basketball", email: "chirag.kapoor@domain.com" },
      { name: "Neel Das", team: "Harbor Hornets", sport: "Basketball", email: "neel.das@domain.com" },
      { name: "Manav Mann", team: "Harbor Hornets", sport: "Basketball", email: "manav.mann@domain.com" },
      { name: "Rahul Chopra", team: "Harbor Hornets", sport: "Basketball", email: "rahul.chopra@domain.com" },
      { name: "Advait Mishra", team: "Harbor Hornets", sport: "Basketball", email: "advait.mishra@domain.com" },
      { name: "Ayaan Bajwa", team: "Harbor Hornets", sport: "Basketball", email: "ayaan.bajwa@domain.com" },
      { name: "Armaan Gupta", team: "Harbor Hornets", sport: "Basketball", email: "armaan.gupta@domain.com" },
      { name: "Parth Sandhu", team: "Skyline Kings", sport: "Basketball", email: "parth.sandhu@domain.com" },
      { name: "Hemant Joshi", team: "Skyline Kings", sport: "Basketball", email: "hemant.joshi@domain.com" },
      { name: "Karan Khanna", team: "Skyline Kings", sport: "Basketball", email: "karan.khanna@domain.com" },
      { name: "Harsh Gill", team: "Skyline Kings", sport: "Basketball", email: "harsh.gill@domain.com" },
      { name: "Pranav Patel", team: "Skyline Kings", sport: "Basketball", email: "pranav.patel@domain.com" },
      { name: "Bhavesh Arora", team: "Skyline Kings", sport: "Basketball", email: "bhavesh.arora@domain.com" },
      { name: "Darsh Bajwa", team: "Skyline Kings", sport: "Basketball", email: "darsh.bajwa@domain.com" },
      { name: "Eshan Reddy", team: "Skyline Kings", sport: "Basketball", email: "eshan.reddy@domain.com" },
      { name: "Ayush Sethi", team: "Skyline Kings", sport: "Basketball", email: "ayush.sethi@domain.com" },
      { name: "Vikram Sandhu", team: "Skyline Kings", sport: "Basketball", email: "vikram.sandhu@domain.com" },
      { name: "Rohan Reddy", team: "Skyline Kings", sport: "Basketball", email: "rohan.reddy@domain.com" },
      { name: "Farhan Rao", team: "Smash Squad", sport: "Badminton", email: "farhan.rao@domain.com" },
      { name: "Dhruv Menon", team: "Smash Squad", sport: "Badminton", email: "dhruv.menon@domain.com" },
      { name: "Vikram Rathore", team: "Ace Racquets", sport: "Badminton", email: "vikram.rathore@domain.com" },
      { name: "Vihaan Grewal", team: "Ace Racquets", sport: "Badminton", email: "vihaan.grewal@domain.com" },
      { name: "Aditya Joshi", team: "Shuttle Stars", sport: "Badminton", email: "aditya.joshi@domain.com" },
      { name: "Veer Sethi", team: "Shuttle Stars", sport: "Badminton", email: "veer.sethi@domain.com" },
      { name: "Govind Bose", team: "Net Ninjas", sport: "Badminton", email: "govind.bose@domain.com" },
      { name: "Hrithik Brar", team: "Net Ninjas", sport: "Badminton", email: "hrithik.brar@domain.com" }
    ];

    let matches = [
      { sport: "Football", home: "River Hawks", away: "City Strikers", date: "2026-10-28", score: "3 – 2" },
      { sport: "Basketball", home: "Northside Bulls", away: "Metro Hoopers", date: "2026-10-29", score: "Pending" },
      { sport: "Badminton", home: "Smash Squad", away: "Ace Racquets", date: "2026-11-04", score: "2 – 1" },
      { sport: "Football", home: "Lakeside Lions", away: "City Strikers", date: "2026-11-28", score: "Pending" },
      { sport: "Football", home: "Eastside Rovers", away: "Capital Warriors", date: "2026-11-28", score: "Pending" },
      { sport: "Football", home: "Lakeside Lions", away: "River Hawks", date: "2026-12-05", score: "Pending" },
      { sport: "Football", home: "Eastside Rovers", away: "City Strikers", date: "2026-12-05", score: "Pending" },
      { sport: "Football", home: "River Hawks", away: "Capital Warriors", date: "2026-12-12", score: "Pending" },
      { sport: "Football", home: "Eastside Rovers", away: "Lakeside Lions", date: "2026-12-12", score: "Pending" },
      { sport: "Football", home: "Eastside Rovers", away: "River Hawks", date: "2026-12-19", score: "Pending" },
      { sport: "Football", home: "Capital Warriors", away: "City Strikers", date: "2026-12-19", score: "Pending" },
      { sport: "Football", home: "Capital Warriors", away: "Lakeside Lions", date: "2026-12-26", score: "Pending" },
      { sport: "Basketball", home: "Skyline Kings", away: "Metro Hoopers", date: "2026-11-27", score: "Pending" },
      { sport: "Basketball", home: "Downtown Dunkers", away: "Harbor Hornets", date: "2026-11-27", score: "Pending" },
      { sport: "Basketball", home: "Skyline Kings", away: "Northside Bulls", date: "2026-12-04", score: "Pending" },
      { sport: "Basketball", home: "Downtown Dunkers", away: "Metro Hoopers", date: "2026-12-04", score: "Pending" },
      { sport: "Basketball", home: "Northside Bulls", away: "Harbor Hornets", date: "2026-12-11", score: "Pending" },
      { sport: "Basketball", home: "Downtown Dunkers", away: "Skyline Kings", date: "2026-12-11", score: "Pending" },
      { sport: "Basketball", home: "Downtown Dunkers", away: "Northside Bulls", date: "2026-12-18", score: "Pending" },
      { sport: "Basketball", home: "Harbor Hornets", away: "Metro Hoopers", date: "2026-12-18", score: "Pending" },
      { sport: "Basketball", home: "Harbor Hornets", away: "Skyline Kings", date: "2026-12-25", score: "Pending" },
      { sport: "Cricket", home: "Jaipur Jaguars", away: "Delhi Dynamos", date: "2026-11-29", score: "Pending" },
      { sport: "Cricket", home: "Punjab Panthers", away: "Bengal Blazers", date: "2026-11-29", score: "Pending" },
      { sport: "Cricket", home: "Jaipur Jaguars", away: "Mumbai Mavericks", date: "2026-12-06", score: "Pending" },
      { sport: "Cricket", home: "Punjab Panthers", away: "Delhi Dynamos", date: "2026-12-06", score: "Pending" },
      { sport: "Cricket", home: "Mumbai Mavericks", away: "Bengal Blazers", date: "2026-12-13", score: "Pending" },
      { sport: "Cricket", home: "Punjab Panthers", away: "Jaipur Jaguars", date: "2026-12-13", score: "Pending" },
      { sport: "Cricket", home: "Punjab Panthers", away: "Mumbai Mavericks", date: "2026-12-20", score: "Pending" },
      { sport: "Cricket", home: "Bengal Blazers", away: "Delhi Dynamos", date: "2026-12-20", score: "Pending" },
      { sport: "Cricket", home: "Mumbai Mavericks", away: "Delhi Dynamos", date: "2026-12-27", score: "Pending" },
      { sport: "Cricket", home: "Bengal Blazers", away: "Jaipur Jaguars", date: "2026-12-27", score: "Pending" },
      { sport: "Badminton", home: "Smash Squad", away: "Net Ninjas", date: "2026-11-25", score: "Pending" },
      { sport: "Badminton", home: "Shuttle Stars", away: "Ace Racquets", date: "2026-11-25", score: "Pending" },
      { sport: "Badminton", home: "Shuttle Stars", away: "Smash Squad", date: "2026-12-02", score: "Pending" },
      { sport: "Badminton", home: "Net Ninjas", away: "Ace Racquets", date: "2026-12-02", score: "Pending" },
      { sport: "Badminton", home: "Net Ninjas", away: "Shuttle Stars", date: "2026-12-09", score: "Pending" }
    ];

    // 2. Badges
    function getSportBadge(sport) {
      let badgeClass = "badge-default";
      if (sport === "Football") badgeClass = "badge-football";
      if (sport === "Basketball") badgeClass = "badge-basketball";
      if (sport === "Cricket") badgeClass = "badge-cricket";
      if (sport === "Badminton") badgeClass = "badge-badminton";

      return `<span class="badge ${badgeClass}"><span class="dot"></span>${sport}</span>`;
    }

    function getResultBadge(score) {
      if (score.toLowerCase().includes("pending")) {
        return `<span class="badge status-pending"><span class="dot"></span>Pending</span>`;
      }
      return `<span class="badge status-completed"><span class="dot"></span>${score}</span>`;
    }

    // 3. Navigation
    function showTab(tabName) {
      let tabs = document.querySelectorAll(".tab-content");
      tabs.forEach(function(tab) {
        tab.classList.remove("active");
      });

      let buttons = document.querySelectorAll(".nav-btn");
      buttons.forEach(function(btn) {
        btn.classList.remove("active");
      });

      document.getElementById(tabName).classList.add("active");
      document.getElementById("btn-" + tabName).classList.add("active");
    }

    // 3b. View Switcher (Organiser = full access, Player = read-only)
    let currentView = "organiser";

    function setView(view) {
      currentView = view;
      document.body.classList.toggle("player-view", view === "player");
      document.getElementById("view-organiser").classList.toggle("active", view === "organiser");
      document.getElementById("view-player").classList.toggle("active", view === "player");

      document.querySelectorAll("[data-org]").forEach(function(el) {
        el.textContent = view === "player" ? el.dataset.player : el.dataset.org;
      });
    }

    function isReadOnly() {
      return currentView === "player";
    }

    // 4. Render Tables
    function renderTeams() {
      let container = document.getElementById("teams-groups");
      let sports = ["Football", "Basketball", "Cricket", "Badminton"];
      container.innerHTML = "";

      sports.forEach(function(sport) {
        let rows = "";
        let count = 0;

        // Keep each team's real index so Delete removes the right one
        for (let i = 0; i < teams.length; i++) {
          let team = teams[i];
          if (team.sport !== sport) continue;
          count++;
          rows += `
          <tr>
            <td>
              <div class="item-cell">
                <strong style="color: #0f172a;">${team.name}</strong>
              </div>
            </td>
            <td>${team.captain}</td>
            <td>${team.players} members</td>
            <td class="org-only">
              <button class="btn btn-delete" onclick="deleteTeam(${i})">Delete</button>
            </td>
          </tr>
        `;
        }

        if (count === 0) {
          rows = `<tr class="empty-row"><td colspan="4">No ${sport} teams yet</td></tr>`;
        }

        container.innerHTML += `
          <div class="card">
            <div class="sport-group-head">
              <div class="card-title">${getSportBadge(sport)}</div>
              <span class="sport-count">${count} ${count === 1 ? "team" : "teams"}</span>
            </div>
            <div class="table-container">
              <table>
                <thead>
                  <tr>
                    <th>Team</th>
                    <th>Captain</th>
                    <th>Players</th>
                    <th class="org-only">Actions</th>
                  </tr>
                </thead>
                <tbody>${rows}</tbody>
              </table>
            </div>
          </div>
        `;
      });
      updateStats();
    }

    // Remember which team dropdowns are open so adding/deleting doesn't collapse them
    let openTeams = {};
    document.getElementById("players-groups").addEventListener("toggle", function(e) {
      let el = e.target;
      if (el.classList && el.classList.contains("team-subgroup")) {
        openTeams[el.dataset.key] = el.open;
      }
    }, true);

    function renderPlayers() {
      let container = document.getElementById("players-groups");
      let sports = ["Football", "Basketball", "Cricket", "Badminton"];
      container.innerHTML = "";

      sports.forEach(function(sport) {
        // Collect this sport's teams (case-insensitive) and keep each player's real index
        let teamMap = {};
        let teamOrder = [];
        let total = 0;

        for (let i = 0; i < players.length; i++) {
          let player = players[i];
          if (player.sport !== sport) continue;
          total++;
          let key = player.team.trim().toLowerCase();
          if (!teamMap[key]) {
            teamMap[key] = { label: player.team.trim(), members: [] };
            teamOrder.push(key);
          }
          teamMap[key].members.push({ player: player, index: i });
        }

        let body = "";
        if (total === 0) {
          body = `<table><tbody><tr class="empty-row"><td>No ${sport} players yet</td></tr></tbody></table>`;
        } else {
          teamOrder.forEach(function(key) {
            let group = teamMap[key];
            let rows = group.members.map(function(m) {
              return `
          <tr>
            <td>
              <div class="item-cell">
                <strong style="color: #0f172a;">${m.player.name}</strong>
              </div>
            </td>
            <td>${m.player.email}</td>
            <td class="org-only">
              <button class="btn btn-delete" onclick="deletePlayer(${m.index})">Delete</button>
            </td>
          </tr>`;
            }).join("");

            body += `
          <details class="team-subgroup" data-key="${sport}|${key}" ${openTeams[sport + "|" + key] ? "open" : ""}>
            <summary class="team-subhead">
              <span class="team-subhead-left">
                <span class="chevron"></span>
                <span class="team-subhead-name">${group.label}</span>
              </span>
              <span class="sport-count">${group.members.length} ${group.members.length === 1 ? "player" : "players"}</span>
            </summary>
            <div class="table-container">
              <table>
                <thead>
                  <tr>
                    <th>Athlete</th>
                    <th>Email</th>
                    <th class="org-only">Actions</th>
                  </tr>
                </thead>
                <tbody>${rows}</tbody>
              </table>
            </div>
          </details>`;
          });
        }

        container.innerHTML += `
          <div class="card">
            <div class="sport-group-head">
              <div class="card-title">${getSportBadge(sport)}</div>
              <span class="sport-count">${total} ${total === 1 ? "player" : "players"}</span>
            </div>
            ${body}
          </div>
        `;
      });
      updateStats();
    }

    // A match's sport: the one saved with it, else the sport of a registered team in it
    function sportOf(match) {
      if (match.sport) return match.sport;
      for (let t = 0; t < teams.length; t++) {
        let n = teams[t].name.trim().toLowerCase();
        if (n === match.home.trim().toLowerCase() || n === match.away.trim().toLowerCase()) return teams[t].sport;
      }
      return null;
    }

    // Reads "3 – 2" (home – away). Returns null for Pending or anything that is not a score.
    function parseScore(score) {
      let m = String(score).match(/(\d+)\s*[–—\-:]\s*(\d+)/);
      if (!m) return null;
      return { home: parseInt(m[1], 10), away: parseInt(m[2], 10) };
    }

    function renderPoints() {
      let container = document.getElementById("points-groups");
      let sports = ["Football", "Basketball", "Cricket", "Badminton"];
      container.innerHTML = "";

      sports.forEach(function(sport) {
        let table = {};

        function row(name) {
          let label = name.trim();
          let key = label.toLowerCase();
          if (!table[key]) {
            table[key] = { name: label, p: 0, w: 0, d: 0, l: 0, pts: 0 };
          }
          return table[key];
        }

        // Registered teams of this sport start on zero, so they are listed before they play
        teams.forEach(function(t) { if (t.sport === sport) row(t.name); });

        let counted = 0;
        matches.forEach(function(match) {
          if (sportOf(match) !== sport) return;
          let result = parseScore(match.score);
          if (!result) return;
          counted++;

          let home = row(match.home);
          let away = row(match.away);
          home.p++; away.p++;

          if (result.home > result.away) { home.w++; home.pts += 2; away.l++; }
          else if (result.home < result.away) { away.w++; away.pts += 2; home.l++; }
          else { home.d++; away.d++; home.pts += 1; away.pts += 1; }
        });

        let list = Object.keys(table).map(function(k) { return table[k]; });
        list.sort(function(a, b) {
          if (b.pts !== a.pts) return b.pts - a.pts;
          if (b.w !== a.w) return b.w - a.w;
          return a.name.localeCompare(b.name);
        });

        let body = "";
        if (list.length === 0) {
          body = `<tr class="empty-row"><td colspan="7">No ${sport} teams yet</td></tr>`;
        } else {
          list.forEach(function(t, idx) {
            let leader = idx === 0 && t.p > 0 ? "leader" : "";
            body += `
          <tr class="${leader}">
            <td class="pos">${idx + 1}</td>
            <td><strong style="color: #0f172a;">${t.name}</strong></td>
            <td class="num">${t.p}</td>
            <td class="num">${t.w}</td>
            <td class="num">${t.d}</td>
            <td class="num">${t.l}</td>
            <td class="num pts">${t.pts}</td>
          </tr>`;
          });
        }

        container.innerHTML += `
          <div class="card">
            <div class="sport-group-head">
              <div class="card-title">${getSportBadge(sport)}</div>
              <span class="sport-count">${counted} ${counted === 1 ? "result" : "results"} counted</span>
            </div>
            <div class="table-container">
              <table class="points-table">
                <thead>
                  <tr>
                    <th class="pos">#</th>
                    <th>Team</th>
                    <th class="num" title="Played">P</th>
                    <th class="num" title="Won">W</th>
                    <th class="num" title="Drawn">D</th>
                    <th class="num" title="Lost">L</th>
                    <th class="num" title="Points">Pts</th>
                  </tr>
                </thead>
                <tbody>${body}</tbody>
              </table>
            </div>
          </div>
        `;
      });
    }

    // Dashboard date filter (defaults to today, in the viewer's local time)
    let dashboardDate = "";

    function todayString() {
      let d = new Date();
      return d.getFullYear() + "-" + String(d.getMonth() + 1).padStart(2, "0") + "-" + String(d.getDate()).padStart(2, "0");
    }

    function setDashboardDate(value) {
      if (!value) return;
      dashboardDate = value;
      renderMatches();
    }

    function shiftDashboardDate(days) {
      let base = dashboardDate || todayString();
      let parts = base.split("-");
      let d = new Date(parseInt(parts[0], 10), parseInt(parts[1], 10) - 1, parseInt(parts[2], 10) + days);
      setDashboardDate(d.getFullYear() + "-" + String(d.getMonth() + 1).padStart(2, "0") + "-" + String(d.getDate()).padStart(2, "0"));
    }

    function renderMatches() {
      let container = document.getElementById("matches-groups");
      let dashBody = document.getElementById("dashboard-matches-body");
      let sports = ["Football", "Basketball", "Cricket", "Badminton"];
      container.innerHTML = "";
      dashBody.innerHTML = "";

      // Dashboard shows only the matches on the selected date
      let dateInput = document.getElementById("dashboard-date");
      if (!dashboardDate) dashboardDate = todayString();
      dateInput.value = dashboardDate;

      let shown = 0;
      matches.forEach(function(match) {
        if (match.date !== dashboardDate) return;
        shown++;
        dashBody.innerHTML += `
          <tr>
            <td>${getSportBadge(sportOf(match))}</td>
            <td>${match.home}</td>
            <td>${match.away}</td>
            <td>${match.date}</td>
            <td>${getResultBadge(match.score)}</td>
          </tr>
        `;
      });

      if (shown === 0) {
        dashBody.innerHTML = `<tr class="empty-row"><td colspan="5">No matches on this date</td></tr>`;
      }

      sports.forEach(function(sport) {
        let rows = "";
        let count = 0;

        // Keep each match's real index so Delete removes the right fixture
        for (let i = 0; i < matches.length; i++) {
          let match = matches[i];
          if (sportOf(match) !== sport) continue;
          count++;
          rows += `
          <tr>
            <td>
              <div class="vs-cell">
                <strong>${match.home}</strong>
                <span class="vs">vs</span>
                <strong>${match.away}</strong>
              </div>
            </td>
            <td>${match.date}</td>
            <td>${getResultBadge(match.score)}</td>
            <td class="org-only">
              <button class="btn btn-delete" onclick="deleteMatch(${i})">Delete</button>
            </td>
          </tr>`;
        }

        if (count === 0) {
          rows = `<tr class="empty-row"><td colspan="4">No ${sport} matches yet</td></tr>`;
        }

        container.innerHTML += `
          <div class="card">
            <div class="sport-group-head">
              <div class="card-title">${getSportBadge(sport)}</div>
              <span class="sport-count">${count} ${count === 1 ? "match" : "matches"}</span>
            </div>
            <div class="table-container">
              <table>
                <thead>
                  <tr>
                    <th>Match</th>
                    <th>Date</th>
                    <th>Result</th>
                    <th class="org-only">Actions</th>
                  </tr>
                </thead>
                <tbody>${rows}</tbody>
              </table>
            </div>
          </div>
        `;
      });
      renderPoints();
      updateStats();
    }

    // 5. Update Stats Numbers
    function updateStats() {
      document.getElementById("stat-teams").innerText = teams.length;
      document.getElementById("stat-players").innerText = players.length;
      document.getElementById("stat-matches").innerText = matches.length;
    }

    // 6. Add Handlers
    function addTeam(event) {
      event.preventDefault();
      if (isReadOnly()) return;
      
      teams.push({
        name: document.getElementById("team-name").value,
        sport: document.getElementById("team-sport").value,
        captain: document.getElementById("team-captain").value,
        players: document.getElementById("team-players").value
      });
      saveData();

      document.getElementById("team-form").reset();
      renderTeams();
      renderMatches();
    }

    function addPlayer(event) {
      event.preventDefault();
      if (isReadOnly()) return;

      players.push({
        name: document.getElementById("player-name").value,
        team: document.getElementById("player-team").value,
        sport: document.getElementById("player-sport").value,
        email: document.getElementById("player-email").value
      });
      saveData();

      document.getElementById("player-form").reset();
      renderPlayers();
    }

    function addMatch(event) {
      event.preventDefault();
      if (isReadOnly()) return;

      matches.push({
        sport: document.getElementById("match-sport").value,
        home: document.getElementById("match-home").value,
        away: document.getElementById("match-away").value,
        date: document.getElementById("match-date").value,
        score: document.getElementById("match-score").value
      });
      saveData();

      document.getElementById("match-form").reset();
      renderMatches();
    }

    // 7. Delete Handlers
    function deleteTeam(index) {
      if (isReadOnly()) return;
      if (confirm("Remove this team from the league roster?")) {
        teams.splice(index, 1);
        saveData();
        renderTeams();
        renderMatches();
      }
    }

    function deletePlayer(index) {
      if (isReadOnly()) return;
      if (confirm("Remove this player from records?")) {
        players.splice(index, 1);
        saveData();
        renderPlayers();
      }
    }

    function deleteMatch(index) {
      if (isReadOnly()) return;
      if (confirm("Delete this fixture?")) {
        matches.splice(index, 1);
        saveData();
        renderMatches();
      }
    }

    // 8. Saving: teams, players and matches are kept in this browser, so they are still here after a refresh
    const STORAGE_KEY = "playleague-data-v5";

    function saveData() {
      try {
        localStorage.setItem(STORAGE_KEY, JSON.stringify({ teams: teams, players: players, matches: matches }));
      } catch (err) {
        // Storage blocked or full: the page still works, it just will not remember
      }
    }

    function loadData() {
      try {
        let raw = localStorage.getItem(STORAGE_KEY);
        if (!raw) return;
        let data = JSON.parse(raw);
        if (Array.isArray(data.teams)) teams = data.teams;
        if (Array.isArray(data.players)) players = data.players;
        if (Array.isArray(data.matches)) matches = data.matches;
      } catch (err) {
        // Nothing usable saved: keep the sample data
      }
    }

    // Initial Load
    loadData();
    renderTeams();
    renderPlayers();
    renderMatches();
  </script>
</body>
</html>
