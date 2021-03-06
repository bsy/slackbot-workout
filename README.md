# slackbot-workout

A fun hack that gets Slackbot to force your teammates to work out! This is a fork from the [original](https://github.com/brandonshin/slackbot-workout) to add Heroku support, plus dial down the numbers (we're not as fit yet).

<img src = "https://ctrlla-blog.s3.amazonaws.com/2015/Jun/Screen_Shot_2015_06_10_at_5_57_55_PM-1433984292189.png" width = 500>

## Running on Heroku

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

1. Get a test token from https://api.slack.com/docs/oauth-test-tokens, put that in ``SLACK_USER_TOKEN_STRING``
2. Set ``SLACK_TEAM_DOMAIN`` to your slack subdomain - i.e. this ``https://{SLACK_TEAM_DOMAIN}.slack.com/home``
3. Go to https://www.slack.com/apps/A0F81R8ET-slackbot, add a new configuration and set ``SLACK_URL_TOKEN_STRING`` to the token from the URL.
4. Pick a slack channel ``SLACK_CHANNEL_NAME`` and find or set the ID ``SLACK_CHANNEL_ID`` (you can fetch using ``$ python fetchChannelId.py channelname`` if you have your this installed locally...)

## Running outside Heroku (aka, the hard way) 

1. Clone the repo and navigate into the directory in your terminal.

    `$ git clone git@github.com:brandonshin/slackbot-workout.git`

2. Go to your slack home page [https://{yourgroup}.slack.com/home](http://my.slack.com/home) & click on **Integrations** on the left sidebar.

    <img src = "https://ctrlla-blog.s3.amazonaws.com/2015/Jun/Screen_Shot_2015_06_05_at_7_21_33_PM-1433557303531.png" width = 300>

3. Scroll All the Way Down until you see **Slack API** and **Slackbot**. You'll need to access these two integrations.

    <img src="https://ctrlla-blog.s3.amazonaws.com/2015/Jun/Screen_Shot_2015_06_05_at_7_19_44_PM-1433557206307.png" width = 500>

4. In the **Slack API Page**, select **WebAPI** in the left side bar, scroll all the way down, and register yourself an auth token. You should see this. Take note of the token, e.g. `xoxp-2751727432-4028172038-5281317294-3c46b1`. This is your **User Auth Token**

    <img src="https://ctrlla-blog.s3.amazonaws.com/2015/Jun/Screen_Shot_2015_06_05_at_7_00_24_PM-1433557433415.png" width = 500>

5. In the **Slackbot** (Remote control page). Register an integration & you should see this. __Make sure you grab just the token out of the url__, e.g. `AizJbQ24l38ai4DlQD9yFELb`

    <img src="https://ctrlla-blog.s3.amazonaws.com/2015/Jun/Screen_Shot_2015_06_03_at_8_44_00_AM-1433557565175.png" width = 500>

6. Save your SLACK_USER_TOKEN_STRING and SLACK_URL_TOKEN_STRING as environmental variables in your terminal.

    `$ export SLACK_USER_TOKEN_STRING=YOURUSERTOKEN`
    
    `$ export SLACK_URL_TOKEN_STRING=YOURURLTOKEN`
    
    If you need help with this, try adapting the first 5 steps of the guide to [edit your .bash_profile](http://natelandau.com/my-mac-osx-bash_profile/)
    
7. Set up slack domain, channel name and id

    If you don't know the channel Id, fetch it using

    `$ python fetchChannelId.py channelname`

    Then export using:

    `$ export SLACK_TEAM_DOMAIN=YOURTEAMDOMANIO`
    `$ export SLACK_CHANNEL_NAME=YOURURLTOKEN`
    `$ export SLACK_CHANNEL_ID=YOURURLTOKEN`

8. If you haven't set up pip for python, go in your terminal and run.
`$ sudo easy_install pip`

9. While in the project directory, run

    `$ sudo pip install -r requirements.txt`

    `$ python slackbotExercise.py`

Run the script to start the workouts and hit ctrl+c to stop the script. Hope you have fun with it!
