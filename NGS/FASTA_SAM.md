# FASTA
https://kodomo.fbb.msu.ru/FBB/year_10/term1/fasta.html

Формат FASTA позволяет хранить следующую информацию о последовательности:
##### 1. Идентификатор последовательности (например, CCPA_BACSU)
##### 2. Описание последовательности (например, Catabolite control protein A)
##### 3. Саму последовательность.
#### 
Признаком начала информации о последовательности служит символ ">" в первой позиции строки.

Слово в этой строке, начинающееся в позиции 2 и заканчивающееся первым пробелом, считается идентификатором последовательности.

Тeкст во всех последующих строках рассматривается как последовательность белка. Служебные символы - пробелы, концы строки, символы табуляции и т.п. а также цифры, игнорируются.

### Пример: 
```
	 | ID     | | Описание                 |
	>CCPA_BACSU Catabolite control protein A
	
	| Последовательность                                       |
	MSNITIYDVAREANVSMATVSRVVNGNPNVKPTTRKKVLEAIERLGYRPNAVARGLASKK
	TTTVGVIIPDISSIFYSELARGIEDIATMYKYNIILSNSDQNMEKELHLLNTMLGKQVDG
	IVFMGGNITDEHVAEFKRSPVPIVLAASVEEQEETPSVAIDYEQAIYDAVKLLVDKGHTD
	IAFVSGPMAEPINRSKKLQGYKRALEEANLPFNEQFVAEGDYTYDSGLEALQHLMSLDKK
	PTAILSATDEMALGIIHAAQDQGLSIPEDLDIIGFDNTRLSLMVRPQLSTVVQPTYDIGA
	VAMRLLTKLMNKEPVEEHIVELPHRIELRKSTKS
```
Простота FASTA-формата позволяет легко осуществлять различные действия с последовательностями при помощи инструментов редактирования текста и скриптовых языков программирования, таких как Python, Ruby, Perl, Java.

### Модификации:
-	FASTQ — текстовый формат данных, используемый для представления биологической последовательности и показателей качества каждого элемента последовательности. 
https://ru.wikipedia.org/wiki/FASTQ

# Sequence Alignment Map (SAM)
https://en.wikipedia.org/wiki/SAM_(file_format)

Формат SAM состоит из заголовка и секции выравнивания. Раздел заголовка должен быть перед разделом выравнивания, если он присутствует. Заголовки начинаются с символа «@», который отличает их от секции выравнивания. Разделы выравнивания имеют 11 обязательных полей, а также переменное количество необязательных полей(Подробнее). 
| Столбец   | Поле  | Тип    |	Краткое описание                        |
| --------- | ----- | ------ | ---------------------------------------- |
| 1         | QNAME | String | Query template NAME                      | 
| 2         | FLAG  | Int    | bitwise FLAG                             |
| 3         | RNAME | String | References sequence NAME                 |
| 4         | POS   | Int    | 1-based leftmost mapping POSition        |
| 5         | MAPQ  | Int    | MAPping Quality                          |
| 6         | CIGAR | String | CIGAR String                             |
| 7         | RNEXT | String | Ref. name of mate/next read              |
| 8         | PNEXT | Int    | Position of the mate/next read           |
| 9         | TLEN  | Int    | observed Template LENgth                 |
|10         | SEQ   | String | Segment SEQurnce                         |
|11         | QUAL  | String | ASCII of Phred-scaled base QUAlity+33    |

### Пример:
```
@HD VN:1.6 SO:coordinate 
@SQ SN:ref LN:45 
r001   99 ref  7 30 8M2I4M1D3M = 37  39	TTAGATAAAGGATACTG *	
r002    0 ref  9 30 3S6M1P1I4M *  0   0	AAAAGATAAGGATA    *	
r003    0 ref  9 30 5S6M	   *  0   0	GCCTAAGCTAA       * 
r004    0 ref 16 30 6M14N5M	   *  0   0 ATAGCTTCAGC       *	
r003 2064 ref 29 17 6H5M	   *  0   0	TAGGC             *	
r001  147 ref 37 30 9M         =  7 -39	CAGCGGCAT         *	
```
Файлы SAM можно анализировать и редактировать с помощью программного обеспечения SAMtools.

### Модификации:
-	Binary Alignment Map (BAM) — это сжатое двоичное представление SAM.
https://en.wikipedia.org/wiki/Binary_Alignment_Map
-	CRAM — это сжатый столбчатый формат файла для хранения биологических последовательностей, выровненных по эталонной последовательности.
https://en.wikipedia.org/wiki/CRAM_(file_format)
