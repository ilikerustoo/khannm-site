+++
date = "2019-05-1"
title = "Advisagator - Secure your future"
math = "true"

+++

## What is Advisagator?

Advisagator is a tool built by me and other members in the class of "481 - Software Innovation II". The class was split up into teams and each group was tasked with a different tool and our tool help students create and upload a four year old plan of the classes that they are required to take to fulfill their major requirements in order to graduate. The four year plans is made by the student and tool simply facilitates communicating and send this information to their adviser. The adviser must be informed of this plan in order to point any flaws or overlooked aspects of the classes being taken and makes it easier to gain approval to sign up for classes. This also help advisers track where their students are in the four year plans to see if things are going according to plan and if not, changes must be made before the students falls through. The tool can be seen in this repository on GitHub:

## Tools we used

The application is built using `flask` which is web framework that provides one with tools, libraries, and technologies that allow one to build a web application. These web applications can be whole sites to a few pages or even short blogs. `flask` does not have many dependencies and managing our various pages easy to handle especially if any changes were made. The alternative `django` was considered was ultimately deemed overkill for a small project like this.

## How does it work?

When you enter the site, you are presented with a login screen that could be either as a professor/adviser or a student. Depending on the login, different options are presented. At the navigation bar at the top, we have the `4 year plan` option that redirects you tool another page which allows the student to upload a `csv` which is converted to a `pdf` and then viewable by the adviser.
