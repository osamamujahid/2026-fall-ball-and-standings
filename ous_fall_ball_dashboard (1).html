<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2026 OUS Fall Ball Dashboard</title>
    <style>
        :root {
            --primary: #1e3a8a;
            --primary-hover: #172554;
            --accent: #f59e0b;
            --bg-main: #f8fafc;
            --bg-card: #ffffff;
            --text-main: #1e293b;
            --text-muted: #64748b;
            --border: #e2e8f0;
            --win: #22c55e;
            --loss: #ef4444;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-main);
            padding: 2rem 1rem;
            line-height: 1.5;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 2.5rem;
            padding-bottom: 1.5rem;
            border-bottom: 2px solid var(--border);
        }

        header h1 {
            color: var(--primary);
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
        }

        header p {
            color: var(--text-muted);
            font-size: 1.1rem;
        }

        .section-title {
            font-size: 1.5rem;
            color: var(--primary);
            margin: 2rem 0 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        /* Standings Table Styling */
        .table-container {
            background: var(--bg-card);
            border-radius: 8px;
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1);
            overflow-x: auto;
            margin-bottom: 2rem;
            border: 1px solid var(--border);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
            min-width: 600px;
        }

        th {
            background-color: var(--primary);
            color: white;
            padding: 1rem;
            font-weight: 600;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        td {
            padding: 1rem;
            border-bottom: 1px solid var(--border);
            font-size: 0.95rem;
        }

        tr:last-child td {
            border-bottom: none;
        }

        tr:nth-child(even) {
            background-color: #f8fafc;
        }

        .rank-col { font-weight: bold; width: 60px; text-align: center; }
        .team-col { font-weight: 600; color: #0f172a; }
        .num-col { text-align: center; width: 60px; }
        .bold-num { font-weight: bold; text-align: center; }

        /* Schedule Layout */
        .week-container {
            margin-bottom: 2.5rem;
        }

        .week-title {
            background: #e2e8f0;
            color: #334155;
            padding: 0.75rem 1rem;
            border-radius: 6px;
            font-weight: 700;
            margin-bottom: 1rem;
            font-size: 1.1rem;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 1rem;
        }

        .match-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 1rem;
            box-shadow: 0 2px 4px rgb(0 0 0 / 0.05);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .match-meta {
            display: flex;
            justify-content: space-between;
            font-size: 0.8rem;
            color: var(--text-muted);
            margin-bottom: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            font-weight: 600;
        }

        .diamond-tag {
            background: #edd1d1;
            color: #991b1b;
            padding: 0.1rem 0.4rem;
            border-radius: 4px;
            font-size: 0.75rem;
        }

        .match-team {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.25rem 0;
            font-size: 1.05rem;
        }

        .match-team.winner {
            font-weight: 700;
            color: #000;
        }

        .match-team.loser {
            color: var(--text-muted);
        }

        .score-box {
            font-variant-numeric: tabular-nums;
            font-weight: bold;
            min-width: 25px;
            text-align: right;
        }

        .vs-divider {
            text-align: center;
            color: var(--text-muted);
            font-size: 0.85rem;
            margin: 0.5rem 0;
            font-style: italic;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>2026 OUS Fall Ball</h1>
        <p>League Dashboard, Automated Standings & Schedules</p>
    </header>

    <div class="section-title">🏆 Current Standings</div>
    <div class="table-container">
        <table>
            <thead>
                <tr>
                    <th class="rank-col">Rank</th>
                    <th class="team-col">Team</th>
                    <th class="num-col">GP</th>
                    <th class="num-col">W</th>
                    <th class="num-col">L</th>
                    <th class="num-col">T</th>
                    <th class="num-col">RF</th>
                    <th class="num-col">RA</th>
                    <th class="num-col">GD</th>
                    <th class="bold-num">PTS</th>
                </tr>
            </thead>
            <tbody id="standings-body">
                <!-- Injected via JavaScript -->
            </tbody>
        </table>
    </div>

    <div class="section-title">📅 Schedule & Match Results</div>
    <div id="schedule-container">
        <!-- Injected via JavaScript -->
    </div>
</div>

<script>
    // =========================================================================
    // ✏️ ENTER/EDIT GAME SCORES IN THIS ARRAY
    // -------------------------------------------------------------------------
    // To record scores, change the 'homeScore: null' or 'awayScore: null' 
    // values to numbers (e.g., homeScore: 18, awayScore: 17).
    // The standings, points, and differentials update automatically on save.
    // =========================================================================
    const gamesData = [
        // Week 1: Oct 01, 2026
        { date: "2026-10-01", week: "Week 1: Thursday, October 1, 2026", time: "7:00 PM", diamond: "Dunton 2", home: "Team Zeshan", away: "Team Ali", homeScore: 18, awayScore: 17 },
        { date: "2026-10-01", week: "Week 1: Thursday, October 1, 2026", time: "7:00 PM", diamond: "Dunton 3", home: "Team Yasir", away: "Team Yusuf", homeScore: 17, awayScore: 14 },
        { date: "2026-10-01", week: "Week 1: Thursday, October 1, 2026", time: "7:00 PM", diamond: "Dunton 4", home: "Team Emad", away: "Team Zohaid", homeScore: 11, awayScore: 8 },
        { date: "2026-10-01", week: "Week 1: Thursday, October 1, 2026", time: "8:30 PM", diamond: "Dunton 2", home: "Team Ali", away: "Team Emad", homeScore: 16, awayScore: 20 },
        { date: "2026-10-01", week: "Week 1: Thursday, October 1, 2026", time: "8:30 PM", diamond: "Dunton 3", home: "Team Yusuf", away: "Team Zeshan", homeScore: 17, awayScore: 16 },
        { date: "2026-10-01", week: "Week 1: Thursday, October 1, 2026", time: "8:30 PM", diamond: "Dunton 4", home: "Team Zohaid", away: "Team Yasir", homeScore: 6, awayScore: 20 },

        // Week 2: Oct 04, 2026
        { date: "2026-10-04", week: "Week 2: Sunday, October 4, 2026", time: "6:30 PM", diamond: "Brickyard 1", home: "Team Yasir", away: "Team Ali", homeScore: null, awayScore: null },
        { date: "2026-10-04", week: "Week 2: Sunday, October 4, 2026", time: "6:30 PM", diamond: "Brickyard 2", home: "Team Yusuf", away: "Team Emad", homeScore: null, awayScore: null },
        { date: "2026-10-04", week: "Week 2: Sunday, October 4, 2026", time: "8:00 PM", diamond: "Brickyard 1", home: "Team Zohaid", away: "Team Yasir", homeScore: null, awayScore: null },
        { date: "2026-10-04", week: "Week 2: Sunday, October 4, 2026", time: "8:00 PM", diamond: "Brickyard 2", home: "Team Zeshan", away: "Team Yusuf", homeScore: null, awayScore: null },
        { date: "2026-10-04", week: "Week 2: Sunday, October 4, 2026", time: "9:30 PM", diamond: "Brickyard 1", home: "Team Ali", away: "Team Zohaid", homeScore: null, awayScore: null },
        { date: "2026-10-04", week: "Week 2: Sunday, October 4, 2026", time: "9:30 PM", diamond: "Brickyard 2", home: "Team Emad", away: "Team Zeshan", homeScore: null, awayScore: null },

        // Week 3: Oct 08, 2026
        { date: "2026-10-08", week: "Week 3: Thursday, October 8, 2026", time: "7:00 PM", diamond: "CAA Red", home: "Team Yasir", away: "Team Yusuf", homeScore: null, awayScore: null },
        { date: "2026-10-08", week: "Week 3: Thursday, October 8, 2026", time: "7:00 PM", diamond: "CAA Yellow", home: "Team Zeshan", away: "Team Emad", homeScore: null, awayScore: null },
        { date: "2026-10-08", week: "Week 3: Thursday, October 8, 2026", time: "7:00 PM", diamond: "CAA Green", home: "Team Ali", away: "Team Zohaid", homeScore: null, awayScore: null },
        { date: "2026-10-08", week: "Week 3: Thursday, October 8, 2026", time: "8:30 PM", diamond: "CAA Red", home: "Team Emad", away: "Team Yasir", homeScore: null, awayScore: null },
        { date: "2026-10-08", week: "Week 3: Thursday, October 8, 2026", time: "8:30 PM", diamond: "CAA Yellow", home: "Team Zohaid", away: "Team Zeshan", homeScore: null, awayScore: null },
        { date: "2026-10-08", week: "Week 3: Thursday, October 8, 2026", time: "8:30 PM", diamond: "CAA Green", home: "Team Yusuf", away: "Team Ali", homeScore: null, awayScore: null },

        // Week 4: Oct 15, 2026
        { date: "2026-10-15", week: "Week 4: Thursday, October 15, 2026", time: "7:00 PM", diamond: "CAA Red", home: "Team Zohaid", away: "Team Zeshan", homeScore: null, awayScore: null },
        { date: "2026-10-15", week: "Week 4: Thursday, October 15, 2026", time: "7:00 PM", diamond: "CAA Yellow", home: "Team Emad", away: "Team Yusuf", homeScore: null, awayScore: null },
        { date: "2026-10-15", week: "Week 4: Thursday, October 15, 2026", time: "7:00 PM", diamond: "CAA Green", home: "Team Yasir", away: "Team Ali", homeScore: null, awayScore: null },
        { date: "2026-10-15", week: "Week 4: Thursday, October 15, 2026", time: "8:30 PM", diamond: "CAA Red", home: "Team Yusuf", away: "Team Zohaid", homeScore: null, awayScore: null },
        { date: "2026-10-15", week: "Week 4: Thursday, October 15, 2026", time: "8:30 PM", diamond: "CAA Yellow", home: "Team Ali", away: "Team Emad", homeScore: null, awayScore: null },
        { date: "2026-10-15", week: "Week 4: Thursday, October 15, 2026", time: "8:30 PM", diamond: "CAA Green", home: "Team Zeshan", away: "Team Yasir", homeScore: null, awayScore: null }
    ];

    // Core Processing Engine
    function renderDashboard() {
        const teams = {};

        // Find all unique teams listed
        gamesData.forEach(g => {
            if (!teams[g.home]) teams[g.home] = { name: g.home, gp: 0, w: 0, l: 0, t: 0, rf: 0, ra: 0, gd: 0, pts: 0 };
            if (!teams[g.away]) teams[g.away] = { name: g.away, gp: 0, w: 0, l: 0, t: 0, rf: 0, ra: 0, gd: 0, pts: 0 };
        });

        // Compute metrics based on updated score cards
        gamesData.forEach(g => {
            if (g.homeScore !== null && g.awayScore !== null) {
                const hs = parseInt(g.homeScore);
                const as = parseInt(g.awayScore);

                teams[g.home].gp++;
                teams[g.away].gp++;
                teams[g.home].rf += hs;
                teams[g.home].ra += as;
                teams[g.away].rf += as;
                teams[g.away].ra += hs;

                if (hs > as) {
                    teams[g.home].w++;
                    teams[g.home].pts += 2;
                    teams[g.away].l++;
                } else if (as > hs) {
                    teams[g.away].w++;
                    teams[g.away].pts += 2;
                    teams[g.home].l++;
                } else {
                    teams[g.home].t++;
                    teams[g.away].t++;
                    teams[g.home].pts += 1;
                    teams[g.away].pts += 1;
                }
            }
        });

        // Run details logic
        Object.values(teams).forEach(t => {
            t.gd = t.rf - t.ra;
        });

        // Sort via Tie-breaker logic (Points -> Run Diff -> Runs For)
        const sortedTeams = Object.values(teams).sort((a, b) => {
            if (b.pts !== a.pts) return b.pts - a.pts;
            if (b.gd !== a.gd) return b.gd - a.gd;
            return b.rf - a.rf;
        });

        // Render Standings
        const standingsBody = document.getElementById('standings-body');
        standingsBody.innerHTML = '';
        sortedTeams.forEach((team, index) => {
            const tr = document.createElement('tr');
            tr.innerHTML = `
                <td class="rank-col">${index + 1}</td>
                <td class="team-col">${team.name}</td>
                <td class="num-col">${team.gp}</td>
                <td class="num-col">${team.w}</td>
                <td class="num-col">${team.l}</td>
                <td class="num-col">${team.t}</td>
                <td class="num-col">${team.rf}</td>
                <td class="num-col">${team.ra}</td>
                <td class="num-col">${team.gd > 0 ? '+' + team.gd : team.gd}</td>
                <td class="bold-num">${team.pts}</td>
            `;
            standingsBody.appendChild(tr);
        });

        // Render Schedule grouped by operational weeks
        const scheduleContainer = document.getElementById('schedule-container');
        scheduleContainer.innerHTML = '';

        const weeks = {};
        gamesData.forEach(g => {
            if (!weeks[g.week]) weeks[g.week] = [];
            weeks[g.week].push(g);
        });

        Object.keys(weeks).forEach(weekName => {
            const weekDiv = document.createElement('div');
            weekDiv.className = 'week-container';
            weekDiv.innerHTML = `<div class="week-title">${weekName}</div>`;

            const gridDiv = document.createElement('div');
            gridDiv.className = 'grid';

            weeks[weekName].forEach(g => {
                const card = document.createElement('div');
                card.className = 'match-card';

                let matchBody = '';
                if (g.homeScore !== null && g.awayScore !== null) {
                    const hs = parseInt(g.homeScore);
                    const as = parseInt(g.awayScore);
                    const homeWinClass = hs > as ? 'winner' : (hs < as ? 'loser' : '');
                    const awayWinClass = as > hs ? 'winner' : (as < hs ? 'loser' : '');

                    matchBody = `
                        <div class="match-team ${homeWinClass}">
                            <span>🏠 ${g.home}</span>
                            <span class="score-box">${hs}</span>
                        </div>
                        <div class="match-team ${awayWinClass}">
                            <span>✈️ ${g.away}</span>
                            <span class="score-box">${as}</span>
                        </div>
                    `;
                } else {
                    matchBody = `
                        <div class="match-team"><span>🏠 ${g.home}</span></div>
                        <div class="vs-divider">vs</div>
                        <div class="match-team"><span>✈️ ${g.away}</span></div>
                    `;
                }

                card.innerHTML = `
                    <div>
                        <div class="match-meta">
                            <span>🕒 ${g.time}</span>
                            <span class="diamond-tag">💎 ${g.diamond}</span>
                        </div>
                        ${matchBody}
                    </div>
                `;
                gridDiv.appendChild(card);
            });

            weekDiv.appendChild(gridDiv);
            scheduleContainer.appendChild(weekDiv);
        });
    }

    // Run Engine Initializer
    window.onload = renderDashboard;
</script>

</body>
</html>
