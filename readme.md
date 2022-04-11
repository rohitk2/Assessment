# Carbon calculator

ChargeNet Stations builds solar-powered electric vehicle charging stations at fast food restaurants. Our mission is to accelerate the transition to green energy and combat climate change. To understand how we're doing, we need to measure the amount of "avoided carbon emissions", or carbon that we’re preventing from being released into the atmosphere when users charge their cars with our solar-powered chargers. The goal of this exercise is to calculate that carbon saving.

Write a program that:
* can be invoked from the command line
* takes as arguments:
    - a JSON file with data about cars charging at our chargers
    - a CSV file with data about the charging behavior and efficiency of various electric cars
* prints out information about the energy used for each charging car

You may complete this exercise in any language that you're comfortable with. We expect it to take about 30 minutes to an hour to complete. We want to be respectful of your time, so please feel free to submit a partial solution rather than spend much longer than that!

## Inputs

The program must take two arguments that provide data inputs.

The first argument, `cars`, is a CSV file containing information about various electric vehicles that will help you with the calculations. A sample `cars.csv` file is included. The data in this CSV is:
* the car's make and model
* the total amount of energy the car's battery can store, in kWh (kilowatt-hours)
* the car's charging rate, or how much power it can funnel into the battery, in kW (kilowatts)
* the car's energy (in kWh) consumed per 100 miles driven -- a measure of the car's energy efficiency
* the car's MPGe, or Miles per Gallon equivalent -- another measure of the car's energy efficiency that lets us compare to gas cars

The second argument, `charge-sessions`, is a JSON file with information about cars charging at our chargers. A sample `charge-sessions.json` file is included. Each element in this JSON array contains:
* the car's name
* the car's make and model
* the time the car started charging
* the time the car finished charging

We'll invoke your program using parameters named passed in like so:
`$ <run-program> --cars path/to/cars_file.csv --charge-sessions path_to_charge_sessions_file.json`

Lastly, it will be helpful for you to know:
* Energy and power are similar; try not to get them confused. Think of water flowing through a hose into a bucket. _Power_ is analagous to the amount of water coming through the hose at any given moment; it's the rate of flow. _Energy_ is the total amount of water in the bucket, accumulated over time. We measure power in kW (kilowatts) and energy in kWh (kilowatt hours). To convert between them, take _power_, in kW, and multiply that by time, in hours, to get energy, in kWh.
* On average, burning one gallon of gas releases 382 grams CO2e (carbon dioxide equivalents) into the atmosphere.

As a side note, EVs consume electricity that is typically generated in a way that produces carbon emissions. In other words, the true carbon savings here should equal the avoided carbon from our charge session, _minus_ the amount of carbon it took to produce the electricity consumed during the charge. For the sake of simplicity, in this exercise, we're assuming that our chargers are using 100% solar energy with no associated emissions, which unfortunately isn't completely accurate in the real world.

## Output

For each car that's charged at our station, the program should calculate the amount of energy consumed during the charge session, and the amount of CO2e avoided from this charge -- i.e. the amount of carbon, in kilograms, that would have been emitted by a gas-powered car over the same amount of driving. Then, print out those values along with the charge session's ID and the name of the car. Round decimals to 3 decimal places, and sort the results alphabetically by car name.

When you run the program with the sample files given, the output should match:

```bash
$ python carbon_calculator.py --cars cars.csv --charge-sessions charge_sessions.json
[{'id': 456, 'car name': "Ellie's Tesla", 'kWh charged': 75.0, 'kg CO2 avoided': 0.855}, {'id': 123, 'car name': "Leah's Leaf", 'kWh charged': 45.0, 'kg CO2 avoided': 0.516}, {'id': 789, 'car name': "Morgan's Ioniq", 'kWh charged': 20.533, 'kg CO2 avoided': 0.236}]
```

## Your submission

For your submission, please email us a .zip file that includes all source code for your program, as well as a readme containing:
* instructions for compiling and running your program
* a high-level description of how your program works (think of this as a commit message or PR description to help a coworker reviewing your code understand it)
* any tradeoffs or potentially risky decisions you made
* approximately how long you spent on this exercise, and any thoughts you may have about what you'd do with more time (improvements, ways to extend the program, etc.)
