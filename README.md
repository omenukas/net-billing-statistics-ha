# Net Billing Statistics for Home Assistant

![dashboard](dashboard.PNG)

Šis projektas skirtas pateikti išsamią „net billing“ elektros apskaitą Home Assistant aplinkoje:  
pirkimo, pardavimo, grynosios kainos, energijos balanso, mėnesio ir metinių suvestinių bei vizualizacijų pagrindu naudojant „ApexCharts“.

Projektas sukurtas taip, kad būtų lengvai diegiamas, paprastai prižiūrimas ir aiškiai suprantamas kiekvienam Home Assistant naudotojui, naudojančiam elektros apskaitą pagal biržos kainą (NordPool).

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

---

## 📁 Failų struktūra

Projekte pateikiami keturi pagrindiniai failai:

net-billing-statistics-ha/
├── 02_charging_prices.yaml # pagrindinis Home Assistant paketų failas
├── templates.yaml # NordPool kainų templat'ai (šiandien / rytoj / su PVM)
├── dashboard.yaml # Lovelace skydelio (Dashboard) kodas su visomis kortelėmis
├── Dashboard.png # pavyzdinė skydelio ekrano nuotrauka
└── README.md 
