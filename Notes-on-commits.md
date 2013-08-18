**Add any notes on the commits here with date and name.  New bits on top.**
***
08/18/13
Merge Rubric branch with 8 commits
The main changes in the commits include a Rubric insert for edocs and is taken from the Page listing (there is now a switch to designate a page as a rubric.  Note that the insert does not allow for different rubrics at this point. 
Also, this commit added an review upload (found under More in the file listing).
Finally, a shot at fixing the scrolling in the editor on an ipad.
***
08/05/13 by Ron

**Research consent and updates for migrating to 2.3**
This commit makes some updates required for migrating to 2.3.
This commit creates the ability to track a research consent by users:  DB changes.  Institution will now have a research boolean (yes this institution has a research consent or not) and a research integer for users (0 no response, 1 yes, 2, no).  After update, db admin should update these two db fields setting institution.research appropriately and marca_user.research = 0.


***
11/15/2012 by Ron
Now using the spectrum jquery colorpicker
https://github.com/bgrins/spectrum

***
6/17/2012 by Andy (commit https://github.com/calliopeinitiative/marca/commit/21f6c745e83402564c0817b11db7bf9bc8c560ec)
* In this commit I introduce the restrictAccessTo function in the base controller. This function, which only works in the course context (route must include a {courseid}) does the following: 
** checks to see if the current user has one of the course roles passed to it in an array
** throws a access denied exception if the user does not have one of the passed roles
** returns true if they do

* I also use the fosUserBundle roles and the course owner object to control access to some features. 

* The forum bundle now has access controls throughout


***
5/24/2012 by Andy (commit https://github.com/calliopeinitiative/marca/commit/392578668886d63ac8f94d06a3b9d0b17ad0caec )
* Refactored "project" and "getProject" in \CourseBundle\Course.php" to "projects" and "getProjects" respectively (they deal with the entire collection of projects for a course)

* The delete function isn't checking for a user authentication token. Is it secure? I'm still a little fuzzy on where we need to check for that. 

* The deleteProject and createProject functions in Marca/CourseBundle/Controller/ProjectController now redirect to course_show instead of project_show on successful completion. The project_show template wasn't working, and project manipulation was being done on the course_show page. 