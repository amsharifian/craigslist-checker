Craiglist Checker
=================
Send a text when there's a new "For Sale" post for a given keyword or phrase.

The script sends an SMS message to a given phone number using GMail's SMTP protocol, so you'll need to add your GMail username and password to the config file.

An SMS message will only be sent if a new post appears (based on the full URL).

Setup
-----
Install the required libraries via pip:

    pip install -r requirements.txt

Usage
-----
    python craigslist-checker.py <search-term> <phone-number>

It's useful to setup a cronjob that will run the script every N minutes.

Setting up cron job
----
Put a shell script in one of these folders:

    /etc/cron.daily, /etc/cron.hourly, /etc/cron.monthly or /etc/cron.weekly.
    
If these are not enough for you you can add more specific tasks eg. twice a month or every 5 minutes or... go to the terminal and type:
    
    corntab -e
    
this will open your personal crontab (cron configuration file), the first line in that file explains it all (don't you think)! In every line you can define one command to run, and the format is quite simple when you get the hang of it. So the structure is:

    minute hour day-of-month month day-of-week command
    
For all the numbers you can use lists eg`, 5,34,55` in the first field will mean run at 5 past 34 past and 55 past what ever hour is defined.

You can also use intervals, they are defined like this: `*/20` this example means every 20th and if in the minutes column this will be equivalent to 0,20,40
So to run a command every monday at 5:30 in afternoon:

    30 17 * * 1 /path/to/command
    
or every 15 minutes

    */15 * * * * /path/to/command
    
Note that the day-of-week goes from 0-6 where 0 is sunday.

You can read more [here](https://help.ubuntu.com/community/CronHowto).
