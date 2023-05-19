# Gjenbrukbar kode

Gjenbrukbar kode er kode som er utformet på en måte som gjør det enkelt å bruke igjen i ulike deler av et program eller i forskjellige prosjekter. Den er generelt skrevet på en modulær og fleksibel måte, slik at den kan tilpasses ulike behov uten å måtte skrives på nytt. Gjenbrukbar kode bidrar til økt effektivitet, redusert utviklingstid og bedre kvalitet i programvareutviklingen.

## Eksempler
> Klasse:
```python
class User(db.Model, UserMixin):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(20), unique=True, nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)
    password = db.Column(db.String(60), nullable=False)
    # Likes har et forhold til Like modellen som vil si at en Like vil ha user_id og sin egen id.
    likes = db.relationship('Like', backref='user', lazy=True)

    def __repr__(self):
        return f"User('{self.username}', '{self.email}')"
```
> Funksjon:
```python
def get_likes(self):
        return [like.movie_id for like in self.likes]
```

- [Gjenbrukbar kode i flask prosjekt](https://github.com/BlindSanji/movieapp/blob/main/project/models.py)
