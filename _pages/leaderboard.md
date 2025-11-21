---
layout: splash
permalink: /leaderboard/
title: "Leaderboard"
---
<style>
#leaderboard {
  /* Fix theme's broken table display */
  display: table !important;
  overflow-x: visible !important;
  
  /* Table layout */
  width: 100%;
  table-layout: fixed;
  border-collapse: collapse;
  margin: 0 auto;
}

#leaderboard th,
#leaderboard td {
  padding: 12px 8px;
  text-align: center;
  border: 1px solid #ccc;
}

#leaderboard th {
  background: #ddd;
  font-weight: bold;
}

#leaderboard tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}

#leaderboard tbody tr:hover {
  background-color: #f0f0f0;
}

/* Column widths */
#leaderboard th:nth-child(1),
#leaderboard td:nth-child(1) {
  width: 10%;
}

#leaderboard th:nth-child(2),
#leaderboard td:nth-child(2) {
  width: 40%;
  text-align: left;
}

#leaderboard th:nth-child(3),
#leaderboard td:nth-child(3),
#leaderboard th:nth-child(4),
#leaderboard td:nth-child(4),
#leaderboard th:nth-child(5),
#leaderboard td:nth-child(5) {
  width: 16.67%;
}

#leaderboard_best {
  display: table !important;
  overflow-x: visible !important;

  width: 100%;
  table-layout: fixed;
  border-collapse: collapse;
  margin: 0 auto;
}

#leaderboard_best th,
#leaderboard_best td {
  padding: 12px 8px;
  text-align: center;
  border: 1px solid #ccc;
}

#leaderboard_best th {
  background: #ddd;
  font-weight: bold;
}

#leaderboard_best tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}

#leaderboard_best tbody tr:hover {
  background-color: #f0f0f0;
}

/* Column widths for best leaderboard */
#leaderboard_best th:nth-child(1),
#leaderboard_best td:nth-child(1) {
  width: 10%;
}

#leaderboard_best th:nth-child(2),
#leaderboard_best td:nth-child(2) {
  width: 40%;
  text-align: left;
}

#leaderboard_best th:nth-child(3),
#leaderboard_best td:nth-child(3),
#leaderboard_best th:nth-child(4),
#leaderboard_best td:nth-child(4),
#leaderboard_best th:nth-child(5),
#leaderboard_best td:nth-child(5) {
  width: 16.67%;
}

</style>



<h2 style="text-align: center;">🏆 Track 1 Team Leaderboard</h2>

<table id="leaderboard_best">
  <thead>
    <tr>
      <th>Rank</th>
      <th>Team Name</th>
      <th>ASR</th>
      <th>MSR</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<hr style="margin: 3em 0;">

<script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js"></script>

<script>
fetch('/assets/data/leaderboard_best.csv')
  .then(r => r.text())
  .then(csv => {
    const rows = Papa.parse(csv, { header: false }).data
      .filter(r => r.length>1 && r[0] !== 'submission' && r[r.length-1] !== 'score')
      .sort((a,b) => parseFloat(b[b.length-1]) - parseFloat(a[a.length-1]));
      const tbody = document.querySelector('#leaderboard_best tbody');
      tbody.innerHTML = '';
      rows.forEach((r,i) => {
        const [name, asrVal, msrVal] = r;
        const score = parseFloat(r[r.length-1]).toFixed(4);
        tbody.innerHTML += `
          <tr>
            <td>${i+1}</td>
            <td>${name}</td>
            <td>${parseFloat(asrVal).toFixed(4)}</td>
            <td>${parseFloat(msrVal).toFixed(4)}</td>
            <td><strong>${score}</strong></td>
          </tr>`;
      });
    });
</script>


<h2 style="text-align: center;">Track 1 Leaderboard</h2>

<table id="leaderboard">
  <thead>
    <tr>
      <th>Rank</th>
      <th>Submission Name</th>
      <th>ASR</th>
      <th>MSR</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<div style="margin: 1.5em 0; text-align: left;">
  <strong>Legend:</strong>
  <ul>
    <li><strong>ASR</strong>: average success rate across all submissions</li>
    <li><strong>MSR</strong>: minimum success rate across all conditions</li>
    <li><strong>Score</strong> = (ASR + MSR) / 2</li>
  </ul>
  <p style="text-align: center; font-style: italic;">
    Note: Track 2 leaderboard will be added soon.
  </p>
</div>


<script>
fetch('/assets/data/leaderboard_merged.csv')
  .then(r => r.text())
  .then(csv => {
    const rows = Papa.parse(csv, { header: false }).data
      .filter(r => r.length>1 && r[0] !== 'submission' && r[r.length-1] !== 'score')
      .sort((a,b) => parseFloat(b[b.length-1]) - parseFloat(a[a.length-1]));
    const tbody = document.querySelector('#leaderboard tbody');
    tbody.innerHTML = '';
    rows.forEach((r,i) => {
      const [name, asrVal, msrVal] = r;
      const score = parseFloat(r[r.length-1]).toFixed(4);
      tbody.innerHTML += `
        <tr>
          <td>${i+1}</td>
          <td>${name}</td>
          <td>${parseFloat(asrVal).toFixed(4)}</td>
          <td>${parseFloat(msrVal).toFixed(4)}</td>
          <td><strong>${score}</strong></td>
        </tr>`;
    });
  });
</script>
