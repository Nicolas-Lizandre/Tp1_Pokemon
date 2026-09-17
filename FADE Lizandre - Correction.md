##Correction :

Je vais lister tous les problèmes que j'ai repéré dans ton dépôt GitHub :

- Pour un clean code il faut que les noms soient cohérents et suffisant pour deviner le sens de la fonction : tu mélanges les termes français et anglais (ex : rajouter/get/retirer/attaque/attack)
- Il faudrait utiliser uniformément les namespace
- PockemonVector (typo - vérifie pour tous les Pok...) + Dans PockemonVector.h, il faudrait mettre listePockemons en private (oui c'est pénible mais c'est le clean code qui demande)
- Certaines fonctions sont trop complexes (une fonctionnalité à la fois) - il faut rajouter des fonctions "internes" (ex: Pokedex::Pokedex(const string& csvFile) - tu rajoutes une fonction : getListPokemon(const string& csvFile) puis tu corriges ton Singleton OU void Pokemon::attaquer(Pokemon& target) tu mets : isPokemonKO())
- Pourquoi #include <memory> dans PokemonParty.h ?? - Les librairies en trop peuvent diluer la clarté.
- Le Singleton est mal fait - on peut le copier et en obtenir des instances différentes.
Pour emêcher les copies on utilise :
*#Singleton(Singleton &other) = delete;
#void operator=(const Singleton &) = delete;

Pour empêcher l'obtention de plusieurs instances personnalisées :
#std::lock_guard<std::mutex> lock(mutex_);
#if (pinstance_ == nullptr)
#{pinstance_ = new Singleton(value);}
#return pinstance_;

Vois le cours pour plus de détails (lock sert à éviter la concurrence de ressource sur le Singleton)




Ici je te rappelle des choses qui seront à corriger avant de rendre le devoir au professeur () :
- Expliquer succintement le projet et mettre un graphe UML dans le README
- Mettre des javadocs pour chaque classe



##Conclusion :
J'ai bien aimé la mise en forme globale et les commentaires de Pokemon.hpp et du main.cpp. Le Singleton est une erreur, les autres problèmes sont de l'ordre du clean code.
