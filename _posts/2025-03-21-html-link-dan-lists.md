---
layout: post
title: "HTML link dan lists"
---

Penjelasan tentang Link dan Lists pada HTML.

# Link (tautan) di HTML
 
 link di gunakan untuk menghubungkan halaman satu dengan yang lain, 
 baik itu halaman di situs yang sama maupun ke situs lain.
   contohnya : klik disini

   - Tag Dasar
       * <a href="URL">Teks yang diklik</a>
   - Atribut penting
       * href: alamat tujuan link (URL atau path).
       * terget="_blank": membuka link di tab baru.
       * title: menampilkan keterangan saat cursor diarahkan ke link.
       * contoh: <a href="https://ww.google.com"
         target="_blank" title="kunjungi google" >Buka Google</a>

# LISTS (daftar) di HTML

HTML memiliki tiga jenis daftar(list):

   - Ordered List(<ol>)
      menurut angka / huruf
       * <ol>
           <li>item pertama</li>
           <li>item kedua</li>
         </ol>

   - unordered List(<ul>)
      tidak berurutan (menggunakan bullet).
      * <ul>
             <li>item A</li>
             <li>item B</li>
           </ul>

   - Description lists (<dl>)
      untuk mendeskripsikan atau daftar berpasangan .
      * <dl>
             <dt>HTML</dt>
             <dd>bahasa markup untuk membuat halaman web.</dd>
           </dl>

# kesimpulan
   - ul = unordered lidt sebagai wadah menu.
   - li = setiap item menu.
   - a = link ke halaman lain.
   - CSS digunakan untuk membuat tampilan horizontal dan interaktif.
   