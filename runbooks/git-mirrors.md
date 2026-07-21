# Mirrory repozytoriów Git

## Cel

Repozytoria z GitHub są dodatkowo przechowywane jako mirrory bare w `tank/git` na hoście `homelab`.

## Dodanie nowego mirrora

Na HomeLab:

```bash
cd /tank/git
git clone --mirror https://github.com/OWNER/REPO.git REPO.git
```

Sprawdzenie:

```bash
git --git-dir=/tank/git/REPO.git remote -v
git --git-dir=/tank/git/REPO.git show-ref --head
```

## Aktualizacja mirrora z GitHub

```bash
git --git-dir=/tank/git/REPO.git remote update --prune
```

## Wypchnięcie lokalnego repozytorium do GitHub i mirrora

W zwykłym klonie roboczym:

```bash
git status
git push origin main
git push homelab main
```

Remote `homelab` powinien wskazywać repozytorium bare, np.:

```bash
git remote add homelab cloud@192.168.100.22:/tank/git/REPO.git
```

## Kontrola spójności

```bash
git ls-remote origin refs/heads/main
git ls-remote homelab refs/heads/main
```

SHA gałęzi `main` powinny być zgodne.

## Uwagi

Mirror Git nie zastępuje backupu off-site ani snapshotów. Chroni przed utratą pojedynczego serwisu lub przypadkowym usunięciem repozytorium, ale wymaga okresowej kontroli i kopii poza lokalizacją.