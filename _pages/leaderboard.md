---
layout: splash
permalink: /leaderboard/
title: "Leaderboard"
---
<center>
<img
  src="/assets/images/mouse-fighting_banner2.png"
  alt="Robust Visual Foraging Challenge Banner"
  width="640"
  height="320"
/>
</center>

<pre>

</pre>

<center>
  <h2>Track 1 Leaderboard</h2>
  <table id="leaderboard" style="width:90%;">
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

**Legend**  
- **ASR**: average success rate across all submissions  
- **MSR**: minimum success rate across all conditions  
- **Score** = (ASR + MSR) / 2

  
</center> 



<script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js"></script>
<script>
fetch('/assets/data/leaderboard.csv')
  .then(response => response.text())
  .then(csv => {
    const parsed = Papa.parse(csv, { header: false }).data;

    // Remove the header row
    const data = parsed.filter(row => row.length > 1 && row[0] !== 'submission' && row[row.length - 1] !== 'score');

    // Sort descending by score (last column)
    data.sort((a, b) => parseFloat(b[b.length - 1]) - parseFloat(a[a.length - 1]));

    const tableBody = document.querySelector('#leaderboard tbody');
    tableBody.innerHTML = ''; // Clear existing

    data.forEach((row, index) => {
      const name = row[0];
      const overall = parseFloat(row[1]).toFixed(4);
      const minRate = parseFloat(row[2]).toFixed(4);
      const score = parseFloat(row[row.length - 1]).toFixed(4);
      const rank = index + 1;

      tableBody.innerHTML += `
        <tr>
          <td>${rank}</td>
          <td>${name}</td>
          <td>${overall}</td>
          <td>${minRate}</td>
          <td><strong>${score}</strong></td>
        </tr>`;
    });
  });
</script>
