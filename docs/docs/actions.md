---
title: Aksiyonlar
description: Aksiyonlar ve onların Gatsby içerisinde statünüzü nasıl güncellemeye yardımcı olduğunun dökümantasyonu
jsdoc:
  - "gatsby/src/redux/actions/public.js"
  - "gatsby/src/redux/actions/restricted.js"
contentsHeading: Fonksiyonlar
---

Gatsby sistem içerisinde statü yönetimi için [Redux](http://redux.js.org) kullanmaktadır. Gatsby API kullanılığında size bir seri aksiyon (Redux'ta aksiyon ile bağlanan [bindActionCreators](https://redux.js.org/api/bindactioncreators/) ile aynı) verilmektedir, bunlar sitenizdeki statü'yü değiştirebilmenizi sağlar.

`actions` objesi içinde fonksiyonlar bulundurmaktadır ve bu fonksiyonlari teker teker ES6 obje ayrıştırma kullanarak çağırabilirsiniz.

```javascript
// createNodeField fonksiyonu için
exports.onCreateNode = ({ node, getNode, actions }) => {
  const { createNodeField } = actions
}
```
