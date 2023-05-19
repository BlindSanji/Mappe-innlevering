# Innhente, analysere og presentere data med flask

Flask er et populært rammeverk for webutvikling i Python som kan brukes til å bygge applikasjoner som innhenter, analyserer og presenterer data. Med Flask kan man opprette API-endepunkter som tillater innhenting av data fra forskjellige kilder, som databasesystemer eller eksterne API-er. Deretter kan man bruke Flask og tilhørende biblioteker for å utføre analyser på dataen og generere visualiseringer eller rapporter som kan presenteres i nettleseren. Flask gir dermed et fleksibelt og kraftig verktøysett for å håndtere hele dataflyten fra innhenting til presentasjon.

## Eksempler
- Innhenting av data fra api
```python
# Importerer api
import imdb

ia = imdb.Cinemagoer()

# Rute i flask som henter input fra brukeren 'q' og bruker det for å søke etter filmer via 'GET' metoden
@app.route('/search', methods=['GET', 'POST'])
def search():
    q = request.args.get('q')

    if q:
        try:
            # Henter inn og gir variabel til resultatene
            results = ia.search_movie(q, results=20)
            return render_template('search.html', results=results, q=q)
        except Exception as e:
            print(e)
            flash("Sorry, an error ocurred while processing your request.", 'error')
            return redirect('home')
```
- Presentering av data
```html
<!-- Bruker resultatene fra søket og viser film-plakaten til filmene i resultatene. -->
{% for movie in results %}
<div>
    <img src="{{ movie['full-size cover url'] }}" alt="{{movie['title']}}">
</div>
{% endfor %}
```
- [Filmapp ruter fil](https://github.com/BlindSanji/movieapp/blob/main/project/routes.py)
- [Filmapp search.html](https://github.com/BlindSanji/movieapp/blob/main/project/templates/search.html)
