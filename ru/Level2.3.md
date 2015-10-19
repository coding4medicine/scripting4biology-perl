# String processing in PERL

## PERL

### Simple string

In PERL, a string is described as a variable.

~~~~~~~~
#!/usr/bin/perl
$x="My name is Alice";
print $x,"\n";
~~~~~~~~

Joining two strings

You can join two strings by using '.'.

~~~~~~~~
#!/usr/bin/perl
$x="My name";
$y="is Alice";
$z=$x.$y;
print $z,"\n";
~~~~~~~~

### Splitting a string

You can use 'substr' to extract part of a string. The first parameter in substr command is a string, second parameter is starting position (begins with 0) and third parameter is number of letters to be extracted. The following command should extract 'Seattle' from the sentence.

~~~~~~~~
#!/usr/bin/perl
$s="I am flying from Seattle to San Francisco";
$t=substr($s,17,7);
print "$t\n";
~~~~~~~~


### Searching within a string

You can use grep-like regular expression to search within a string. We are looking for letters S or F in the original string. All other grep-like regular expression commands can be used in this kind of searches.

~~~~~~~~
#!/usr/bin/perl
$s="I am flying from Seattle to San Francisco";
if($s=~/[SF]/)
{
   print "The line has S or F\n";
}
else
{
  print "No S or F found\n";
}
~~~~~~~~

### Search and replace

You can also use regular expression to replace words. The following command replaces all occurrences of Seattle with London.

~~~~~~~~
#!/usr/bin/perl
$s="I am flying from Seattle to San Francisco";
$s=~ s/Seattle/London/g;
print "$s\n";
~~~~~~~~

