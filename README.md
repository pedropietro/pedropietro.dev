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

GitHub Pages via GitHub Actions ([`.github/workflows/deploy.yml`](.github/workflows/deploy.yml)), conforme
[docs do Roq](https://iamroq.dev/docs/publishing/):

- Push em `main` (ou execução manual/agendada diária) roda `quarkiverse/quarkus-roq` (JDK 25), gera `target/roq/` e
  publica com `actions/deploy-pages`.
- Em **Settings > Pages**: *Source* = **GitHub Actions**, *Custom domain* = `pedropietro.dev`.
- `public/CNAME` vai para a raiz do site gerado.
- DNS do apex `pedropietro.dev`: registros `A` para `185.199.108.153`, `185.199.109.153`, `185.199.110.153` e
  `185.199.111.153`; `www` como `CNAME` para `pedropietro.github.io`.

## Licença

[GNU GPL v2.0](./LICENSE)
