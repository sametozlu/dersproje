# GitHub Egitimi - Python ile Tek Dosya Rehberi

Bu dersin amaci:
- Basit bir projeyi Git ile yonetmek
- GitHub'a push etmek
- Ayni repoyu clone etmek
- Yeni branch acmak
- Branch'leri merge etmek

Bu dosyadaki komutlari ogrenciler satir satir uygulayabilir.

---

## 1) Basit proje kodu (`app.py`)

Asagidaki kodu `app.py` dosyasina yazin:

```python
def main():
    tasks = [
        "Repo olustur",
        "Projeyi push et",
        "Repoyu clone et",
        "Yeni branch ac",
        "Branch merge yap",
    ]

    print("GitHub Egitim Projesi (Python)")
    print("-" * 32)
    for i, task in enumerate(tasks, start=1):
        print(f"{i}. {task}")

if __name__ == "__main__":
    main()
```

Calistirma:

```bash
python app.py
```

---

## 2) Projeyi ilk kez Git ile baslatma

Proje klasorunde terminal acin ve su komutlari calistirin:

```bash
git init
git add .
git commit -m "ilk commit: app.py eklendi"
```

Kontrol:

```bash
git log --oneline
```

---

## 3) GitHub repo olustur ve push et

### GitHub uzerinden repo olusturma
1. GitHub'da yeni repo acin (ornek: `github-egitim-projesi`)
2. Repo bos olsun (README secmeyin)

### Local projeyi remote'a baglama

`<REPO_URL>` yerine kendi repo linkinizi yazin:

```bash
git remote add origin <REPO_URL>
git branch -M main
git push -u origin main
```

Ornek `<REPO_URL>`:

```text
https://github.com/kullanici-adi/github-egitim-projesi.git
```

---

## 4) Repoyu clone etme

Ana klasore geri donup clone islemi yapin:

```bash
cd ..
git clone <REPO_URL>
cd github-egitim-projesi
```

Kontrol:

```bash
git branch
git remote -v
```

---

## 5) Yeni branch olusturma ve degisiklik yapma

Yeni branch ac:

```bash
git checkout -b feature/ogrenci-mesaji
```

`app.py` dosyasina su satiri ekleyin:

```python
print("Bu satir feature branch uzerinde eklendi.")
```

Sonra commit at:

```bash
git add .
git commit -m "feature: ogrenci mesaji eklendi"
git push -u origin feature/ogrenci-mesaji
```

---

## 6) Main branch'e don ve merge yap

```bash
git checkout main
git pull origin main
git merge feature/ogrenci-mesaji
git push origin main
```

Kontrol:

```bash
git log --oneline --graph --all
```

---

## 7) Ogrencilere verilecek mini odev

1. Her ogrenci kendi adiyla bir branch acsin:

```bash
git checkout -b feature/ad-soyad
```

2. `app.py` dosyasina kendi adini eklesin (ornek: `print("Hazirlayan: Ahmet")`)
3. Commit + push yapsin.
4. Main branch'e merge etsin.

---

## 8) Hata olursa hizli cozum

Remote zaten varsa:

```bash
git remote set-url origin <REPO_URL>
```

Push reddedilirse:

```bash
git pull --rebase origin main
git push origin main
```

Merge conflict olursa:
1. Cakisan dosyayi ac
2. `<<<<<<<`, `=======`, `>>>>>>>` kisimlarini duzelt
3. Asagidaki komutlari calistir:

```bash
git add .
git commit -m "fix: merge conflict cozuldu"
git push origin main
```

---

Bu kadar. Bu tek dokuman ile ogrenciler bastan sona GitHub akisini Python dosyasi ile uygulayabilir.
