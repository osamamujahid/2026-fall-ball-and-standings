<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>League Standings & Schedule</title>
    <style>
        :root {
            --primary: #1e3a8a;
            --primary-hover: #172554;
            --accent: #3b82f6;
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --text: #0f172a;
            --text-light: #64748b;
            --border: #e2e8f0;
            --success: #10b981;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg);
            color: var(--text);
            padding: 20px;
            line-height: 1.5;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            padding: 30px 20px;
            border-radius: 12px;
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1);
        }

        header h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
        }

        .sync-panel {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            margin-top: 15px;
            flex-wrap: wrap;
        }

        .btn {
            background-color: white;
            color: var(--primary);
            border: none;
            padding: 10px 20px;
            font-weight: 600;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.2s;
            box-shadow: 0 2px 4px rgb(0 0 0 / 0.1);
        }

        .btn:hover {
            background-color: #f1f5f9;
            transform: translateY(-1px);
        }

        .status-badge {
            font-size: 0.85rem;
            padding: 6px 12px;
            border-radius: 20px;
            background-color: rgba(255, 255, 255, 0.2);
        }

        .section-title {
            font-size: 1.5rem;
            margin: 30px 0 15px 0;
            position: relative;
            padding-bottom: 8px;
            border-bottom: 2px solid var(--border);
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 12px;
            border: 1px solid var(--border);
            box-shadow: 0 1px 3px rgb(0 0 0 / 0.05);
            overflow: hidden;
            margin-bottom: 30px;
        }

        .table-responsive {
            width: 100%;
            overflow-x: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
        }

        th {
            background-color: #f1f5f9;
            color: var(--text-light);
            font-weight: 600;
            padding: 14px 16px;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        td {
            padding: 14px 16px;
            border-bottom: 1px solid var(--border);
            font-size: 0.95rem;
        }

        tr:last-child td {
            border-bottom: none;
        }

        tr:hover td {
            background-color: #f8fafc;
        }

        .font-semibold {
            font-weight: 600;
        }

        .text-center {
            text-align: center;
        }

        .filters {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            flex-wrap: wrap;
        }

        .filter-btn {
            background-color: #e2e8f0;
            color: var(--text-light);
            border: none;
            padding: 8px 16px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.2s;
        }

        .filter-btn.active {
            background-color: var(--primary);
            color: white;
        }

        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 20px;
        }

        .game-card {
            background-color: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 16px;
            box-shadow: 0 1px 3px rgb(0 0 0 / 0.05);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .game-header {
            display: flex;
            justify-content: space-between;
            color: var(--text-light);
            font-size: 0.8rem;
            margin-bottom: 12px;
            padding-bottom: 8px;
            border-bottom: 1px dashed var(--border);
        }

        .game-team-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 6px 0;
            font-size: 1rem;
        }

        .game-score {
            font-weight: 700;
            font-size: 1.1rem;
            background-color: #f1f5f9;
            padding: 2px 8px;
            border-radius: 4px;
            min-width: 32px;
            text-align: center;
        }

        .game-score.winner {
            background-color: #d1fae5;
            color: #065f46;
        }

        .game-status-label {
            margin-top: 12px;
            font-size: 0.75rem;
            font-weight: 600;
            text-align: center;
            padding: 4px;
            background-color: #f8fafc;
            border-radius: 4px;
            color: var(--text-light);
            text-transform: uppercase;
        }

        .game-status-label.live {
            background-color: #d1fae5;
            color: #065f46;
        }

        #error-message {
            background-color: #fee2e2;
            border: 1px solid #fca5a5;
            color: #991b1b;
            padding: 12px;
            border-radius: 6px;
            margin-bottom: 20px;
            display: none;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>League Dashboard</h1>
        <p>Live Scores & Standings tracking platform</p>
        <div class="sync-panel">
            <button class="btn" onclick="fetchLeagueData()">Sync Live Data</button>
            <div class="status-badge" id="sync-status">Status: Initializing...</div>
        </div>
    </header>

    <div id="error-message"></div>

    <h2 class="section-title">🏆 League Standings</h2>
    <div class="card">
        <div class="table-responsive">
            <table>
                <thead>
                    <tr>
                        <th>Rank</th>
                        <th>Team</th>
                        <th class="text-center">W</th>
                        <th class="text-center">L</th>
                        <th class="text-center">T</th>
                        <th class="text-center">PTS</th>
                        <th class="text-center">RF</th>
                        <th class="text-center">RA</th>
                        <th class="text-center">DIFF</th>
                    </tr>
                </thead>
                <tbody id="standings-body">
                    <tr>
                        <td colspan="9" class="text-center" style="color: var(--text-light);">Syncing with Google Sheets table...</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

    <h2 class="section-title">📅 Match Schedule & Results</h2>
    <div class="filters">
        <button class="filter-btn active" onclick="filterGames('all', this)">All Games</button>
        <button class="filter-btn" onclick="filterGames('completed', this)">Completed</button>
        <button class="filter-btn" onclick="filterGames('upcoming', this)">Upcoming</button>
    </div>

    <div class="games-grid" id="games-container">
        <!-- Rendered via JavaScript -->
    </div>
</div>

<script>
    // Configured directly to your specific sheet and tab ID (gid=665334959) using the background CSV exporter format
    const SPREADSHEET_CSV_URL = "https://google.com";

    let masterGames = [];
    let currentFilter = 'all';

    // Local schedule baseline
    const fallbackSchedule = [
        ["10/1/2026","7:00 PM","Dunton 2","Team Zeshan","Team Ali"],
        ["10/1/2026","7:00 PM","Dunton 3","Team Yasir","Team Yusuf"],
        ["10/1/2026","7:00 PM","Dunton 4","Team Emad","Team Zohaid"],
        ["10/1/2026","8:30 PM","Dunton 2","Team Ali","Team Emad"],
        ["10/1/2026","8:30 PM","Dunton 3","Team Yusuf","Team Zeshan"],
        ["10/1/2026","8:30 PM","Dunton 4","Team Zohaid","Team Yasir"],
        ["10/4/2026","6:30 PM","Brickyard 1","Team Yasir","Team Ali"],
        ["10/4/2026","6:30 PM","Brickyard 2","Team Yusuf","Team Emad"],
        ["10/4/2026","8:00 PM","Brickyard 1","Team Zohaid","Team Yasir"],
        ["10/4/2026","8:00 PM","Brickyard 2","Team Zeshan","Team Yusuf"],
        ["10/4/2026","9:30 PM","Brickyard 1","Team Ali","Team Zohaid"],
        ["10/4/2026","9:30 PM","Brickyard 2","Team Emad","Team Zeshan"],
        ["10/8/2026","7:00 PM","CAA Red","Team Yasir","Team Yusuf"],
        ["10/8/2026","7:00 PM","CAA Yellow","Team Zeshan","Team Emad"],
        ["10/8/2026","7:00 PM","CAA Green","Team Ali","Team Zohaid"],
        ["10/8/2026","8:30 PM","CAA Red","Team Emad","Team Yasir"],
        ["10/8/2026","8:30 PM","CAA Yellow","Team Zohaid","Team Zeshan"],
        ["10/8/2026","8:30 PM","CAA Green","Team Yusuf","Team Ali"],
        ["10/15/2026","7:00 PM","CAA Red","Team Zohaid","Team Zeshan"],
        ["10/15/2026","7:00 PM","CAA Yellow","Team Emad","Team Yusuf"],
Use code with caution.
["10/15/2026","7:00 PM","CAA Green","Team Yasir","Team Ali"],
["10/15/2026","8:30 PM","CAA Red","Team Yusuf","Team Zohaid"],
["10/15/2026","8:30 PM","CAA Yellow","Team Ali","Team Emad"],
["10/15/2026","8:30 PM","CAA Green","Team Zeshan","Team Yasir"]
];
async function fetchLeagueData() {
const statusElement = document.getElementById('sync-status');
const errorElement = document.getElementById('error-message');
statusElement.innerText = "Status: Syncing matrix rows...";
errorElement.style.display = 'none';
try {
const response = await fetch(SPREADSHEET_CSV_URL);
if (!response.ok) throw new Error("Spreadsheet validation mismatch.");
const textData = await response.text();
parseCSVData(textData);
statusElement.innerText = "Status: Live Synced";
} catch (error) {
console.error("External sync warning, loading fallback array layout:", error);
statusElement.innerText = "Status: Offline Preview Active";
errorElement.innerHTML = ⚠️ <strong>Access Restriction Warning:</strong> The site could not fetch data from your Google Sheet because its access is set to private. To fix this, open your Google Sheet, click the blue <strong>"Share"</strong> button in the top right, change General Access to <strong>"Anyone with the link can view"</strong>, and then refresh this page!;
errorElement.style.display = 'block';
masterGames = fallbackSchedule.map(row => ({
date: row[0], time: row[1], diamond: row[2], home: row[3], away: row[4],
homeScore: null, awayScore: null
}));
calculateStandingsAndRender();
}
}
function parseCSVData(csvText) {
const lines = csvText.split(/\r?\n/);
const parsedGames = [];
for (let i = 1; i < lines.length; i++) {
if (!lines[i].trim()) continue;
const cols = lines[i].split(/,(?=(?:(?:[^"]"){2})[^"]*$)/).map(c => c.replace(/^"|"$/g, '').trim());
if (cols.length >= 5) {
const homeS = (cols[5] !== undefined && cols[5] !== "") ? parseInt(cols[5], 10) : null;
const awayS = (cols[6] !== undefined && cols[6] !== "") ? parseInt(cols[6], 10) : null;
parsedGames.push({
date: cols[0],
time: cols[1],
diamond: cols[2],
home: cols[3],
away: cols[4],
homeScore: isNaN(homeS) ? null : homeS,
awayScore: isNaN(awayS) ? null : awayS
});
}
}
if (parsedGames.length > 0) {
masterGames = parsedGames;
} else {
throw new Error("No layout fields detected.");
}
calculateStandingsAndRender();
}
function calculateStandingsAndRender() {
const teams = {};
masterGames.forEach(g => {
if (g.home && !teams[g.home]) teams[g.home] = { name: g.home, w: 0, l: 0, t: 0, pts: 0, rf: 0, ra: 0, diff: 0 };
if (g.away && !teams[g.away]) teams[g.away] = { name: g.away, w: 0, l: 0, t: 0, pts: 0, rf: 0, ra: 0, diff: 0 };
});
masterGames.forEach(g => {
if (g.homeScore !== null && g.awayScore !== null) {
const hs = g.homeScore;
const as = g.awayScore;
teams[g.home].rf += hs;
teams[g.home].ra += as;
teams[g.away].rf += as;
teams[g.away].ra += hs;
if (hs > as) {
teams[g.home].w += 1;
teams[g.home].pts += 2;
teams[g.away].l += 1;
} else if (as > hs) {
teams[g.away].w += 1;
teams[g.away].pts += 2;
teams[g.home].l += 1;
} else {
teams[g.home].t += 1;
teams[g.home].pts += 1;
teams[g.away].t += 1;
teams[g.away].pts += 1;
}
}
});
const standingsArray = Object.values(teams).map(t => {
t.diff = t.rf - t.ra;
return t;
});
standingsArray.sort((a, b) => {
if (b.pts !== a.pts) return b.pts - a.pts;
if (b.diff !== a.diff) return b.diff - a.diff;
return b.rf - a.rf;
});
renderStandingsTable(standingsArray);
renderGamesGrid();
}
function renderStandingsTable(standings) {
const tbody = document.getElementById('standings-body');
tbody.innerHTML = "";
if (standings.length === 0) {
tbody.innerHTML = <tr><td colspan="9" class="text-center">No league configuration teams structural rows discovered.</td></tr>;
return;
}
standings.forEach((team, index) => {
const tr = document.createElement('tr');
tr.innerHTML = `
${index + 1}
${team.name}
${team.w}
${team.l}
${team.t}
${team.pts}
${team.rf}
${team.ra}
${team.diff > 0 ? '+' + team.diff : team.diff}
`;
tbody.appendChild(tr);
});
}
function renderGamesGrid() {
const container = document.getElementById('games-container');
container.innerHTML = "";
const filtered = masterGames.filter(g => {
const isPlayed = g.homeScore !== null && g.awayScore !== null;
if (currentFilter === 'completed') return isPlayed;
if (currentFilter === 'upcoming') return !isPlayed;
return true;
});
if (filtered.length === 0) {
container.innerHTML = <div style="grid-column: 1/-1; text-align: center; color: var(--text-light); padding: 30px;">No matches found matching filter rule parameters.</div>;
return;
}
filtered.forEach(g => {
const isPlayed = g.homeScore !== null && g.awayScore !== null;
const card = document.createElement('div');
card.className = 'game-card';
let statusLabel = <div class="game-status-label">Upcoming Match</div>;
let homeClass = "";
let awayClass = "";
if (isPlayed) {
statusLabel = <div class="game-status-label live">Final Score</div>;
if (g.homeScore > g.awayScore) homeClass = "winner";
if (g.awayScore > g.homeScore) awayClass = "winner";
}
card.innerHTML = <div> <div class="game-header"> <span>🗓️ ${g.date}</span> <span>⏰ ${g.time}</span> <span>📍 ${g.diamond}</span> </div> <div class="game-team-row"> <span>${g.home}</span> <span class="game-score ${homeClass}">${g.homeScore !== null ? g.homeScore : '-'}</span> </div> <div class="game-team-row"> <span>${g.away}</span> <span class="game-score ${awayClass}">${g.awayScore !== null ? g.awayScore : '-'}</span> </div> </div> ${statusLabel};
container.appendChild(card);
});
}
function filterGames(type, btn) {
currentFilter = type;
document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
btn.classList.add('active');
renderGamesGrid();
}
window.onload = fetchLeagueData;
