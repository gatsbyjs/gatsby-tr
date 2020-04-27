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
2. Sayfalar dizinine bir bileşen dosyası ekleyin (`about.js`):

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

## Sayfalar arasında bağlantı oluşturma

Gatsby'de yönlendirme (routing) `<Link />` bileşenine dayanır.

### Ön şartlar

- İki tane sayfa bileşenli bir Gatsby sitesi: `index.js` ve `contact.js`
- Gatsby'nin `<Link />` bileşeni
- `gatsby develop` komutunu çalıştırmak için [Gatsby CLI](/docs/gatsby-cli/)

### Talimatlar

1. index sayfası bileşenini açın (`src/pages/index.js`), `<Link />` bileşenini Gatsby'den içe aktarın, başlığın üstüne bir `<Link />` bileşeni ekleyin, ve yol adı için `"/contact/"` değerine sahip bir `to` özelliği verin:

```jsx:title=src/pages/index.js
import React from "react"
import { Link } from "gatsby"

export default () => (
  <div style={{ color: `purple` }}>
    <Link to="/contact/">İletişim</Link>
    <p>Ne dünya ama.</p>
  </div>
)
```

2. `gatsby develop` komutunu çalıştırın ve index sayfasına gidin. Tıklandığında sizi iletişim (`/contact`) sayfasına götüren bir bağlantınız olmalı!

> **Not**: Gatsby'nin `<Link />` bileşeni, [`@reach/router`'s Link bileşeni](https://reach.tech/router/api/Link) için bir sarmalayıcıdır. Gatsby'nin `<Link />` bileşeni hakkında daha fazla bilgi için, buraya danışabilirsiniz: [`<Link />` için API referansı](/docs/gatsby-link/).

## Bir yerleşim (layout) bileşeni oluşturma

Biçimlendirme, stil ve işlevselliği birden çok sayfada paylaşmayı mümkün kılan bir React yerleşim bileşeniyle sayfaları sarmak yaygındır.

### Ön şartlar

- Bir [Gatsby sitesi](/docs/quick-start/)

### Talimatlar

1. Alt bileşenlerin prop'lar olarak aktarılacağı `src/components` içinde, bir yerleşim bileşeni oluşturun (`layout.js`):

```jsx:title=src/components/layout.js
import React from "react"

export default ({ children }) => (
  <div style={{ margin: `0 auto`, maxWidth: 650, padding: `0 1rem` }}>
    {children}
  </div>
)
```

2. Bir sayfada yerleşim bileşenini içe aktarın ve kullanın:

```jsx:title=src/pages/index.js
import React from "react"
import { Link } from "gatsby"
import Layout from "../components/layout"

export default () => (
  <Layout>
    <Link to="/contact/">İletişim</Link>
    <p>Ne dünya ama.</p>
  </Layout>
)
```

### Ek kaynaklar

- [Öğretici - bölüm üç](/tutorial/part-three/#your-first-layout-component) 'te, bir yerleşim bileşeni oluşturun
- [Yerleşim Bileşenleri](/docs/layout-components/) ile şekillendirme

## createPage ile programlanabilir bir biçimde sayfalar oluşturma

Gatsby'nin sağladığı yardımcı metodlarla, `gatsby-node.js` dosyasında programlanabilir bir biçimde sayfalar oluşturabilirsiniz.

### Ön şartlar

- Bir [Gatsby sitesi](/docs/quick-start)
- Bir `gatsby-node.js` dosyası

### Talimatlar

1. `gatsby-node.js` içinde, `createPages` için bir dışa aktarım (export) ekleyin

```javascript:title=gatsby-node.js
// highlight-start
exports.createPages = ({ actions }) => {
  // ...
}
// highlight-end
```

2. Kendi başına çağırabilmek için `createPage` aksiyonunu `actions` parametresi içinden alın, ve veri ekleyin veya alın

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

3. `gatsby-node.js` içindeki veriler arasında dolaşın ve yolu, şablonu ve bağlamı (sayfaya pageContext prop'u olarak iletilecek veriler) `createPage`'e her iterasyonda sağlayın

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

4. Sayfanız için, `createPage` içinde kullanılan şablon olarak işlev görmek üzere bir React bileşeni oluşturun

```jsx:title=src/templates/dog-template.js
import React from "react"

export default ({ pageContext: { dog } }) => (
  <section>
    {dog.name} - {dog.breed}
  </section>
)
```

5. `gatsby develop` komutunu çalıştırın ve geçirdiğiniz verileri görmek için oluşturduğunuz sayfalardan birinin yoluna gidin (`http://localhost:8000/Fido` gibi)

### Ek kaynaklar

- Eğitim bölümü: [programlanabilir bir biçimde verilerden sayfa oluşturma](/tutorial/part-seven/)
- Referans kılavuzu: [GraphQL olmadan Gatsby kullanımı](/docs/using-gatsby-without-graphql/)
- Bu tarif için [örnek repo](https://github.com/gatsbyjs/gatsby/tree/master/examples/recipe-createPage)
