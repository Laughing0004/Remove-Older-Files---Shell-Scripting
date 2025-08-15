# Automated File Cleanup Script

This is a simple **Linux Shell Script** that automatically removes files older than a specified number of days from the current directory. It helps automate cleanup tasks, save disk space, and keep directories organized.

---

## 📌 Features
- Deletes files older than a specified number of days  
- Uses Linux commands (`date`, `rm`) to calculate file age  
- Works in any Linux/Unix environment with **Bash shell**  
- Can be scheduled with **cron jobs** for automatic cleanup  

---

## 🛠️ Technologies Used
- Linux  
- Bash Shell Scripting  
- Linux Command-Line Tools (`date`, `rm`, file handling)  

---

## 🚀 How It Works
1. The script sets a threshold number of days (`days=4` by default)  
2. It calculates the current time in **seconds since epoch**  
3. It checks each file’s last modified time using `date -r`  
4. If a file is older than the threshold, it is removed automatically  

---



## 📂 Script Example
```bash
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
```


📥 Installation & Usage

Save the script into a file, e.g. cleanup.sh


Make the script executable:
```bash
chmod +x cleanup.sh
```


Run the script:
```bash
./cleanup.sh
```


The script will remove all files in the current directory older than 4 days (or the number you set)



⚠️ Important Notes

This script permanently deletes files → test it in a safe directory first

You can change the number of days by modifying:

Days=4



⏲️ Automating with Cron (Optional)

To run this script automatically every day at midnight:
```bash
crontab -e
```


Add the following line:
```bash
0 0 * * * /path/to/cleanup.sh
```


📌 Example Use Cases

-> Automatically clear old log files

-> Remove temporary files in project directories

-> Keep system folders clean and optimized


## 👨‍💻 Author

  Purushottam Kumar

## Skills: Linux, Bash Scripting, File Handling, Automation
