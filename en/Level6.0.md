# Level 6 - Complex Programs

## Computing GC-content

~~~~~~~~
#!/usr/bin/perl

#
#
#

open(IN,$ARGV[0]);
while(<IN>)
{
        if($_=~/^>(\S+)/)
        {
                $name=$1;
                print "WARNING: duplicate name $name\n" if($gene{$name} ne "");
        }
        else
        {
                $line=$1 if($_=~/(\S+)/);
                $gene{$name} .=$line;
        }
}
close(IN);


foreach $key (keys(%gene))
{
        $seq=$gene{$key};
        $seq=~s/N//g;
        $L=length($seq);
        $seq=~s/[AT]//g;
        $r=length($seq)/$L; print "$r\n";
}

~~~~~~~





## K-mer counting



~~~~~~~
#!/usr/bin/perl

open(IN,$ARGV[0]);
while(<IN>)
{
        if($_=~/^>(\S+)/)
        {
                $name=$1;
                print "WARNING: duplicate name $name\n" if($gene{$name} ne "");
        }
        else
        {
                $line=$1 if($_=~/(\S+)/);
                $gene{$name} .=$line;
        }
}
close(IN);

$N=1;

foreach $key (keys(%gene))
{
        $seq=$gene{$key};
        for($i=0; $i<=length($seq)-$N; $i++)
        {
                $sub=substr($seq,$i,$N);
                print "$sub\n";
        }
        $seq=reverse($seq);
        $seq=~s/A/X/g; $seq=~s/T/A/g; $seq=~s/X/T/g;
        $seq=~s/C/X/g; $seq=~s/G/C/g; $seq=~s/X/G/g;

        for($i=0; $i<=length($seq)-$N; $i++)
        {
                $sub=substr($seq,$i,$N);
                print "$sub\n";
        }
}
~~~~~~~


## Translating nucleotides into proteins


~~~~~~~~
#!/usr/bin/perl


$code{"AAA"}="K"; $code{"AAT"}="N"; $code{"AAC"}="N"; $code{"AAG"}="K";
$code{"TTT"}="F"; $code{"TTA"}="L"; $code{"TTC"}="F"; $code{"TTG"}="L";
$code{"CCC"}="P"; $code{"CCA"}="P"; $code{"CCT"}="P"; $code{"CCG"}="P";
$code{"GGG"}="G"; $code{"GGA"}="G"; $code{"GGT"}="G"; $code{"GGC"}="G";
$code{"ATA"}="I"; $code{"ATT"}="I"; $code{"ATC"}="I"; $code{"ATG"}="M";
$code{"TAA"}="*"; $code{"TAT"}="Y"; $code{"TAC"}="Y"; $code{"TAG"}="*";
$code{"CAA"}="Q"; $code{"CAT"}="H"; $code{"CAC"}="H"; $code{"CAG"}="Q";
$code{"GAA"}="E"; $code{"GAT"}="D"; $code{"GAC"}="D"; $code{"GAG"}="E";
$code{"ACA"}="T"; $code{"ACT"}="T"; $code{"ACC"}="T"; $code{"ACG"}="T";
$code{"TCA"}="S"; $code{"TCT"}="S"; $code{"TCC"}="S"; $code{"TCG"}="S";
$code{"CTA"}="L"; $code{"CTT"}="L"; $code{"CTC"}="L"; $code{"CTG"}="L";
$code{"GTA"}="V"; $code{"GTT"}="V"; $code{"GTC"}="V"; $code{"GTG"}="V";
$code{"AGA"}="R"; $code{"AGT"}="S"; $code{"AGC"}="S"; $code{"AGG"}="R";
$code{"TGA"}="*"; $code{"TGT"}="C"; $code{"TGC"}="C"; $code{"TGG"}="W";
$code{"CGA"}="R"; $code{"CGT"}="R"; $code{"CGC"}="R"; $code{"CGG"}="R";
$code{"GCA"}="A"; $code{"GCT"}="A"; $code{"GCC"}="A"; $code{"GCG"}="A";

open(IN,"gene");
$line=<IN>;

$count=0;

while($count<=100000)
{
        $section= substr $line, $count, 3;
        print $code{$section};
        $count=$count+3;
}
print "\n";

~~~~~~~~


## Finding RNase P RNA
