Build done, get customer by customer id has a random long (50%) and short delay (50%) to a 3rd party service to retrieve enriched data. Metric: get.3rdPartyEnrichCustomerService.v3

# Database problems?

- Endpoint POST /customers
- Simuleren trage database? Elke keer als we een customer toevoegen duurt het lang voor de database update (Thread.sleep, DBMS.sleep() ?)
- Meerdere calls doen naar andere versie van het endpoint die vertraging heeft, hoe maak je dit duidelijk? Downdrillen naar hikaricp metrics om zichtbaar te maken waar het probleem zit
-- Eerste laag=>basketitem call wordt traag
-- Tweede laag=>transactie met hikariCP duurt lang?