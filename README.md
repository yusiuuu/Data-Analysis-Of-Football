# Data-Analysis-Of-Football
Analyzed Kaggle football datasets to evaluate team performance by identifying strengths (goals, penalties, shots on target) and weaknesses (fouls, offsides, missed shots, goals conceded). Extracted key match events to provide actionable insights and support performance improvement and strategic decision-making.

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/bca30c53-4884-4b6e-8f87-4024b4d72eb6" />

```Python
## grouping by player when is goal
goal = df_events[df_events['is_goal']==1]

## Plotting the hist
# fig=plt.figure(figsize=(13,10))
plt.hist(goal.time, 100)
plt.xlabel("TIME",fontsize=10)
plt.ylabel("# of goals",fontsize=10)
plt.title("goal counts vs time",fontsize=15)
x=goal.groupby(by='time')['time'].count().sort_values(ascending=False).index[0]
y=goal.groupby(by='time')['time'].count().sort_values(ascending=False).iloc[0]
x1=goal.groupby(by='time')['time'].count().sort_values(ascending=False).index[1]
y1=goal.groupby(by='time')['time'].count().sort_values(ascending=False).iloc[1]
plt.text(x=x-10,y=y+10,s='time:'+str(x)+',max:'+str(y),fontsize=12,fontdict={'color':'red'})
plt.text(x=x1-10,y=y1+10,s='time:'+str(x1)+',the 2nd max:'+str(y1),fontsize=12,fontdict={'color':'black'})
plt.show()
```
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/47833b98-dfb0-4784-ae6b-8cbd9475500a" />

```Python
import matplotlib.pyplot as plt

top_left = sum(penalties["shot_place"] == 12)
bot_left = sum(penalties["shot_place"] == 3)
top_right = sum(penalties["shot_place"] == 13)
bot_right = sum(penalties["shot_place"] == 4)
centre = sum(penalties["shot_place"] == 5) + sum(penalties["shot_place"] == 11)
missed = sum(penalties["shot_place"] == 1) + sum(penalties["shot_place"] == 6) + sum(penalties["shot_place"] == 7) + sum(penalties["shot_place"] == 8) + sum(penalties["shot_place"] == 9) + sum(penalties["shot_place"] == 10)

labels_pen = ["Top Left", "Bottom Left", "Centre", "Top Right", "Bottom Right", "Missed"]
num_pen = [top_left, bot_left, centre, top_right, bot_right, missed]
colors_pen = ["red", "aqua", "royalblue", "yellow", "violet", "m"]

plt.figure(figsize=(10, 8))  # Bigger figure

plt.pie(
    num_pen,
    labels=labels_pen,
    colors=colors_pen,
    autopct='%1.1f%%',
    startangle=90,
    explode=(0, 0, 0.1, 0, 0, 0.2),  # Emphasize 'Centre' and 'Missed'
    shadow=True,
    labeldistance=1.1,  # Move labels further out
    wedgeprops={'edgecolor': 'black'}
)

plt.axis('equal')
plt.title("Percentage of Each Placement of Penalties", fontsize=18, fontweight="bold")
plt.tight_layout()
plt.show()

```
<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/ac9b0f0d-c971-48f7-9696-9ea5a9a74258" />
