# Modelado_en_NetLogo
Este repositorio contiene una modificación del modelo original de NetLogo llamado "Moths" (Polillas). En este modelo, se simula el comportamiento de las polillas en respuesta a dos tipos de luces con diferentes longitudes de onda (luces rojas y azules). El objetivo de este modelo es explorar cómo las polillas reaccionan ante estos dos tipos de luces y analizar su comportamiento en diferentes condiciones de iluminación.
breed [ lights light ]
breed [ moths moth ]

globals
[
  scale-factor  ;; to control the form of the light field
  trails        ;; list to store the trails of the moths
  moth-speed    ;; variable to control the speed of the moths
  violet-sensitivity
  red-sensitivity
]

lights-own
[
  intensity
]

moths-own
[
  ;; +1 means the moths turn to the right to try to evade a bright light
  ;; (and thus circle the light source clockwise). -1 means the moths
  ;; turn to the left (and circle the light counter-clockwise)
  ;; The direction tendency is assigned to each moth when it is created and does not
  ;; change during the moth's lifetime.
  direction
]

patches-own
[
  light-level ;; represents the light energy from all light sources
]

to setup
  clear-all
  set-default-shape lights "circle 2"
  set-default-shape moths "butterfly"
  set scale-factor 50
  set trails []
  set moth-speed 2 ;; adjust this value to change the speed of the moths
  set violet-sensitivity 0.5  ;; Sensibilidad baja para luces violetas
  set red-sensitivity 2  ;; Sensibilidad alta para luces rojas
  if number-lights > 0
  [
    make-lights number-lights
    ask patches [ generate-field ]
  ]
  make-moths number-moths
  reset-ticks
end

to go
  ask moths [
    move-thru-field
    ;; add current position to trails
    set trails lput (list xcor ycor ticks) trails
  ]
  ;; draw trails
  draw-trails
  ;; remove old trails
  remove-old-trails
  tick
end

;;;;;;;;;;;;;;;;;;;;;;
;; Setup Procedures ;;
;;;;;;;;;;;;;;;;;;;;;;

to make-lights [ number ]
  create-lights number [
    let chosen-color random 2
    if chosen-color = 0 [
      set color red
      set intensity 10  ;; Luminancia baja para luces rojas
    ]
    if chosen-color = 1 [
      set color violet
      set intensity 100  ;; Luminancia alta para luces violetas
    ]

    jump 10 + random-float (max-pxcor - 30)
    set size 10
  ]
end

to make-moths [ number ]
  create-moths number [
    ifelse (random 2 = 0)
      [ set direction 1 ]
      [ set direction -1 ]
    set color white
    jump random-float max-pxcor
    set size 5
  ]
end

to generate-field ;; patch procedure
  set light-level 0
  ;; every patch needs to check in with every light
  ask lights
    [ set-field myself ]
  set pcolor scale-color white (sqrt light-level) 0.1 ( sqrt ( 20 * max [intensity] of lights ) )
end

;; do the calculations for the light on one patch due to one light
;; which is proportional to the distance from the light squared.
to set-field [p]  ;; turtle procedure; input p is a patch
  let rsquared (distance p) ^ 2
  let amount intensity * scale-factor
  ifelse rsquared = 0
    [ set amount amount * 1000 ]
    [ set amount amount / rsquared ]
  ;; Aumentar el impacto de las luces violetas
  if color = violet [
    set amount amount * 2  ;; Incrementa el impacto de las luces violetas
  ]
  ask p [ set light-level light-level + amount ]
end

;;;;;;;;;;;;;;;;;;;;;;;;
;; Runtime Procedures ;;
;;;;;;;;;;;;;;;;;;;;;;;;

to move-thru-field    ;; turtle procedure
  ifelse (light-level <= (1 / (10 * (ifelse-value ( [light-level] of patch-here > 20) [ violet-sensitivity ] [ red-sensitivity ] ))))
  [
    ;; if there is no detectable light move randomly
    rt flutter-amount 45
  ]
  [
    ifelse (random 25 = 0)
    ;; add some additional randomness to the moth's movement, this allows some small
    ;; probability that the moth might "escape" from the light.
    [
      rt flutter-amount 60
    ]
    [
      ;; turn toward the brightest light
      maximize
      ;; if the light ahead is not above the sensitivity threshold  head towards the light
      ;; otherwise move randomly
      ifelse ([light-level] of patch-ahead 1 / light-level > (1 + 1 / (10 * (ifelse-value ( [light-level] of patch-here > 20) [ violet-sensitivity ] [ red-sensitivity ] ))))
      [
        lt ( direction * turn-angle )
      ]
      [
        rt flutter-amount 60
      ]
    ]
  ]
  if not can-move? moth-speed
    [ maximize ]
  fd moth-speed
end

to maximize  ;; turtle procedure
  face max-one-of patches in-radius 1 [light-level]
end

to-report flutter-amount [limit]
  ;; This routine takes a number as an input and returns a random value between
  ;; (+1 * input value) and (-1 * input value).
  ;; It is used to add a random flutter to the moth's movements
  report random-float (2 * limit) - limit
end

to draw-trails
  ask patches [ set pcolor scale-color white (sqrt light-level) 0.1 (sqrt (20 * max [intensity] of lights)) ] ;; redraw light field
  foreach trails [
    pos ->
    let x item 0 pos
    let y item 1 pos
    ask patch x y [ set pcolor blue ]
  ]
end

to remove-old-trails
  let new-trails []
  foreach trails [
    pos ->
    let age ticks - item 2 pos
    if age < 100 [
      set new-trails lput pos new-trails
    ]
  ]
  set trails new-trails
end
; Copyright 2005 Uri Wilensky.
; See Info tab for full copyright and license.
