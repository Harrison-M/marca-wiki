## Notes on Development
**Add any notes on the dev process here with date and name.  New bits on top.**

***


5/24/2012 by Andy (commit [392578668886d63ac8f94d06a3b9d0b17ad0caec])
* Refactored "project" and "getProject" in \CourseBundle\Course.php" to "projects" and "getProjects" respectively (they deal with the entire collection of projects for a course)

* The delete function isn't checking for a user authentication token. Is it secure? I'm still a little fuzzy on where we need to check for that. 

* The deleteProject and createProject functions in Marca/CourseBundle/Controller/ProjectController now redirect to course_show instead of project_show on successful completion. The project_show template wasn't working, and project manipulation was being done on the course_show page. 