# 🖼️ Image Watermark Service

Serviço REST desenvolvido em Spring Boot para aplicação automática de marca d'água em imagens PNG e JPG.

## 📋 Visão Geral

O **Image Watermark Service** é uma API REST que permite aplicar marcas d'água em imagens de forma automatizada. O serviço processa imagens enviadas via requisições HTTP e retorna a imagem processada com a marca d'água aplicada.

### Características Principais

- ✅ Processamento automático de imagens PNG e JPG
- ✅ Marca d'água configurável (tamanho e opacidade)
- ✅ API RESTful simples e intuitiva
- ✅ Suporte a CORS para integração web
- ✅ Validação robusta de entrada
- ✅ Processamento eficiente usando bibliotecas otimizadas

## 🚀 Início Rápido

### Pré-requisitos

- Java 21 ou superior
- Maven 3.6+ (ou use `mvnw` incluído no projeto)

### Executar o Serviço

```bash
# Compilar o projeto
mvn clean package

# Executar o servidor
mvn spring-boot:run
```

O servidor estará disponível em: `http://localhost:8080`

### Testar a API

```bash
# Exemplo com cURL
curl -X POST \
  -F "image=@sua-imagem.jpg" \
  http://localhost:8080/api/images/watermark \
  --output resultado.jpg
```

## 📡 Endpoint da API

### POST /api/images/watermark

Aplica marca d'água na imagem enviada.

**Request:**
- Content-Type: `multipart/form-data`
- Parâmetro: `image` (arquivo PNG ou JPG)

**Response:**
- Status: `200 OK`
- Content-Type: `image/png` ou `image/jpeg`
- Body: Imagem processada (binário)

**Exemplo de Requisição:**

```javascript
const formData = new FormData();
formData.append('image', fileInput.files[0]);

const response = await fetch('http://localhost:8080/api/images/watermark', {
    method: 'POST',
    body: formData
});

const blob = await response.blob();
// Usar o blob (imagem com watermark)
```

## ⚙️ Configuração

### Tamanho da Marca d'Água

Edite em `ImagesService.java`:

```java
private static final double WATERMARK_SIZE_PERCENTAGE = 0.50; // 50% da largura
```

### Opacidade da Marca d'Água

Edite em `ImagesService.java`:

```java
private static final float WATERMARK_OPACITY = 0.5f; // 50% opaco
```

### Arquivo de Marca d'Água

Coloque o arquivo `waterMark.jpg` em:
```
src/main/resources/waterMark.jpg
```

## 🛠️ Tecnologias

- **Spring Boot 4.0.1** - Framework Java
- **Java 21** - Linguagem de programação
- **Thumbnailator 0.4.20** - Processamento de imagens
- **TwelveMonkeys ImageIO 3.10.1** - Leitura/escrita de imagens
- **Lombok** - Redução de boilerplate
- **Log4j2** - Sistema de logging

## 📊 Estrutura do Projeto

```
Image_WaterMark_Service/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/TestFocusTextil/example/Image_WaterMark_Service/
│   │   │       ├── Controller/      # Endpoints REST
│   │   │       ├── Service/         # Lógica de negócio
│   │   │       ├── Domain/          # Modelos de domínio
│   │   │       └── Util/            # Utilitários
│   │   └── resources/
│   │       ├── waterMark.jpg        # Arquivo de marca d'água
│   │       └── application.properties
│   └── test/
├── docs/                             # Documentação
├── pom.xml
└── README.md
```

## 🔧 Desenvolvimento

### Compilar

```bash
mvn clean compile
```

### Executar Testes

```bash
mvn test
```

### Gerar JAR

```bash
mvn clean package
```

O JAR será gerado em: `target/Image_WaterMark_Service-0.0.1-SNAPSHOT.jar`

## 🆘 Troubleshooting

### Erro: "Image can't be Null"
- Verifique se o parâmetro se chama exatamente `image` (minúsculo)
- Certifique-se de que o tipo é `File` no Postman

### Erro: "Only PNG and JPG images are allowed"
- Use apenas arquivos `.png`, `.jpg` ou `.jpeg`
- Verifique o Content-Type do arquivo

### Erro: "waterMark not found"
- Verifique se `waterMark.jpg` está em `src/main/resources/`
- Recompile o projeto após adicionar o arquivo

### Erro de CORS
- Verifique se `@CrossOrigin` está presente no controller
- Reinicie o servidor

Para mais detalhes, consulte a [Documentação Técnica](./docs/API_DOCUMENTATION.md).

## 📝 Licença

Este projeto é propriedade da Focus Têxtil.

## 👥 Equipe

Desenvolvido pela equipe de desenvolvimento da Focus Têxtil.

---

**Versão:** 0.0.1-SNAPSHOT  
**Última atualização:** 2025-01-15

