# youtube-dl-for-downloading-courses
youtube-dl is a command-line program to download videos from YouTube.com and a few more sites. It requires the Python interpreter, version 2.6, 2.7, or 3.2+, and it is not platform specific. It should work on your Unix box, on Windows or on macOS. It is released to the public domain, which means you can modify it, redistribute it or use it however you like.

## Getting Started
The example used in this instructions will be focused on downloading a full course or multiple courses from pluralsight to your local machine. See the [documentation](https://github.com/rg3/youtube-dl/blob/master/README.md#readme) for other options.

### Prerequisites
You'll have to install the youtube-dl on your system

### Installing
To install it right away for all UNIX users (Linux, macOS, etc.), type:
```
sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl
sudo chmod a+rx /usr/local/bin/youtube-dl
```
If you do not have curl, you can alternatively use a recent wget:
```
sudo wget https://yt-dl.org/downloads/latest/youtube-dl -O /usr/local/bin/youtube-dl
sudo chmod a+rx /usr/local/bin/youtube-dl
```
Windows users can [download the .exe file](https://yt-dl.org/latest/youtube-dl.exe) and place it in any location on their PATH except for `%SYSTEMROOT%\System32` (e.g. do not put in C:\Windows\System32).

### Configuration
You can configure youtube-dl by placing any supported command line option to a configuration file. On Linux and macOS, the system configuration file is located at `/etc/youtube-dl.conf` and the user wide configuration file at `~/.config/youtube-dl/config`. On Windows, the user wide configuration file locations are `%APPDATA%\youtube-dl\config.txt` or `C:\Users\<user name>\youtube-dl.conf` Note that by default configuration file may not exist so you may need to create it yourself.
Add the following line to the  `youtube-dl.conf` file

```
-u <Username>
-p <Password>
-i
-c
--no-warnings
--console-title
--batch-file='batch-file.txt'
--max-sleep-interval 80
--min-sleep-interval 60
-o '%(playlist_title)s/%(chapter_number)s - %(chapter)s/%(playlist_index)s-%(title)s.%(ext)s'
-f 'best[height<=720]/worst[height>720]'
```
Replace <Username> and <Password> with your id and password for Pluralsight

### Adding the batch file
create a `batch-file.txt` file in the same location where you want to download the courses.
Add the URL of the course to the batch file. eg
```
https://app.pluralsight.com/library/courses/getting-started-git
```
Alternatively, you may add multiple courses to the batch file like this:
```
https://app.pluralsight.com/library/courses/getting-started-git
https://app.pluralsight.com/library/courses/front-end-web-development-get-started
https://app.pluralsight.com/library/courses/tactics-tools-troubleshooting-front-end-web-development
```
### Downloading through the terminal
Open the terminal and navigate to where the batch file was saved and run `youtube-dl`. e.g if you saved the batch file in `C:\Users\Videos` then go to that directory and type
```
 C:\Users\Videos> youtube-dl
```
All you courses will be downloaded in that directory, To download a different course paste the link in the `batch-file.txt` and run the command

##### Important
Pluralsight may block your account if you download too many courses at once. 3–5 is a good size if the course size is average.
