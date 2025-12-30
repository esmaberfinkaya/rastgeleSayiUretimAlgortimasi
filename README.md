# rastgeleSayiUretimAlgortimasi
flowchart TD
    A([BAŞLA]) --> B[/Kullanıcıdan Seed Al/]
    B --> C{Girdi Geçerli mi?}
    C -- Hayır --> D[Hata Mesajı Göster]
    D --> B
    C -- Evet --> E[PureMathRNG Başlat\nLCG Sabitlerini Ayarla]
    
    E --> F[Generate Fonksiyonu Başlat]
    F --> G{Kota Doldu mu?\nÇift < Limit OR Tek < Limit}
    
    G -- Evet, Devam --> H[ChaosStep Çağır\nCollatz + LCG İşlemi]
    H --> I[Sayıyı Sıkıştır\nBit Shift & Mod]
    I --> J{Sayı Çift mi?}
    
    J -- Evet --> K{Çift Kotası\nDoldu mu?}
    K -- Hayır --> L[Listeye Çift Ekle]
    K -- Evet --> M[Sayıyı Tek Yap\nListeye Ekle]
    
    J -- Hayır --> N{Tek Kotası\nDoldu mu?}
    N -- Hayır --> O[Listeye Tek Ekle]
    N -- Evet --> P[Sayıyı Çift Yap\nListeye Ekle]
    
    L --> G
    M --> G
    O --> G
    P --> G
    
    G -- Hayır, Kota Doldu --> Q[ManualShuffle Çağır\nKarıştırma İşlemi]
    Q --> R[Dönüştürme Döngüsü\nÇift=0, Tek=1]
    R --> S[/Çıktı: Bit Dizisi/]
    S --> T([BİTİR])

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style T fill:#f9f,stroke:#333,stroke-width:2px
    style H fill:#bbf,stroke:#333,stroke-width:2px
    style Q fill:#bbf,stroke:#333,stroke-width:2px