# LOL_Model_Building
<html>
<body>
<p>
  <strong>Name(s):</strong>
  Leni Dai, Hongyu Yu
</p>
<h2>Introduction:</h2>
<p> 
  Our data encompasses every professional League of Legends match held in 2023, detailed in 12 rows per game—each player is represented by one row, 
  with an additional two rows summarizing team statistics. The dataset is extensive, with over 100 columns encapsulating a wide array of 
  information pertaining to match specifics. We seek to explore if the initial side selection—blue or red—affects the game's outcome. 
  Teams alternate sides across matches within a game. Due to the “team wins three matches first wins the game” format, 
  the team starting on the blue side might play an extra match from that position if eventually the number of matches is odd. 
  Many players harbor the belief that commencing on the blue side increases their chances of victory. 
  Our research aims to determine if there is a statistical difference in victory rates between the sides.
  In order to answer the question of “whether the assignment of side (blue or red) influences the result of the game?”, 
  we are interested in only a few columns in the dataset. Since some data are inclusively collected for the row that summarizes team statistics, 
  we want to include the column “position” to only get rows that store team statistics. Our analyzing objectives, side and match result, 
  which are stored in columns “side” and “result” are definitely included in our dataframe. The ‘side’ column is binary: ‘red’ for red side, 
  ‘blue’ for blue side. The 'result' column in the dataset is also binary: a '1' denotes a victory, while a '0' indicates a defeat. 
</p>
<p>
   In our investigation, we primarily scrutinize the interplay between two binary variables to discern the impact on match outcomes. 
   However, supplementary variables are occasionally utilized for deeper analysis. For instance, in our univariate analysis, 
  we examine the "teamname" column, which records the competing teams, to assess whether teams with a history of multiple 
  world championship wins are more frequently assigned to the blue side. Additionally, we explore strategic advantages by 
  aggregating binary variables such as "firstbaron" and "firstherald," analyzing whether securing these objectives correlates 
  with a higher win probability. Regarding data completeness, we evaluate the "barons," "dragons," and "firstdragon" columns 
  to categorize the patterns of missing data and understand their implications on our research.
</p>
<p>
  Here is a list of the relevant columns in our research, and their corresponding descriptions. 
</p>
<p>
  <strong>●teamname:</strong>
  the name of team playing
</p>
<p>
  <strong>●side:</strong>
  red or blue side
</p>
<p>
  <strong>●result:</strong>
  '1' for a victory, '0' for a defeat
</p>
<p>
  <strong>●position:</strong>
  the player’s position or team
</p>
<p>
  <strong>●firstdragon:</strong>
  '1' for killing the first dragon, '0' for not
</p>
<p>
  <strong>●firstherald:</strong>
  '1' for killing the first herald, '0' for not
</p>
  
<p> 
  <strong>●barons:</strong>
  number of barons killed in the match 
</p>
<p>
  <strong>
    ●dragons:
  </strong>
  number of dragons killed in the match 
</p>

<h2> Cleaning and EDA (Exploratory Data Analysis):</h2>
<h3> Data Cleaning</h3>
<p>
  For the data cleaning process, we initially focused on streamlining our dataset by retaining only essential columns: 'teamname', 'side', 'result', 
  'firstdragon', 'firstherald', 'barons', and 'dragons'. Correspondingly, we filtered the dataset to include only pertinent rows, specifically those 
  where the 'position' column is labeled as 'team', indicating team statistics. Once these rows were isolated, we droped the 'position' column from our dataset.
</p>
<p>
  <strong>
     Here is the head of our Cleaned DataFrame:
  </strong>
</p>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th style="text-align: left">side</th>
      <th style="text-align: left">result</th>
      <th style="text-align: left">teamname</th>
      <th style="text-align: left">barons</th>
      <th style="text-align: left">dragons</th>
      <th style="text-align: left">firstdragon</th>
      <th style="text-align: left">firstherald</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Blue</td>
      <td>1</td>
      <td>Klanik Esport</td>
      <td>1.0</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <td>Red</td>
      <td>0</td>
      <td>MS Company</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>Blue</td>
      <td>0</td>
      <td>beGenius ESC</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <td>Red</td>
      <td>1</td>
      <td>ViV Esport</td>
      <td>1.0</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>Blue</td>
      <td>1</td>
      <td>Team du Sud</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>
<strong> Here is the head of our side DataFrame: </strong>   
</p>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th style="text-align: left">side</th>
      <th style="text-align: left">result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Blue</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Red</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Blue</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Red</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Blue</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>
<strong> Below is the table of result distribution: </strong>   
</p>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th style="text-align: left">result_side</th>
      <th style="text-align: left">Loss</th>
      <th style="text-align: left">Win</th>
      <th style="text-align: left">Total</th>
      <th style="text-align: left">Loss_prop</th>
      <th style="text-align: left">Win_prop</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Blue</th>
      <td>5026</td>
      <td>5772</td>
      <td>10798</td>
      <td>0.465457</td>
      <td>0.534543</td>
    </tr>
    <tr>
      <th>Red</th>
      <td>5772</td>
      <td>5026</td>
      <td>10798</td>
      <td>0.534543</td>
      <td>0.465457</td>
    </tr>
  </tbody>
</table>
<h3>Univariate Analysis: </h3>
<iframe src="assets/pie.html" width=800 height=600 frameBorder=0></iframe>
<p>
  This is a pie chart that shows the percentage of wins and losses for matches played on Blue Side.
  We can notice matches played on the blue side have a higher percentage of victory. 
</p>
<iframe src="assets/pie2.html" width=800 height=600 frameBorder=0></iframe>
<p>
  From the last chart we can tell that the blue side does provide a higher percentage of victory from the data. 
  Now, we want to see whether teams that won more were assigned to the blue side more. Since there are about 500 teams, 
  we would only look at one team that won the world championship most of the time, which is T1. 
  Here is a pie chart that shows the percentage of red and blue sides T1 played in all 2023 matches. 
  We can notice that T1 has been assigned to the blue side more than the red side. 
</p>
<h3>Bivariate Analysis:</h3>
<iframe src="assets/Bivariate3.html" width=800 height=600 frameBorder=0></iframe>
<p>
  This is a normalized stacked bar chart that shows the percentage of victory and defeat by the sides.
  The Blue side has a higher chance of winning than the red side.
</p>
<h3>Interesting Aggregates:</h3>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th style="text-align: left">result</th>
      <th style="text-align: left">firstdragon</th>
      <th style="text-align: left">firstherald</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Loss</th>
      <td>0.379878</td>
      <td>0.416830</td>
    </tr>
    <tr>
      <th>Win</th>
      <td>0.619904</td>
      <td>0.582952</td>
    </tr>
  </tbody>
</table>
<p>
  Our research objectives are two binary data, so our exploration into interesting aggregates is limited. 
  Therefore, we want to explore a topic that many followers are interested in. Does killing the first dragon 
  or killing the first herald provide a higher chance of victory? It is a strategic decision because the first dragon 
  and the first herald appear at the same time, so in most cases the one playing with the jungle position has to decide which one to kill. 
  You can see the distribution between winning or losing with killing the first dragon and killing the first herald. Interestingly, 
  it tells us killing the first dragon has a 61.9904% chance of winning, while killing the first herald only provides a 58.2952% chance of winning. 
  However, killing either of them has a higher chance of winning than not killing them. So, an interesting piece of advice from aggregating the dataset is that,
  killing the first dragon and first herald increases the probability of victory; if the situation only allows one to kill one of them, choose the first dragon.
</p>
<h2>Assessment of Missingness: </h2>
<h3>NMAR Analysis: </h3>
<p>
  One of the columns in our dataset that has missing values and may be NMAR is the 'ban4' column. In LOL matches, each team can ban up to five heroes, 
  but the game does not stipulate that teams must ban five heroes during the match, so there may be some teams that do not use all available bans. 
  And a team's decision not to ban a character is a deliberate choice influenced by the team's own strategy or the game environment, 
  so missingness is directly related to their choice not to ban a character. So the missingness of the 'ban4' column does not depend on other columns in the data set. 
  The missingness of the 'ban4' column is related to actual missing value itself, so 'ban4' missingness should be NMAR.
</p>
<p>
 If we could generate another column indicating the list of hero names that each team is best at, then the missing value of the 'ban4' column might be 'MAR'. Because in the game, each 
 team first bans three heroes, and then each team selects three heroes. If a team has a relatively small list of hero names, this will lead to the team's pool of heroes being emptied out 
 when three heroes are banned and three heroes are selected in the first round. Then this situation will lead to each team not knowing what to ban when banning the fourth one, and then 
 they will give up banning the hero according to their strategy. Then this situation will cause the 'ban4' column to have missing values. So it can be seen that the missingness of the 
 ‘ban4’ columns are related to the observed data of generated column in the data set. Hence, the missing value in the ‘ban4’ column should be MAR.
  
</p>
<h3>Missingness Dependency: </h3>
<p>
  Here we want to check whether the Missingness of the 'firstdragon' column depends on the 'dragons' column.
  We first obtain the distribution observed when "firstdragon" is not lost and the distribution observed 
  when "firstdragon" is lost, and then do the permutation test.
</p>
<p> Below is the observed distribution when "firstdragon" was not missing:</p>

<table border="1" class="dataframe">
  <thead>
    <tr>
      <th style="text-align: left">dragons</th>
      <th style="text-align: left">Not Missing firstdragon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3.0</th>
      <td>0.229671</td>
    </tr>
    <tr>
      <th>2.0</th>
      <td>0.224166</td>
    </tr>
    <tr>
      <th>1.0</th>
      <td>0.190702</td>
    </tr>
    <tr>
      <th>4.0</th>
      <td>0.174951</td>
    </tr>
    <tr>
      <th>0.0</th>
      <td>0.151679</td>
    </tr>
    <tr>
      <th>5.0</th>
      <td>0.027523</td>
    </tr>
    <tr>
      <th>6.0</th>
      <td>0.001308</td>
    </tr>
  </tbody>
</table>

<p> Below is the observed distribution when "firstdragon" was missing:</p>

<table border="1" class="dataframe">
  <thead>
    <tr>
      <th style="text-align: left">dragons</th>
      <th style="text-align: left"> Missing firstdragon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3.0</th>
      <td>0.304841</td>
    </tr>
    <tr>
      <th>4.0</th>
      <td>0.281182</td>
    </tr>
    <tr>
      <th>2.0</th>
      <td>0.227867</td>
    </tr>
    <tr>
      <th>1.0</th>
      <td>0.136284</td>
    </tr>
    <tr>
      <th>5.0</th>
      <td>0.047645</td>
    </tr>
    <tr>
      <th>6.0</th>
      <td>0.002181</td>
    </tr>
  </tbody>
</table>
<p>
  After looking at the distribution observed when "firstdragon" is not lost and 
  the distribution observed when "firstdragon" is lost, we start to do the permutation test. 
  The first thing is to set up our hypothesis.
</p>
<p>
  <strong>Null Hypothesis (H0):</strong>
   The Missingness of the 'firstdragon' column does not depend on the 'dragons' column.
</p>
<p>
  <strong>Alternative Hypothesis (H1):</strong>
  The Missingness of the 'firstdragon' column depends on the 'dragons' column.
</p>
<iframe src="assets/dragons1.html" width=800 height=600 frameBorder=0></iframe>
<p> <strong>observed_tvd:</strong> 0.021956259443855583 </p>
<p> <strong>p_value:</strong> 0.028</p>
<p> <strong>Significant Level:</strong> 0.05</p>
<p>In the permutation test, we set up n_repetitions = 500 which means it will perform
   permutation test 500 times. After permutation test, we get the p_value was 0.028 
   which is smaller than the significant level. So we reject the Null Hypothesis (H0). 
</p>
<p>
  <strong>Conclusion:</strong>
</p>
<p>
  p-value=0.028 which indicate a statistically significant association between the 'dragons' column 
  and the missingness of the 'firstdragon' column. Hence, we reject the null hypothesis(H0) that the Missingness 
  of the 'firstdragon' column does not depend on the 'dragons' column. This results supports the alternative hypothesis 
  that the missingness of 'firstdragon' depends on the 'dragons' column.
</p>

<p>
  Here we want to check whether the Missingness of the 'firstdragon' column depends on the 'barons' column.
  We first obtain the distribution observed when "firstdragon" is not lost and the distribution observed 
  when "firstdragon" is lost, and then do the permutation test.
</p>

<p> Below is the observed distribution when "firstdragon" was not missing:</p>

<table border="1" class="dataframe">
  <thead>
    <th style="text-align: left">barons</th>
    <th style="text-align: left">Not Missing firstdragon</th>
  </thead>
  <tbody>
    <tr>
      <th>0.0</th>
      <td>0.438794</td>
    </tr>
    <tr>
      <th>1.0</th>
      <td>0.396283</td>
    </tr>
    <tr>
      <th>2.0</th>
      <td>0.148245</td>
    </tr>
    <tr>
      <th>3.0</th>
      <td>0.015261</td>
    </tr>
    <tr>
      <th>4.0</th>
      <td>0.001417</td>
    </tr>
  </tbody>
</table>



<p> Below is the observed distribution when "firstdragon" was missing:</p>

<table border="1" class="dataframe">
  <thead>
    <th style="text-align: left">barons</th>
    <th style="text-align: left">Missing firstdragon</th>
  </thead>
  <tbody>
    <tr>
      <th>0.0</th>
      <td>0.442734</td>
    </tr>
    <tr>
      <th>1.0</th>
      <td>0.413177</td>
    </tr>
    <tr>
      <th>2.0</th>
      <td>0.128387</td>
    </tr>
    <tr>
      <th>3.0</th>
      <td>0.015394</td>
    </tr>
    <tr>
      <th>4.0</th>
      <td>0.000308</td>
    </tr>
  </tbody>
</table>
<p>
  After looking at the distribution observed when "firstdragon" is not lost and 
  the distribution observed when "firstdragon" is lost, we start to do the permutation test. 
  The first thing is to set up our hypothesis.
</p>
<p>
  <strong>Null Hypothesis (H0):</strong>
   The Missingness of the 'firstdragon' column does not depend on the 'barons' column.
</p>
<p>
  <strong>Alternative Hypothesis (H1):</strong>
  The Missingness of the 'firstdragon' column depends on the 'barons' column.
</p>
<iframe src="assets/barons1.html" width=800 height=600 frameBorder=0></iframe>
<p> <strong>observed_tvd:</strong> 0.0209675072302212</p>
<p> <strong>p_value:</strong> 0.082</p>
<p> <strong>Significant Level:</strong> 0.05</p>
<p>
  In the permutation test, we set up n_repetitions = 500 which means it will perform
  permutation test 500 times. After permutation test, we get the p_value was 0.082 
  which is greater than the significant level. So we Fail to reject the Null Hypothesis (H0). 
</p>
<p>
  <strong>Conclusion:</strong>
</p>
<p>
  p-value=0.082 which does not indicate a statistically significant association between the 'barons' column 
  and the missingness of the 'firstdragon' column. Hence, we maintain the Null hypothesis(H0) that the missingness of 'firstdragon' 
  does not depend the 'barons' column.
</p>
<h2> Hypothesis Testing: </h2>
<p>
  <strong>Null Hypothesis (H0):</strong>
  The win rate of the red side is equal to the win rate of the blue side.
</p>
<p>
  <strong>Alternative Hypothesis (H1):</strong>
  The win rate of the red side is different from the win rate of the blue side.
</p>
<p>
  <strong>t_statistic:10.176559519346588</strong>
</p>
<p>
   We use the difference between the two sample means divided by the standard 
   error of the difference between those means to calculate the t_statistic.
</p>
<p>
  <strong>Significant Level: 0.05</strong>
</p>
<p>
  <strong>p_value:2.86252172582626e-24</strong>
</p>
<p>
  <strong>Result:Reject the Null Hypothesis(H0).</strong>
</p>
<p>
  <strong>Conclusion:</strong>
</p>
<p>
  In our statistical hypothesis testing, the p-value obtained was approximately 2.86252172582626e-24, which rounds off to 0.00 
  when truncated to two decimal places. This value is markedly lower than the conventional significance threshold of 0.05, 
  leading us to reject the null hypothesis—that there is no difference in win rates between the red and blue sides. 
  Thus, our analysis concludes that there is a statistically significant disparity in the win probabilities of the two sides. 
  This discrepancy could potentially be attributed to the initial ban/pick phase, where the blue side has the first move advantage, 
  as well as a more advantageous position for killing objectives like the herald and barons. Nonetheless, it is important to recognize 
  that this result does not imply that being on the blue side guarantees a victory; the game's design has been balanced to mitigate side advantages, 
  and the outcome is contingent upon a multitude of factors beyond the starting side.
</p>




  
</body>
</html>
