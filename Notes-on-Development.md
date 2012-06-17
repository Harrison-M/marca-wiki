**Add any notes on the dev process here with date and name.  New bits on top.**

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