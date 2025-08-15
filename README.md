Automated File Cleanup Script

This project is a simple Linux Shell Script that automatically removes files older than a specified number of days from the current directory. It is useful for automating cleanup tasks, saving disk space, and keeping directories organized.

📌 Features

Deletes files older than a specified number of days.

Uses Linux commands (date, rm) to calculate file age.

Works in any Linux/Unix environment with Bash shell.

Can be scheduled with cron jobs for automatic cleanup.

🛠️ Technologies Used

Linux

Bash Shell Scripting

Linux Command-Line Tools (date, rm, file handling)

🚀 How It Works

The script sets a threshold number of days (days=4 by default).

It calculates the current time in seconds since epoch.

It checks each file’s last modified time using date -r.

If a file is older than the threshold, it is removed automatically.

📂 Script Example
#!/bin/bash

# Set the number of days
days=4

# Get the current date in seconds
current=$(date +%s)

# Loop through all files in the current directory
for file in *
do
  # Check if the file is older than X days
  if [ -f "$file" ] && [ $(($current - $(date +%s -r "$file"))) -gt $(($days * 24 * 60 * 60)) ]
  then
    # Remove the file
    rm "$file"
  fi
done


📥 Installation & Usage

Save the script into a file, e.g. cleanup.sh.

Make the script executable:

chmod +x cleanup.sh


Run the script:

./cleanup.sh


The script will remove all files in the current directory older than 4 days (or the number you set).

⚠️ Important Notes

This script permanently deletes files. Test it in a safe directory before using in production.

You can change the number of days by modifying:

days=4

⏲️ Automating with Cron (Optional)

To run this script automatically every day at midnight:

crontab -e


Add the following line:

0 0 * * * /path/to/cleanup.sh

📌 Example Use Cases

Automatically clear old log files.

Remove temporary files in project directories.

Keep system folders clean and optimized.

👨‍💻 Author

Purushottam Kumar

Skills: Linux, Bash Scripting, File Handling, Automation
