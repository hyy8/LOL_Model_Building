# LOL_Model_Building
<html>
<body>
<p>
  <strong>Name(s):</strong>
  Leni Dai, Hongyu Yu
</p>
<h1><strong> Framing the Problem </strong></h1>
<p>
In League of Legends, achieving certain milestones can significantly sway the momentum towards a 'temporary victory.' One of these pivotal moments is securing the first baron, which spawns twenty minutes into the game. The team that vanquishes the first baron gains substantial advantages, including a 300 gold and 900 experience boost per player, equating to the benefits of a solo kill for each team member. Given the strategic importance of this objective, predicting which team will secure the first baron using match data from the initial twenty minutes offers valuable insights into the early game dynamics.
</p>
<p>
For our predictive model, we utilized data from professional league matches in 2023, focusing on the binary outcome of whether a team secures the first baron. We observed that some matches conclude before the baron's appearance, leading us to exclude any game ending in less than 20 minutes as they do not align with our research objective. Although this ensures the presence of the baron in each analyzed match, we still face an imbalanced dataset as some matches conclude without either team defeating the baron. Given the equal significance of false positives (incorrectly predicting a team will secure the first baron) and false negatives (failing to predict a team's success in this endeavor), we identified the F1 score as the most suitable metric. It strikes a balance between precision and recall, offering a comprehensive evaluation of our model's performance amidst the dataset's imbalance.
</p>
<p>
To ensure the rationality of our predictions, we exclusively utilize features derived from the first twenty minutes of gameplay. This approach excludes data elements not guaranteed within this timeframe, such as firstTower and firstKill. Our focus remains on discerning which team is more likely to claim the first baron, based on differential variables like experience, gold, and creep score (cs), gathered during the early stages of the match.
</p>

<h1><strong> Baseline Model </strong></h1>
<h2><strong> Model Description</strong></h2>
<h2><strong> Features</strong></h2>
<h2><strong> Performance</strong></h2>

<table border="1" class="dataframe">
  <thead>
    <tr>
      <th style="text-align: left">Metrics</th>
      <th style="text-align: left">Training Set</th>
      <th style="text-align: left">Testing Set</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Accuracy</th>
      <td>0.631882</td>
      <td>0.622429</td>
    </tr>
    <tr>
      <th>Precision</th>
      <td>0.640237</td>
      <td>0.623310</td>
    </tr>
    <tr>
      <th>Recall</th>
      <td>0.561376</td>
      <td>0.550000</td>
    </tr>
    <tr>
      <th>F1 Score</th>
      <td>0.598219</td>
      <td>0.584365</td>
    </tr>
  </tbody>
</table>

<h1><strong> Final Model </strong></h1>
<h2><strong> Data Visualization</strong></h2>
<p>Below are visual representations of ‘killsat15’, ‘golddiffat15’, ‘xpdiffat15’, ‘csdiffat15’, ‘heralds.html’:</p>
<iframe src="killsat15.html" width=500 height=300 frameBorder=0></iframe>

<iframe src="golddiffat15.html" width=500 height=300 frameBorder=0></iframe>

<iframe src="xpdiffat15.html" width=500 height=300 frameBorder=0></iframe>

<iframe src="csdiffat15.html" width=500 height=300 frameBorder=0></iframe>

<iframe src="heralds.html" width=500 height=300 frameBorder=0></iframe>

<table border="1" class="dataframe">
  <thead>
    <tr>
      <th style="text-align: left">Metrics</th>
      <th style="text-align: left">Training Set</th>
      <th style="text-align: left">Testing Set</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Accuracy</th>
      <td>0.712993</td>
      <td>0.708253</td>
    </tr>
    <tr>
      <th>Precision</th>
      <td>0.709751</td>
      <td>0.698404</td>
    </tr>
    <tr>
      <th>Recall</th>
      <td>0.697191</td>
      <td>0.696023</td>
    </tr>
    <tr>
      <th>F1 Score</th>
      <td>0.703415</td>
      <td>0.697211</td>
    </tr>
  </tbody>
</table>
<iframe src="assets/confusion_matrix.html" width=800 height=800 frameBorder=0></iframe>

<h1><strong> Fairness Analysis </strong></h1>




  
</body>
</html>
