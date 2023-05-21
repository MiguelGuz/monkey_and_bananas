# monkey_and_bananas
mueve(Estado1, Movimiento1, Estado2): El Movimiento1 desde el % Estado1 conduce al Estado2%
estado(MonoHorizontal, MonoVertical, PosiciónCaja, TienePlatano)
MonoHorizontal={puerta, debajo, ventana}
MonoVertical={suelo, sobre_caja}
PosiciónCaja={puerta, debajo, ventana} 
TienePlátano={tiene, no_tiene} mueve (estado(debajo, sobre_caja, debajo, no_tiene)
estado(debajo, sobre_caja, debajo, tiene)
mueve(estado(P, suelo, P, H)
estado(P, sobre_caja, P, H))
mueve(estado(P1, suelo, P1, H)
estado(P2, suelo, P2, H))
mueve(estado(P1, suelo, B, H)
estado(P2, suelo, B, H))
puedetomar(Estado): el mono puede coger el platano en Estado puedecoger(estado(_, _, _, tiene)). % 1. El mono ya lo tiene puedecoger(Estado1):- % 2. Hay que trabajar un % poco para cogerlo mueve(Estado1, Accion, Estado2), % Intenta hacer algo puedecoger(Estado2). % Inténtalo de nuevo
