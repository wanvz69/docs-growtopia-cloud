🎮 Player Callbacks

Semua callback yang berhubungan langsung dengan player (join, leave, chat, gems, dll).

---

onPlayerJoinCallback

Description:
Dipanggil saat player masuk ke server.

Parameters:

- player (Player)

Example:

onPlayerJoinCallback(function(player)
    print(player:getName() .. " joined the game")
end)

Notes:

- Cocok untuk init data player
- Bisa dipakai untuk welcome message / give item awal

---

onPlayerLeaveCallback

Description:
Dipanggil saat player keluar dari server.

Parameters:

- player (Player)

Example:

onPlayerLeaveCallback(function(player)
    print(player:getName() .. " left the game")
end)

Notes:

- Gunakan untuk save data
- Jangan taruh logic berat (biar ga delay disconnect)

---

onPlayerChatCallback

Description:
Dipanggil saat player mengirim chat.

Parameters:

- player (Player)
- message (string)

Example:

onPlayerChatCallback(function(player, message)
    if message == "!ping" then
        player:sendMessage("Pong!")
    end
end)

Notes:

- Bisa buat command system
- Hati-hati spam / exploit chat

---

onPlayerGemsObtainedCallback

Description:
Dipanggil saat player mendapatkan gems (pickup).

Parameters:

- world (World)
- player (Player)
- amount (number)

Example:

onPlayerGemsObtainedCallback(function(world, player, amount)
    local bonus = amount
    world:adjustGems(player, nil, bonus)
end)

Notes:

- Trigger saat pickup, bukan saat gems spawn di tile
- Kalau salah logic bisa jadi dupe / exploit

⚠️ Common Mistake:

- Menganggap ini trigger dari block break → salah
- Over-add gems tanpa limit → economy hancur

---

onPlayerDeathCallback

Description:
Dipanggil saat player mati.

Parameters:

- player (Player)

Example:

onPlayerDeathCallback(function(player)
    player:sendMessage("You died 💀")
end)

Notes:

- Bisa dipakai untuk penalty system
- Atau event PvP

---

onPlayerRespawnCallback

Description:
Dipanggil saat player respawn setelah mati.

Parameters:

- player (Player)

Example:

onPlayerRespawnCallback(function(player)
    player:sendMessage("Welcome back!")
end)

Notes:

- Cocok untuk reset state
- Bisa kasih buff setelah mati

---

onPlayerLevelUpCallback

Description:
Dipanggil saat player naik level.

Parameters:

- player (Player)
- level (number)

Example:

onPlayerLevelUpCallback(function(player, level)
    player:sendMessage("Level up! Now level " .. level)
end)

Notes:

- Cocok buat reward system
- Bisa unlock fitur tertentu

---

🧠 Tips Umum

- Jangan spam logic berat di callback → bisa lag server
- Selalu validasi input (terutama dari chat)
- Hindari duplikasi reward (exploit risk 🚨)
- Gunakan limit / cap untuk system ekonomi

---
