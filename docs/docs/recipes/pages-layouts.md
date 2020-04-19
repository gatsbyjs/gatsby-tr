---
title: "Tarifler: Sayfalar ve Yerleşimler (Layouts)"
tableOfContentsDepth: 1
---

Gatsby sitenize sayfalar ekleyin ve ortak sayfa öğelerini yönetmek için yerleşimleri kullanın.

## Proje yapısı

Bir Gatsby projesinin içinde, aşağıdaki klasör ve dosyaların bazılarını veya tümünü görebilirsiniz:

```
|-- /.cache
|-- /plugins
|-- /public
|-- /src
    |-- /pages
    |-- /templates
    |-- html.js
|-- /static
|-- gatsby-config.js
|-- gatsby-node.js
|-- gatsby-ssr.js
|-- gatsby-browser.js
```

Bazı önemli dosyalar ve tanımları:

- `gatsby-config.js` — proje başlığı, açıklama, eklentiler vb. için meta verilerle, bir Gatsby sitesinin seçeneklerini yapılandırma
- `gatsby-node.js` — build etme işlemini etkileyen varsayılan ayarları özelleştirmek ve genişletmek için Gatsby’nin Node.js API'lerini uygulama
- `gatsby-browser.js` — Gatsby’nin tarayıcı API'lerini kullanarak tarayıcıyı etkileyen varsayılan ayarları özelleştirme ve genişletme
- `gatsby-ssr.js` — sunucu tarafı render etmeyi etkileyen varsayılan ayarları özelleştirmek için Gatsby’nin sunucu tarafı render etme API'lerini kullanma

### Ek kaynaklar

- Tüm ortak klasör ve dosyalar'da bir tur için [Gatsby'nin Proje Yapısı](/docs/gatsby-project-structure/) üzerindeki dokümanları okuyun
- Genel komutlar için, [Gatsby CLI dokümanları](/docs/gatsby-cli) 'nı kontrol edin
- İndirilebilir bir bakışta bilgi için [Gatsby Cheat Sheet](/docs/cheat-sheet/) sayfasına göz atın

## Sayfaları otomatik olarak oluşturma

Gatsby çekirdeği (core), otomatik olarak `src/pages` içindeki React bileşenlerini, URL'i olan sayfalara dönüştürür.
Örneğin, `src/pages/index.js` ve `src/pages/about.js` adresindeki bileşenler, otomatik olarak sitenin dizin sayfası (`/`) ve `/about` için, bu dosya adlarından sayfalar oluşturur.

### Ön şartlar

- Bir [Gatsby sitesi](/docs/quick-start)
- Kurulmuş [Gatsby CLI](/docs/gatsby-cli)

### Talimatlar

1. Sitenizde eğer yoksa `src/pages` için bir dizin oluşturun.
2. Sayfalar dizinine bir bileşen dosyası ekleyin (about.js):

```jsx:title=src/pages/about.js
import React from "react"

const AboutPage = () => (
  <main>
    <h1>Yazar Hakkında</h1>
    <p>Gatsby siteme hoş geldiniz.</p>
  </main>
)

export default AboutPage
```

3. Geliştirme sunucusunu başlatmak için, proje dizininde `gatsby develop` komutunu çalıştırın.
4. Tarayıcıda yeni sayfanızı ziyaret edin: `http://localhost:8000/about`

### Ek kaynaklar

- [Sayfaları oluşturma ve değiştirme](/docs/creating-and-modifying-pages/)

## Linking between pages

Routing in Gatsby relies on the `<Link />` component.

### Prerequisites

- A Gatsby site with two page components: `index.js` and `contact.js`
- The Gatsby `<Link />` component
- The [Gatsby CLI](/docs/gatsby-cli/) to run `gatsby develop`

### Directions

1. Open the index page component (`src/pages/index.js`), import the `<Link />` component from Gatsby, add a `<Link />` component above the header, and give it a `to` property with the value of `"/contact/"` for the pathname:

```jsx:title=src/pages/index.js
import React from "react"
import { Link } from "gatsby"

export default () => (
  <div style={{ color: `purple` }}>
    <Link to="/contact/">Contact</Link>
    <p>What a world.</p>
  </div>
)
```

2. Run `gatsby develop` and navigate to the index page. You should have a link that takes you to the contact page when clicked!

> **Note**: Gatsby's `<Link />` component is a wrapper around [`@reach/router`'s Link component](https://reach.tech/router/api/Link). For more information about Gatsby's `<Link />` component, consult the [API reference for `<Link />`](/docs/gatsby-link/).

## Creating a layout component

It's common to wrap pages with a React layout component, which makes it possible to share markup, styles, and functionality across multiple pages.

### Prerequisites

- [A Gatsby Site](/docs/quick-start/)

### Directions

1. Create a layout component in `src/components`, where child components will be passed in as props:

```jsx:title=src/components/layout.js
import React from "react"

export default ({ children }) => (
  <div style={{ margin: `0 auto`, maxWidth: 650, padding: `0 1rem` }}>
    {children}
  </div>
)
```

2. Import and use the layout component in a page:

```jsx:title=src/pages/index.js
import React from "react"
import { Link } from "gatsby"
import Layout from "../components/layout"

export default () => (
  <Layout>
    <Link to="/contact/">Contact</Link>
    <p>What a world.</p>
  </Layout>
)
```

### Additional resources

- Create a layout component in [tutorial part three](/tutorial/part-three/#your-first-layout-component)
- Styling with [Layout Components](/docs/layout-components/)

## Creating pages programmatically with createPage

You can create pages programmatically in the `gatsby-node.js` file with helper methods Gatsby provides.

### Prerequisites

- A [Gatsby site](/docs/quick-start)
- A `gatsby-node.js` file

### Directions

1. In `gatsby-node.js`, add an export for `createPages`

```javascript:title=gatsby-node.js
// highlight-start
exports.createPages = ({ actions }) => {
  // ...
}
// highlight-end
```

2. Destructure the `createPage` action from the available actions so it can be called by itself, and add or get data

```javascript:title=gatsby-node.js
exports.createPages = ({ actions }) => {
  // highlight-start
  const { createPage } = actions
  // pull in or use whatever data
  const dogData = [
    {
      name: "Fido",
      breed: "Sheltie",
    },
    {
      name: "Sparky",
      breed: "Corgi",
    },
  ]
  // highlight-end
}
```

3. Loop through the data in `gatsby-node.js` and provide the path, template, and context (data that will be passed in the props' pageContext) to `createPage` for each invocation

```javascript:title=gatsby-node.js
exports.createPages = ({ actions }) => {
  const { createPage } = actions

  const dogData = [
    {
      name: "Fido",
      breed: "Sheltie",
    },
    {
      name: "Sparky",
      breed: "Corgi",
    },
  ]
  // highlight-start
  dogData.forEach(dog => {
    createPage({
      path: `/${dog.name}`,
      component: require.resolve(`./src/templates/dog-template.js`),
      context: { dog },
    })
  })
  // highlight-end
}
```

4. Create a React component to serve as the template for your page that was used in `createPage`

```jsx:title=src/templates/dog-template.js
import React from "react"

export default ({ pageContext: { dog } }) => (
  <section>
    {dog.name} - {dog.breed}
  </section>
)
```

5. Run `gatsby develop` and navigate to the path of one of the pages you created (like at `http://localhost:8000/Fido`) to see the data you passed it displayed on the page

### Additional resources

- Tutorial section on [programmatically creating pages from data](/tutorial/part-seven/)
- Reference guide on [using Gatsby without GraphQL](/docs/using-gatsby-without-graphql/)
- [Example repo](https://github.com/gatsbyjs/gatsby/tree/master/examples/recipe-createPage) for this recipe
