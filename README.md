# S. strongyloides
genome and annotation of S.strongyloides genome.

## Genome assembly

The genome was assembled from ONT data using Flye 2.8.1 with a minimum overlap allowance of 2500bp, following assembly we did not run any sort of polishing step as this is built into flye.

Following assembly we quantified the quality of our scaffolds compared to previous versions of the genome using QUAST and estimated its completeness compared to S.ratti using BUSCO.

## Genome annotation

We next annotated the genes and repeats of the genome.

We used RepeatModeler followed by RepeatMasker (params: -u -s -poly -engine rmblast -gff -no_is -gccalc -norna) to annotate the repeat content of the genome.

We annotated the genes in the genome using both the MAKER pipeline and the FunAnnotate pipeline:

For MAKER we ran three iterations of annotation, the first generates a gene model using proteins and transcripts taken from WormBase (https://parasite.wormbase.org/Strongyloides_stercoralis_prjeb528/Info/Index/). The second iteration used the gene model taken from the first, and the final iteration used the second iterations gene model.

For FunAnnotate we first predicted gene models using the Augustus c_elegans_trsk database, the BUSCO nematoda_odb10 database, and the proteins and transcripts for S. strongyloides taken from WormBase (https://parasite.wormbase.org/Strongyloides_stercoralis_prjeb528/Info/Index/). Following gene prediction we then annotated the genome using the gene model.

After both annotations were generated, we then found the overlap between the two and generated a combined annotation which used high quality genes found in either GFF.

