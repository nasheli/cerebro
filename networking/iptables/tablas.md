filter (por defecto)
  INPUT
  FORWARD
  OUTPUT

nat
  PREROUTING
  INPUT
  OUTPUT
  POSTROUTING

raw
  PREROUTING
  OUTPUT

mangle
  PREROUTING
  INPUT
  FORWARD
  OUTPUT
  POSTROUTING
