# SCAIA

## Installer

This component contains the required files for installing SCAIA back-end. Additionally, the whole installation procedure is provided here.

### Requirements

- A web server with PHP installed (7.1+)
- A rename rule allowing to access .php files without the extension (e.g. /api/new_job.php -> /api/new_job)
- MariaDB or MySQL, curl and cron installed and configured on the web server
- Node.js with Angular CLI

### Installation

1. Download the [back-end](https://github.com/GaborFarkas/scaia-backend) and extract the files to their destination on the web server.
2. Download the installer (this repository) and extract its content to the back-end's `admin` folder.
3. Run the back-end installer by connecting to the install endpoint from a browser (e.g. https://localhost/admin/install) and following the usual UserSpice installation steps provided on screen.
4. Download the [front-end](https://github.com/GaborFarkas/scaia-frontend) package and extract it where your Node.js environment is set up.
5. Build the front-end by running `ng build`.
6. Copy the built site next to the back-end.
7. Set up the back-end's job updater (/admin/users/cron/update_jobs.php) as a cron job with curl.
```
    * * * * * /usr/bin/curl --silent https://localhost/admin/users/cron/update_jobs.php >/dev/null 2>&1 
```