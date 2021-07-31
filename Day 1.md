# Day 1

## introduction

Rust adalah bahasa pemrograman [multi-paradigm](https://en.wikipedia.org/wiki/Programming_paradigm#Support_for_multiple_paradigms),  hight-level, [general-purpose](https://en.wikipedia.org/wiki/General-purpose_programming_language), dan didisain untuk performa dan safety, terlebih untuk concurrency.  Rust dibuat pada tahun 2006 oleh tim mozilla, Rust memiliki syntax yang mirip dengan c++



## Variabel dan mutabillity

Pada umumnya bahasa pemrograman lain yang memiliki variabel, di Rust juga terdapat variabel. Tetapi variabel di rust sedikit berbeda dibandingkan dengan variabel lain yaitu memiliki feature mutabillity, yang artinya kita bisa menentukan apakah nilai dari suatu variabel itu dapat diubah atau tidak.

Untuk membuat variabel di rust kita bisa menggunakan keyword `let`, contoh:

``` rust
let a = 5;
```

Dengan code diatas kita barusaja mebuat `immutable variabel` yang artinya nilai dari variabel itu tidak dapat diubah setelahnya, sebagai contoh ketika kita mengubah nilainya

``` rust
let a = 5;
a = 1;
```

Ketika dicompile akan menghasilkan pesan error `cannot assign twice to immutable variable 'a'`, lalu bagaimana kalau kita ingin membuat variabel yang dapat diubah nilainya?, kita cukup menambahkan keyword `mut` sebelum nama variabel, contoh :

``` rust
let mut a = 5;
```

Code diatas menunjukan kita telah membuat `mutable variabel a` yang mana kita dapat mengubah nilai dari variabel setelahnya. 

Perbedaan variabel immutable dengan constant, constant secara default itu immutable dan tidak bisa diubah ke mutable

### Shadowing

Di rust kita bisa mendeklarasikan variabel baru dengan nama variabel sebelumnya, contoh :

``` rust
fn main() {
	let a = 3;
	let a = a * 3;
    
    println!("value of a {}", a);
}
```

Hasil dari code diatas adalah 9. Shadowing berbeda dengan mutable variabel, karna kita akan mendapat error saat compilasi bila kita tidak menggunakan keyword `let`. Perbedaan lain dengan mutable variabel, dengan shadowing kita dapat membuat variabel baru secara efektif, kita juga dapat mengubah nilai dari variabel dengan menggunakan kembali nama yang sama, contoh :

``` rust
let name = "chandra";
let name = name.len();
```

Code di atas variabel name sekarang bernilai 7, lalu kita coba menggunakan mut agar telihat perbedaan mutable varabel dengan shadowing

``` rust
let mut name = "chandra";
name = name.len();
```

Dari code diatas kita akan mendapatkan error :

``` bash
error[E0308]: mismatched types
 --> main.rs:3:12
  |
3 |     name = name.len();
  |            ^^^^^^^^^^ expected `&str`, found `usize`
```

