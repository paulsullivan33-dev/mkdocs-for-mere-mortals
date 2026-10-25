# Looking After Your Plot

Day-to-day care, in the order the
garden notices it: water, weeds, then
everything else.

## Watering

The garden has one standpipe by the
shed. In a dry spell the rota below
decides who waters the communal beds;
your own plot is your own job.

=== "Dry spell rota"

    | Day       | Bed        | Who   |
    | --------- | ---------- | ----- |
    | Monday    | Herb bed   | Ana   |
    | Wednesday | Soft fruit | Tomás |
    | Friday    | Nursery bed | Priya |

=== "Normal weeks"

    Water your own plot as it needs
    it. As a rule of thumb, a raised
    bed wants a watering can on any
    day it hasn't rained — deeper and
    less often beats a daily sprinkle.

!!! tip "Mulch is cheaper than water"
    A layer of compost or straw on
    bare soil halves how often you
    need to water. See
    [Compost](compost.md) for what
    the heap produces.

## Weeding

Little and often. Ten minutes with a
hoe on a dry day kills more weeds
than an hour of pulling after rain,
and the seedlings shrivel where they
fall.

## A small helper script

One member keeps sowing dates in a
notebook; another wrote this tiny
script for working out when a packet's
"weeks to harvest" lands. It is kept
here so nobody has to reinvent it:

```python
from datetime import date, timedelta

def harvest_window(sown: date, weeks: int) -> tuple[date, date]:
    """Earliest and latest likely harvest dates."""
    earliest = sown + timedelta(weeks=weeks)
    latest = earliest + timedelta(weeks=2)
    return earliest, latest

if __name__ == "__main__":
    start, end = harvest_window(date(2026, 4, 12), 10)
    print(f"Peas sown 12 April: pick between {start} and {end}")
```

Nobody is expected to run it. It is
here because the handbook is where
the garden keeps things.
