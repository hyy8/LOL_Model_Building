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
<p>
  In our Baseline model, we intend to predict whether the team will secure the first baron based on whether the team has secured the binary features such as first dragon and first herald, and the quantitative feature like the number of kills of the team at the first 15 minutes. We use a logistic regression classifier, which is a suitable choice for binary classification problems.

</p>
<h2><strong> Features in the Model</strong></h2>
<p>
The baseline model uses three features:
</p>
<p><strong>●firstdragon -</strong>
  Indicates whether the team got the first dragon (Nominal).
</p>
<p><strong>●killsat15 -</strong>
  The number of kills at 15 minutes (Quantitative).
</p>
<p><strong>●firstherald -</strong>
  Indicates whether the team got the first herald (Nominal).
</p>
<p>
 These features combine both nominal and quantitative data types.
</p>
<h2><strong>Feature Processing</strong></h2>
<p><strong>●Standardization: </strong>
  The killsat15 feature is standardized using StandardScaler. This process normalizes the feature, ensuring that it has a mean of 0 and a standard deviation of 1, which is essential for logistic regression to perform well.

</p><strong>●One-Hot Encoding:  </strong>
The nominal features (firstdragon and firstherald) are one-hot encoded using OneHotEncoder. This encoding is crucial for handling nominal data in logistic regression, as it converts categorical variables into a form that could be provided to ML algorithms to do a better job in prediction.

<p>
  
</p>
<h2><strong> Performance</strong></h2>
<p>The metrics below presented in the table provide a quantitative assessment of the Baseline model's performance on both the training and testing datasets.</p>
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
<p>
  The model achieved an F1 score of 0.5924. The F1 score is a balanced measure of a model's precision and recall, especially important in the context of your dataset's imbalance. An F1 score close to 0.6 suggests that our model has a moderate performance in balancing precision and recall.
</p>

<h1><strong> Final Model </strong></h1>
<h2><strong> Data Visualization</strong></h2>
<p>Below is a graph showing the relationship between  ‘killsat15’ and 'firstbaron.</p>
<iframe src="assets/killsat15.html" width=500 height=300 frameBorder=0></iframe>

<p>Below is a graph showing the relationship between  ‘golddiffat15’ and 'firstbaron.</p>
<iframe src="assets/golddiffat15.html" width=500 height=300 frameBorder=0></iframe>

<p>Below is a graph showing the relationship between  ‘xpdiffat15’ and 'firstbaron.</p>
<iframe src="assets/xpdiffat15.html" width=500 height=300 frameBorder=0></iframe>

<p>Below is a graph showing the relationship between  ‘csdiffat15’ and 'firstbaron.</p>
<iframe src="assets/csdiffat15.html" width=500 height=300 frameBorder=0></iframe>

<p>Below is a graph showing the relationship between  ‘heralds’ and 'firstbaron.</p>
<iframe src="assets/heralds.html" width=500 height=300 frameBorder=0></iframe>

<p>The metrics below presented in the table provide a quantitative assessment of the Final model's performance on both the training and testing datasets.</p>
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
