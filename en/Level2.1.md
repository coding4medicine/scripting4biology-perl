Reading from a file  -


~~~~~~~~
#!/usr/bin/perl
open(IN,"filename");
$_=<IN>;
while(<IN>)
{
	print $_;
}
close(IN);
~~~~~~~~

