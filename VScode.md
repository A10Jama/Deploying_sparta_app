## Adding folder that will be ignored by your repo
<img width="842" alt="Screenshot 2023-04-18 at 15 53 47" src="https://user-images.githubusercontent.com/129948378/232819091-0170df03-8b42-4f9c-8d11-23c4a07f9304.png">

If there are any file that contain some private information, such as IP adresses, Passwords, etc., you can create a file that will contain the list of all the files and folders you want to be ignored by git add, meaining they wont be uploaded to your repository.

To add ignore file you have to:

It's optional, but can be a good practice to create a folder called ignores (or name whatever you like) that will contain the files you want to be ignored by git
Create .gitignore file
Open the file and list all the folders and files you want to be ignored, for example /ignores to select our folder we created
Move the files you want to be ignored into /ignores folder
Now, if you try to use git commands your ignores folder will be skipped
