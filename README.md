// This source code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © RicardoSantos

//@version=4
study(title='Distance to Demand Vector', overlay=false)

length = input(100)

lv = lowest(length)
lb = abs(lowestbars(length))
hv = highest(length)
hb = abs(highestbars(length))
demand_vector = (hv - lv) / max(hb-lb, lb-hb)

distance_to_long_vector = close - (lv + demand_vector * lb)
distance_to_short_vector = close - (hv - demand_vector * hb)
plot(series=distance_to_long_vector, title='+dv', color=color.lime)
plot(series=distance_to_short_vector, title='-dv', color=color.red)
