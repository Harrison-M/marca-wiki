Notes on Development

by Andy 5/24
* Refactored "project" and "getProject" in \CourseBundle\Course.php" to "projects" and "getProjects" respectively (they deal with the entire collection of projects for a course)

* The delete function isn't checking for a user authentication token. Is it secure? I'm still a little fuzzy on where we need to check for that. 

* The deleteProject and createProject functions in Marca/CourseBundle/Controller/ProjectController now redirect to course_show instead of project_show on successful completion. The project_show template wasn't working, and project manipulation was being done on the course_show page. 