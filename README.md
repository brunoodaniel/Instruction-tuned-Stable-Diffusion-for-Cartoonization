Instruction-tuned Stable Diffusion for Cartoonization
Este projeto utiliza uma versão "instruction-tuned" do modelo Stable Diffusion v1.5, que foi ajustado a partir dos checkpoints do InstructPix2Pix. O objetivo é melhorar a capacidade do Stable Diffusion de seguir instruções específicas para operações de transformação de imagem.

Motivação do Pipeline
A motivação por trás deste pipeline vem parcialmente do FLAN e do InstructPix2Pix. A ideia principal é criar um conjunto de dados com instruções (como descrito no blog) e, em seguida, realizar um treinamento no estilo do InstructPix2Pix. O objetivo final é aprimorar o modelo para que ele consiga seguir instruções específicas que envolvem operações de transformação de imagem.

Descrição do Pipeline
O pipeline foi treinado com o conjunto de dados cartoonization, que pode ser encontrado neste repositório. O treinamento foi conduzido de maneira a refinar o modelo para realizar a tarefa de cartoonization, ou seja, transformar uma imagem normal em uma versão de desenho animado.

Como Funciona
Este modelo pode ser utilizado para a tarefa de cartoonização de imagens, onde você fornece uma imagem de entrada e uma instrução como entrada para o modelo. O modelo então gera uma versão "cartoonizada" dessa imagem com base na instrução fornecida.

Treinamento e Resultados
O treinamento foi realizado no conjunto de dados instruction-tuning-sd/cartoonization. Para mais detalhes sobre o treinamento, consulte o repositório e os logs de treinamento aqui.

Exemplo de Resultado
Veja abaixo alguns resultados obtidos com o pipeline:

Imagem Original: (imagem de exemplo)
Imagem Cartoonizada: (imagem de exemplo)
Casos de Uso Pretendidos e Limitações
O pipeline pode ser usado para realizar cartoonization com uma imagem de entrada e uma instrução de entrada. No entanto, é importante observar as limitações do modelo:

O modelo pode não funcionar bem em imagens com características altamente complexas ou não convencionais.
O uso indevido, uso malicioso ou fora do escopo do modelo não é recomendado. Consulte o cartão do modelo para mais informações.
Como Usar
Para usar este modelo, basta seguir os passos abaixo:

Instalação
Instale as dependências necessárias:

bash
Copiar código
pip install torch diffusers
Código de Exemplo
python
Copiar código
import torch
from diffusers import StableDiffusionInstructPix2PixPipeline
from diffusers.utils import load_image

# Carregar o modelo
model_id = "instruction-tuning-sd/cartoonizer"
pipeline = StableDiffusionInstructPix2PixPipeline.from_pretrained(
    model_id, torch_dtype=torch.float16, use_auth_token=True
).to("cuda")

# Carregar a imagem de entrada
image_path = "https://hf.co/datasets/diffusers/diffusers-images-docs/resolve/main/mountain.png"
image = load_image(image_path)

# Aplicar a cartoonização
image = pipeline("Cartoonize the following image", image=image).images[0]

# Salvar a imagem gerada
image.save("image.png")
Este código irá carregar uma imagem de exemplo, aplicar a instrução de cartoonização e salvar a imagem gerada.

Referências
FLAN: Wei et al., Finetuned Language Models are Zero-Shot Learners, ICLR, 2022. Link para o artigo
InstructPix2Pix: Brooks et al., InstructPix2Pix: Learning to Follow Image Editing Instructions, CVPR, 2023.
Instrução de treinamento para Stable Diffusion: Paul, Sayak, Instruction-tuning Stable Diffusion with InstructPix2Pix, Hugging Face Blog, 2023. Link para o blog
