# **Instruction-tuned Stable Diffusion for Cartoonization**

---

## **📜 Introdução**

O Stable Diffusion for Cartoonization é uma inteligência artificial (IA) baseada em um modelo de aprendizado profundo. Especificamente, é uma extensão da arquitetura Stable Diffusion, que utiliza redes neurais de difusão para gerar ou transformar imagens com base em instruções textuais fornecidas pelo usuário.

## **O que é isso na prática?**
- Modelo de IA para imagens: Ele transforma imagens reais em versões estilizadas, parecidas com desenhos animados (cartoonization).
  
- Baseado em Stable Diffusion: O Stable Diffusion é uma tecnologia de geração de imagens amplamente utilizada, treinada para criar imagens de alta qualidade a partir de descrições textuais ou aplicar transformações visuais em imagens existentes.
  
- Pipeline Ajustado: Esse modelo foi ajustado especificamente para a tarefa de cartoonização, o que significa que ele foi treinado com dados para interpretar e executar essas transformações de maneira eficiente.

---

## **🎯 Objetivo e Motivação**

O objetivo deste modelo é aprimorar a capacidade do **Stable Diffusion** de executar transformações precisas e estilísticas a partir de instruções textuais. Baseado no pipeline do **InstructPix2Pix**, ele foi ajustado para interpretar e aplicar a cartoonização de maneira consistente e de alta qualidade.

### **Motivações principais:**

- Expandir o uso de IA em artes visuais.
- Tornar a cartoonização mais acessível para criadores de conteúdo.
- Oferecer um modelo eficiente e ajustado para transformações específicas.

---

## **✨ Principais Características**

- **Instruções Textuais**: Transforma imagens reais em desenhos animados baseando-se em comandos como *"Cartoonize this image"*.  
- **Alta Qualidade**: Gera resultados detalhados, estilizados e prontos para uso profissional.  
- **Flexibilidade e Eficiência**: Adaptado para diferentes tipos de imagens com rápido tempo de execução.  

---

## **⚙️ Como Funciona**

A técnica combina o modelo de difusão estável com um conjunto de dados de cartoonização. As instruções textuais orientam o modelo, que foi ajustado para aprender as transformações estilísticas desejadas.

### **Pipeline Resumido**:

1. **Entrada**: Uma imagem e uma instrução textual, como *"Cartoonize this image."*  
2. **Transformação**: O modelo processa a imagem real e aplica o estilo cartoon.  
3. **Saída**: Uma imagem estilizada semelhante a um desenho animado.  

![image](https://github.com/user-attachments/assets/05462ef9-8311-4143-8bf1-e66ffe36afdb)


---

## **📊 Casos de Uso e Limitações**

### **Casos de Uso**

- Criação de **personagens animados** a partir de fotos reais.  
- **Design gráfico** rápido e estilizado.  
- Suporte para artistas em **animações e ilustrações**.  

### **Limitações**

- A qualidade final depende da **imagem de entrada** (imagens borradas ou de baixa resolução podem afetar o resultado).  
- Algumas imagens muito complexas ou abstratas podem não ser cartoonizadas corretamente.  
- O modelo foi treinado especificamente para cartoonização, não sendo ideal para outras transformações estilísticas.

---

## **🚀 Como Usar**

### **Pré-requisitos**

Certifique-se de ter:

- Python 3.8 ou superior.  
- PyTorch 1.8.1 ou superior.  
- Biblioteca `diffusers` instalada.  

### **Passos para Instalação e Execução**

#### **1. Clonar o Repositório**

```bash
git clone https://github.com/seu-usuario/instruction-tuned-cartoonizer
cd instruction-tuned-cartoonizer
```

#### **2. Instalar as Dependências**

Instale as bibliotecas necessárias:

```bash
pip install -r requirements.txt
```

#### **3. Executar o Modelo**

Após a instalação, você pode executar o modelo com o seguinte código:

```bash
import torch
from diffusers import StableDiffusionInstructPix2PixPipeline
from diffusers.utils import load_image

# Carregar o modelo
model_id = "instruction-tuning-sd/cartoonizer"
pipeline = StableDiffusionInstructPix2PixPipeline.from_pretrained(
    model_id, torch_dtype=torch.float16, use_auth_token=True
).to("cuda")

# Carregar a imagem de entrada
image_path = "caminho/para/imagem.jpg"
image = load_image(image_path)

# Aplicar a cartoonização
image = pipeline("Cartoonize the following image", image=image).images[0]

# Salvar a imagem gerada
image.save("imagem_cartoonizada.png")

```

Este código irá carregar uma imagem de entrada, aplicar a cartoonização e salvar a imagem resultante.

#### **4. Problemas Comuns e Soluções**

- **Erro de Memória**: Se você estiver recebendo erros de memória, verifique se sua GPU possui memória suficiente para executar o modelo.
- **Dependências Não Encontradas**: Se alguma biblioteca não for encontrada, execute pip install -r requirements.txt para garantir que todas as dependências sejam instaladas corretamente.

#### **5. Limitações e Uso Ético**

- **Qualidade da Imagem**: A qualidade do modelo depende fortemente da qualidade da imagem de entrada, ou seja deve-se usar imagens claras e bem definidas para melhores resultados.
- **Uso Indevido**: O uso do modelo para gerar conteúdos prejudiciais ou não autorizados é estritamente proibido.

#### **📚 Exemplo de Saída**

Antes e depois da cartoonização:

![image](https://github.com/user-attachments/assets/39ae54a8-9236-474b-82b2-7b43e9abe7d5)

