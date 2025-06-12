# pipeline-detection-virale
Un pipeline bioinformatique pour l'alignement de reads, l’analyse de k-mers et la détection de génomes viraux.
Pipeline d’analyse de reads, alignement, analyse de k-mers et détection virale
📖 Présentation
Ce projet bioinformatique a été réalisé dans le cadre de la formation en bioinformatique et vise à développer un pipeline automatisé capable de :

Simuler des reads à partir de génomes viraux.

Effectuer un alignement rapide des reads simulés ou réels sur des génomes de référence.

Analyser les k-mers des reads non alignés pour détecter d’éventuelles signatures spécifiques.

Valider les alignements en testant les k-mers détectés contre plusieurs génomes viraux.

Générer des rapports statistiques et graphiques sur les résultats.

Ce pipeline permet d'illustrer les étapes essentielles d’une analyse comparative de séquences et peut être adapté à des cas réels de détection virale ou de métagénomique ciblée.

📑 Table des matières
Objectifs du projet

Organisation du dépôt

Installation et dépendances

Détails du pipeline

Spécifications des fichiers

Commandes d’exécution

Analyse des résultats

Exemple de workflow complet

Crédits et Licence

Contact

🎯 Objectifs du projet
Simuler des jeux de reads à partir de génomes viraux FASTA.

Réaliser un alignement par parcours de k-mers avec calcul de score.

Extraire les reads non alignés et effectuer une analyse de fréquence de leurs k-mers.

Valider les k-mers les plus fréquents en les recherchant dans d’autres génomes viraux.

Produire des rapports textuels et graphiques exploitables pour l’analyse.

📁 Organisation du dépôt

.
├── simulate_reads.py             # Script de simulation de reads FASTQ
├── Final.py                      # Script d'alignement reads ↔ génomes par k-mers
├── analyse_kmers.py              # Script d’analyse de k-mers sur reads non alignés
├── validation_coronavirus.py     # Validation finale des k-mers contre plusieurs génomes
├── requirements.txt              # Liste des dépendances Python
├── README.md                     # Ce fichier
├── genomes/                      # Dossier contenant les fichiers de génomes viraux
├── data/                         # Dossier de jeux de données et reads simulés
├── results/                      # Dossier de résultats d’alignement et k-mers
└── figures/                      # Graphiques générés
⚙️ Installation et dépendances:
--------------
Prérequis
Python ≥ 3.8
---------------
Modules Python requis :

- Biopython

- Parasail

- Pandas

- Matplotlib
--------------
Installation rapide

pip install -r requirements.txt
-------------------------------
Sinon, installation manuelle :

pip install biopython parasail pandas matplotlib
----------------------------------------
📊 Détails du pipeline
📌 1. Simulation de reads
Script : simulate_reads.py

Prend en entrée un fichier FASTA compressé ou non.

Génère un nombre défini de reads aléatoires.

Produit un fichier FASTQ.gz contenant les reads simulés.
##################################################################
📌 2. Alignement des reads sur génomes
Script : Final.py

Alignement par k-mers avec Parasail.

Paramètres personnalisables :

Taille des k-mers (--k)

Seuil de score minimal (--score_threshold)

Produit :

Fichier TSV des alignements (out_dir/alignement.tsv)

Fichier des reads non alignés.
##################################
📌 3. Analyse des k-mers des reads non alignés
Script : analyse_kmers.py

Compte la fréquence des k-mers dans les reads restants.

Produit :

Fichier texte des k-mers les plus fréquents.

Graphique PNG des k-mers dominants.
###########################################

📌 4. Validation des k-mers contre plusieurs génomes
Script : validation_coronavirus.py

Recherche les k-mers fréquents dans plusieurs génomes viraux.

Affiche les occurrences et génère un résumé des alignements.

📥 Spécifications des fichiers
Fichiers d’entrée :
Génomes : FASTA (.fna ou .fna.gz)

Reads simulés ou réels : FASTQ (.fastq.gz)

Fichiers de sortie :
Alignements : .tsv

Reads non alignés : .fastq.gz

Top k-mers : fichier texte et graphique

Validation multi-génomes : résumé final .txt
------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------
🖥️ Commandes d’exécution:
---------------------------
Simulation de reads:

python simulate_reads.py --fasta_path genomes/virus.fna.gz --output_path data/sim_reads.fastq.gz --num_reads 10000

Alignement:

python Final.py --genomes genomes/genome1.fna genomes/genome2.fna --reads data/sim_reads.fastq.gz --out_dir results/ --k 11 --score_threshold 90

Analyse de k-mers:

python analyse_kmers.py --input results/non_aligned_reads.fastq.gz --k 31 --top_n 50

Validation multi-génomes:

python validation_coronavirus.py --genomes genomes/genome1.fna genomes/genome2.fna --reads1 data/reads_1.fastq.gz --reads2 data/reads_2.fastq.gz

############################################
###########################################


📊 Analyse des résultats
Alignements : Score ≥90 → alignement fiable.

K-mers fréquents : peuvent indiquer des signatures virales spécifiques.

Validation multi-génomes : Permet de confirmer ou d’éliminer des virus candidats.

Les graphiques produits permettent de visualiser :

La répartition des scores.

Les fréquences des k-mers dominants.
*************************************************************************************************************
🛠️ Exemple de workflow complet

# 1. Simuler des reads
python simulate_reads.py --fasta_path genomes/GCF_000862245.1_ViralProj15330_genomic.fna.gz --output_path data/sim_reads.fastq.gz --num_reads 10000

# 2. Aligner les reads
python Final.py --genomes genomes/genome1.fna genomes/genome2.fna --reads data/sim_reads.fastq.gz --out_dir results/ --k 11 --score_threshold 90

# 3. Analyser les k-mers non alignés
python analyse_kmers.py --input results/non_aligned_reads.fastq.gz --k 31 --top_n 50

# 4. Valider sur plusieurs génomes
python validation_coronavirus.py --genomes genomes/genome1.fna genomes/genome2.fna --reads1 data/reads_1.fastq.gz --reads2 data/reads_2.fastq.gz
***************************************************************************************************************
📜 Crédits 
Projet réalisé dans le cadre d’une formation universitaire en bioinformatique.
Développé par Attabi Mohamed El Mahdi.


📬 Contact
Pour toute question, suggestion ou collaboration :

📧 attabi.mahdi@gmail.com

📌 Remarque
Ce pipeline est optimisé pour les analyses virales à petite ou moyenne échelle et peut être facilement adapté à d’autres applications (détection bactérienne, métagénomique environnementale, etc).

