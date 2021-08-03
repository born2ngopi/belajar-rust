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

## Data types

### Scalar types

Rust memiliki 4 jenis tipe scalar: integer, float, boolean, dan character

#### Integer

Seperti bahasa pemrograman lainnya integer adalah tipe data bilangan bulat

| Length  | Signed  | Unsigned |
| ------- | ------- | -------- |
| 8-bit   | `i8`    | `u8`     |
| 16-bit  | `i16`   | `u16`    |
| 32-bit  | `i32`   | `u32`    |
| 64-bit  | `i64`   | `u64`    |
| 128-bit | `i128`  | `u128`   |
| arch    | `isize` | `usize`  |

contoh

``` rust
let a: i8 = 10;
```

#### Float

Float adalah tipe data bilangan decimal. Di rust float ada dua, yaitu 32bit `f32` dan 64bit `f64`. Secara default bila kita tidak menentukan tipe data bilangan decimal pada saat membuat variabel rust akan secara otomatis menerjemahkannya ke 64bit, contoh

``` rust
let a = 6.7; // 64 bit
let b: f32 = 6.7 // 32 bit
```

##### Numeric operation

Seperti bahasa pemrograman lain, di rust juga terdapat beberapa operasi bilangan seperti penjumlahan, pengurangan, pembagian, perkalian, dan modulo

``` rust
	// penambahan
	let sum = 5 + 10;

    // pengurangan
    let difference = 95.5 - 4.3;

    // perkalian
    let product = 4 * 30;

    // pembagian
    let quotient = 56.7 / 32.2;

    // modulo
    let remainder = 43 % 5;
```



#### Boolean

Type data ini hanya terdiri dari 2 value, yaitu `true` dan `false`. Contoh :

``` rust
let a = true;

let b: bool = false;
```



#### Character

**Tipe data character** merupakan salah satu **tipe data** yang memungkinkan kita untuk memesan memori berformat text (huruf, angka, dan simbol) dengan karakter tunggal. Contoh

``` rust
let rune = 'C';
let emoji = '😻';
```

### Compound type

Compound type dapat mengelompokan banyak nilai kedalam satu type. Di rust memiliki 2 jenis compound type yaitu tuples dan array.

#### Tuples

tuple adalah cara umum untuk mengelompokan beberapa nilai dengan berbagai type. contoh

``` rust
let tup: (i8, f32) = (10, 3.8);
```

kita bisa mengakses spesifik nilainya dengan menggunakan index posisinya, contoh

``` rust
let ten = x.0; // ten == 10

let double = x.1; // double == 3.8
```

#### Array

**Array** merupakan tipe data terstruktur **dalam pemrograman**, **array** memungkinkan untuk menyimpan data maupun referensi objek **dalam** jumlah banyak dan terindeks. Berbeda dengan tuples yang dapat menyimpan banyak nilai dengan tipe data berbeda, array dapat menyimpan banyak nilai **tetapi** dengan tipe data yang sama. Contoh

``` rust
let a = [1,2,3,4,5];
```

Kita juga dapat menentukan panjang atau kapasitas dari array

``` rust
let a: [u8, 5] = [1,2,3,4,5];
```



## Function

Fungsi adalah sub-program yang bisa digunakan kembali baik di dalam program itu sendiri, maupun di program yang lain. keyword untuk mendeklarasikan fungsi di rust adalah `fn` contoh

``` rust
fn main() {
    print_hallo();
}

fn print_hallo() {
    println!{"hallo"};
}
```

Pada contoh code diatas, fungsi main merupakan fungsi yang pertama kali akan dijalankan saat program pertama kali dijalankan. di rust bila kita membuat fungsi atau variabel yang menggunakan lebih dari 2 kata itu menggunakan snake case (ex : `print_hallo`) dan tidak menggunakan camel case (ex : `printHallo`). Kita juga dapat mengirim suatu nilai kedalam fungsi, contoh

``` rust
fn main() {
    let age: i32 = 21;
    
    print_age(age);
}

fn print_age(age: i32) {
    println!{"my age is {}", age};
}
```

fungsi juga dapat mengembalikan nilai, contoh :

``` rust
fn main() {
    let number = get_number();
    
    println!{"number is {}", number};
}

fn get_number() -> i32 {
    return 6 
    // atau bisa juga ditulis 6 tanpa keyword `return`
}
```

