# Player-score
## 1. Topic and research question
This dataset provides detailed information about football players, including their physical
attributes, personal information, skills, wages, clubs, and the date they joined their clubs. Using
this data, it is possible to determine the market value, potential, and performance of each athlete.
This information influences decisions regarding the renewal, signing, or cancellation of contracts
with organizations or football clubs that may work with the athletes.
Research questions:
● How does a player's popularity impact their market value and release clause?
● Which stats (Attacking Skills and Goalkeeping Skills) have the biggest effects on a
player's market value and pay, and how do these effects differ depending on the player's
position?
● What effects does age have on a player's performance (rating, skill attributes)?
This information will help football clubs identify players who fit their tactics and strategy. For
coaches, it assists in improving team playmaking and formation. Players can identify their
weaknesses and work on improving their skills, which in turn helps increase their market value.

## 2. Data description
The data selected is from the publicly available dataset titled "Player Score Regression." It was
downloaded from the Sofifa website, located at the URL: https://sofifa.com/players . The dataset
includes attributes for 18,979 football players. The provided dataset indicates that each player
has about 77 attributes. These attributes include financial information (wage, market value, etc.),
skill evaluations (dribbling, passing), physical characteristics (height, weight), and personal details
(full name, date of birth), amounting to a total of 1,461,383 data points.

## 3. Data ingestion and cleaning
### Data ingestion:
For this project, I primarily used the Pandas(3.0.1) library. Functions such as drop(), info(), describe(),
isnull() and to_numeric() were utilized to clean and analyze the data. The drop() function helped
remove irrelevant columns and rows with invalid values, while info() and describe() provided an
overview of the dataset's structure, mean , min and max values. The isnull() function was crucial
in identifying missing data, and to_numeric() ensured that values were correctly converted to
numerical types where needed.
### Data cleaning:
Before cleaning the dataset, I began by analyzing the entire dataset. I examined the data using
the describe() and info() functions to get an overview. The describe() function provided a summary 
of the statistical properties of the numerical columns, such as the mean, standard
deviation, min and max values . On the other hand, the info() function helped to identify the data
types and missing values of each column. I found that some of the columns had missing values
after carefully going over each column, which might have an effect on the analysis. I also saw that
some of the columns had the wrong data types.
After examination, I found that the 'Rating in Scale 100' and 'Potential in Scale 100' columns
contained outliers, as some values exceeded 100. To correct these errors, I fixed the values by
subtracting 100 from those that were over the limit.
The 'International Reputation' column had 6 unique values instead of the expected 5 (between
5★ and 1★). To clean this column, I first identified all the invalid values, then used the drop()
function to remove the corresponding rows from the dataset. The reason for dropping these rows
is that the invalid values do not contribute to the research and could distort the analysis.
Using the isnull() function, I identified columns with null or missing values. The 'LoanEndDate'
and 'Popularity Hits' columns had 94.6% and 13.6% null values, respectively. During the cleaning
process, I dropped the 'LoanEndDate' column, and for 'Popularity Hits', I deleted the rows with
invalid values. These deletions will not impact my research, as the removed data is not relevant.
My research question primarily focuses on market value and player statistics, which is why I
dropped several irrelevant columns. For instance, columns like FullName, PhotoURL, PlayerURL,
Height, Weight, Country, CurrentClub, ContractInfo, PlayingPositions, PreferredFoot, DateJoined,
and LoanEndDate are not used in my research. Additionally, after analyzing the data, I
discovered that some columns are the sum of other columns. Therefore, I kept the summed
columns and dropped the others, as using the summed data is more effective for my research.
For example:
● CrossingAbility + FinishingAbility + HeadingAccuracy + ShortPassing + Volleys =
AttackingSkills
● Dribbling + CurveAbility + FreeKickAccuracy + LongPassing + BallControl =
SkillAttributes
● Acceleration + SprintSpeed + Agility + Reactions + Balance = MovementSkills
● ShotPower + JumpingAbility + Stamina + Strength + LongShots = PowerSkills
● Marking + StandingTackle + SlidingTackle = DefendingSkills
● GoalkeeperDiving + GoalkeeperHandling + GoalkeeperKicking + GoalkeeperPositioning,
GoalkeeperReflexes = GoalkeepingSkill
● Pace + Shooting + Dribbling.1 + Defending + Physical = BaseStats
After cleaning, 24 columns and 16,110 rows remained, resulting in 386,640 data points, which
represents 26.4% of the original dataset
