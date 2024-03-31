
# Dice Roller Application (Aplikasi pelempar dadu)

by Arya Widia Putra / 5025201016

This project is based on Android Basics with Compose course by Android Developers.

<details>
    <summary>Versi Indonesia</summary>
    Pelemparan dadu adalah salah satu cara untuk mendapatkan angka secara acak. Dalam aplikasi Dice Roller ini, pelemparan dadu direpresentasikan dengan gambar dan tombol untuk melempar dadu. Project ini didasarkan pada Android Basics with Compose course oleh Android Developers.
</details>

## 1. Dokumentasi

- Programming language (bahasa): Kotlin (Android Studio dan Jetpack Compose)
- Goal (tujuan): Membuat aplikasi pelempar dadu yang dapat dimainkan oleh user.
- Full code (kode): [https://github.com/aryawidiap/HappyBirthday](https://github.com/aryawidiap/DiceRoller/)

### Code explanation

1. Fungsi logika utama dari aplikasi Dice Roller

    Logika utama aplikasi dan layout aplikasi terdapat di dalam fungsi ini.

    ``` kotlin
    @Composable
    fun DiceRollerWithImageAndButton(modifier: Modifier = Modifier){
        ...
    }
    ```

2. Membuat logika percabangan dari pelemparan dadu

   Variable `result` berfungsi untuk menyimpan angka yang dihasilkan secara acak saat pelemparan dadu. Dalam aplikasi ini, gambar akan digunakan untuk melambangkan angka yang didapatkan pada pelemparan dadu. Hal ini ditunjukkan dengan kode melalui variabel `imageResource` yang nilainya berubah sesuai dengan nilai `result` (menggunakan percabangan `when`). Nilai `imageResource` akan menjadi file gambar yang sesuai dengan `result`.

   ``` kotlin
    @Composable
    fun DiceRollerWithImageAndButton(modifier: Modifier = Modifier){
        var result by remember { mutableIntStateOf(1) }
        val imageResource = when(result) {
            1 -> R.drawable.dice_1
            2 -> R.drawable.dice_2
            3 -> R.drawable.dice_3
            4 -> R.drawable.dice_4
            5 -> R.drawable.dice_5
            else -> R.drawable.dice_6
        }
        ...
    }
    ```

3. Membuat layout dari aplikasi

    Nilai variabel `result` dan `imageResource` akan digunakan dan ditampilkan melalui kode yang menyertai. Fungsi *composable* `Column` berfungsi untuk menata agar komponen UI tertata berurutan secara vertikal. Argumen `horizontalAlignment = Alignment.CenterHorizontally` diteruskan ke fungsi `Column` untuk membuat konten di dalam komponen `Column` menjadi rata tengah.

    Terdapat tiga fungsi `composable` di dalam `Column`. `Image` berfungsi untuk menampilkan gambar dari dadu. `Spacer` berfungsi untuk memberikan jarak antara komponen `Image` dan `Button`. `Button` berfungsi untuk alat berinteraksi user dengan aplikasi. `Button` sendiri memiliki satu fungsi *composable* di dalamnya, `Text` yang berfungsi untuk menampilkan teks "Roll". Satu logika penting terdapat dalam potongan kode ini: Argumen `onClick` diteruskan ke `Button`. Argumen ini menunjukkan fungsi yang akan dipanggil saat tombol (`Button`) ditekan. Fungsi yang diberikan ke dalam argumen `onClick` di dalam kode ini adalah `result = (1..6).random()`, yang berarti `result` akan diberikan nilai acak (`random`) yang terdapat pada rentang 1 sampai 6.

    ``` kotlin
    @Composable
    fun DiceRollerWithImageAndButton(modifier: Modifier = Modifier){
        ...
        Column(
            modifier = modifier,
            horizontalAlignment = Alignment.CenterHorizontally
        ) {
            Image(painter = painterResource(id = imageResource), contentDescription = result.toString())
            Spacer(modifier = Modifier.height(16.dp))
            Button(onClick = { result = (1..6).random() }) {
                Text(text = stringResource(R.string.roll))
            }
        }
    }
    ```

4. Fungsi untuk penampilan pada perangkat dan kelas utama

    Fungsi *composable* `DiceRollerApp` mengatur tampilan aplikasi dengan meneruskan argumen `modifier = Modifier.fillMaxSize().wrapContentSize(Alignment.Center))` ke `DiceRollerWithImageAndButton` untuk membuat tampilan memenuhi layar perangkat dan membuat konten rata tengah.

    ``` kotlin
    @Preview(showBackground = true)
    @Composable
    fun DiceRollerApp(){
        DiceRollerWithImageAndButton(modifier = Modifier
            .fillMaxSize()
            .wrapContentSize(Alignment.Center)
        )
    }
    ```

    Akhirnya, fungsi `onCreate` dari kelas `MainActivity` memanggil `DiceRollerApp` sebagai fungsi utama untuk menjalankan aplikasi.

    ``` kotlin
    class MainActivity : ComponentActivity() {
        override fun onCreate(savedInstanceState: Bundle?) {
            super.onCreate(savedInstanceState)
            setContent {
                DiceRollerTheme {
                    DiceRollerApp()
                }
            }
        }
    }
    ```

## 2. User interface (Tampilan UI)

![Die with number 1 on top](https://github.com/aryawidiap/DiceRoller/blob/main/resources/img/dice-roller-1.JPG)
*User interface for a die with number 1 on top*

![Die with number 2 on top](https://github.com/aryawidiap/DiceRoller/blob/main/resources/img/dice-roller-2.JPG)
*User interface for a die with number 2 on top*

![Die with number 3 on top](https://github.com/aryawidiap/DiceRoller/blob/main/resources/img/dice-roller-3.JPG)
*User interface for a die with number 3 on top*

![Die with number 4 on top](https://github.com/aryawidiap/DiceRoller/blob/main/resources/img/dice-roller-4.JPG)
*User interface for a die with number 4 on top*

![Die with number 5 on top](https://github.com/aryawidiap/DiceRoller/blob/main/resources/img/dice-roller-5.JPG)
*User interface for a die with number 5 on top*

![Die with number 6 on top](https://github.com/aryawidiap/DiceRoller/blob/main/resources/img/dice-roller-6.JPG)
*User interface for a die with number 6 on top*

## 3. Demonstration video (video demonstrasi)

<iframe width="560" height="315" src="https://www.youtube.com/embed/Vg9MJ22xm0M?si=AWnqj2XCt9JJw-l2" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 4. Reference (referensi)

[https://developer.android.com/codelabs/basic-android-kotlin-compose-text-composables?hl=id#0](https://developer.android.com/codelabs/basic-android-kotlin-compose-build-a-dice-roller-app?hl=id)
