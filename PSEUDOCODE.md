# rastgeleSayiUretimAlgortimasi
ALGORİTMA: PureMathRNG (Saf Matematiksel Rastgele Sayı Üreteci)

GİRDİ: Seed (Tohum) Değeri, Toplam_Uzunluk (Çift Sayı)
ÇIKTI: 0 ve 1'lerden oluşan Rastgele Bit Dizisi

BAŞLA

    SINIF PureMathRNG:
        
        FONKSİYON Başlat(seed, uzunluk):
            State = seed
            Çarpan = 1664525
            Artış = (seed * 19937) + 1013904223
            Modül = 4294967296
            Limit = uzunluk / 2
        
        FONKSİYON ChaosStep():
            EĞER State ÇİFT İSE:
                State = State / 2
            DEĞİLSE:
                State = 3 * State + 1
            
            State = (Çarpan * State + Artış) MOD Modül
            DÖNDÜR State

        FONKSİYON Generate():
            Ham_Liste = []
            Çift_Sayacı = 0
            Tek_Sayacı = 0
            
            DÖNGÜ (Çift_Sayacı < Limit VEYA Tek_Sayacı < Limit):
                Ham_Sayı = ChaosStep()
                İşlenmiş_Sayı = (Ham_Sayı SAĞA_KAYDIR 10) MOD 1000
                EĞER İşlenmiş_Sayı == 0 İSE: İşlenmiş_Sayı = 1
                
                EĞER İşlenmiş_Sayı ÇİFT İSE:
                    EĞER Çift_Sayacı < Limit:
                        Ham_Liste.EKLE(İşlenmiş_Sayı)
                        Çift_Sayacı artır
                    DEĞİLSE EĞER Tek_Sayacı < Limit:
                        Ham_Liste.EKLE(İşlenmiş_Sayı + 1)
                        Tek_Sayacı artır
                DEĞİLSE (Sayı Tek İSE):
                    EĞER Tek_Sayacı < Limit:
                        Ham_Liste.EKLE(İşlenmiş_Sayı)
                        Tek_Sayacı artır
                    DEĞİLSE EĞER Çift_Sayacı < Limit:
                        Ham_Liste.EKLE(İşlenmiş_Sayı + 1)
                        Çift_Sayacı artır
            
            Ham_Liste = ManualShuffle(Ham_Liste)
            
            Bit_Dizisi = []
            HER Numara İÇİN Ham_Liste:
                EĞER Numara ÇİFT İSE: Bit_Dizisi.EKLE(0)
                DEĞİLSE: Bit_Dizisi.EKLE(1)
                
            DÖNDÜR Bit_Dizisi

        FONKSİYON ManualShuffle(Dizi):
            N = Dizi.Uzunluğu
            DÖNGÜ i -> N-1'den 1'e kadar (Ters):
                Rastgele_Değer = ChaosStep()
                Hedef_İndeks = Rastgele_Değer MOD (i + 1)
                Dizi[i] ile Dizi[Hedef_İndeks] YER DEĞİŞTİR
            DÖNDÜR Dizi

ANA PROGRAM:
    Kullanıcıdan Seed al (Pozitif Tamsayı Doğrulaması yap)
    RNG Nesnesi oluştur (Seed, 20)
    Sonuç = RNG.Generate()
    YAZDIR Sonuç
    YAZDIR "Analiz: 0 ve 1 Sayıları Eşit"

BİTİR