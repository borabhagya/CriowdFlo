# CriowdFlo
A Simulation-Driven Crowd Intelligence and Operational Decision-Support Platform for Urban Bus Transportation

Passengers on urban bus networks seldom know whether an approaching vehicle has
room for them, and transport planners rarely have a forward-looking view of how
queues and vehicle loads will evolve. This report presents CrowdFlo, a simulation-
driven decision-support platform that addresses both problems on a synthetic bus
network anchored to five real Chennai locations: Broadway/Parrys, Chennai Central,
Egmore, Anna Salai and Guindy. The network comprises twelve stops and three
synthetic routes (CF-01, CF-02, CF-03), operated as six directional lines. It is not
official Metropolitan Transport Corporation (MTC) data.
The computational core is a deterministic, seeded, discrete-time (one-minute)
passenger-flow simulator. Passenger arrivals are generated from a product of route
demand, stop weights, Gaussian morning and evening profiles, a directional bias, a
demand multiplier and an optional surge factor. Passengers are grouped into
destination cohorts, wait in first-in-first-out stop queues, board subject to vehicle
capacity, alight at their destinations, and may transfer between routes at shared stops.
Passenger conservation, capacity limits and queue non-negativity are enforced and
tested. Forecasts are obtained from an ensemble of eight independently seeded
simulation runs, reporting the ensemble mean and the range between the 10th and 90th
sample percentiles; with eight runs these percentile indices coincide with the sample
minimum and maximum. The forecast is a statistical Monte Carlo summary, not
trained machine learning. A journey planner enumerates direct and one-transfer
itineraries, attaches predicted loads and model-estimated boarding probabilities, and
ranks them by earliest arrival, least crowding, reliability or a balanced score. An
operations dashboard and an intervention sandbox compare baseline and modified
configurations under identical random seeds.
The implementation is a single self-contained HTML file in vanilla JavaScript, with
the engine, a 13-test suite and the application controller in separate script blocks. In
development, all 13 tests passed and a full baseline-plus-eight-run computation took
approximately 224 ms; these are reported development measurements, not
independent benchmarks. Engine outputs generated for this report show, for example,
that in the seed-7 morning-peak scenario an additional CF-01 dispatch stream reduces
mean waiting time from 5.38 to 3.99 min while adding 192 trips and about 156.8 bus-
hours, and that a capacity increase of 20 % reduces peak load without changing
waiting time. The model is uncalibrated and unvalidated against real data; limitations
and a roadmap toward GTFS, GPS, passenger-count and ticketing integration are
discussed.
