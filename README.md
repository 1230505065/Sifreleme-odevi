# 

## Program Hakkında Bilgiler
- Şifreleme Programı  sizin Verdiğiniz tam Sayı Kadar Girdiğiniz Metni İleri veyahut da  Gerye Doğru Öteleyebilir 
- Programı Çalıştırırsanız  2 Seçenek Göreceksiniz Bunlardan 1.si Şifreleme, 2.si Deşifreleme seçeneği olacaktır.
- **Program Sadece İngiliz Alfabesini İçermektedir diğer alfabeleri kabul etmez .**
- Yani Gireceğiniz Türkçe veya Tanımlı Olmayan Bir Karakter Girdiğinizde Hata Alabilir veya Öteleme İşleminin Verdiğiniz Değer İçin Gerçekleşmediğini Görebilirsiniz.
- dosya içerisinde seçeceğiniz seçeneklere göre yönlendireleceksiniz. 


## Operasyonları Kullanma prosedürleri
### Şifreleme Operasyon prosedürü
- Şifreleme Operasyonu Metni Girdiğiniz Sayı Kadar **Alfabe Sınırları** İçerisinde ileriye doğru atar.
  Yani Eğer "salamlar" Metnini Girerseniz ve kaydırma  Miktarı Olarak  5 Sayısını Girerseniz Size Çıktı Olarak "xfqfeqfw" Metnini Verecektir.
- Bu Çıktı Sizin Girdiğiniz Metnin Her Bir Harfinin 5  Kez İleri kaydırılmış  Halidir.

---

### Deşifreleme Operasyon prosedürü
- Deşifreleme Operasyonu Metni Girdiğiniz Sayı Kadar **Alfabe Sınırları** İçerisinde Geriye doğru kaydırır.
- Yani Yukarıdaki Verdiğim Örneği Kullanırsak ve Şifreyi Tekrar Anlamlı Bir Metne Dönüştürmek İstiyorsak  Metninin Her Bir Harfini 5 Kez Geri kaydırmamız  Gerekir.
- Program içinde deşifrelemeyi seçip yaparsak,  Metni Yazdığımızda ve Öteleme Miktarını 5 Olarak Girdiğimizde Çıktı Olarak "salam" Metnini Alırız.



## Dosya Okuma ve dosyayı  Yazma
- Şifreleme ve Deşifreleme Operasyonları İçin Aynı Dosyaları okuma  ve Yazma Operasyonlarını  Çalışmaktadır.
- Dosyanız Yoksa ve Dosya Oluşturmak için seçenek  Seçerseniz Kod Sizin İçin Bir 'input.txt' Dosyası Oluşturur.
- Kendi Dosyanızı Oluşturmak adına  SifrelemeProgram.exe' nin Olduğu Klasörde kendiniz için bir  Dosya Oluşturabilirsiniz.
- Kendi Oluşturduğunuz başka adlı  Bir Dosyayı Okutmak İsterseniz Kod İçindeki **'input.txt'**  içeriğini  Değiştirebilirsiniz.

### Ekran Görüntüleri
![Şifreleme Görüntüsü](https://github.com/1230505065/Sifreleme-odevi/blob/main/sifreleme%20ss.png)


![Deşifreleme Görüntüsü](https://github.com/1230505065/Sifreleme-odevi/blob/main/ss%20desifreleme%20do%C4%9Frusu.png)

### Kod İçeriği
#include <stdio.h>
#include <ctype.h>

// Fonksiyonların prototipleri
void encrypt(char password[], int scroll);
void deEncrypt(char password[], int scrollToBack);

int main() {
    char input[1000];
    int choice, scroll;

    // Doğru bir seçenek girilene kadar döngü
    while (1) {
        printf("Şifreleme (1) veya Deşifreleme (2) yapmak için bir seçenek girin: ");
        if (scanf("%d", &choice) == 1 && (choice == 1 || choice == 2)) {
            break;
        } else {
            printf("Geçersiz seçenek. Lütfen 1 veya 2 girin.\n");
            fflush(stdin);
        }
    }

    printf("Metni girin: ");
    scanf(" %[^\n]", input);  // Metni boşluklarla birlikte okumak için boşluk bırakıldı.

    printf("Kaydırma miktarını girin: ");
    scanf("%d", &scroll);

    if (choice == 1) {
        encrypt(input, scroll);
        printf("Şifrelenmiş Metin: %s\n", input);
    } else if (choice == 2) {
        deEncrypt(input, scroll);
        printf("Deşifre Edilmiş Metin: %s\n", input);
    }

    return 0;
}

// Şifreleme fonksiyonu
void encrypt(char password[], int scroll) {
    int i = 0;
    while (password[i] != '\0') {
        if (isalpha(password[i])) {
            char base = islower(password[i]) ? 'a' : 'A';
            password[i] = base + (password[i] - base + scroll) % 26;
        }
        ++i;
    }
}

// Deşifreleme fonksiyonu
void deEncrypt(char password[], int scrollToBack) {
    encrypt(password, -scrollToBack);
}





    
