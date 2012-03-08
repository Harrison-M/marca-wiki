# Marca Queries Refactored to Repositories for reuse throughout the app

_Call functions by naming the repository in the controller and then the function_
`$roll = $em->getRepository('MarcaCourseBundle:Roll')->findRollByCourse($id);`

## Roll Repository
findRollByCourse($id)
`       public function findRollByCourse($id)
    {
        return $this->getEntityManager()
            ->createQuery('SELECT p.lastname,p.firstname,r.role from MarcaCourseBundle:Roll r JOIN r.profile p JOIN r.course c WHERE c.id = ?1 ORDER BY p.lastname,p.firstname')->setParameter('1',$id)->getResult();
    }`
_Finds roll based on the course id._