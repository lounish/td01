# Td01
Lounis HADJI 
 M1 MIAGE


EXO 1 :
	2) CTRL+SPACE après sysout permet d'afficher la méthode System.out.println()
	3) CTRL+SPACE après toStr dans une classe permet de nous afficher la rédifinition
		de la méthode toString
	4) CTRL+SPACE après main permet de nous afficher la méthode
			public void main(String[] args)
	5) Nous propose de définir les méthodes public void setFoo(int) et public int getFoo()
	6) nous permet d'utiliser le Refractor qui nous permet de changer le nom d'un élément partout
			dans le document


EXO 2 :
 
 * 1) Ici ça marche car nous sommes dans la même classe et la visibilité private nous permet de voir
 * les éléments dans la même classe
 
 * 2) Dans une autre classe, la visibilité de private nous permet pas d'accéder aux attributs x et y,
 * il faudrait alors créer une méthode getX() et getY() pour récupérer les valeurs ou en changeant la
 * visibilté en mettant public (déconseillé).
 
 * 3) On doit mettre tous les attributs en private car cela permet de garder un contrôle et de garder
 * une cohérence entre les attributs
  
 * 4) C'est une méthode permettant de récupérer la valeur d'un attribut (un get), ici on doit créer la
 * méthode getX() et getY() dans la classe point pour récupérer la valeur des attributs
 
 * 5) Le mot clé this est utilisé pour accéder Ã  un champ/méthode de la classe
 * Par exemple en étant dans la classe Point, pour utiliser l'attribut x dans une méthode, il faut utiliser
 * le mot clé this suivi du nom de l'attribut : this.x = 10 par exemple
   
 6) Output : fr.dauphine.javaavance.td1.Point@3764951d
 * Cela nous écrit le nom du package suivi du nom de la classe et de l'id de Objet, on peut voir que chaque
 * objet possède un identifiant
  
 * 7) 
 * 	private static int nbInstance = 0;
	public Point() {
		this.nbInstance++;
	}
	public int getInstance() {
		return this.nbInstance;
	}  
 * 	On crée un attribut privé mais en ajoutant le mot clé static c'est à  dire qu'il sera partagé à  toutes
 * 	les instances de la classe et non à  chaque instance. Cet attribut doit donc être incrémenté à  chaque
 * 	fois que le constructeur est appelé. On récupère la valeur avec un get. 
 * 
 * 8) public Point(Point p2) {
		this.nbInstance++;
		this.x = p2.getX();
		this.y = p2.getY();
	}
 *	Il sait quel constructeur appeler en fonction des arguments
 *
 *	9) 
 *	@Override
	public String toString() {
		return "("+this.x+","+this.y+")";
	}
 *
 *														
 *													EXO 3
 *
 *
 *	1) Output : true
 *				false
 *	Point p2=p1 nous permet de faire une copie exacte de l'objet, alors que Point p3=new Point(1,2);
 *	nous permet uniquement de créer un autre objet point qui a les mêmes coordonnées donc qui a des
 *	attributs de mêmes valeurs.
 *
 *	2)	 
 *		public boolean isSameAs(Point p3) {
		if((this.x == p3.getX()) && (this.y == p3.getY())) {
			return true;
		}
		return false;
	}
 *	
		System.out.println(p1.isSameAs(p3));
 *	Output : true
 *
 *	3) La méthode indexOf fait appel à la méthode equals, le problème ici c'est qu'on demande l'index de p1
 *		et vu que on a dit que p2=p1, rechercher p2 revient à rechercher p1. Donc la méthode indexOf ne répond
 *		pas à ce que nous voulons chercher. On peut alors redéfinir la méthode equals 
 *		@Override
		public boolean equals(Object j) {
			if(j instanceof Point) {
				Point temp = (Point) j;
				if((this.x == temp.getX()) && (this.y == temp.getY())) {
					return true;
				}
				return false;
			}
			return false;
		}

 
/**

EXO 4	
 * 2) Si on ajoute plus de points que la capacité maximale du tableau, une exception
 * 		java.lang.ArrayIndexOutOfBoundsException se lève. Ce qu'on peut faire c'est 
 * 		qu'à chaque fois que nous voulons ajouter un Point, on recrée un nouveau 
 * 		tableau de points qui sera de taille n+1 avec n = à la capacité du tableau précédent
 * 		et on y ajoute à la fin le nouveau Point. Ou alors on peut faire l'exercice avec une taille
 * 			
 * 
 * 3) 
 * 	public int pointCapacity() {
				return this.myPoints.length;
			}
			public int nbPoints() {
			int compt = 0;
			for(int i=0;i<this.myPoints.length;i++) {
				if(this.myPoints[i] instanceof Point) {
				compt++;
				}
			}
			return compt;
		}
	
 * 
 * 	5) La méthode renvoie alors false, et lorsqu'on ajoute un élément null, la méthode contains fait 
 * 		lever une exception (NullPointerException). On utilise alors Objects.requireNonNull(Point p)
 * 		dans la méthode add pour éviter d'ajouter un Point null.
 * 
 * 	6) Avec une LinkedList, la méthode pointCapacity devient obsolète car c'est tout le but de la classe
 * 		LinkedList. En effet, la liste va plus ou moins s'aggrandir en fonction des ajouts de point.
 * 		Donc c'est beaucoup plus flexible lorsqu'on connait pas la taille exacte du nombre de points.
 * 		nbPoints() est obtenu avec la méthode size() de la classe LinkedList qui renvoie le nombre d'
 * 		éléments. Et contains est obtenu aussi par la méthode contains(Object o) de la classe LinkedList.
 *
 * 	
 EXO 5
 * 1) On peut définir la méthode translate sous deux formes, translate(double dx, double dy) ou translate(Point p)
 * 
 * 5) Les deux cercles sont alors translatés vu qu'ils sont liés au même point, il faudrait alors mettre
 * 		 x et y et la classe Point en final pour qu'ils ne soient plus modifiés 
 *
 * 6) Il faut alors faire une copie défensive, créer un objet Point qui sera égal et aura les mêmes attributs
 * 		que le centre du cercle à renvoyer et on renvoie l'objet temporaire.
 *
  9) On peut rendre la méthode static en plus de publique car nous n'utilisons pas de variables propre à la classe
 *		et on peut utiliser cette méthode dans une autre classe sans instancier forcément un Cercle en faisant 
 *		Circle.contains(....)
  EXO 6
 * 	1) Un anneau n'est ni un point, ni un cercle ou ni une Polyligne donc il ne faut pas utiliser
 * 		l'héritage
 * 
 * 	4) fr.dauphine.javaavance.td1.Ring@2a33fae0
		Il faut redéfinir la fonction toString
 * 
 * 
 * *
 */
