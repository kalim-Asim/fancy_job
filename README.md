# Daily Number Incrementer

A Python script that automatically increments a number in a text file, commits the change to Git, and updates a cron job to run the script at a new random time daily. Perfect for maintaining a daily commit streak or tracking sequential values with a dynamic schedule.


You might want to run the script manually for the first time to verify it works
before setting up a cronjob

3. # Optional: If you prefer to ensure the script runs at a fixed time initially, you can manually set up a cron job:
   However, if you wish to use LLM-based commit message generation, you need to
   install [uv](https://docs.astral.sh/uv) to manage dependencies.
   The first time you run it, it will download packages required for its execution
   and also a large language model from Hugging Face

```bash
# Use LLM
FANCY_JOB_USE_LLM=true uv run python update_number.py
```

3. Setup a cron job to run the script daily:

```bash
crontab -e
```

Add the following line to the crontab file:

```bash
0 6 * * * cd /path/to/your/repo && python update_number.py
# or with LLM
0 6 * * * cd /path/to/your/repo && FANCY_JOB_USE_LLM=true uv run python update_number.py
```

This will initially run the script at 6am the next day.

