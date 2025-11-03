# Configuração do Codespaces

Este repositório está configurado para uso com GitHub Codespaces, permitindo que você execute o notebook `oficina-dados-mi-aws-jupyper.ipynb` diretamente no navegador.

## Como usar o Codespaces

1. Clique no botão verde "Code" no GitHub
2. Selecione a aba "Codespaces"
3. Clique em "Create codespace on [branch]"
4. Aguarde a criação do ambiente (pode levar alguns minutos na primeira vez)

## Recursos disponíveis

O ambiente Codespaces inclui:

- **Python 3.10** com Jupyter Lab/Notebook
- **Bibliotecas Python**:
  - `boto3` - AWS SDK para Python
  - `PyAthena` - Conector para AWS Athena
  - `pandas` - Análise de dados
  - `matplotlib` - Visualização de dados
  - `numpy`, `scipy`, `seaborn` - Ferramentas de análise científica
- **LaTeX** completo para produção de artigos acadêmicos
  - `texlive-latex-base` e `texlive-latex-extra`
  - Suporte para português (`texlive-lang-portuguese`)
  - Pacotes científicos e bibliográficos
- **AWS CLI** para interação com serviços AWS
- **Extensões VS Code**:
  - Python
  - Jupyter
  - LaTeX Workshop

## Como executar o notebook

### Opção 1: VS Code (recomendado)
1. Abra o arquivo `oficina-dados-mi-aws-jupyper.ipynb`
2. Selecione o kernel Python quando solicitado
3. Execute as células normalmente

### Opção 2: Jupyter Lab
1. Abra o terminal integrado no VS Code
2. Execute: `jupyter lab --ip=0.0.0.0 --port=8888 --no-browser`
3. Clique no link que aparece no terminal ou use a aba "Ports" para acessar

## Configuração AWS

Para executar o notebook que interage com AWS:

1. Configure suas credenciais AWS no terminal:
   ```bash
   aws configure
   ```
2. Forneça suas credenciais do AWS Academy Learner Lab
3. Certifique-se de que a região está configurada para `us-east-1` (Norte da Virgínia)

## Produção de Artigos com LaTeX

Para compilar documentos LaTeX:

1. Crie seus arquivos `.tex` no repositório
2. Use a extensão LaTeX Workshop no VS Code para compilar
3. Ou compile via terminal:
   ```bash
   pdflatex seu-artigo.tex
   bibtex seu-artigo    # Se usar bibliografia
   pdflatex seu-artigo.tex
   pdflatex seu-artigo.tex
   ```

## Suporte

Para problemas com o ambiente Codespaces, verifique:
- A conexão com a internet está estável
- As credenciais AWS estão configuradas corretamente
- Os pacotes Python foram instalados (veja o log do postCreateCommand)
