### Project - analise-sentimentos_NLP

**Instruções Rápidas:** O projeto foi corrido no google colab, ao reutilizar o mesmo fora desta plataforma, poderá haver alguns problemas de ajustes.

**Problema de Negócio:** Desenvolvimentio de um sistema para filtrar e categorizar resenhas de filmes.

**Solução:** Treinar um modelo para detectar automaticamente resenhas negativas. O modelo precisará ter um valor F1 de pelo menos 0,85. Onde o Modelo-BERT obteve um valor de F1 de pelo menos 0,86, superando o exigido.

## ⚠️ Limitações e Evolução Futura

### Limitações dos Dados e do Modelo
* **Desempenho Experimental vs. Produção:** O modelo baseado na arquitetura **BERT** alcançou um **F1-Score de 0,86** na deteção automática de resenhas negativas no conjunto de teste, superando abordagens clássicas baseadas apenas em frequência de palavras (*TF-IDF*). Contudo, esse resultado reflete a avaliação em uma base histórica estática e **não representa garantia de desempenho contínuo em produção**, onde gírias, novos produtos e mudanças na linguagem dos utilizadores alteram a distribuição do texto (*data drift*).
* **Truncamento de Texto, Nuances Linguísticas e Custo Computacional:** Por limitações arquiteturais do BERT e de memória durante a extração de *embeddings* (`max_length`), resenhas muito longas sofrem truncamento, podendo perder críticas relevantes no final do texto. Além disso, expressões de ironia, sarcasmo, erros ortográficos severos e opiniões mistas (elogio seguido de crítica) ainda geram ambiguidade, enquanto o custo computacional e a latência de inferência do BERT são significativamente maiores do que modelos lineares tradicionais.

### Melhorias Futuras
* **Fine-Tuning Completo e Modelos Mais Leves:** Realizar o ajuste fino (*fine-tuning*) end-to-end das camadas superiores do BERT diretamente na tarefa de classificação (em vez de apenas extrair *embeddings* fixos) e avaliar arquiteturas destiladas mais rápidas para produção, como **DistilBERT** ou **RoBERTa**, reduzindo a latência e o consumo de GPU/CPU.
* **Tratamento de Textos Longos e Calibração de Probabilidades:** Aplicar estratégias de janela deslizante (*sliding window*) ou truncamento combinado (início + fim da resenha) para textos extensos, além de calibrar o limiar de decisão (*threshold tuning*) para maximizar o **Recall** de avaliações críticas sem gerar excesso de falsos positivos.
* **Monitoramento em Produção:** Implementar pipelines de monitorização de desvio semântico (*concept/data drift*) e análise periódica de erros (*error analysis*) sobre resenhas mal classificadas antes de integrar o modelo a sistemas reais de atendimento ao cliente.


**Foco Técnico:** Utilização de um conjunto de dados de resenhas de filmes do IMDB com rotulagem de polaridade para criar um modelo para classificar resenhas como positivas e negativas. 

### 🚀 Tecnologias
- Python
- Pandas
- Seaborn
- Matplotlib.dates
- Matplotlib.pyplot
- Spacy
- tqdm
- Sklearn
- Nltk
- Stopwords
- LGBMClassifier
- Torch
- Transformers
- BERT


### 📦 Como instalar

``` bash
git clone https://github.com/awvn/analise-sentimentos_NLP.git
cd analise-sentimentos_NLP
pip install -r requirements.txt
