<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>League Portal & Live Standings</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        .score-input::-webkit-outer-spin-button,
        .score-input::-webkit-inner-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }
        .score-input {
            -moz-appearance: textfield;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800 font-sans antialiased">

    <!-- Header Section -->
    <header class="bg-blue-900 text-white shadow-md">
        <div class="max-w-7xl mx-auto px-4 py-6 flex flex-col md:flex-row justify-between items-center gap-4">
            <div>
                <h1 class="text-3xl font-bold tracking-tight">League Management Hub</h1>
                <p class="text-blue-200 text-sm mt-1">Schedules, Live Standings & Venue Directories</p>
            </div>
            <div class="flex items-center gap-3">
                <button onclick="resetAllScores()" class="bg-red-600 hover:bg-red-700 text-white font-semibold py-2 px-4 rounded transition text-sm shadow">
                    Clear All Scores
                </button>
            </div>
        </div>
    </header>

    <main class="max-w-7xl mx-auto px-4 py-8 grid grid-cols-1 lg:grid-cols-3 gap-8">
        
        <!-- LEFT/CENTER COLUMNS -->
        <div class="lg:col-span-2 space-y-8">
            
            <!-- Weather & Fields Widget Panel -->
            <section class="bg-white p-6 rounded-xl shadow-sm border border-gray-200">
                <h2 class="text-xl font-bold text-gray-900 mb-4 flex items-center gap-2">
                    ☀️ Field Venues & Weather Outlook
                </h2>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
                    <div class="p-4 bg-blue-50 border border-blue-100 rounded-lg flex justify-between items-center">
                        <div>
                            <p class="font-semibold text-blue-900 text-sm">Mississauga Grounds</p>
                            <p class="text-xs text-blue-700 mt-0.5">Dunton & Brickyard Status</p>
                        </div>
                        <div class="text-right">
                            <span class="text-xl font-bold text-blue-900">18°C</span>
                            <span class="block text-[10px] uppercase font-bold text-green-600 tracking-wider">Clear & Playable</span>
                        </div>
                    </div>
                    <div class="p-4 bg-indigo-50 border border-indigo-100 rounded-lg flex justify-between items-center">
                        <div>
                            <p class="font-semibold text-indigo-900 text-sm">Brampton Grounds</p>
                            <p class="text-xs text-indigo-700 mt-0.5">CAA Centre Complex Status</p>
                        </div>
                        <div class="text-right">
                            <span class="text-xl font-bold text-indigo-900">17°C</span>
                            <span class="block text-[10px] uppercase font-bold text-green-600 tracking-wider">Clear & Playable</span>
                        </div>
                    </div>
                </div>

                <p class="text-xs font-semibold uppercase text-gray-400 tracking-wider mb-2">Venue Navigation Directories</p>
                <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 text-xs">
                    <a href="https://www.mississauga.ca/events-and-attractions/parks/dunton-athletic-fields/" target="_blank" class="p-3 bg-gray-50 hover:bg-gray-100 border border-gray-200 rounded block transition text-center">
                        <span class="font-bold text-gray-900 block mb-0.5">Dunton Athletic Fields</span>
                        <span class="text-gray-500">6180 Kennedy Rd, Mississauga</span>
                    </a>
                    <a href="https://www.mississauga.ca/events-and-attractions/parks/brickyard-park/" target="_blank" class="p-3 bg-gray-50 hover:bg-gray-100 border border-gray-200 rounded block transition text-center">
                        <span class="font-bold text-gray-900 block mb-0.5">Brickyard Park</span>
                        <span class="text-gray-500">3061 Clayhill Rd, Mississauga</span>
                    </a>
                    <a href="https://caacentre.com/" target="_blank" class="p-3 bg-gray-50 hover:bg-gray-100 border border-gray-200 rounded block transition text-center">
                        <span class="font-bold text-gray-900 block mb-0.5">CAA Centre Complex</span>
                        <span class="text-gray-500">7575 Kennedy Rd S, Brampton</span>
                    </a>
                </div>
            </section>

            <!-- Schedule Panel -->
            <section class="bg-white rounded-xl shadow-sm border border-gray-200 overflow-hidden">
                <div class="px-6 py-4 bg-gray-100 border-b border-gray-200 flex justify-between items-center flex-wrap gap-2">
                    <h2 class="text-xl font-bold text-gray-900">Interactive League Schedule</h2>
                    <span class="text-xs bg-blue-100 text-blue-800 px-2.5 py-1 rounded-full font-medium">Input scores to update standings live</span>
                </div>

                <div class="divide-y divide-gray-100" id="schedule-container"></div>
            </section>
        </div>

        <!-- RIGHT COLUMN -->
        <div class="lg:col-span-1">
            <div class="bg-white rounded-xl shadow-sm border border-gray-200 overflow-hidden lg:sticky lg:top-8">
                <div class="px-6 py-4 bg-gray-100 border-b border-gray-200">
                    <h2 class="text-xl font-bold text-gray-900">Live Standings Leaderboard</h2>
                    <p class="text-xs text-gray-500 mt-0.5">Win: 2 PTS | Tie: 1 PT | Loss: 0 PTS</p>
                </div>
                
                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse">
                        <thead>
                            <tr class="bg-gray-50 text-gray-400 text-[11px] font-bold uppercase tracking-wider border-b border-gray-100">
                                <th class="py-3 px-4">Team</th>
                                <th class="py-3 px-2 text-center">W-L-T</th>
                                <th class="py-3 px-2 text-center">Diff</th>
                                <th class="py-3 px-4 text-center text-blue-900">Pts</th>
                            </tr>
                        </thead>
                        <tbody id="standings-rows" class="divide-y divide-gray-100 text-sm"></tbody>
                    </table>
                </div>

                <div class="p-4 bg-gray-50 border-t border-gray-100 text-xs text-gray-400 text-center">
                    Tie-breaker logic ranks higher Run Differential (RD) if points match.
                </div>
            </div>
        </div>

    </main>

    <script>
        const matches = [
            { id: 1, date: "10/1/2026", time: "7:00 PM", diamond: "Dunton 2", home: "Team Zeshan", away: "Team Ali" },
            { id: 2, date: "10/1/2026", time: "7:00 PM", diamond: "Dunton 3", home: "Team Yasir", away: "Team Yusuf" },
            { id: 3, date: "10/1/2026", time: "7:00 PM", diamond: "Dunton 4", home: "Team Emad", away: "Team Zohaid" },
            { id: 4, date: "10/1/2026", time: "8:30 PM", diamond: "Dunton 2", home: "Team Ali", away: "Team Emad" },
            { id: 5, date: "10/1/2026", time: "8:30 PM", diamond: "Dunton 3", home: "Team Yusuf", away: "Team Zeshan" },
            { id: 6, date: "10/1/2026", time: "8:30 PM", diamond: "Dunton 4", home: "Team Zohaid", away: "Team Yasir" },
            { id: 7, date: "10/4/2026", time: "6:30 PM", diamond: "Brickyard 1", home: "Team Yasir", away: "Team Ali" },
            { id: 8, date: "10/4/2026", time: "6:30 PM", diamond: "Brickyard 2", home: "Team Yusuf", away: "Team Emad" },
            { id: 9, date: "10/4/2026", time: "8:00 PM", diamond: "Brickyard 1", home: "Team Zohaid", away: "Team Yasir" },
            { id: 10, date: "10/4/2026", time: "8:00 PM", diamond: "Brickyard 2", home: "Team Zeshan", away: "Team Yusuf" },
            { id: 11, date: "10/4/2026", time: "9:30 PM", diamond: "Brickyard 1", home: "Team Ali", away: "Team Zohaid" },
            { id: 12, date: "10/4/2026", time: "9:30 PM", diamond: "Brickyard 2", home: "Team Emad", away: "Team Zeshan" },
            { id: 13, date: "10/8/2026", time: "7:00 PM", diamond: "CAA Red", home: "Team Yasir", away: "Team Yusuf" },
            { id: 14, date: "10/8/2026", time: "7:00 PM", diamond: "CAA Yellow", home: "Team Zeshan", away: "Team Emad" },
            { id: 15, date: "10/8/2026", time: "7:00 PM", diamond: "CAA Green", home: "Team Ali", away: "Team Zohaid" },
            { id: 16, date: "10/8/2026", time: "8:30 PM", diamond: "CAA Red", home: "Team Emad", away: "Team Yasir" },
            { id: 17, date: "10/8/2026", time: "8:30 PM", diamond: "CAA Yellow", home: "Team Zohaid", away: "Team Zeshan" },
            { id: 18, date: "10/8/2026", time: "8:30 PM", diamond: "CAA Green", home: "Team Yusuf", away: "Team Ali" },
            { id: 19, date: "10/15/2026", time: "7:00 PM", diamond: "CAA Red", home: "Team Zohaid", away: "Team Zeshan" },
            { id: 20, date: "10/15/2026", time: "7:00 PM", diamond: "CAA Yellow", home: "Team Emad", away: "Team Yusuf" },
            { id: 21, date: "10/15/2026", time: "7:00 PM", diamond: "CAA Green", home: "Team Yasir", away: "Team Ali" },
            { id: 22, date: "10/15/2026", time: "8:30 PM", diamond: "CAA Red", home: "Team Yusuf", away: "Team Zohaid" },
            { id: 23, date: "10/15/2026", time: "8:30 PM", diamond: "CAA Yellow", home: "Team Ali", away: "Team Emad" },
            { id: 24, date: "10/15/2026", time: "8:30 PM", diamond: "CAA Green", home: "Team Zeshan", away: "Team Yasir" }
        ];

        const teamsList = [
            "Team Zeshan", "Team Ali", "Team Yasir", "Team Yusuf", "Team Emad", "Team Zohaid"
        ];

        let scoresState = {};

        function initApp() {
            loadSavedScores();
            renderSchedule();
            calculateAndRenderStandings();
        }

        function saveScores() {
            localStorage.setItem('league_scores_state', JSON.stringify(scoresState));
        }

        function loadSavedScores() {
            const saved = localStorage.getItem('league_scores_state');
            if (saved) {
                try { scoresState = JSON.parse(saved); } catch (e) { scoresState = {}; }
            }
        }

        function renderSchedule() {
            const container = document.getElementById("schedule-container");
            container.innerHTML = "";

            const groupedByDate = {};
            matches.forEach(match => {
                if (!groupedByDate[match.date]) {
                    groupedByDate[match.date] = [];
                }
                groupedByDate[match.date].push(match);
            });

            for (const date in groupedByDate) {
                const dateHeader = document.createElement("div");
                dateHeader.className = "bg-gray-50 px-6 py-2 text-xs font-bold text-gray-500 uppercase tracking-wider border-y border-gray-100";
                dateHeader.innerText = date;
                container.appendChild(dateHeader);

                groupedByDate[date].forEach(match => {
                    const homeVal = scoresState[`${match.id}_home`] !== undefined ? scoresState[`${match.id}_home`] : "";
                    const awayVal = scoresState[`${match.id}_away`] !== undefined ? scoresState[`${match.id}_away`] : "";

                    const row = document.createElement("div");
                    row.className = "p-6 hover:bg-gray-50 transition flex flex-col sm:flex-row sm:items-center justify-between gap-4";
                    row.innerHTML = `
                        <div class="flex-1">
                            <div class="flex items-center gap-2 text-xs text-gray-500 font-medium mb-1">
                                <span>⏰ ${match.time}</span>
                                <span class="text-gray-300">•</span>
                                <span class="px-2 py-0.5 bg-gray-100 border border-gray-200 text-gray-700 rounded font-semibold text-[11px]">${match.diamond}</span>
                            </div>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 text-sm font-semibold text-gray-900 mt-2">
                                <div class="flex items-center justify-between sm:justify-start gap-4 p-2 bg-gray-50 sm:bg-transparent rounded">
                                    <span class="min-w-[100px]"><span class="text-xs font-normal text-gray-400 mr-1.5">[H]</span>${match.home}</span>
                                    <input type="number" min="0" placeholder="-" 
                                        value="${homeVal}"
                                        oninput="updateScore(${match.id}, 'home', this.value)"
                                        class="score-input w-12 text-center bg-white border border-gray-300 rounded p-1 font-bold focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                                </div>
                                <div class="flex items-center justify-between sm:justify-start gap-4 p-2 bg-gray-50 sm:bg-transparent rounded">
                                    <span class="min-w-[100px]"><span class="text-xs font-normal text-gray-400 mr-1.5">[A]</span>${match.away}</span>
                                    <input type="number" min="0" placeholder="-" 
                                        value="${awayVal}"
                                        oninput="updateScore(${match.id}, 'away', this.value)"
                                        class="score-input w-12 text-center bg-white border border-gray-300 rounded p-1 font-bold focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
                                </div>
                            </div>
                        </div>
                    `;
                    container.appendChild(row);
                });
            }
        }

        function updateScore(matchId, side, value) {
            if (value.trim() === "") {
                delete scoresState[`${matchId}_${side}`];
            } else {
                scoresState[`${matchId}_${side}`] = parseInt(value, 10) || 0;
            }
            saveScores();
            calculateAndRenderStandings();
        }

        function calculateAndRenderStandings() {
            const standings = {};
            teamsList.forEach(team => {
                standings[team] = { wins: 0, losses: 0, ties: 0, rf: 0, ra: 0, diff: 0, pts: 0 };
            });

            matches.forEach(match => {
                const homeScore = scoresState[`${match.id}_home`];
                const awayScore = scoresState[`${match.id}_away`];

                if (homeScore !== undefined && awayScore !== undefined) {
                    const h = parseInt(homeScore, 10);
                    const a = parseInt(awayScore, 10);

                    standings[match.home].rf += h;
                    standings[match.home].ra += a;
                    standings[match.away].rf += a;
                    standings[match.away].ra += h;

                    if (h > a) {
                        standings[match.home].wins += 1;
                        standings[match.home].pts += 2;
                        standings[match.away].losses += 1;
                    } else if (a > h) {
                        standings[match.away].wins += 1;
                        standings[match.away].pts += 2;
                        standings[match.home].losses += 1;
                    } else {
                        standings[match.home].ties += 1;
                        standings[match.home].pts += 1;
                        standings[match.away].ties += 1;
                        standings[match.away].pts += 1;
                    }
                }
            });

            const sortedTeams = Object.keys(standings).map(teamName => {
                const data = standings[teamName];
                data.diff = data.rf - data.ra;
                return { name: teamName, ...data };
            });

            sortedTeams.sort((teamA, teamB) => {
                if (teamB.pts !== teamA.pts) {
                    return teamB.pts - teamA.pts;
                }
                return teamB.diff - teamA.diff;
            });

            const tbody = document.getElementById("standings-rows");
            tbody.innerHTML = "";

            sortedTeams.forEach(team => {
                const row = document.createElement("tr");
                row.className = "hover:bg-gray-50 transition border-b border-gray-100 last:border-0";
                
                const diffClass = team.diff > 0 ? "text-green-600 font-semibold" : (team.diff < 0 ? "text-red-500" : "text-gray-400");
                const formattedDiff = team.diff > 0 ? `+${team.diff}` : team.diff;

                row.innerHTML = `
                    <td class="py-3 px-4 font-bold text-gray-900">${team.name}</td>
                    <td class="py-3 px-2 text-center text-gray-600">${team.wins}-${team.losses}-${team.ties}</td>
                    <td class="py-3 px-2 text-center ${diffClass}">${formattedDiff}</td>
                    <td class="py-3 px-4 text-center font-bold text-blue-900 text-base bg-blue-50/50">${team.pts}</td>
                `;
                tbody.appendChild(row);
            });
        }

        function resetAllScores() {
            if (confirm("Are you sure you want to completely clear all saved match scores and reset the standings table?")) {
                scoresState = {};
                saveScores();
                renderSchedule();
                calculateAndRenderStandings();
            }
        }

        window.addEventListener("DOMContentLoaded", initApp);
    </script>
</body>
</html>
