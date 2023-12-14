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
<p><strong>● firstdragon -</strong>
  Indicates whether the team got the first dragon (Nominal).
</p>
<p><strong>● killsat15 -</strong>
  The number of kills at 15 minutes (Quantitative).
</p>
<p><strong>● firstherald -</strong>
  Indicates whether the team got the first herald (Nominal).
</p>
<p>
 These features combine both nominal and quantitative data types.
</p>
<h2><strong>Feature Processing</strong></h2>
<p><strong>● Standardization: </strong>
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
<p>We found that the model's metrics are relatively consistent between the training and testing sets, suggesting that it has not overfitted to the training data. However, the values of the metrics indicate there is room for improvement.</p>
<p>
  The model achieved an F1 score of 0.5924. The F1 score is a balanced measure of a model's precision and recall, especially important in the context of your dataset's imbalance. An F1 score close to 0.6 suggests that our model has a moderate performance in balancing precision and recall.
</p>

<h1><strong> Final Model </strong></h1>
<h2><strong> Added Features and Their Rationale</strong></h2>
<p>In enhancing our baseline model for predicting the first baron kill in League of Legends matches, we integrated a mix of quantitative and nominal features into the final model. These include 'golddiffat15', 'heralds', 'xpdiffat15', 'csdiffat15', and 'side'. The rationale behind incorporating these features stems from their intrinsic relevance to the game's dynamics and their potential impact on a team's ability to secure the first baron.
</p>
<p><strong>● golddiffat15: </strong>
  The difference in gold between teams at 15 minutes. This is a crucial metric as gold difference can indicate a team's overall advantage in terms of items and power, directly impacting their ability to secure objectives like the baron.
</p>
<iframe src="assets/golddiffat15.html" width=500 height=300 frameBorder=0></iframe>

<p><strong>● heralds: </strong>
The number of heralds a team has slain. Securing heralds is often correlated with map control and the ability to secure further objectives, including the baron.
</p>
<iframe src="assets/heralds.html" width=500 height=300 frameBorder=0></iframe>
<p><strong>● xpdiffat15: </strong>
The experience difference between teams at 15 minutes. Similar to gold difference, experience difference can suggest a team's level advantage, which is significant in team fights for objectives.
</p>
<iframe src="assets/xpdiffat15.html" width=500 height=300 frameBorder=0></iframe>

<p><strong>● csdiffat15: </strong>
   The creep score difference at 15 minutes. Creep score reflects a team's farming efficiency, which is another aspect of resource advantage.

</p>
<iframe src="assets/csdiffat15.html" width=500 height=300 frameBorder=0></iframe>

<p><strong>● side: </strong>
  Which side of the map the team is on. Map side can subtly influence a team's strategy and ease of access to baron.
</p>
<p>Other than the features we newly added to the final model, we decided to keep the features in our baseline model because they are all related to the team’s performance in the first twenty minutes.
</p>
<p><strong>● firstdragon: </strong>
   This feature indicates whether the team secured the first dragon of the game. The significance of the first dragon kill is twofold. Firstly, it provides a direct combat or utility advantage based on the type of dragon slain. Secondly, it suggests early game control, which can correlate with a team's ability to secure other objectives like the baron. This is a strategic indicator reflecting early game dominance.
</p>
<p><strong>● killsat15: </strong>
   The number of kills at 15 minutes is a direct measure of a team's aggression and success in early game skirmishes. A higher kill count can indicate a team's strength and control, which can translate into a higher likelihood of securing major objectives. Kills also lead to gold and experience advantages, further influencing a team's capacity to contest and secure the baron.
</p>
<iframe src="assets/killsat15.html" width=500 height=300 frameBorder=0></iframe>
<p><strong>● firstherald: </strong>
   Similar to the first dragon, securing the first herald is indicative of early game map control. The Rift Herald, specifically, provides a strategic advantage in terms of pushing lanes and creating pressure, which could translate into better positioning and control around the baron pit. It's also a sign of a team's prioritization of early objectives, which can be a precursor to their approach towards the baron.

</p>
<p>
  These features are directly related to a team's performance and resource control in the game, making them highly relevant for predicting the likelihood of securing the first baron.
</p>
<h2><strong>Modeling Algorithm, Hyperparameters, and Selection Method</strong></h2>
<p>
  We continued using the logistic regression classifier, which is the most suitable algorithm for the binary classification tasks.For hyperparameters, we
</p>

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
<p>The confusion_matrix of the Final model is shown below:</p>
<iframe src="assets/confusion_matrix.html" width=800 height=800 frameBorder=0></iframe>

<h1><strong> Fairness Analysis </strong></h1>
<h2><strong>Choice of Groups</strong></h2>
<p><strong>● Group X: </strong>
   Matches played by the teams from the LCK League.
</p>
<p><strong>● Group Y: </strong>
   Matches played by the teams from the LCS League.
</p>
<p>These groups are chosen based on the different leagues in the dataset to compare the model's performance across these distinct subsets.
</p>
<h2><strong>Null and Alternative Hypotheses</strong></h2>
<p>
  <strong>● Null Hypothesis (H0):</strong>
   The classifier’s F1 score is the same for both LCK league and LCS league matches. Any observed differences in the F1 scores are due to random variation.
</p>
<p>
  <strong>● Alternative Hypothesis (H1):</strong>
   There is a significant difference in the classifier’s F1 score between LCK league and LCS league matches.
</p>
<h2><strong>Choice of Test Statistic</strong></h2>
<p>
  <strong>● Test Statistic:</strong>
   Difference in F1 scores between the two groups.
The test statistic is the absolute difference in F1 scores between Group X (LCK) and Group Y (LCS), as it directly measures the disparity in model performance across the groups.

</p>
<p>
  <strong>Observed difference in f1 score:-0.11534642780056137</strong>
</p>
<h2><strong>Significant Level</strong></h2>
<p>
  The significance level (α) is 0.05, implying a 5% risk of concluding that a difference exists when there is none. 
</p>
<h2><strong>Resulting P-Value</strong></h2>
<p>
  <strong>● p_value: Approximately 0.079</strong>
</p>
<p>This p-value indicates the probability of observing a difference as large as the one in your sample data if the null hypothesis is true.
</p>

<iframe src="assets/permutation_test_distribution.html" width=800 height=500 frameBorder=0></iframe>
<h2><strong>Conclusion</strong></h2>
<p>
 Given the p-value of 0.079, which is much higher than the typical significance level (e.g., 0.05), we fail to reject the null hypothesis. Hence, this result suggests that there is no statistically significant difference in the performance of the model (in terms of F1 score) between matches from the LCK league and the LCS league. Therefore, based on this analysis, we conclude that any observed differences in F1 scores are likely due to chance, implying that the model performs fairly and consistently across these two groups.
</p>

</body>
</html>
