---
layout: post
title: "Belajar memahami Javascript dan Config YML pada web"
---


Belajar memahami Javascript dan Config YML pada web

   1. Javascript
     javascript adalah bahasa pemrograman untuk membuat halaman web menjadi interaktif dan dinamis. karna jekyll menghasilkan halaman HTML dan bisa juga menambahkan javascriptdi folder assets/js/.
       - Buat file javascript
         * assets/js/:
       - Tambahkan tombol di HTML (misal index.html)
          * <button id="tombol">klik disini</button>
       - Sisipkan file js ke layout atau halaman
          * Di_layouts/defauit.html atau index.html sebelum</body>:
          * <script src="{{ site.baseurl }}/assets/js/scripts.js"></script>

    2. Config YML
        config yml adalah format file konfigurasi yang di gunakan untuk menyimpan peraturan. File_config.yml digunakan untuk mangatur nama situs, deskripsi, tema, struktur dan peraturan build.
         - contoh file_conlig.yml jekyll
             title: "belajar jekyll"
             description: "belajar web static dengan jekyll"
            url: 'https://apaansih.github.io'

               plugins:
               - jekyll-feed
               - jekyll-sitemap
               - jekyll-seo-tag
         