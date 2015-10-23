# Level 8 - Packages

Modules/packages  -
~~~~~~~~
#!/usr/bin/perl

use Useful;
open(IN,"gene");
$_=<IN>;

$x=Useful::translate($_);

print $x,"\n";
~~~~~~~~
