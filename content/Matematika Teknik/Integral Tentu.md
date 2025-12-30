#MK/Matematika_Teknik

# Matematika Teknik: Integral Tentu (P13)

Daftar isi
1. [[#Integral Riemann]]
2. [[#Integral Tentu]]

## Integral Riemann

> Mendefinisikan apa itu integral tentu

Key points:
- Dikembangkan oleh Bernhard Riemann, matematikan asal Jerman
- **Konsep Dasar**: Metode ini menghitung luas di bawah kurva dengan membagi interval integrasi $[a,b]$ menjadi sub-interval (partisi) yang sangat kecil.
- **Proses**: Pada setiap sub-interval, dibuat persegi panjang dan luasnya dihitung. Jumlah total luas persegi panjang ini disebut **Jumlah Riemann**.
- **Hubungan dengan Integral Tentu:** Integral tentu didefinisikan sebagai limit dari Jumlah Riemann ketika lebar partisi mendekati nol dan jumlah partisi mendekati tak terhingga. Jika limit ini ada, maka fungsi tersebut dikatakan terintegral Riemann

## Integral Tentu

- Definisi secara notasi: $\int_{a}^{b}{f(x)dx} = \lim_{ |P| \to 0 }{\sum_{i=0}^{n}{f(\bar{x_{i}})\Delta{x_{i}}}}$
- $\int_{a}^{b}{f(x)dx} = F(x)|_{a}^{b} = F(b) - F(a)$

Sifat-sifat:
- $\int_{a}^{a}{f(x)dx} = 0$
- $\int_{a}^{b}{f(x)dx} = - \int_{b}^{a}{f(x)dx}$

## Additional Resources:

- <https://www.mathsisfun.com/calculus/integration-definite.html>
