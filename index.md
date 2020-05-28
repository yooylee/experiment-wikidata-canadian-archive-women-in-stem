## Welcome to the Experiment Page with Wikidata

### Example 1 - Canadian GLAMs Institutions containing Archive of Women in STEM

Click the 🔴red map markers to see which GLAMs hold archival fonds!

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AMap%0ASELECT%20DISTINCT%20%3Fcoordinate%20%3Finstitution%20%3FinstitutionLabel%0AWHERE%0A%7B%0A%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%20%3Farchive%20wdt%3AP361%20wd%3AQ63647303.%0A%20%3Farchive%20wdt%3AP126%20%3Finstitution.%0A%20%3Finstitution%20wdt%3AP625%20%3Fcoordinate.%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

#### Methods
Using [Wikidata's query service](https://query.wikidata.org/), I used the following SPQRQL query to generate a map with GLAM institutions.
```
#defaultView:Map
SELECT DISTINCT ?coordinate ?institution ?institutionLabel
WHERE
{
 SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
 ?archive wdt:P361 wd:Q63647303.
 ?archive wdt:P126 ?institution.
 ?institution wdt:P625 ?coordinate.
}
```

### Example 2 - What is their occupation?

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ABubbleChart%20%0ASELECT%20DISTINCT%20%3FoccupationLabel%20(COUNT%20(%3Fwoman)%20as%20%3Fcount)%0AWHERE%0A%7B%0A%20%20%3Farchive%20wdt%3AP361%20wd%3AQ63647303.%0A%20%20%3Farchive%20wdt%3AP6241%20%3Fwoman.%0A%20%20%3Fwoman%20wdt%3AP106%20%3Foccupation.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%22.%20%7D%0A%7D%0AGROUP%20BY%20%3FoccupationLabel%0AORDER%20BY%20DESC%20(%3Fcount)" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

#### Methods
Using [Wikidata's query service](https://query.wikidata.org/), I used the following SPQRQL query to generate a bubble chart.
```
#defaultView:BubbleChart
SELECT DISTINCT ?occupationLabel (COUNT (?woman) as ?count)
WHERE
{
  ?archive wdt:P361 wd:Q63647303.
  ?archive wdt:P6241 ?woman.
  ?woman wdt:P106 ?occupation.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE]". }
}
GROUP BY ?occupationLabel
ORDER BY DESC (?count)
```

### Example 3 - Timeline

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3ATimeline%0ASELECT%20%3Fitem%20%3FitemLabel%20%3Fstartdate%0AWHERE%0A%7B%0A%20%20%3Fitem%20wdt%3AP361%20wd%3AQ63647303%20%3B%0A%20%20%20%20%20%20%20%20(wdt%3AP580%7Cwdt%3AP7103)%20%3Fstartdate%20.%0A%20%20%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22%20%7D%0A%7D%0A%20%20" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

#### Methods
Using [Wikidata's query service](https://query.wikidata.org/), I used the following SPQRQL query to generate timeline based on the start date of the archival fonds.

```
#defaultView:Timeline
SELECT ?item ?itemLabel ?startdate
WHERE
{
  ?item wdt:P361 wd:Q63647303 ;
        (wdt:P580|wdt:P7103) ?startdate .

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en" }
}
```
