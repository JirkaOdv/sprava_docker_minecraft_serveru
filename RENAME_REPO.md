# Přejmenování GitHub Repozitáře na CraftControl

## Postup přejmenování

### 1. Jdi na GitHub repozitář
https://github.com/jiriodv/sprava_docker_minecraft_serveru

### 2. Otevři Settings
- Klikni na **Settings** (nahoře vpravo v menu repozitáře)

### 3. Přejmenuj repozitář
- Najdi sekci **Repository name** (úplně nahoře)
- Změň název z `sprava_docker_minecraft_serveru` na `craftcontrol`
- Klikni **Rename**

### 4. Aktualizuj lokální Git remote

Po přejmenování na GitHubu spusť:

```bash
cd /Users/jirka/Documents/Antigravity/Aplikace/mc_server
git remote set-url origin https://github.com/jiriodv/craftcontrol.git
```

## Hotovo! ✅

Nové URL repozitáře bude:
🔗 **https://github.com/jiriodv/craftcontrol**

GitHub automaticky přesměruje staré URL na nové, takže všechny existující odkazy budou fungovat!

---

## Bonus: Přejmenuj i lokální složku (volitelné)

Pokud chceš mít i lokální složku pojmenovanou správně:

```bash
cd /Users/jirka/Documents/Antigravity/Aplikace
mv mc_server craftcontrol
cd craftcontrol
```
