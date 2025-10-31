# Análise de Regressão Linear - Erupções

Este projeto realiza uma análise de regressão linear completa sobre dados de duração de erupções e seus respectivos intervalos até a próxima erupção.

## Descrição do Projeto

O notebook implementa uma análise estatística completa que inclui:

- **Leitura e preparação dos dados** (25 observações de erupções)
- **Cálculo da reta de regressão linear** usando o método dos mínimos quadrados
- **Visualização gráfica** com gráfico de dispersão e reta sobreposta  
- **Cálculo do coeficiente de determinação (R²)** para avaliar a qualidade do ajuste
- **Análise de resíduos** para validação do modelo
- **Interpretação estatística** dos resultados

## Objetivos

1. Determinar a relação linear entre duração da erupção (x) e intervalo até a próxima erupção (y)
2. Calcular a equação da reta: `y = ax + b`
3. Avaliar a qualidade do ajuste através do R²
4. Visualizar os dados e o modelo graficamente
5. Realizar predições baseadas no modelo

## Estrutura do Projeto

```
data-analysis-regression/
│
├── analise_regressao_erupcoes.ipynb    # Notebook principal
├── requirements.txt                    # Dependências do projeto
└── README.md                          # Este arquivo
```

## Tecnologias Utilizadas

- **Python 3.8+**
- **Pandas** - Manipulação de dados
- **NumPy** - Operações numéricas
- **Matplotlib** - Visualização de dados
- **Seaborn** - Gráficos estatísticos
- **Scikit-learn** - Machine Learning (Regressão Linear)
- **Jupyter Notebook** - Ambiente de desenvolvimento

## Como Executar o Projeto

### Pré-requisitos

- Python 3.8 ou superior instalado
- Git (opcional, para clonar o repositório)

### Passo 1: Preparar o Ambiente

#### Clonando um repositório
```bash
git clone <url-do-repositorio>
cd data-analysis-regression
```

### Passo 2: Criar Ambiente Virtual (Recomendado)

```bash
# Criar ambiente virtual
python -m venv venv
```

#### Ativar o Ambiente Virtual

**ATENÇÃO: Se estiver usando PowerShell no Windows, e der erro de permissão:**
```powershell
# Liberar execução de scripts (execute como Administrador se necessário)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**Depois ative o ambiente:**
```bash
# No Windows PowerShell:
venv\Scripts\activate

# No Linux/Mac:
source venv/bin/activate
```

**Você saberá que o ambiente está ativo quando ver `(venv)` no início da linha de comando.**

### Passo 3: Instalar Dependências

```bash
# Instalar todas as dependências
pip install -r requirements.txt

# OU instalar manualmente:
pip install pandas numpy matplotlib seaborn scikit-learn jupyter notebook
```

### Passo 4: Executar o Jupyter Notebook

```bash
# Iniciar o Jupyter Notebook
jupyter notebook

# OU usar Jupyter Lab (alternativa moderna)
jupyter lab
```

### Passo 5: Abrir e Executar o Notebook

1. No navegador, abra o arquivo `analise_regressao_erupcoes.ipynb`
2. Execute as células sequencialmente usando `Shift + Enter`
3. Ou execute todas as células: `Cell > Run All`

## Dados Utilizados

O projeto utiliza 25 observações de erupções com os seguintes dados:

| Duração (x) | Intervalo (y) | Duração (x) | Intervalo (y) | Duração (x) | Intervalo (y) |
|-------------|---------------|-------------|---------------|-------------|---------------|
| 1,80        | 56            | 2,82        | 73            | 4,30        | 89            |
| 1,82        | 58            | 3,13        | 76            | 4,43        | 89            |
| 1,90        | 62            | 3,27        | 77            | 4,47        | 86            |
| 1,93        | 56            | 3,65        | 77            | 4,53        | 89            |
| 1,98        | 57            | 3,78        | 79            | 4,55        | 86            |
| 2,05        | 57            | 3,83        | 85            | 4,60        | 92            |
| 2,13        | 60            | 3,88        | 80            | 4,63        | 91            |
| 2,30        | 57            | 4,10        | 89            | -           | -             |
| 2,37        | 61            | 4,27        | 90            | -           | -             |

*Os dados estão incorporados diretamente no notebook. Total: 25 observações.*

## Resultados Esperados

O projeto gerará:

1. **Equação da reta de regressão**: `y = ax + b`
2. **Coeficiente de determinação (R²)**: Medida da qualidade do ajuste
3. **Gráfico de dispersão** com reta de regressão sobreposta
4. **Análise de resíduos** para validação do modelo
5. **Interpretação estatística** dos resultados

## Solução de Problemas

### Erro: "a execução de scripts foi desabilitada neste sistema" (Windows PowerShell)

**Problema:** `venv\Scripts\activate` retorna erro de política de execução.

#### Por que isso acontece?

O Windows PowerShell possui **Execution Policies** (Políticas de Execução) como medida de segurança para prevenir execução de scripts maliciosos. Por padrão, o Windows vem configurado com:

- **`Restricted`**: Não permite execução de nenhum script
- **`RemoteSigned`**: Permite scripts locais, mas scripts baixados da internet precisam ser assinados digitalmente
- **`Unrestricted`**: Permite todos os scripts (menos seguro)

Quando você cria um ambiente virtual (`python -m venv venv`), o Python gera um arquivo `Activate.ps1` que é um **script PowerShell**. Como a política padrão é `Restricted`, o sistema bloqueia sua execução.

#### Soluções (em ordem de segurança):

**Solução 1 - Alterar política apenas para o usuário atual (MAIS SEGURA):**
```powershell
# NÃO precisa ser Administrador - só afeta seu usuário
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Depois ative normalmente:
venv\Scripts\Activate.ps1
```

**Observação:** Na verdade, **NÃO é necessário ser Administrador** quando você usa `-Scope CurrentUser`. Isso só afeta seu usuário, não todo o sistema.

**Solução 2 (Temporária):**
```powershell
# Execute uma única vez:
PowerShell -ExecutionPolicy Bypass -File venv\Scripts\Activate.ps1
```

**Solução 3 (Alternativa):**
```bash
# Use o CMD do Windows em vez do PowerShell:
venv\Scripts\activate.bat
```

### Erro: "ModuleNotFoundError"
```bash
# Certifique-se de que o ambiente virtual está ativado (venv)
# E instale as dependências novamente
pip install -r requirements.txt
```

### Erro: "Jupyter not found"
```bash
# Instale o Jupyter
pip install jupyter notebook
```

### Problemas com matplotlib no Windows
```bash
# Se houver problemas de visualização, instale:
pip install --upgrade matplotlib
```

### Kernel não encontrado no Jupyter
```bash
# Adicione o ambiente virtual como kernel
python -m ipykernel install --user --name=venv --display-name="Python (Regressao)"
```

## Conceitos Abordados

- **Regressão Linear Simples**
- **Método dos Mínimos Quadrados**
- **Coeficiente de Determinação (R²)**
- **Correlação de Pearson**
- **Análise de Resíduos**
- **Visualização de Dados Estatísticos**

## Estrutura do Notebook

1. **Importação de Bibliotecas**
2. **Leitura e Preparação dos Dados**
3. **Cálculo da Reta de Regressão Linear**
4. **Gráfico de Dispersão com Reta de Regressão**
5. **Cálculo e Análise do R²**
6. **Análise de Resíduos**
7. **Resumo e Conclusões**

## Para Estudantes

Este projeto é ideal para:
- Estudantes de Estatística
- Alunos de Ciência de Dados
- Pessoas aprendendo Python para análise de dados
- Quem quer entender regressão linear na prática

## Critérios de Avaliação Atendidos

- **Correção dos cálculos** - Implementação correta da regressão linear  
- **Clareza e organização** - Código bem comentado e estruturado  
- **Qualidade dos gráficos** - Visualizações profissionais com matplotlib  
- **Interpretação do R²** - Análise completa da qualidade do ajuste  

## Contribuições

Para contribuir com o projeto:
1. Faça um fork do repositório
2. Crie uma branch para sua feature
3. Commit suas mudanças
4. Push para a branch
5. Abra um Pull Request

## Autor

**Caio Thomas Bandeira**
- GitHub: [@caiothomasbandeira](https://github.com/caiothomasbandeira)
- Email: [caiothomas16@gmail.com]
- LinkedIn: [caiothomasbandeira](https://www.linkedin.com/in/caiothomasbandeira)

---

**Última atualização**: Outubro 2025  
**Versão do Python testada**: 3.8+  
**Status**: Funcional
