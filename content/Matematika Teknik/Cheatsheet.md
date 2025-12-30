
# Cheatsheet – Kalkulus Integral

## Dasar

Definisi: Kalkulus = Antiturunan

Notasi:
$$
\int{f(x) \, dx} = F(x) + C
$$

Rumus Dasar:
$$
\int{ax^n \, dx} = \frac{a}{n+1}x^{n+1} + C, n \ne -1
$$

## Integral Parsial

Bentuk Umum:
$$
\int{u \, dv} = uv - \int{v \, du}
$$
 
Contoh:

$\int x^2 \sqrt{ x - 3 } \, dx$

Jawab:
1. Jadikan bentuk: $\int u \, dv$
2. $u = x^2$, $dv = \sqrt{ x-1 } \, dx$
3. $du = 2x$, $v = \frac{2}{3}(x-1)^{\frac{3}{2}}$
4. Masukkan ke: $\int{u \, dv} = uv - \int{v \, du}$
5. ::
	- $\int x^2 \sqrt{ x-1 } \, dx = x^2 .\frac{2}{3}(x-1)^{\frac{3}{2}} - \int \frac{2}{3}(x-1)^{\frac{3}{2}} 2x \, dx$
	- $= x^2 .\frac{2}{3}(x-1)^{\frac{3}{2}} - \frac{4}{3} \int x (x-1)^{\frac{3}{2}} \, dx$
6. ...

### Metode Tanzalin

...


## Integral Substitusi

### Integral Substitusi Trigonometri

## Integral Tentu

- Jumlah Riemann

## Aplikasi Integral

## Persamaan Diferensial Biasa Orde 1