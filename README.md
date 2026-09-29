# pedropietro.dev

Site pessoal de links de [Pedro Pietroluongo](https://pedropietro.dev), construído com [Quarkus Roq](https://iamroq.com) — um Static Site Generator em Java sobre Quarkus.

Migrado do Jekyll original ([harsh98trivedi/Links](https://github.com/harsh98trivedi/Links)) para Roq.

## Requisitos

- JDK 21+ (dev usou JDK 25)
- Maven Wrapper incluso (`./mvnw`)

## Rodar em dev

```bash
./mvnw quarkus:dev
```

Abre `http://localhost:8080`. Live-reload em `content/`, `templates/`, `data/` e `public/`.

## Gerar site estático

```bash
./mvnw package quarkus:run -Dquarkus.roq.generator.enabled=true
```

Saída em `target/roq/`.

## Estrutura

```
content/              Páginas (front-matter + Qute/HTML)
  index.html          Grid de links
  404.html
templates/layouts/    Layouts Qute
  base.html
data/
  profile.yml         Nome, tagline, cover, lista de links
public/               Assets estáticos servidos como estão
  assets/css/main.css
  assets/images/
  favicon.ico
src/main/resources/
  application.properties  site.url e config Quarkus
pom.xml
```

## Editar links

Editar `data/profile.yml`. Cada entrada aceita `name`, `url`, `username` (opcional, concatenado a `url`), `color`, `icon_class` (Font Awesome), `text_color` (opcional).

## Deploy

Publicar conteúdo de `target/roq/` em qualquer host estático (GitHub Pages, Netlify, S3 etc).

## Licença

[GNU GPL v2.0](./LICENSE)
