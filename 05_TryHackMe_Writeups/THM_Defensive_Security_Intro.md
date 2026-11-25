# TryHackMe: Defensive Security Intro
**Modül:** Pre-Security / Savunma (Blue Team) Temelleri  
**Kapsam:** SOC Analizi, Saldırı Tespiti (Detection) ve Müdahale (Mitigation)

---

## 1. Temel Mantık: Bir Savunucu (Defender) Ne Yapar?
- **Asıl Görev:** Sistemleri izlemek, anormal/şüpheli trafiği tespit etmek (**Investigate**) ve saldırganı durdurmaktır (**Stop**).
- **Kritik Kural:** Savunucu asla karşı saldırı yapmaz ("Hack back" yasalara aykırıdır). Yalnızca sistem güvenliğini sağlar ve açığı kapatır.

---

## 2. Tespit Süreci (Investigation)
Saldırganlar web sitelerinde gizli dizinleri bulmak için tarama yaptığında arkalarında log bırakırlar.
- **SIEM / SOC Paneli:** Anormal sayıda gelen istekleri fark edip analiste **Critical Alert** (Kritik Uyarı) üretir.
- **Kaynak IP (Source IP):** Saldırının hangi IP adresinden geldiği loglardan tespit edilir (Örn: `32.122.195.63`).
- **Hedef Analizi (Path Enumeration):** Saldırganın sırayla hangi URL'leri yokladığı incelenir (Örn: `/backup`, `/login`, `/admin`).

---

## 3. Müdahale ve Engelleme Adımları (Response & Mitigation)
Gerçek dünyada bir web saldırısı tespit edildiğinde 3 temel savunma kalkanı devreye alınır:

1. **IP Engelleme (Block the Attacker / Firewall):**
   - Saldırganın IP adresi ağ güvenlik duvarı (Firewall) üzerinden engellenir, sunucuya erişimi tamamen kesilir.
2. **Hız Sınırlama (Rate Limiting / Slow Requests):**
   - Belirli bir IP'den gelen saniyelik istek sayısı sınırlandırılır. Saldırganın kaba kuvvet (brute-force) veya dizin tarama araçları (`dirb`, `gobuster`) çalışamaz hale gelir.
3. **Web Uygulama Güvenlik Duvarı (WAF - Turn on Protection):**
   - Web trafiğini filtreleyerek bilinen saldırı desenlerini ve otomatik tarama araçlarını kapıda durdurur.
