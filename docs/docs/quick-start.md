---
title: Hızlı Başlangıç
---

Bu hızlı başlangıç rehberi, orta ve ileri düzey yazılımcılar için tasarlandı. Gatsby'ye daha temelden başlamak için, [eğitim bölümüne gidin](/tutorial/)!

## Gatsby CLI kullanımı

<EggheadEmbed
  lessonLink="https://egghead.io/lessons/gatsby-quick-start-with-gatsby-create-develop-and-build-gatsby-sites-from-the-command-line"
  lessonTitle="Quick Start with Gatsby: Create, Develop, and Build Gatsby Sites From the Command Line"
/>

**Not**: Bu videoda npm paketini yüklemeden önce çalıştırılan `npx` aracı kullanılıyor. Dolayısıyla bilgisayarınıza gatsby-cli'ını yüklediğinizde `gatsby new` komutu, videodaki `npx gatsby new` komutuyla aynı görevi görecektir.  

<<<<<<< HEAD

### Gatsby CLI'ı yükleyin
=======
### Install the Gatsby CLI
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
npm install -g gatsby-cli
```

<<<<<<< HEAD
### Yeni bir site oluşturun
=======
> The above command installs Gatsby CLI globally on your machine.

### Create a new site
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby new gatsby-site
```

<<<<<<< HEAD
### Sitenin bulunduğu klasöre geçin
=======
### Change directories into site folder
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
cd gatsby-site
```

<<<<<<< HEAD
### Geliştirme sunucusunu başlatın
=======
### Start development server
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby develop
```

<<<<<<< HEAD
Gatsby varsayılan olarak `localhost:8000` adresinde geliştirici ortamını erişime açacaktır.
 `src/pages` içindeki JavaScript sayfalarını düzenlemeye çalışın. Yapılan değişiklikleri tarayıcınızda anlık olarak göreceksiniz.

### Sitenizi çalıştırın
=======
Gatsby will start a hot-reloading development environment accessible by default at `http://localhost:8000`.

Try editing the JavaScript pages in `src/pages`. Saved changes will live reload in the browser.

### Create a production build
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby build
```

Gatsby, statik HTML ve her bir adres için JavaScript kod demetlerini yaratarak sitenizi oluşturmaya başlayacaktır. 

<<<<<<< HEAD
### Sitenizi yerel sunucuda çalıştırın
=======
### Serve the production build locally
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby serve
```

Gatsby, oluşturduğunuz sitenizi yerel HTML sunucunuzda çalıştırarak test etme imkânı sunar. Ancak sitenizi çalıştırmadan önce `gatsby build` komutunu çalıştırdığınızdan emin olun. 

### CLI komutları için dökümantasyona ulaşma

CLI komutlarını ayrıntılarıyla incelemek için terminale `gatsby --help` yazmanız yeterli.

Özel komut ayrıntıları için; `gatsby COMMAND_NAME --help` örnek: `gatsby new --help`.

 Gatsby CLI hakkında daha detaylı bilgiye ulaşmak için dökümanlar bölümündeki [CLI Referansları](/docs/gatsby-cli/)'nı inceleyin.
