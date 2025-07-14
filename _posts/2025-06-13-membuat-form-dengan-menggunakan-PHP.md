---
layout: post
title: "membuat form dengan menggunakan PHP"
---

membuat form dengan menggunakan_PHP



13 jun 2025 Pada praktikum 8 membuat sebuah form pendaftaran menggunakan bahasa PHP

Berikut Langkah-langkahnya:
1. pertama, masuk ke folder xampp 
2. Kemudian, buat sebuah folder dengan nama"latihan"
3. buatlah file php dengan nama "koneksi.php" dan isi file tersebut.
4. kemudian masuk ke terminal/cmd yang kamu gunakan  dan masuk ke folder mysql mu dengan cara:
    "mysqll -uroot -p"

1. Setelah berhasil masuk ke mysql,buat form dengan nama"latihan" dengan cara:
    "CREATE DATABASE latihan;"

2. Kemudian isi
    USE latihan;(untuk masuk ke folder form)

3. Kemudian buat tabel siswa dengan cara berikut:
    create table siswa ( id int auto_increment primary key, nama varchar(100), alamt varchar(200), jenis_kelamin tinyint(1), agama varchar(20), sekolah_asal varchar(50));

4. setelah itu,buat file baru dengan nama "create.php" dan isi kode berikut:
    <?php

    include "koneksi.php";

    $nama = $_POST['nama'];
    $alamat = $_POST['alamat'];
    $jenis_kelamin = $_POST['jenis_kelamin'];
    $agama = $_POST['agama'];
    $sekolah_asal = $_POST['sekolah_asal'];

    $sql = "INSERT INTO siswa (nama, alamat, jenis_kelamin, agama, sekolah_asal) VALUES ('$nama', '$alamat', '$jenis_kelamin', '$agama', '$sekolah_asal')";

    if (mysqli_query($koneksi, $sql)) {
        header("location: list-siswa.php");
    } else {
        echo "Error: " . $sql . "<br>" . mysqli_error($koneksi);
    }

    ?>

5. Buat lagi file baru dengan nama "delete.form" dan isi kode berikut:
    <?php

    include 'koneksi.php';

    $id = $_POST['id'];

    $sql = "DELETE FROM siswa WHERE id='$id'";

    if (mysqli_query($koneksi, $sql)) {
        header("location: list-siswa.php");
    } else {
        echo "Error: " . $sql . "<br>" . mysqli_error($koneksi);
    }

6. Lanjut buat file lagi dengan nama"form-daftar.php" dan isi kode berikut:
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>Form Pendaftaran Siswa Baru | Digital Talent</title>
    </head>
    <body>
        <h2>Formulir Pendaftaran Siswa Baru</h2>
        <form action="create.php" method="POST">
            <table>
                <tr>
                    <td>Nama</td>
                    <td>:</td>
                    <td><input type="text" name="nama"></td>
                </tr>
                <tr>
                    <td>Alamat</td>
                    <td>:</td>
                    <td><textarea name="alamat"></textarea></td>
                </tr>
                <tr>
                    <td>Jenis Kelamin</td>
                    <td>:</td>
                    <td>
                        <input type="radio" name="jenis_kelamin" value="1"> Laki-laki
                        <input type="radio" name="jenis_kelamin" value="0"> Perempuan
                    </td>
                </tr>
                <tr>
                    <td>Agama</td>
                    <td>:</td>
                    <td>
                        <select name="agama">
                            <option>--Pilih Agama--</option>
                            <option>Islam</option>
                            <option>Kristen</option>
                            <option>Hindu</option>
                            <option>Budha</option>
                        </select>
                    </td>
                </tr>
                <tr>
                    <td>Sekolah Asal</td>
                    <td>:</td>
                    <td><input type="text" name="sekolah_asal"> <br/></td>
                </tr>
                <tr>
                    <td colspan="2">
                    <td>
                        <button type="submit">Daftar</button>
                        <a href="index.php">Batal</a>
                    </td>
                </tr>
            </table>
        </form>
    </body>
    </html>

7. Kemudian buat file baru lagi dengan "form-delete.php" dan isi kode:
    <doctype html>
    <html>
    <head>
    <meta charset="utf-8">
    <title>Form Hapus Siswa</title>
    </head>
    <body>
    <?php
    include "koneksi.php";
    $id = $_GET['id'];
    $sql = "SELECT * FROM siswa WHERE id=$id";
    $result = mysqli_query($koneksi, $sql);
    $row = mysqli_fetch_assoc($result);
    ?>
    <h2>Apakah Anda yakin akan menghapus data berikut?</h2>
    <form action="delete.php" method="POST">
    <input type="hidden" name="id" value="<?php echo $row['id']?>"> Nama <?php echo $row['nama'] ?> <br/>
    Alamat: <?php echo $row['alamat'] ?> <br/>
    Jenis Kelamin :
    <?php
    if ($row['jenis kelamin'] == 1) {
    echo "Laki-laki";
    } else {
    }
    echo "Perempuan";
    ?> <br/>
    Agama <?php echo $row['agama'] ?> <br/>
    Sekolah Asal : <?php echo $row['sekolah_asal'] ?> <br/>
    <button type="submit">Ya</button>
    <a href="list-siswa.php">Tidak</a>
    </form>
    </body>
    </html>

8. kemudian lanjut buat file lagi dengan nama "form-edit.php" dan isi kode berikut:
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>Form Edit Siswa</title>
    </head>
    <body>
        <?php
            include "koneksi.php";
            $id = $_GET['id'];
            $sql = "SELECT * FROM siswa WHERE id=$id";
            $result = mysqli_query($koneksi, $sql);
            $row = mysqli_fetch_assoc($result);
        ?>

        <h2>Formulir Edit Siswa</h2>
        <form action="update.php" method="POST">
            <input type="hidden" name="id" value="<?php echo $row['id'] ?>">
            Nama :
            <input type="text" name="nama" value="<?php echo $row['nama'] ?>"><br/>
            Alamat :
            <textarea name="alamat">
                <?php echo $row['alamat'] ?>
            </textarea><br/>
            Jenis Kelamin :
            <input type="radio" name="jenis_kelamin" value="1" <?php if ($row['jenis_kelamin'] == 1) echo "checked" ?>>
            Laki-Laki
            <input type="radio" name="jenis_kelamin" value="0" <?php if ($row['jenis_kelamin'] == 0) echo "checked" ?>>
            Perempuan <br/>
            Agama :
            <select name="agama">
                <option>--Pilih Agama--</option>
                <option value="Islam">Islam</option>
                <option value="Kristen">Kristen</option>
                <option value="Hindu">Hindu</option>
                <option value="Budha">Budha</option>
            </select><br/>
            Sekolah Asal :
            <input type="text" name="sekolah_asal" value="<?php echo $row['sekolah_asal'] ?>"><br/>

            <br/>
            <button type="submit">Update</button>
            <a href="list-siswa.php">Batal</a>
        </form>
    </body>
    </html>

9. buat file lagi dengan nama"index.php" dan isi kode :
    <?php
    echo "<h2> Pendaftaran Siswa Baru</h2>
    <h1>Digital Talent</h1>
    <h3>Menu</h3>
    <ul>
    <li><a href='form-daftar.php'>Daftar Baru</a></li> <li><a href='list-siswa.php'>Pendaftaran</a></li> </ul>";
    ?>

10. terus buat file dengan nama"list-siswa.php" dan isi kode:
    <!DOCTYPE html>
    <html>
    <head>
        <title>Daftar Siswa</title>
    </head>
    <body>
        <h2>Siswa yang sudah mendaftar</h2>
        <ul>
            <li><a href="index.php">Home</a></li>
            <li><a href="form-daftar.php">[+] Tambah Baru</a></li>
        </ul>

        <?php
        include "koneksi.php";

        $sql = "SELECT * FROM siswa";
        $result = mysqli_query($koneksi, $sql);
        ?>
        <table border="1">
            <thead>
                <tr>
                    <th>No</th>
                    <th>Nama</th>
                    <th>Alamat</th>
                    <th>Jenis Kelamin</th>
                    <th>Agama</th>
                    <th>Sekolah Asal</th>
                    <th>Tindakan</th>
                </tr>
            </thead>
            <tbody>
                <?php
                $no = 1;
                while ($row = mysqli_fetch_assoc($result)) {
                ?>
                    <tr>
                        <td><?php echo $no++; ?></td>
                        <td><?php echo $row['nama']; ?></td>
                        <td><?php echo $row['alamat']; ?></td>
                        <td><?php
                            if ($row['jenis_kelamin'] == 1) {
                                echo "Laki-Laki";
                            } else {
                                echo "Perempuan";
                            }
                            ?></td>
                        <td><?php echo $row['agama']; ?></td>
                        <td><?php echo $row['sekolah_asal']; ?></td>
                        <td>
                            <a href="form-edit.php?id=<?php echo $row['id']; ?>">Edit</a>
                            <a href="form-delete.php?id=<?php echo $row['id']; ?>">Delete</a>
                        </td>
                    </tr>
                <?php
                }
                ?>
            </tbody>
        </table>
    </body>
    </html>

11. Dan menambahkan file baru lagi bernama "update.php" dan isi kode:
    <?php

    include "koneksi.php";

    $id = $_POST['id'];
    $nama = $_POST['nama'];
    $alamat = $_POST['alamat'];
    $jenis_kelamin = $_POST['jenis_kelamin'];
    $agama = $_POST['agama'];
    $sekolah_asal = $_POST['sekolah_asal'];

    $sql = "UPDATE siswa SET nama='$nama', alamat='$alamat', jenis_kelamin='$jenis_kelamin', 
    agama='$agama', sekolah_asal='$sekolah_asal' WHERE id=$id";

    if (mysqli_query($koneksi, $sql)) {
        header("location:list-siswa.php");
    } else {
        echo "Error updating record: " . mysqli_error($koneksi);
    }

    ?>

12. Dan terakhir yg terpenting adalah file yang bernama "koneksi.php" dengan code:
    <?php

    $host = 'localhost';
    $username = 'root';
    $password = '';
    $db_name = 'latihan';

    $koneksi = mysqli_connect($host, $username, $password, $db_name);
    if (!$koneksi) {
        echo("ada yg salah");
    }
    else {
        echo "Koneksi berhasil";
    }