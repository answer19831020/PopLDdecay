# PopLDdecay
<b>PopLDdecay: A new simple and efficient software for Linkage Disequilibrium Decay analysis based Variant Call Format</b>

1) Install
------------
 For <b>linux /Unix </b>
<pre>
        tar -zxvf  PopLDdecayXXX.tar.gz
        cd PopLDdecayXXX;                            # if Link do not work ,Try <b>re-install</b>  two  library
        cd src;                                      #【zlib and gzstream】 and copy them to the  library Dir
        make ; make clean                            # PopLDdecayXX/src/include/zlib 
        ../bin/PopLDdecay                            # PopLDdecayXX/src/include/gzstream
</pre>
</br>

</br> 
For <b>macOS </b>
<pre>
#step1 :Should must <b>re-install</b>  two  library 【zlib and gzstream】
              see  [zlib and gzstream] website 
#step2  :  # Copy these two library into Dirs
              cp libz.a libz.so*  PopLDdecayXX/src/include/zlib
              cp libgzstream.a  PopLDdecayXX/src/include/gzstream
#step3  : 
              sh make.sh # or [make && make clean]
</pre>

2) Example
------------
* 1) Calculate LD decay 
```
# 1） For gatk VCF file deal , run PopLDdecay  direct
./bin/PopLDdecay    -InVCF  SNP.vcf.gz  -OutStat LDdecay   
# 2)  # for plink [.ped .map], chang plink 2 genotype first  2) run PopLDdecay  
perl bin/mis/plink2genotype.pl    -inPED in.ped -inMAP in.map  -outGenotype out.genotype ;      ./bin/PopLDdecay        -InGenotype out.genotype -OutStat LDdecay 
# 3)  To Calculate the subgroup GroupA LDdecay in VCF Files   # put GroupA sample name into GroupA_sample.list
 ./bin/PopLDdecay   -InVCF  <in.vcf.gz>  -OutStat <out.stat>   -SubPop    GroupA_sample.list
```
* 2) draw the Figure
```
        #    2.1  For one Population
        perl  bin/Plot_OnePop.pl  -inFile   LDdecay.stat.gz  -output  Fig
        #    2.2  For one Population  muti chr          # List Format [chrResultPathWay]
        perl  bin/Plot_OnePop.pl  -inList   Chr.ReslutPath.List  -output Fig
        #    2.3  For muti Population                   #  List Format :[Pop.ResultPath  PopID ]
        perl  bin/Plot_MutiPop.pl  -inList  Pop.ReslutPath.list  -output Fig
```
* 3) you can see the  result  [LDdecay.stat.gz]  and   [Fig.png Fig.pdf]

3) Introduction
------------
Linkage disequilibrium (LD) decay[1] is the most important and most common analysis in the population resequencing[2]. Special in the self-pollinated crops, the LD decay may not only reveal much about domestication and breed history[3], but also can reveal gene flow phenomenon, selection regions[1].However, to measure the LD decay, it takes too much resources and time by using currently existent software and tools. The LD decay studies also generate extraordinarily large amounts of data to temporary storage when you using the mainstream software "Haploview"[4], the classical LD processing tools. Effective use and analysis to get the LD decay result remains a difficult task for individual researchers. Here, we introduce PopLDdecay, a simple- efficient software for LD decay analysis, which processes the Variant Call Format (VCF)[5] file to produce the LD decay statistics results and plot the LD decay graphs. PopLDdecay is designed to use compressed data files as input or output to save storage space and it facilitates faster and more computationally efficient than the currently existent softwares. This software makes the LD decay pipeline significantly
* <b> Parameter description</b>
```php
	Usage: PopLDDecay -InVCF  <in.vcf.gz>  -OutStat <out.stat>

		-InVCF       <str>    Input SNP VCF Format
		-InGenotype  <str>    Input SNP Genotype Format
		-OutStat     <str>    OutPut Stat Dist ~ r^2 File

		-SubPop      <str>    SubGroup SampleList of VCFFile [ALLsample]
		-MaxDist     <int>    Max Distance (kb) between two SNP [300]
		-MAF         <float>  Min minor allele frequency filter [0.005]
		-Het         <float>  Max ratio of het allele filter [0.88]
		-Miss        <float>  Max ratio of miss allele filter [0.25]
		-OutFilterSNP         OutPut the final SNP to calculate
		-OutPairLD   <int>    OutPut the PairWise SNP LD info [0]
		                      0/2:No_Out 1/3/4:Out_Brief 5:Out_Full

		-help                 Show this help [hewm2008 v3.30]

```
4) Results
------------
some LD decay images which I draw in the paper before.

* [50 Rices NBT](http://www.nature.com/nbt/journal/v30/n1/images/nbt.2050-F2.jpg)
* [31 soybeans  NG]( http://www.nature.com/ng/journal/v42/n12/images/ng.715-F1.jpg)

5）Discussing
------------
- email: hewm2008@gmail.com / hewm2008@qq.com  
- join the<b><i> QQ Group : 125293663</b></i>



######################swimming in the sky and flying in the sea ########################### ##

