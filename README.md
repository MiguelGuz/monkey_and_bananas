(defrule init =>
 (bind start-state (crear (crear mono at-door) (crear on-ceiling bananas) (create on-ceiling bananas) (crear at-window on-floor) (crear on-floor door) (crear at-window door) (crear at-window monkey)))
 (bind goal-state (crear (create on-ceiling bananas) (crear on-ceiling bananas)))
 (assert (inicio (value inicio-state)))
 (assert (meta (value meta-state))))

(defrule move-monkey <- (state (value state))
(test (and (member (create monkey pos1) state)
(member (create object pos2) state)
(not (eq pos1 pos2)))) =>
  
(printout  "Move monkey from " pos1 " to " pos2 crlf)
 (bind new-state (replace state (create monkey ?pos1) (create monkey pos2)))
  (modify s (value new-state)))

(defrule take-bananas <- (state (value state))
(test (and (member (create monkey pos) state)
(member (create on-floor bananas) state)
(member (create at-floor pos) state))) =>

  (printout "Monkey takes bananas" crlf)
  (bind new-state (replacestate (create on-floor bananas) (create monkey has-bananas)))
  (modify s (value new-state)))

(defrule done
  s <- (state (value $?state))
  g <- (goal (value $?state))
  =>
  (printout t "Goal state reached" crlf)
  (retract s)
  (retract g))
  
  
