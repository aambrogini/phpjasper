## This project is a fork from [PHPJasper/phpjasper](https://github.com/PHPJasper/phpjasper) but it has been modified to working into symfony applications.

### Symfony
To get start in symfony, simple use the guide in the phpjasper example section but change paths and not use require autoload.
Example (symfony 3.x controller):

```
<?php

namespace AppBundle\Controller;

use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
use Symfony\Bundle\FrameworkBundle\Controller\Controller;
use Symfony\Component\HttpFoundation\Request;
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Method;
use PHPJasper\PHPJasper;

class DefaultController extends Controller {

    /**
     * @Route("/", name="default")
     */
    public function indexAction(Request $request) {
        $input = '/src/SymfonyProject/vendor/geekcom/phpjasper/examples/hello_world.jrxml';   

        $output = '/src/SymfonyProject/vendor/geekcom/phpjasper/examples';    
        $options = [ 
            'format' => ['pdf', 'rtf'] 
        ];

        $jasper = new PHPJasper;

        $jasper->process(
            $input,
            $output,
            $options
        )->execute();
        
        return $this->render('default/index.html.twig');
    }

}
```
