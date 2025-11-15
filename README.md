# Net Billing Statistics for Home Assistant

![dashboard](Dashboard.PNG)

Šis projektas skirtas pateikti „net billing“ elektros apskaitą Home Assistant aplinkoje:  
pirkimo, pardavimo, grynosios kainos, energijos balanso, mėnesio ir metinių suvestinių bei vizualizacijų pagrindu naudojant „ApexCharts“.

## SVARBU!!! 
Tai dar ne galutinė versija ir gali būti taisytinų vietų.

---

## 🧩 Savybės

- Apskaičiuoja **realias elektros pirkimo ir pardavimo kainas**, pridedant:
  - NordPool kainą
  - PVM (reguliuojama)
  - dedamąsias pirkimui ir pardavimui (reguliuojama)

- Automatiškai apskaičiuoja:
  - **pirkimo ir pardavimo galią (kW)**
  - **importo ir eksporto energiją (kWh)**
  - **pirkimo ir pardavimo kainą per valandą (€/h)**
  - **bendrą kainą (EUR)**: dienos, mėnesio, metų

- Rodo **dienos**, **mėnesio** ir **metų** grafikus, įskaitant:
  - valandinį suvartojimą / gamybą
  - dienų stulpelius per mėnesį
  - mėnesių stulpelius per metus
  - bendras šių laikotarpių sumas

- Išskiriami:
  - pirkimo kaštai
  - pardavimo pajamos
  - grynasis balansas (import – eksport)
  - pirkimo/pardavimo santykiai

- Suderinama su visais energijos skaitikliais, kurie:
  - importą rodo su **minuso ženklu**
  - eksportą rodo **be minuso**

## Diegimas
Home Assistant reikalavimai:
 - įdiegti [NordPool](https://www.home-assistant.io/integrations/nordpool/) integraciją.
 - iš HACS įdiegti [apexcharts-card](https://github.com/RomRider/apexcharts-card) 
 - NordPool kainų grafikui reikalingas `templates.yaml`, kuriame reikia dvejose vietose įrašyti savo `config_entry` reikšmes. Kaip gauti    `config_entry` reikšmes, rasite [čia:](https://www.creatingsmarthome.com/index.php/2025/09/12/home-assistant-migrating-to-the-official-nord-pool-integration/)
 - Statistikoms visi reikalingi sensoriai, helperiai ir templeitai sudėti į vieną `02_charging_prices.yaml`, kurį reikia įdėti į config/packages/ direktoriją. Jeigu dar nenaudojate /packages, tai šakninėje /config direktorijoje susikurkite `packages` direktoriją, į `configuration.yaml` įdėkite tokią eilutę:
 ```
homeassistant:
  packages: !include_dir_named packages

```
Nepamirškite yaml failuose pakoreguoti pagal save inverterio sensorius. Mano pateiktuose koduose naudojami inverterio sensoriai:
- 'sensor.solis_waveshare_meter_total_active_power`. Tai vienas sensorius, kurio teigiama reikšmė reiškia atidavimą į tinklą, o neigiama, kai perkama iš tinklo.
- `sensor.nord_pool_lt_current_price`. Patikrinkite ar jis tikrai toks pas jus ir pakeisti jį į savo sensorių.
Perkrauti Home Assistant.
- į `dahboard.yaml` sudėtos visos statistikos kortelės.

---

## 📁 Failų struktūra

Projekte pateikiami keturi pagrindiniai failai:
```
net-billing-statistics-ha/
├── 02_charging_prices.yaml # pagrindinis Home Assistant paketų failas
├── templates.yaml # NordPool kainų templat'ai (šiandien / rytoj / su PVM)
├── dashboard.yaml # Lovelace skydelio (Dashboard) kodas su visomis kortelėmis
├── Dashboard.png # pavyzdinė skydelio ekrano nuotrauka
└── README.md

```

<a href="https://buymeacoffee.com/omenukas">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="42">
</a>
