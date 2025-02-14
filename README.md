# CLC Database Project

## Project Aims and Goals

The goal of this project is to create a cohesive full-stack application that will allow users to quickly and easily check in and out equipment and rentals from the CLC front desk. This app will be hosted on the local network to ensure accessibility from other computers in case of technical issues on the main front desk computer.

### Features:
- Register new users.
- Check in/out existing equipment.
- Restrict/un-restrict users.
- Review checked-out items.
- View the database itself.

### Improvements:
- Enhanced performance for obtaining user and equipment/video data via barcodes.
- Associate one user with multiple barcodes, preventing multiple simultaneous item checkouts across different barcodes.
- Prevent direct editing of database tables via the app to ensure data integrity.
- Introduce dedicated pages for clean data entry for new equipment and videos.
- Enable multi-field search functionality for faculty, equipment, and videos (e.g., serial number, title, author).


## UI/UX Design

While the initial homepage design is complete, the rest of the app still requires design work. The design can be completed in this file using **Figma** or another UI/UX design tool.


## Technical Specifications

The app will be developed in two stages:

1. **Database Setup**  
   - Design, create, and upload data to a MySQL database hosted locally.
   - The database has been created using MySQL Workbench but needs further data upload and testing.

2. **Application Development**  
   - **Frontend**: Implemented in HTML.  
   - **Backend**: Built using the Django web framework with a Model-View-Template (MVT) architecture.  


## Running the Project

1. Open **VS Code**, then navigate to:  
   `File > Open Folder > Desktop > CLC Database Project > clc_database_app`
2. Open the terminal in VS Code:  
   `Terminal > New Terminal`
3. Start the development server:  
   ```bash
   python3 manage.py runserver
   ```
4. If the project was successfully started, the following information should appear on the command line:
   ```bash
   Watching for file changes with StatReloader
   Performing system checks...
  
   System check identified no issues (0 silenced).
   November 21, 2024 - 18:07:45
   Django version 5.1.3, using settings 'clc_database_app.settings'
   Starting development server at http://127.0.0.1:8000/
   Quit the server with CONTROL-C.
   ```
5. When you are done with the server session, make sure to shut it down using CTRL-C, as noted above. If you fail to do this step, this will leave the server running indefinitely


## Creating New HTML Pages

1. To create a new HTML Page, navigate to the `src > templates` subfolder of the project
2. Once you have completed it, add the following code to the *views.py* document, replacing *name_of_page* with your page name:
   ```bash
   def name_of_page(request):
     template = loader.get_template('name_of_page.html')
     return HttpResponse(template.render())
   ```
3. Then, add the following code to the *urls.py* document
   ```bash
   path('name_of_page/', views.name_of_page, name='name_of_page')
   ```


## Source Control with Git

1. To push new code to the repository, first ensure that you are in the *clc_database_app* directory
2. Make sure you are using your credentials for each commit. To view the email and name associated with git, use the following commands:
```bash
git config --list
```
3. To change the user and email associated with commits for local instance, use the following commands, replacing *<your_name>* and *<your_email>* appropriately:
```bash
git config --local user.name "<your_name>"
git config --local user.email "<your_email>"
```
4. To add, commit and push new code, follow the workflow:
```bash
git add .
git commit -m "Your commit message"
git push
```
5. To create a new branch and push to that branch the code from the current branch you are on, use the following commands, replacing *<your_branch_name>* appropriately:
```bash
git checkout -b <your_branch_name>
git push --set-upstream origin <your_branch_name>
```
6. If there are changes on the remote repository that need to be added to your local repository or you need to push new code make sure to run this command first, replacing *<your_branch_name>* with main or appropriately:
```bash
git pull origin <your_branch_name>
```
7. Make sure you are in the correct branch before pulling, otherwise this will cause merge issues. I.e. Do not pull from main if you are in “dev” branch


## Common Troubleshooting Issues

1. If the project fails to start with an *Error: Port already in use error*, run the following command to obtain the port that the server is running on:
   ```bash
   ps auxw | grep runserver
   ```
2. The command line should then return something similar to this:
   ```bash
   beethoven         7501   0.0  0.0 410773520   3744 s001  T    11:42AM   0:00.21 /Library/Frameworks/Python.framework/Versions/3.13/Resources/Python.app/Contents/MacOS/Python manage.py runserver
   beethoven         7830   0.0  0.0 410072768    800 s001  R+   11:49AM   0:00.00 grep runserver
   ```
3. Now, using the port obtained from running the grep command, you’re going to want to kill that process with the following command (assuming 7501 is the listed port ID):
   ```bash
   kill -9 7501
   ```
