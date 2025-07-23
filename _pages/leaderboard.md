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

<div style="max-width: 900px; margin: 0 auto;">

  <h2 style="text-align: center;">Track 1 Leaderboard</h2>

  <table id="leaderboard" style="width: 100%; margin: 0 auto; border-collapse: collapse;">
    <thead>
      <tr style="background: #ddd;">
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

</div>

<script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js"></script>
<script>
fetch('/assets/data/leaderboard.csv')
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
