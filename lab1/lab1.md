
````plantuml

abstract class Player {
+List<pin> possible_colors
+Player(List<Color>)
+placeCombination()
{abstract} +playturn() :List<Pin>;
}

class CodificateurAI{
    +makeCombination()
    +playturn(Row) :List<Pin>
}
Player <|-- CodificateurAI

class DécodeurAI{
 +playturn(Row) :List<Pin>
}
Player <|- DécodeurAI




class Codificateur{
    +makeCombination()
    +playturn() :List<Pin>
}
Player <|-- Codificateur

class Décodeur{
 +playturn() :List<Pin>
}
Player <|- Décodeur



class Pin{
+PinColor : Color
+pin(Color)
}
Pin "2..10" <--o "*" Player


Pin "0..4" <--o "*" Rows

class Rows{
+Placedpin : ListPin> 
+ResultPins : List<Pin>
+NbPinByRow : int
+Rows(int)
+PlaceColoredPins(List<Pin>) : void
+PlaceResultPins(List<Pin>) : void
}
Pin "2..6" <--o "*" Rows


class Board{
+NumberOfRow : int
+NumberPinByRow : int
+AvailableColors : List<Color>
+DécodeurRows: List<Rows> 
+CombinationRow: Row
+Players : List<Player>

+Board(List<Color>, int, int)
+StartGame() :void
+AddRow() :void
}
Rows "10..12" <-- "1" Board
Player "2" <-- "1" Board
