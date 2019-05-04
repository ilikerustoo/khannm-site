+++
date = "2019-05-02"
title = "Advisagator - Secure Your Future"
math = "true"

+++

## What is Advisagator?

Advisagator is a tool built by me and other members in the class of "481 - Software Innovation II". The class was split up into teams and each group was tasked with a different tool and our tool help students create and upload a four year old plan of the classes that they are required to take to fulfill their major requirements in order to graduate. The four year plans is made by the student and tool simply facilitates communicating and send this information to their adviser. The adviser must be informed of this plan in order to point any flaws or overlooked aspects of the classes being taken and makes it easier to gain approval to sign up for classes. This also help advisers track where their students are in the four year plans to see if things are going according to plan and if not, changes must be made before the students falls through. The tool can be seen in this repository on GitHub:

## Tools we used

The application is built using `flask` which is web framework that provides one with tools, libraries, and technologies that allow one to build a web application. These web applications can be whole sites to a few pages or even short blogs. `flask` does not have many dependencies and managing our various pages easy to handle especially if any changes were made. The alternative `django` was considered was ultimately deemed overkill for a small project like this.

## How does it work?

When you enter the site, you are presented with a login screen that could be either as a professor/adviser or a student. Depending on the login, different options are presented.

![Login_Screen](/images/login_screen.png)

A register option is also available at the top to register as a student or teacher as can be seen below

![Register_Page](/images/create_account.png)

After login, you are the student or teacher dashboard that welcomes you and presented several options at the top of the navigation bar depending on a student or teacher login. However, both contain the `4 year plan` option. Here is an example of one from the student's point of view.

![student_welcome](/images/welcome_screen.png)

After clicking the 4 year plan, you are presented with two options. The student is meant to download a template in the `.xlsx` format to be filled out and uploaded. This upload refers to the database, retrieves the user's name, and renames the uploaded file by appending the first and last name to the beginning of a file. This can be seen the following code:

```
if file:
    student_name = db.query_db(
        "select name from people where person_id=?;", [flask.session["id"]]
    )[0][0]
    contents = file.stream.read()
    with open(
        f"{app.config['UPLOAD_FOLDER']}/{student_name}_{file.filename}", "wb"
    ) as out_file:
        out_file.write(contents)
return flask.redirect("/students/4yrplan/")

return flask.render_template("/students/4yrplan.html")
```

If the file was named `4yrplan.xlsx`, then the file would be renamed as `JoeSmith_4yrplan.xlsx`. This would make it easier for a teacher to find a student's file. Upon clicking the `4 year plan` on a teacher login, the teacher would be redirected to a view of a folder containing every student file.

![student_files_view](/images/student_file_view.png)

If you are interested in this project or would like to extend it further, you could visit this [repository](https://github.com/GatorEducator/advisagator).
