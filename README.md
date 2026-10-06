# pneus-loja

Catálogo de pneus raspado para montar uma loja própria.

## Conteúdo

- `data/products.json` — **1.318 pneus** enriquecidos (fonte canônica para a loja).
- `data/products_raw.json` — dump bruto da raspagem (antes da limpeza), para referência.
- `public/produtos/*.webp` — imagens internalizadas (1 por produto, nomeadas por `slug`). ~94 MB.

## Origem

Raspado da Store API pública do WooCommerce (`/wp-json/wc/store/v1/products`) da fonte.
Imagens baixadas e servidas localmente — **nada aponta de volta para a origem** em produção
(regra: dados independentes por loja).

## Esquema de cada produto (`data/products.json`)

| campo | descrição |
|---|---|
| `id` | id original |
| `name` | nome completo |
| `slug` | slug (também o nome do arquivo de imagem) |
| `sku` | SKU |
| `brand` | marca já normalizada (Title Case, sem duplicatas tipo `X / X`) |
| `categories` | categorias (Passeio, SUV, Aro 14, Scooter, etc.) |
| `aro` / `largura` / `perfil` / `medida` | medida extraída do nome (ex: `205/55 R16`) |
| `tipo_pneu` | `carro` / `moto` / `carga` |
| `price` / `regular_price` / `sale_price` / `on_sale` | preços em BRL |
| `in_stock` | disponibilidade |
| `image_local` | caminho da imagem interna (`/produtos/<slug>.webp`) |
| `image_src` | URL original (referência; não usar em produção) |
| `description` | descrição |
| `source_url` | link do produto na origem |

## Números

- 1.318 produtos, 100% com imagem e preço.
- Marcas principais: Goodyear, Pirelli, Kumho, Marshal, Michelin, Aeolus, Westlake, Dunlop, Hankook.
- Categorias: Passeio (643), Vans/Utilitários, SUV/Caminhonete, por aro (13–19), Scooter/Moto, Alta Performance.
