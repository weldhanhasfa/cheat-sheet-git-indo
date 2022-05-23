GIT Cheat Sheet Indonesia
===
<hr>
  <p align="center">
    <img alt="Git" src="./img/git-logo.png" height="190" width="455">
</p>
<hr>

## Konfigurasi Git

Tampilkan konfigurasi saat ini:
```
git config --list
```
Tampilkan konfigurasi repository:
```
git config --local --list
```

Tampilkan konfigurasi global:
```
git config --global --list
```

Tampilkan konfigurasi sistem:
```
git config --system --list
```

Tetapkan nama untuk meninjau riwayat versi:
```
git config --global user.name "[nama]"
```

Tetapkan alamat email yang akan dikaitkan dengan setiap penanda riwayat:
```
git config --global user.email "[email]"
```

Setel otomatis pewarnaan baris perintah untuk Git agar mudah ditinjau:
```
git config --global color.ui auto
```


<hr>

## Membuat Repository

Klon repository yang sudah ada:

Via SSH

```
git clone ssh://user@domain.com/repo.git
```

Via HTTP

```
git clone http://domain.com/user/repo.git
```

Buat repository local baru di direktori saat ini:
```
git init
```

Buat repository local baru di direktori tertentu:
```
git init <folder>
```

<hr>

## Perubahan Local
Perubahan dalam direktori saat ini:
```
git status
```

Perubahan/perbedaan pada direktori saat ini:
```
git diff
```

Lihat perubahan/perbedaan dari file tertentu:
```
git diff <file>
```

Tambah semua perubahan saat ini ke commit berikutnya:
```
git add .
```

Tambahkan beberapa perubahan di &lt;file&gt; ke commit berikutnya:
```
git add -p <file>
```

Tambahkan hanya file yang disebutkan ke commit berikutnya:
```
git add <namafile1> <namafile2>
```

Commit semua perubahan local di direktori saat ini :
```
git commit -a
```

Commit perubahan yang telah dilakukan sebelumnya:
```
git commit
```

Commit dengan pesan:
```
git commit -m 'pesannya'
```

Ubah commit terakhir:<br>
<em><sub>Jangan mengubah commit yang telah dicommit sebelumnya</sub></em>

```
git commit -a --amend
```

Ubah dengan commit terakhir tetapi gunakan pesan log commit sebelumnya:<br>
<em><sub>Jangan mengubah commit yang telah dicommit sebelumnya</sub></em>

```shell
git commit --amend --no-edit
```

Ubah tanggal commit dari commit terakhir:
```
GIT_COMMITTER_DATE="tanggal" git commit --amend
```

Ubah tanggal Penulis dari commit terakhir:
```shell
git commit --amend --date="tanggal"
```

Pindahkan perubahan yang tidak dicommit dari branch saat ini ke branch lain:<br>
```
git stash
```
```
git checkout branch2
```
```
git stash pop
```

Mengembalikan perubahan stash kembali ke branch saat ini:
```shell
git stash apply
```

Mengembalikan stash tertentu kembali ke branch saat ini:
- *{nomor_stash}* dapat diperoleh dari `git stash list`

```shell
git stash apply stash@{nomor_stash}
```

Hapus kumpulan perubahan stash terakhir:
```
git stash drop
```

<hr>

## Riwayat Commit

Tampilkan semua Commit, dimulai dengan yang terbaru:
```
git log
```

Tampilkan semua Commit tetapi hanya akan menampilkan hash Commit dan pesan Commit:
```
git log --oneline
```

Tampilkan semua Commit dari pengguna tertentu:
```
git log --author="username"
```

Tampilkan perubahan dari waktu ke waktu dari file tertentu:
```
git log -p <file>
```

Tampilkan commit yang hanya ada di remote/branch di sisi kanan
```
git log --oneline <origin/master>..<remote/master> --left-right
```

Siapa yang Merubah, apa dan kapan dalam &lt;file&gt;:
```
git blame <file>
```

Tampilkan Referensi log:
```
git reflog show
```

Hapus Referensi log:
```
git reflog delete
```
<hr>

## Update & Publish

Daftar semua remote yang dikonfigurasi saat ini:
```
git remote -v
```

Tampilkan informasi tentang remote:
```
git remote show <remote>
```

Tambahkan repository remote baru:
```
git remote add <remote> <url>
```

Ganti nama repository remote:
```
git remote rename <remote> <remote_baru>
```

Hapus remote:
```
git remote rm <remote>
```

<em><sub> Catatan: git remote rm tidak menghapus repository Remote dari server. Ini hanya menghapus remote dan referensinya dari repository local</sub></em>

Unduh semua perubahan dari remote, tetapi tidak di integrasikan ke HEAD:
```
git fetch <remote>
```

Unduh perubahan dan langsung gabungkan/integrasikan ke HEAD:
```
git remote pull <remote> <url>
```

Dapatkan semua perubahan dari HEAD ke repository local:
```
git pull origin master
```

Dapatkan semua perubahan dari HEAD ke repository local tanpa penggabungan:
```
git pull --rebase <remote> <branch>
```

Publish perubahan local pada remote:
```
git push <remote> <branch>
```

Hapus branch pada remote:
```
git push <remote> --delete <branch>
```

<hr>

## Branch

Daftar semua branch local:
```
git branch
```

Daftar branch local/remote
```
git branch -a
```

Daftar semua branch remote:
```
git branch -r
```

Beralih branch:
```
git checkout <branch>
```

Periksa satu file dari branch yang berbeda:
```
git checkout <branch> -- <namafile>
```

Buat dan pindah branch baru:
```
git checkout -b <branch>
```

Beralih ke branch sebelumnya, tanpa menyebutkan nama branchnya:
```
git checkout -
```

Buat branch baru dari branch yang ada dan pindah ke branch baru:
```
git checkout -b <branch_baru> <branch_sekarang>
```

Checkout dan buat branch baru dari commit yang ada:
```
git checkout <commit-hash> -b <branch-baru>
```

Buat branch baru berdasarkan HEAD saat ini:
```
git branch <branch-baru>
```

Buat branch pelacakan baru berdasarkan branch remote:
```
git branch --track <branch-baru> <remote-branch>
```

Hapus branch local:
```
git branch -d <branch>
```

Ganti nama branch saat ini menjadi nama branch baru
```shell
git branch -m <nama_branch_baru>
```

Hapus paksa branch local:<br>
<em><sub>Akan kehilangan perubahan yang tidak digabungkan!</sub></em>

```
git branch -D <branch>
```

<hr>

## Merge & Rebase

Gabungkan branch ke HEAD saat ini:
```
git merge <branch>
```

Daftarkan branch yang digabungkan:
```
git branch --merged
```

Rebase HEAD saat ini ke branch yang di tuju:<br>
<em><sub>Jangan rebase commit yang diterbitkan!</sub></em>

```
git rebase <branch>
```

Batalkan Rebase:
```
git rebase --abort
```

Lanjutkan rebase setelah menyelesaikan konflik:
```
git rebase --continue
```

Gunakan IDE untuk menyelesaikan konflik secara manual dan setelah menyelesaikannya tandai file sebagai Resolved:
```
git add <nama-file-resolve>
```

```
git rm <nama-file-resolve>
```

<hr>

## Undo

Buang semua perubahan local di direktori saat ini:
```
git reset --hard HEAD
```

Keluarkan semua file dari staging area, yaitu membatalkan `git add` terakhir:
```
git reset HEAD
```

Buang perubahan local dalam file tertentu:
```
git checkout HEAD <file>
```

Kembalikan Commit, dengan membuat Commit baru dengan perubahan sebaliknya:
```
git revert <commit>
```

Atur ulang penunjuk HEAD ke commit sebelumnya dan buang semua perubahan sejak saat itu:
```
git reset --hard <commit>
```

Setel ulang penunjuk HEAD ke a status branch remote saat ini.
```
git reset --hard <remote/branch>
```

Atur ulang penunjuk HEAD ke Commit sebelumnya dan simpan semua perubahan sebagai perubahan yang tidak bertahap:
```
git reset <commit>
```

Atur ulang penunjuk HEAD ke Commit sebelumnya dan pertahankan perubahan local yang tidak di Commit:
```
git reset --keep <commit>
```

Hapus file yang tidak sengaja dibuat sebelum ditambahkan ke .gitignore
```
git rm -r --cached .
```

```
git add .
```

```
git commit -m "hapus file namafile"
```
<hr>