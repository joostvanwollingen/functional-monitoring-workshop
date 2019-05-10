Build not done, don't know how, get customer by customer id

# Database problems?

- Endpoint POST /customers
- Simuleren trage database? Elke keer als we een customer toevoegen duurt het lang voor de database update (Thread.sleep, DBMS.sleep() ?)
- Meerdere calls doen naar andere versie van het endpoint die vertraging heeft, hoe maak je dit duidelijk? Downdrillen naar hikaricp metrics om zichtbaar te maken waar het probleem zit
-- Eerste laag=>basketitem call wordt traag
-- Tweede laag=>transactie met hikariCP duurt lang?