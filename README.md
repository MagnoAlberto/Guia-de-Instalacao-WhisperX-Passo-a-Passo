# Guia de Instalação WhisperX - Passo a Passo
###Guia de Instalação WhisperX - Passo a Passo | How to Install WhisperX Locally – 70 times faster?

> **📝 Sobre este guia:**  
> Este é um guia reorganizado e adaptado do excelente artigo original publicado por **Ricardo Gonzalez**.  
> Todo o conteúdo técnico e instruções são baseados no trabalho deles.
> 
> **Artigo original:** [How to Install WhisperX Locally](https://mistercontenidos.com/en/how-to-install-whisperx-locally/)  
> **Repositório oficial:** [Kit-Whisperx](https://github.com/rgcodeai/Kit-Whisperx)  
> **Créditos:** Ricardo Gonzalez
>
> **O que foi alterado nesta versão:**
> - Reorganização do conteúdo em formato sequencial passo a passo
> - Formatação otimizada para leitura em Markdown
> - Estruturação hierárquica das etapas
> - Tradução para português brasileiro
>
> Se este guia foi útil para você, considere visitar o [site original]([https://mistercontenidos.com/](https://mistercontenidos.com/en/how-to-install-whisperx-locally/)) e apoiar o trabalho doRicardo Gonzalez! 🙏

---

## 📄 Licença e Uso

Este guia é uma adaptação educacional do conteúdo original. 
Por favor, respeite os direitos do autor original visitando o site oficial 
e dando crédito apropriado ao usar este material.

---

## 📋 Pré-requisitos

Antes de começar, você precisará instalar os seguintes componentes na ordem apresentada.

---

## 🐍 Passo 1: Instalar Miniconda3

1. Acesse a [página oficial do Miniconda](https://docs.anaconda.com/free/miniconda/)
2. Baixe o instalador correspondente ao seu sistema operacional (Windows, macOS ou Linux)
3. Execute o instalador baixado
4. Siga as opções de instalação:
   - Clique em **Next**
   - Aceite os termos clicando em **I Agree**
   - Selecione **Just Me** e clique em **Next**
   - Deixe o local padrão de instalação e clique em **Next**
   - Marque **Create start menu shortcuts** e clique em **Install**
5. Aguarde a conclusão da instalação

---

## 🎮 Passo 2: Instalar CUDA (Apenas para GPUs NVIDIA)

> ⚠️ **Se você não possui GPU NVIDIA, pule esta etapa**

1. Verifique se sua GPU é compatível em [CUDA GPUs](https://developer.nvidia.com/cuda-gpus)
2. Acesse a [página de downloads do CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit-archive)
3. Selecione:
   - Versão do CUDA (recomendado: 12.1 ou 11.8)
   - Sistema operacional: Windows
   - Arquitetura: x86_64
   - Versão do Windows: 10 ou 11
   - Tipo de instalador: local exe
4. Baixe e execute o instalador **como administrador** (botão direito > Executar como administrador)
5. Siga o assistente mantendo as opções padrão
6. Verifique a instalação abrindo o **cmd** e executando:
   ```bash
   nvcc --version
   ```

---

## 📦 Passo 3: Instalar Git

### Windows
1. Acesse [Git para Windows](https://git-scm.com/download/win)
2. Baixe e execute o instalador
3. Mantenha as opções padrão durante a instalação
4. Verifique a instalação no cmd:
   ```bash
   git --version
   ```

### macOS
1. Abra o Terminal
2. Se tiver Homebrew instalado:
   ```bash
   brew install git
   ```
3. Se não tiver Homebrew, instale-o em [brew.sh](https://brew.sh/)
4. Verifique a instalação:
   ```bash
   git --version
   ```

### Linux
1. Abra o Terminal
2. Execute conforme sua distribuição:
   - **Debian/Ubuntu:**
     ```bash
     sudo apt update && sudo apt install git
     ```
   - **Fedora:**
     ```bash
     sudo dnf install git
     ```
   - **Arch Linux:**
     ```bash
     sudo pacman -S git
     ```
3. Verifique a instalação:
   ```bash
   git --version
   ```

---

## 📥 Passo 4: Baixar o Repositório do Projeto

### Opção A: Com Git (Recomendado)
1. Abra o **Anaconda Prompt (Miniconda3)**
2. Execute:
   ```bash
   git clone https://github.com/rgcodeai/Kit-Whisperx.git
   ```

### Opção B: Download Manual
1. Acesse [Kit-Whisperx no GitHub](https://github.com/rgcodeai/Kit-Whisperx)
2. Clique no botão verde **Code**
3. Selecione **Download ZIP**
4. Extraia o arquivo no seu Desktop

---

## 💡 Sugestão: Utilize o MAMBA ao inves do CONDA

A pouco dias atrás, não conhecia o `mamba`, e estava tendo muito problema com o `conda`, que foi resolvido como mágica pelo `mamba`. Nesse meu guia explica com mais detalhes.
[Resolvendo o Erro gdk-pixbuf g_module_open specified module could not be found no Windows com Conda](https://github.com/MagnoAlberto/Resolvendo-o-Erro-gdk-pixbuf-g_module_open-specified-module-could-not-be-found-no-Windows-com-Conda)

---

## 🚀 Passo 5: Instalar WhisperX

### Opção A: Instalação Automática (Recomendada)

1. Abra o **Anaconda Prompt (Miniconda3)** (terminal limpo, sem uso anterior)
2. Navegue até a pasta do projeto:
   ```bash
   cd Kit-Whisperx
   ```

3. Execute o comando apropriado:

   **Para usuários COM GPU NVIDIA:**
   ```bash
   conda env create -f environment-cuda.yml
   ```

   **Para usuários SEM GPU NVIDIA:**
   ```bash
   conda env create -f environment-cpu.yml
   ```

4. Aguarde a conclusão (pode demorar alguns minutos)

---

### Opção B: Instalação Manual

Use esta opção apenas se a automática falhar.

1. Abra o **Anaconda Prompt (Miniconda3)** (terminal limpo)

2. Crie um novo ambiente:
   ```bash
   conda create --name whisperx-web-ui python=3.10
   ```

3. Ative o ambiente:
   ```bash
   conda activate whisperx-web-ui
   ```

4. Instale PyTorch e Torchaudio:

   **Para usuários COM GPU NVIDIA:**
   ```bash
   conda install pytorch==2.2.0 torchaudio==2.2.0 pytorch-cuda=12.1 -c pytorch -c nvidia
   ```

   **Para usuários SEM GPU NVIDIA:**
   ```bash
   conda install pytorch==2.2.0 torchvision==0.17.0 torchaudio==2.2.0 cpuonly -c pytorch
   ```

5. Instale dependências adicionais (execute cada comando separadamente):
   ```bash
   conda install -c conda-forge ffmpeg numpy=1.24.4
   ```
   ```bash
   pip install gradio==5.9.1
   ```

6. Instale o WhisperX:
   ```bash
   pip install whisperx==3.3.0
   ```

---

## ▶️ Passo 6: Executar WhisperX

1. Abra o **Anaconda Prompt (Miniconda3)**

2. Execute o comando apropriado:

   **Windows:**
   ```bash
   cd Kit-Whisperx & conda activate whisperx-web-ui & python app.py
   ```

   **Linux/macOS:**
   ```bash
   cd Kit-Whisperx && conda activate whisperx-web-ui && python app.py
   ```

3. Aguarde a interface abrir (primeira execução pode demorar mais)

4. Acesse a interface web que será aberta automaticamente no navegador

---

## 🎯 Uso Diário

Sempre que quiser usar o WhisperX novamente:

**Windows:**
```bash
cd Kit-Whisperx & conda activate whisperx-web-ui & python app.py
```

**Linux/macOS:**
```bash
cd Kit-Whisperx && conda activate whisperx-web-ui && python app.py
```

---

## 📊 Comparativo de Performance

Teste realizado com áudio de 13min38s usando RTX 3060 12GB:

| Modelo    | Whisper (GPU) | WhisperX (GPU) | Ganho        |
|-----------|---------------|----------------|--------------|
| Large-v2  | 3min35s       | 1min25s        | 2.5x mais rápido |
| Medium    | 2min41s       | 52.5s          | 3x mais rápido   |
| Small     | 1min32s       | 32.7s          | 2.8x mais rápido |
| Base      | 48s           | 23.9s          | 2x mais rápido   |

---

## 🔧 Comandos Conda Úteis

```bash
# Listar ambientes
conda env list

# Ativar ambiente
conda activate whisperx-web-ui

# Desativar ambiente
conda deactivate

# Remover ambiente
conda env remove --name whisperx-web-ui

# Voltar um diretório
cd ..

# Navegar para um diretório
cd caminho/do/diretorio
```

---

## 🌐 Traduzir Transcrições (Opcional)

1. Crie uma conta em [Claude.ai](https://claude.ai/)
2. Use o seguinte prompt ajustando os campos entre colchetes:

```
Traduza o seguinte transcript em formato [SRT] seguindo estas instruções:

- Realize a tradução de forma natural em [IDIOMA DE DESTINO], como se fosse escrita por um falante nativo.
- Ajuste a tradução para fazer sentido no idioma de destino, sem alterar o propósito original da mensagem.
- Interprete a intenção do locutor para que cada frase seja expressa da forma que um falante nativo do idioma de destino diria.
- Não modifique os timings das frases.
- O idioma de origem é [IDIOMA ORIGINAL]

"""
COLE SEU TRANSCRIPT AQUI
"""
```

---

## ✅ Conclusão

Seu WhisperX está instalado e pronto para uso! A ferramenta oferece transcrições rápidas e precisas, especialmente quando usada com GPU NVIDIA.
