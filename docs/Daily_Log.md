# March 4th 2026 
## Understanding the dataset.
  * Plan:
    - [] download zea mays promoters from EPDnew,
    - [] answer question,
    - [] validate assumptions,
    - [] make script so show dataset info
  * Questions:
    - what are the two columns?
    - how long are the sequences?
    - Are they always the same length?
    - How many promoters exist in Zea mays?
    - Are all sequences exactly 60 bp?
    - Do sequences contain ambiguous bases?
    - How many promoters exist per gene?
  * Assumptions:
    - the ReadMe says the seq are -49 to +10 around the TSS, verify this
  * Scripting:
    - print number of sequences, max/min length, example sequence.
    - extract promoter_id sequence gene_name chromosome TSS_position strand
## Log
  * I went to https://epd2.vital-it.ch/ftp/epdnew/Z_mays/current/ and there are many file types, I dont understand what they contain.
  >
    Zm_EPDnew.dat
    Zm_EPDnew.fps
    Zm_EPDnew.idx
    Zm_EPDnew.sga
    Zm_EPDnew_001_zm3.dat
    Zm_EPDnew_001_zm3.fps
    Zm_EPDnew_001_zm3.idx
    Zm_EPDnew_001_zm3.sga
  * the ones with the longer names contain the version and the assembly for reproducibilit.
  * **.dat** is the primary full promoter database, this is how its stored: 
  >
      ID   HBB_1
      GN   Name=HBB
      DE   hemoglobin subunit beta
      OS   Homo sapiens
      SE   caggagccagggctgggcataaaagtcagggcagagccatctattgcttACATTTGCTTC
      FP   genomic coordinates
      //

  >
    Information Key
    Field	Meaning
    ID	promoter identifier
    GN	gene name
    DE	gene description
    OS	organism
    **SE	promoter sequence (-49 to +10 around TSS) MOST IMPORTANT**
    FP	genomic position of TSS
      
  * **.sga** simplified genomic coordinate file, it contains:
  >
     chromosome
     feature type (TSS)
     position
     strand
     count
     promoter ID
    
  >
    Example
    chr1 TSS 123456 + 1 PROMOTER_ID
  * **.fps** SSA toolkit format. Stores promoter position, motif information, feature annotations.
  * **.idx** index file. contains promoter ID, byte offset, entry length. 
