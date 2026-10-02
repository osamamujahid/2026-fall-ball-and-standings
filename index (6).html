<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>League Portal & Live Standings (Google Sheets Sync)</title>
    <!-- Tailwind CSS for modern, clean UI layout styling -->
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
</head>
<body class="bg-gray-50 text-gray-800 font-sans antialiased">

    <!-- Header Section -->
    <header class="bg-blue-900 text-white shadow-md">
        <div class="max-w-7xl mx-auto px-4 py-6 flex flex-col md:flex-row justify-between items-center gap-4">
            <div>
                <h1 class="text-3xl font-bold tracking-tight">League Management Hub</h1>
                <p class="text-blue-200 text-sm mt-1">Live Standings Syncing Directly from Google Sheets</p>
            </div>
            <div id="sync-badge" class="bg-blue-800 border border-blue-700 px-3 py-1.5 rounded text-xs flex items-center gap-2">
                <span class="w-2 h-2 rounded-full bg-yellow-400 animate-pulse" id="sync-dot"></span>
                <span id="sync-text">Connecting to Google Sheet...</span>
            </div>
        </div>
    </header>

    <main class="max-w-7xl mx-auto px-4 py-8 space-y-8">

        <!-- SETUP INSTRUCTIONS CALLOUT -->
        <section class="bg-amber-50 border border-amber-200 rounded-xl p-5 text-sm text-amber-900 space-y-2">
            <h3 class="font-bold text-amber-950 flex items-center gap-2">⚙️ How to Connect Your Google Sheet:</h3>
            <ol class="list-decimal pl-5 space-y-1">
                <li>Create a <strong>Google Sheet</strong> with 3 columns named exactly: <code class="bg-amber-100 px-1 rounded font-bold">GameID</code>, <code class="bg-amber-100 px-1 rounded font-bold">HomeScore</code>, and <code class="bg-amber-100 px-1 rounded font-bold">AwayScore</code>.</li>
                <li>List your Game IDs from <strong>1 to 24</strong> down the rows and fill in scores as games conclude.</li>
                <li>In Google Sheets, go to <strong>File &gt; Share &gt; Publish to web</strong>. Select the entire document as a <strong>CSV</strong> file, and hit publish.</li>
                <li>Paste that published CSV link directly inside the script section of this file (look for <code class="bg-amber-100 px-1 rounded font-bold">YOUR_PUBLISHED_CSV_LINK_HERE</code> around line 150).</li>
            </ol>
        </section>

        <!-- TOP SECTION: Standings Table Leaderboard (Full Width, Ranked at top) -->
        <section class="bg-white rounded-xl shadow-sm border border-gray-200 overflow-hidden">
            <div class="px-6 py-4 bg-gray-100 border-b border-gray-200">
                <h2 class="text-xl font-bold text-gray-900">Live Standings Leaderboard</h2>
                <p class="text-xs text-gray-500 mt-0.5">Calculated from Google Sheets Data • Win: 2 PTS | Tie: 1 PT | Loss: 0 PTS</p>
            </div>
            
            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse">
                    <thead>
                        <tr class="bg-gray-50 text-gray-500 text-[11px] font-bold uppercase tracking-wider border-b border-gray-200 text-center">
                            <th class="py-3 px-3 text-left w-12">Pos</th>
                            <th class="py-3 px-4 text-left">Team</th>
                            <th class="py-3 px-2">GP</th>
                            <th class="py-3 px-2">W</th>
                            <th class="py-3 px-2">T</th>
                            <th class="py-3 px-2">L</th>
                            <th class="py-3 px-2">RS</th>
                            <th class="py-3 px-2">RA</th>
                            <th class="py-3 px-2">Diff</th>
                            <th class="py-3 px-4 text-blue-950 bg-blue-50/50">PTS</th>
                        </tr>
                    </thead>
                    <tbody id="standings-rows" class="divide-y divide-gray-100 text-sm text-center">
                        <tr>
                            <td colspan="10" class="py-8 text-gray-400 text-xs italic">Waiting for sheet data sync...</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

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
                        <span class="block text-[10px] uppercase font-bold text-green-600 tracking-wider">Playable</span>
                    </div>
                </div>
                <div class="p-4 bg-indigo-50 border border-indigo-100 rounded-lg flex justify-between items-center">
                    <div>
                        <p class="font-semibold text-indigo-900 text-sm">Brampton Grounds</p>
                        <p class="text-xs text-indigo-700 mt-0.5">CAA Centre Complex Status</p>
                    </div>
                    <div class="text-right">
                        <span class="text-xl font-bold text-indigo-900">17°C</span>
                        <span class="block text-[10px] uppercase font-bold text-green-600 tracking-wider">Playable</span>
                    </div>
                </div>
            </div>

            <!-- Navigation Directories -->
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

        <!-- BOTTOM SECTION: Schedule & Search Panel -->
        <section class="bg-white rounded-xl shadow-sm border border-gray-200 overflow-hidden">
            <div class="px-6 py-4 bg-gray-100 border-b border-gray-200 flex flex-col md:flex-row md:items-center justify-between gap-4">
                <div>
                    <h2 class="text-xl font-bold text-gray-900">League Schedule Tracker</h2>
                    <p class="text-xs text-gray-500 mt-0.5">Scores display directly from your published Google Sheet</p>
                </div>
                <div class="w-full md:w-72">
                    <input type="text" id="schedule-search" oninput="filterSchedule(this.value)" placeholder="🔍 Search team, diamond, or date..." class="w-full text-sm bg-white border border-gray-300 rounded-lg px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500 shadow-sm">
                </div>
            </div>

            <div class="divide-y divide-gray-100" id="schedule-container">
                <!-- Mapped schedule elements with scores load dynamically -->
            </div>
        </section>

    </main>

    <script>
        // REPLACE THIS URL with your actual Google Sheet Published Web CSV address link
        const GOOGLE_SHEET_CSV_URL = "https://docs.google.com/spreadsheets/d/e/2PACX-1vTuH2caMN-qBJjKs49kJ-nC_JfHsGS2rjZGO87XE14u-2ijLFbEJ05uIwcVfqTkKmuJiqNm_fxFCNqb/pubhtml";

        // Master local database schedule definitions
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

        const teamsList = ["Team Zeshan", "Team Ali", "Team Yasir", "Team Yusuf", "Team Emad", "Team Zohaid"];
        let scoresState = {}; 
        let currentSearchQuery = "";

        async function fetchGoogleSheetsData() {
            if (!GOOGLE_SHEET_CSV_URL || GOOGLE_SHEET_CSV_URL === "YOUR_PUBLISHED_CSV_LINK_HERE") {
                setSyncStatus("demo");
                renderSchedule();
                calculateAndRenderStandings();
                return;
            }

            try {
                // Add a cache-buster timestamp to ensure live sheet pulling from the cloud
                const response = await fetch(`${GOOGLE_SHEET_CSV_URL}?t=${new Date().getTime()}`);
                if (!response.ok) throw new Error("Network issues reaching sheet endpoint.");
                
                const csvText = await response.text();
                parseCsvScores(csvText);
                setSyncStatus("success");
            } catch (error) {
                console.error(error);
                setSyncStatus("error");
            }

            renderSchedule();
            calculateAndRenderStandings();
        }

        function parseCsvScores(text) {
            const rows = text.split(/\r?\n/);
            if(rows.length < 2) return;

            // Simple header index lookup matching columns
            const headers = rows[0].split(",").map(h => h.trim().toLowerCase());
            const idIdx = headers.indexOf("gameid");
            const homeIdx = headers.indexOf("homescore");
            const awayIdx = headers.indexOf("awayscore");

            if(idIdx === -1 || homeIdx === -1 || awayIdx === -1) {
                console.warn("Required header columns missing. Check layout checklist instructions.");
                return;
            }

            // Loop and bind data configurations dynamically
            for(let i = 1; i < rows.length; i++) {
                if(!rows[i].trim()) continue;
                const columns = rows[i].split(",");
                
                const gameId = parseInt(columns[idIdx], 10);
                const hScoreRaw = columns[homeIdx]?.trim();
                const aScoreRaw = columns[awayIdx]?.trim();

                if(!isNaN(gameId) && hScoreRaw !== "" && aScoreRaw !== "" && hScoreRaw !== undefined && aScoreRaw !== undefined) {
                    scoresState[`${gameId}_home`] = parseInt(hScoreRaw, 10);
                    scoresState[`${gameId}_away`] = parseInt(aScoreRaw, 10);
                }
            }
        }

        function setSyncStatus(status) {
            const dot = document.getElementById("sync-dot");
            const text = document.getElementById("sync-text");
            
            if (status === "success") {
                dot.className = "w-2 h-2 rounded-full bg-green-500";
                text.innerText = "Synced Live with Google Sheets";
            } else if (status === "error") {
                dot.className = "w-2 h-2 rounded-full bg-red-500";
                text.innerText = "Sync Failed (Using offline memory)";
            } else {
                dot.className = "w-2 h-2 rounded-full bg-amber-500";
                text.innerText = "Offline Mode (Demo Mode)";
            }
        }

        function renderSchedule() {
            const container = document.getElementById("schedule-container");
            container.innerHTML = "";

            const groupedByDate = {};
            matches.forEach(match => {
                const query = currentSearchQuery.toLowerCase();
                if (query && !match.home.toLowerCase().includes(query) && !match.away.toLowerCase().includes(query) && !match.diamond.toLowerCase().includes(query) && !match.date.toLowerCase().includes(query)) {
                    return; 
                }

                if (!groupedByDate[match.date]) groupedByDate[match.date] = [];
                groupedByDate[match.date].push(match);
            });

            if (Object.keys(groupedByDate).length === 0) {
                container.innerHTML = `<div class="p-8 text-center text-gray-400 text-sm">No matches match your filter query string.</div>`;
                return;
            }

            for (const date in groupedByDate) {
                const dateHeader = document.createElement("div");
                dateHeader.className = "bg-gray-50 px-6 py-2 text-xs font-bold text-gray-500 uppercase tracking-wider border-y border-gray-100";
                dateHeader.innerText = date;
                container.appendChild(dateHeader);

                groupedByDate[date].forEach(match => {
                    const homeVal = scoresState[`${match.id}_home`] !== undefined ? scoresState[`${match.id}_home`] : "-";
                    const awayVal = scoresState[`${match.id}_away`] !== undefined ? scoresState[`${match.id}_away`] : "-";

                    const row = document.createElement("div");
                    row.className = "p-6 hover:bg-gray-50 transition flex flex-col sm:flex-row sm:items-center justify-between gap-4";
                    row.innerHTML = `
                        <div class="flex-1">
                            <div class="flex items-center gap-2 text-xs text-gray-500 font-medium mb-1">
                                <span>⏰ ${match.time}</span>
                                <span class="text-gray-300">•</span>
                                <span class="px-2 py-0.5 bg-gray-100 border border-gray-200 text-gray-700 rounded font-semibold text-[11px]">${match.diamond}</span>
                                <span class="text-gray-300">•</span>
                                <span class="text-gray-400 text-[10px]">Game ID: #${match.id}</span>
                            </div>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 text-sm font-semibold text-gray-900 mt-2">
                                <div class="flex items-center justify-between p-2.5 bg-gray-50 rounded border border-gray-100">
                                    <span><span class="text-xs font-normal text-gray-400 mr-1.5">[H]</span>${match.home}</span>
                                    <span class="text-base font-black px-2 text-blue-900">${homeVal}</span>
                                </div>
                                <div class="flex items-center justify-between p-2.5 bg-gray-50 rounded border border-gray-100">
                                    <span><span class="text-xs font-normal text-gray-400 mr-1.5">[A]</span>${match.away}</span>
                                    <span class="text-base font-black px-2 text-blue-900">${awayVal}</span>
                                </div>
                            </div>
                        </div>
                    `;
                    container.appendChild(row);
                });
            }
        }

        function calculateAndRenderStandings() {
            const standings = {};
            teamsList.forEach(team => {
                standings[team] = { gp: 0, wins: 0, losses: 0, ties: 0, rf: 0, ra: 0, diff: 0, pts: 0 };
            });

            matches.forEach(match => {
                const homeScore = scoresState[`${match.id}_home`];
                const awayScore = scoresState[`${match.id}_away`];

                if (homeScore !== undefined && awayScore !== undefined) {
                    const h = parseInt(homeScore, 10);
                    const a = parseInt(awayScore, 10);

                    standings[match.home].gp += 1;
                    standings[match.away].gp += 1;
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
                if (teamB.pts !== teamA.pts) return teamB.pts - teamA.pts;
                if (teamB.diff !== teamA.diff) return teamB.diff - teamA.diff;
                return teamB.rf - teamA.rf; 
            });

            const tbody = document.getElementById("standings-rows");
            tbody.innerHTML = "";

            sortedTeams.forEach((team, index) => {
                const row = document.createElement("tr");
                row.className = "hover:bg-gray-50 transition border-b border-gray-100 last:border-0";
                const diffClass = team.diff > 0 ? "text-green-600 font-semibold" : (team.diff < 0 ? "text-red-500" : "text-gray-400");
                const formattedDiff = team.diff > 0 ? `+${team.diff}` : team.diff;

                row.innerHTML = `
                    <td class="py-3 px-3 text-left font-medium text-gray-400">${index + 1}</td>
                    <td class="py-3 px-4 text-left font-bold text-gray-900">${team.name}</td>
                    <td class="py-3 px-2 font-semibold text-gray-700">${team.gp}</td>
                    <td class="py-3 px-2 text-green-600">${team.wins}</td>
                    <td class="py-3 px-2 text-blue-500">${team.ties}</td>
                    <td class="py-3 px-2 text-red-500">${team.losses}</td>
                    <td class="py-3 px-2 text-gray-600">${team.rf}</td>
                    <td class="py-3 px-2 text-gray-600">${team.ra}</td>
                    <td class="py-3 px-2 ${diffClass}">${formattedDiff}</td>
                    <td class="py-3 px-4 font-bold text-blue-900 text-base bg-blue-50/50">${team.pts}</td>
                `;
                tbody.appendChild(row);
            });
        }

        function filterSchedule(val) {
            currentSearchQuery = val;
            renderSchedule();
        }

        // Initialize setup and run polling engine loops every 60 seconds automatically
        window.addEventListener("DOMContentLoaded", () => {
            fetchGoogleSheetsData();
            setInterval(fetchGoogleSheetsData, 60000); 
        });
    </script>
</body>
</html>
