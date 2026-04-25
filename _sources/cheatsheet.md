# Python Cheat Sheet — Smart Energy Systems Tutorial

## Variables & Types

```python
temperature = 32          # int
humidity    = 65.4        # float
status      = "ON"        # str
is_occupied = True        # bool

print(type(temperature))  # <class 'int'>
```

## f-Strings

```python
temp = 32
print(f"Temperature: {temp}°C")
print(f"Energy: {1.5 * 2:.2f} kWh")   # .2f = 2 decimal places
```

## if / elif / else

```python
if temperature > 30:
    print("AC ON")
elif temperature > 25:
    print("Fan ON")
else:
    print("All OFF")
```

## Logical Operators

```python
if is_occupied and temperature > 30:   # both must be True
if not is_occupied:                    # reverses True/False
if temp > 35 or humidity > 80:        # at least one True
```

## while Loop

```python
cycle = 1
while cycle <= 10:
    print(f"Cycle {cycle}")
    cycle += 1
```

## for Loop

```python
for cycle in range(1, 6):   # 1, 2, 3, 4, 5
    print(cycle)

for item in my_list:
    print(item)
```

## Functions

```python
def calculate_energy(power_kw, hours=1):
    return power_kw * hours

result = calculate_energy(1.5, 3)   # 4.5
result = calculate_energy(1.5)      # 1.5 (default hours)
```

## Classes

```python
class Sensor:
    def __init__(self, location):     # runs when object is created
        self.location = location
        self.temperature = 0

    def generate(self):               # method
        self.temperature = 30

sensor = Sensor("Bedroom")           # create object
sensor.generate()                    # call method
print(sensor.temperature)            # access attribute
```

## Dictionaries

```python
data = {
    "temperature": 29.5,
    "humidity":    68.2,
    "occupancy":   1,
}

print(data["temperature"])    # 29.5
data["hour"] = 14             # add new key
```

## Lists

```python
records = []
records.append({"temperature": 30})  # add item
records[-1]                           # last item
records[-5:]                          # last 5 items
len(records)                          # number of items
```

## List Comprehension

```python
temperatures = [r["temperature"] for r in records]
# Same as:
temperatures = []
for r in records:
    temperatures.append(r["temperature"])
```

## Ternary Expression

```python
energy = 2.0 if ac_on else 0.1
# Same as:
if ac_on:
    energy = 2.0
else:
    energy = 0.1
```

## Imports

```python
import random
from config import DEFAULT_THRESHOLD
from sensor import SensorSimulator
```

## random Module

```python
import random
random.randint(22, 38)                   # random int between 22 and 38
random.uniform(40.0, 90.0)              # random float
random.choice([True, False])            # pick one randomly
random.choices([1, 0], weights=[70, 30])[0]  # weighted random pick
```

---

## Project File Map

| File | Class | Key Method |
|---|---|---|
| `config.py` | — (constants only) | — |
| `sensor.py` | `SensorSimulator` | `get_data(ac_state)` |
| `engine.py` | `DecisionEngine` | `evaluate(data, threshold, buffer, ...)` |
| `calculator.py` | `EnergyCalculator` | `compute(ac_state)` |
| `logger.py` | `DataLogger` | `store(record)`, `get_latest(n)` |
| `main.py` | — (runner) | `main()` |
| `dashboard.py` | — (UI) | `main()` |

## Run Commands

```bash
# Terminal simulation
python3 src/main.py

# Dashboard
streamlit run src/dashboard.py
```
