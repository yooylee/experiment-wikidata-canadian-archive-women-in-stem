## Welcome to the Experiment Page with Wikidata

### Example 1 - Canadian GLAMs Institutions containing Archive of Women in STEM

Click the 🔴red map markers to see which GLAMs hold archival fonds!

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AMap%0ASELECT%20%3Fcoordinate%20%3Finstitution%20%3Finstitution_label%0AWHERE%20%0A%7B%0A%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%20%3Farchive%20wdt%3AP361%20wd%3AQ63647303.%0A%20%3Farchive%20wdt%3AP126%20%3Finstitution.%0A%20%3Finstitution%20wdt%3AP625%20%3Fcoordinate.%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

#### Methods
Using [Wikidata's query service](https://query.wikidata.org/), I used the following SPQRQL query to generate a map with GLAM institutions.
```
#defaultView:Map
SELECT ?coordinate ?institution ?institution_label
WHERE
{
 SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
 ?archive wdt:P361 wd:Q63647303.
 ?archive wdt:P126 ?institution.
 ?institution wdt:P625 ?coordinate.
}
```
