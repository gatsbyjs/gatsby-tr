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


### Gatsby CLI'ı yükleyin

```shell
npm install -g gatsby-cli
```

### Yeni bir site oluşturun

```shell
gatsby new gatsby-sitesi
```

### Sitenin bulunduğu klasöre geçin

```shell
cd gatsby-sitesi
```

### Geliştirme sunucusunu başlatın

```shell
gatsby develop
```

Gatsby varsayılan olarak `localhost:8000` adresinde geliştirici ortamını erişime açacaktır.
 `src/pages` içindeki JavaScript sayfalarını düzenlemeye çalışın. Yapılan değişiklikleri tarayıcınızda anlık olarak göreceksiniz.

### Sitenizi çalıştırın

```shell
gatsby build
```

Gatsby, statik HTML ve her bir adres için JavaScript kod demetlerini yaratarak sitenizi oluşturmaya başlayacaktır. 

### Sitenizi yerel sunucuda çalıştırın

```shell
gatsby serve
```

Gatsby, oluşturduğunuz sitenizi yerel HTML sunucunuzda çalıştırarak test etme imkânı sunar. Ancak sitenizi çalıştırmadan önce `gatsby build` komutunu çalıştırdığınızdan emin olun. 

### CLI komutları için dökümantasyona ulaşma

CLI komutlarını ayrıntılarıyla incelemek için terminale `gatsby --help` yazmanız yeterli.

Özel komut ayrıntıları için; `gatsby COMMAND_NAME --help` örnek: `gatsby new --help`.

 Gatsby CLI hakkında daha detaylı bilgiye ulaşmak için dökümanlar bölümündeki [CLI Referansları](/docs/gatsby-cli/)'nı inceleyin.
