# Quanto te la rischi? Rulebook

1. Non è possibile non prendere parte al gioco "Quanto te la rischi?" se si viene interpellati.
2. L'azione specificata nel "Quanto te la rischi?" deve essere possibile da eseguire, e consensuale nel caso vengano specificate condizioni riguardanti persone esterne alla scommessa.
3. Una volta che un giocatore __B__ riceve un "Quanto te la rischi?" da parte di un giocatore __A__, __B__ deve necessariamente rispondere con un numero _z_ : {_z_ : _z_ ∈ ℕ, _z_ ≠ 0}.
4. __A__ non può più tirarsi indietro una volta pronunciato il "Quanto te la rischi?".
5. Dopo che __B__ sceglie il numero, deve scegliere un altro numero _x_ : {_x_ : _x_ ∈ ℕ, _x_ ≤ _z_, _x_ ≠ 0}.
6. Anche __A__ sceglie un numero _y_ : {_y_ : _y_ ∈ ℕ, _y_ ≤ _z_, _y_ ≠ 0}.
7. Una volta che __B__ e __A__ scelgono i loro numeri _x_ e _y_ non possono più cambiarli.
8. Si fa partire un countdown di tre secondi, al cui termine sia __B__ che __A__ dicono all'unisono i due numeri _x_ e _y_.
9. Se _x_ = _y_ allora __B__ deve eseguire l'azione specificata dal "Quanto te la rischi?" di __A__.
10. Non ci sono limiti al valore che _z_ può assumere, ma andrebbe comunque calibrato in funzione dell'azione scelta.
11. È possibile per __B__ "quotare" il "Quanto te la rischi?" di __A__ prima di dichiarare il numero _z_ dicendo la parola "quoto". Qualora questo avvenga, il gioco procede come di consueto, ma nel caso in cui _x_ ≠ _y_ si esegue ulteriormente il passaggio descritto nella regola _8_. Se _x'_ = _y'_, __A__ deve eseguire l'azione. L'algoritmo che descrive il funzionamento completo del gioco è consultabile [alla fine di questo documento](#algoritmo).
12.  Per una qualunque modifica alle regole è necessario depositare una richiesta presso la [10FlessioniLampo Organization](https://github.com/10FlessioniLampo). Il cambiamento verrà discusso e verrà effettuerà una votazione. La modifica entrerà in vigore se viene raggiunta una maggioranza.
13.  Una regola che viene creata comincia ad avere effetto da subito, e non dal momento in cui appare su questo documento.
14. È proibito a qualunque giocatore specificare azioni legate al suicidio, all'autolesionismo, o a qualsiasi tipo di dolore fisico o psicologico non consensuale.
15. Non è possibile per un giocatore __A__ chiamare un "Quanto te la rischi?" su un giocatore __B__ se __A__ ha già ricevuto da un altro giocatore __C__ un "Quanto te la rischi?" uguale o estremamente simile in un momento precedente.


##### Algoritmo

```js
function quantoTeLaRischi(a, b, z, action, quoto) {
    let x = b.getRandom(1, z)
    let y = a.getRandom(1, z)
    if (x == y) {
        b.perform(action)
    } else if (quoto) {
        quantoTeLaRischi(b, a, z, action, false)
    }
}
```