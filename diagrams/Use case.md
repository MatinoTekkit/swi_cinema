# Use case 

![Use case diagram](Use%20case.svg)

---

## View Screenings

**Aktér:**

- Uživatel

**Cíl:** Zobrazit uživateli seznam dostupných promítání.

### Hlavní scénář

1. Uživatel si vyžádá seznam promítání.
2. Systém načte promítání.
3. Systém zobrazí uživateli seznam promítání.

---

## View Reservations

**Aktér:**

- Uživatel

**Cíl:** Zobrazit uživateli seznam dostupných rezervací.

**Předpoklady:**

- Uživatel je přihlášen.

### Hlavní scénář

1. Uživatel si vyžádá seznam svých rezervací.
2. Systém načte rezervace.
3. Systém zobrazí uživateli seznam rezervací.

---

## Create Reservation

**Aktér:**

- Uživatel

**Cíl:** Zarezervovat si místo.

**Předpoklady:**

- Uživatel je přihlášen.

### Hlavní scénář

1. Uživatel vybere promítání.
2. Uživatel vybere sedadlo.
3. Systém ověří, že sedadlo je `FREE`.
4. Systém nastaví sedadlo na `PENDING`.
5. Systém zobrazí uživateli výsledek rezervace.

### Alternativní scénaře

**4a. Sedadlo je `PENDING` déle než 5 minut**

1. Systém nastaví sedadlo znovu na `PENDING` pro nového uživatele.
2. Systém vynuluje časovač.
3. Pokračuje se krokem 5.

**4b. Sedadlo je `PENDING` méně než 5 minut**

1. Systém rezervaci zamítne.
2. Pokračuje se krokem 5.

**4c. Sedadlo je `RESERVED`**

1. Systém rezervaci zamítne.
2. Pokračuje se krokem 5.

---

## Pay Reservation

**Aktér:**

- Uživatel

**Cíl:** Zaplatit rezervaci, aby se sedadlo potvrdilo.

**Předpoklady:**

- Uživatel je přihlášen.

### Hlavní scénář

1. Uživatel vybere rezervaci.
2. Uživatel požádá o platbu.
3. Systém ověří, že rezervace existuje.
4. Systém ověří, že rezervace je ve stavu `PENDING`.
5. Systém ověří, že rezervace nevypršela.
6. Systém zpracuje platbu.
7. Platba je úspěšná a systém potvrdí rezervaci.
8. Systém nastaví sedadlo na `RESERVED`.
9. Systém zobrazí uživateli výsledek platby.

### Alternativní scénaře

**3a. Rezervace neexistuje**

1. Systém platbu zamítne.
2. Pokračuje se krokem 9.

**4a. Rezervace není ve stavu `PENDING`**

1. Systém platbu zamítne.
2. Pokračuje se krokem 9.

**5a. Rezervace vypršela**

1. Systém zruší rezervaci.
2. Systém nastaví sedadlo na `FREE`.
3. Systém platbu zamítne.
4. Pokračuje se krokem 9.

**7a. Platba selhala**

1. Systém platbu zamítne.
2. Pokračuje se krokem 9.

---

## Cancel Reservation

**Aktér:**

- Uživatel

**Cíl:** Zrušit stávající rezervaci.

**Předpoklady:**

- Uživatel je přihlášen.

### Hlavní scénář

1. Uživatel vybere rezervaci.
2. Uživatel požádá o zrušení rezervace.
3. Systém ověří, že rezervace existuje.
4. Systém ověří, že rezervaci lze zrušit.
5. Systém zruší rezervaci.
6. Systém nastaví sedadlo na `FREE`.
7. Systém zobrazí uživateli výsledek zrušení.

### Alternativní scénaře

**3a. Rezervace neexistuje**

1. Systém zrušení zamítne.
2. Pokračuje se krokem 7.

**4a. Rezervaci nelze zrušit**

1. Systém zrušení zamítne.
2. Pokračuje se krokem 7.

---

## Manage Reservations

**Aktér:**

- Admin

**Cíl:** Umožnit adminovi prohlížet rezervace a rušit je.

### Hlavní scénář

1. Admin si vyžádá seznam rezervací.
2. Systém načte rezervace.
3. Systém zobrazí adminovi seznam rezervací.
4. Admin vybere rezervaci.
5. Admin požádá o zrušení rezervace.
6. Systém ověří, že rezervace existuje.
7. Systém zruší rezervaci.
8. Systém nastaví sedadlo na `FREE`.
9. Systém zobrazí adminovi výsledek zrušení.

### Alternativní scénaře

**7a. Rezervace neexistuje**

1. Systém zrušení zamítne.
2. Pokračuje se krokem 9.
