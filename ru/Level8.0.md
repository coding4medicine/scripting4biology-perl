# Module 8 - Packages
Modules/packages  -
~~~~~~~~
#!/usr/bin/perl

use Useful;
open(IN,"gene");
$_=<IN>;

$x=Useful::translate($_);

print $x,"\n";
~~~~~~~~
Modules/packages  -
~~~~~~~~
#!/usr/bin/env python

import Useful
~~~~~~~~
Modules/packages  -
~~~~~~~~
package main

import ("fmt"
             "Useful")

func main() {

}
~~~~~~~~
