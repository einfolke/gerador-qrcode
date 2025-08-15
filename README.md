
# GERADOR DE QR CODE

![Java](https://img.shields.io/badge/Java-21-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-brightgreen)
![AWS SDK](https://img.shields.io/badge/AWS%20SDK-yellow)
![Docker](https://img.shields.io/badge/Docker-blue)
![Maven](https://img.shields.io/badge/Maven-red)


# Como usar

Pré-requisitos
- Java 21 JDK
- Maven
- AWS Account com acesso ao S3
- AWS CLI configurado com credenciais apropriadas

# Variáveis utilizadas

1.Crie um `env` no arquivo raiz do projeto com as seguintes variáveis:
2.Crie o projeto
```ambiente
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key
AWS_REGION=your_region
AWS_BUCKET_NAME=your_bucket_name
```
# Local de desenvolvimento

 3. Rode a aplicação:
   ```bash
   mvn spring-boot:run
   ```

#### Docker

1. Crie a imagem do Docker:
   ```bash
   docker build -t qrcode-generator:X.X . 
   ```
> Lembre-se de substituir a versão e o nome da imagem que desejar

2. Execute o container:
   ```bash
   docker run --env-file .env -p 5055:5055 qrcode-generator:X.X 
   ```

> Lembre-se de substituir o caminho do arquivo .env pelo caminho do arquivo de ambiente que você criou

### Configuração AWS S3

 1. Crie um S3 bucket na sua conta AWS
 2. Atualize o `AWS_BUCKET_NAME` arquivo `.env` ou execute o comando Docker
 3. Certifique-se de que suas credenciais da AWS tenham permissões apropriadas para    acessar o bucket S3

### POST /qrcode
Gere um códio QR a partir do texto fornecido e armazene0o no AWS S3. O código QR será gerado com imagem PNG com o tamanho de 200x200px.

*Parametros*

| Nome | Requisição | Tipo | Descrição |
|------|----------|------|-------------|
| `text` | obrigatório | string | O conteúdo do seu texto a ser transformado no código QR. pode ser qualquer variavel de String que você queira converter no QRCode. |

**Response**

```json
{
    "url": "https://your-bucket.s3.your-region.amazonaws.com/random-uuid"
}
```
