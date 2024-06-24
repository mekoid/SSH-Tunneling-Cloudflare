# SSH Tunneling Cloudflare
Ini merupakan repositories untuk menyimpan cara akses server dengan ssh yang ditunneling dengan zero trust cloudflare, bisa menjadi salah satu solusi remote server tanpa harus memiliki atau menyewa IP public. 

## Konfigurasi Public Hostname
<image src='./images/hostname.png' width='100%'>
Untuk konfigurasi hostname page sesuai diatas, jangan lupa untuk url bisa disesuikan dengan apa yang bisa diakses di localhost. sebagai contoh disini ssh saya aktif di localhost port 22.

## Remote Via Windows
<image src='./images/windowspathssh.png' width='100%'>

Masuk  ke file explorer langsung aja ke path `C:\Users\(userprofile)\.ssh`. Lalu tambahkan file _config(tanpa ekstensi apapun)_ . 

<image src='./images/configwindows.png' width='100%'>  

Buka file `config` dengan kode editor kalian lalu masukan command seperti diatas.

````
Host ssh.itsenja.my.id
ProxyCommand cloudflared access ssh --hostname %h 
````
Jangan lupa rubah `Host` domain nya sesuikan dengan domain yang kalian punya.

<image src='./images/windowssshacces.png' width='100%'>

Setelah selesai jangan lupa untuk mencoba koneksi ssh nya. Masukkan command ssh `hostname@domainhost`, Jika berhasil itu menandakan konfigurasi berhasil dan jika gagal mungkin ada step yang terlewat.

## Remote Via Linux
<image src='./images/nanoconfig.png' width='100%'>

Login ke `root` terlebih dahulu, Lalu ketik perintah `nano ~/.ssh/config`. Setelah itu Tambahkan command seperti diatas.

```
Host ssh.itsenja.my.id
ProxyCommand /usr/local/bin/cloudflared access ssh --hostname %h
```
Jangan lupa rubah `Host` domain nya sesuikan dengan domain yang kalian punya, Setelah itu simpan file dengan perintah `CTRL + X + Y` lalu `enter`.

<image src='./images/linuxsshacces.png' width='100%'>

Setelah selesai jangan lupa untuk mencoba koneksi ssh nya. Masukkan command ssh `hostname@domainhost`, Jika berhasil itu menandakan konfigurasi berhasil dan jika gagal mungkin ada step yang terlewat.
