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
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>League Dashboard</h1>
        <p>Hardcoded Scores & Standings tracking platform</p>
    </header>

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
                    <!-- Rendered via JavaScript -->
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
    let currentFilter = 'all';

    // 📋 UPDATE SCORES HERE: 
    // Set homeScore and awayScore values to numbers (e.g., 12, 5) to save played games. 
    // Leave them as null if the match hasn't happened yet!
    const masterGames = [
        { date: "10/1/2026", time: "7:00 PM", diamond: "Dunton 2", home: "Team Zeshan", away: "Team Ali", homeScore: 17, awayScore: 18 },
        { date: "10/1/2026", time: "7:00 PM", diamond: "Dunton 3", home: "Team Yasir", away: "Team Yusuf", homeScore: 17, awayScore: 14 },
        { date: "10/1/2026", time: "7:00 PM", diamond: "Dunton 4", home: "Team Emad", away: "Team Zohaid", homeScore: 8, awayScore: 11 },
        { date: "10/1/2026", time: "8:30 PM", diamond: "Dunton 2", home: "Team Ali", away: "Team Emad", homeScore: 20, awayScore: 16 },
        { date: "10/1/2026", time: "8:30 PM", diamond: "Dunton 3", home: "Team Yusuf", away: "Team Zeshan", homeScore: 16, awayScore: 17 },
        { date: "10/1/2026", time: "8:30 PM", diamond: "Dunton 4", home: "Team Zohaid", away: "Team Yasir", homeScore: 20, awayScore: 7 },
        { date: "10/4/2026", time: "6:30 PM", diamond: "Brickyard 1", home: "Team Yasir", away: "Team Ali", homeScore: null, awayScore: null },
        { date: "10/4/2026", time: "6:30 PM", diamond: "Brickyard 2", home: "Team Yusuf", away: "Team Emad", homeScore: null, awayScore: null },
        { date: "10/4/2026", time: "8:00 PM", diamond: "Brickyard 1", home: "Team Zohaid", away: "Team Yasir", homeScore: null, awayScore: null },
        { date: "10/4/2026", time: "8:00 PM", diamond: "Brickyard 2", home: "Team Zeshan", away: "Team Yusuf", homeScore: null, awayScore: null },
        { date: "10/4/2026", time: "9:30 PM", diamond: "Brickyard 1", home: "Team Ali", away: "Team Zohaid", homeScore: null, awayScore: null },
        { date: "10/4/2026", time: "9:30 PM", diamond: "Brickyard 2", home: "Team Emad", away: "Team Zeshan", homeScore: null, awayScore: null },
        { date: "10/8/2026", time: "7:00 PM", diamond: "CAA Red", home: "Team Yasir", away: "Team Yusuf", homeScore: null, awayScore: null },
        { date: "10/8/2026", time: "7:00 PM", diamond: "CAA Yellow", home: "Team Zeshan", away: "Team Emad", homeScore: null, awayScore: null },
        { date: "10/8/2026", time: "7:00 PM", diamond: "CAA Green", home: "Team Ali", away: "Team Zohaid", homeScore: null, awayScore: null },
        { date: "10/8/2026", time: "8:30 PM", diamond: "CAA Red", home: "Team Emad", away: "Team Yasir", homeScore: null, awayScore: null },
        { date: "10/8/2026", time: "8:30 PM", diamond: "CAA Yellow", home: "Team Zohaid", away: "Team Zeshan", homeScore: null, awayScore: null },
        { date: "10/8/2026", time: "8:30 PM", diamond: "CAA Green", home: "Team Yusuf", away: "Team Ali", homeScore: null, awayScore: null },
        { date: "10/15/2026", time: "7:00 PM", diamond: "CAA Red", home: "Team Zohaid", away: "Team Zeshan", homeScore: null, awayScore: null },
        { date: "10/15/2026", time: "7:00 PM", diamond: "CAA Yellow", home: "Team Emad", away: "Team Yusuf", homeScore: null, awayScore: null },
        { date: "10/15/2026", time: "7:00 PM", diamond: "CAA Green", home: "Team Yasir", away: "Team Ali", homeScore: null, awayScore: null },
Use code with caution.
{ date: "10/15/2026", time: "8:30 PM", diamond: "CAA Red", home: "Team Yusuf", away: "Team Zohaid", homeScore: null, awayScore: null },
{ date: "10/15/2026", time: "8:30 PM", diamond: "CAA Yellow", home: "Team Ali", away: "Team Emad", homeScore: null, awayScore: null },
{ date: "10/15/2026", time: "8:30 PM", diamond: "CAA Green", home: "Team Zeshan", away: "Team Yasir", homeScore: null, awayScore: null }
];
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
// Sorting rule: Points -> Run Differential -> Runs For
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
tbody.innerHTML = <tr><td colspan="9" class="text-center">No league teams detected.</td></tr>;
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
container.innerHTML = <div style="grid-column: 1/-1; text-align: center; color: var(--text-light); padding: 30px;">No matches found matching filter parameters.</div>;
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
window.onload = calculateStandingsAndRender;
