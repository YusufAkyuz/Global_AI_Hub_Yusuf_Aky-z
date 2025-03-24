Sürücüsüz Metro Simülasyonu – Rota Optimizasyonu

Bu proje, bir metro ağı üzerinde iki istasyon arasındaki **en az aktarmalı** ve **en hızlı rotayı** bulan bir simülasyon sistemidir. Proje, Breadth-First Search (BFS) ve A* algoritmalarını kullanarak rota hesaplaması yapar.

---

Proje Amacı

- Metro ağını graph veri yapısı ile modellemek
- BFS algoritması ile en az aktarmalı rotayı bulmak
- A* algoritması ile en hızlı rotayı bulmak
- Gerçek dünya problemlerini algoritmalarla çözebilme yetisi kazanmak

---

Kullanılan Teknolojiler ve Kütüphaneler

- Python 3
- `collections` – BFS için `deque` kuyruğu oluşturmak amacıyla kullanıldı
- `heapq` – A* algoritmasında öncelik kuyruğu için kullanıldı
- `typing` – Tip güvenliği ve açıklayıcı fonksiyon imzaları için

---

Algoritmaların Çalışma Mantığı

BFS – En Az Aktarmalı Rota

- Breadth-First Search (Genişlik Öncelikli Arama) kullanılır.
- Kuyruk yapısıyla çalışır; ilk bulunan hedef en kısa adıma sahip olur.
- Ziyaret edilen istasyonlar tekrar kontrol edilmez.
- Süre değil, **geçilen istasyon sayısı** dikkate alınır.

A* – En Hızlı Rota

- A* algoritması, bu projede heuristik olmadan (Dijkstra gibi) uygulanmıştır.
- Toplam seyahat süresi dikkate alınır.
- Öncelik kuyruğu (`heapq`) ile süre bazlı sıralama yapılır.
- En kısa sürede hedefe ulaşan rota döndürülür.

---

Örnek Kullanım

```python
metro = MetroAgi()
metro.istasyon_ekle("A")
metro.istasyon_ekle("B")
metro.istasyon_ekle("C")
metro.istasyon_ekle("D")
metro.baglanti_ekle("A", "B", 4)
metro.baglanti_ekle("B", "C", 3)
metro.baglanti_ekle("A", "D", 10)
metro.baglanti_ekle("D", "C", 2)

# En az aktarmalı rota (BFS)
rota = metro.en_az_aktarma_bul("A", "C")
print("En az aktarmalı rota:", [i.isim for i in rota])

# En hızlı rota (A*)
rota, sure = metro.en_hizli_rota_bul("A", "C")
print("En hızlı rota:", [i.isim for i in rota], "Toplam süre:", sure)
