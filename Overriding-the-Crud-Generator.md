# Overriding Crud Generator

Based on the following two links:

[http://symfony.com/doc/2.0/bundles/SensioGeneratorBundle/index.html](http://symfony.com/doc/2.0/bundles/SensioGeneratorBundle/index.html)
[http://symfony.com/doc/2.0/cookbook/bundles/inheritance.html](http://symfony.com/doc/2.0/cookbook/bundles/inheritance.html)

Like Overriding the FOS user bundle, create a new bundle register the parent (the bundle you want to override) in the core bundle php file.  For example, this Authenticate Bundle overrides the FOSUserBundle:

 <?php
 namespace Marca\AuthenticateBundle;
 use Symfony\Component\HttpKernel\Bundle\Bundle;
 class MarcaAuthenticateBundle extends Bundle
 {
     public function getParent()
     {
         return 'FOSUserBundle';
     }
 }

Once done, you can override controllers or twig files by duplicating the file in the new bundle and then tweaking them as needed (they must be in the same place in the new bundle as they are in the original bundle).

For overriding the Crud generator, Marca uses a Generator Bundle (src/GeneratorBundle).  The twig files for the crud are found in Resources/skeleton/crud/views.  The "others" folder has twig that is included in the standard crud twig files.  
We are overriding the crud generators to create our own displays including layout and display code (elements and css etc).  
The command line is overridden somewhat differently.  Once again, copy the file from the original bundle to the new bundle and rename the function and extend it.  For example, in the Command/MyDoctrineCrudCommand.php file in the GeneratorBundle:

 class MyDoctrineCrudCommand extends \Sensio\Bundle\GeneratorBundle\Command\GenerateDoctrineCrudCommand
 {
     protected function configure()
     {
         parent::configure();
         $this->setName('mydoctrine:generate:crud');
     }

     protected function getGenerator()
     {
         $generator = new DoctrineCrudGenerator($this->getContainer()->get('filesystem'), __DIR__.'/../Resources/skeleton/crud');
         $this->setGenerator($generator);
         return parent::getGenerator();
     }
 }