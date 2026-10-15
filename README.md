# mpalmer2223CodingProject.github.io
[Coding Project.py](https://github.com/user-attachments/files/33465547/Coding.Project.py)
print("--- LIGHTBULB LIFESPAN & ENERGY CALCULATOR ---")
print("This project calculates the annual operating costs and expected lifespan of various lightbulbs based on your daily usage.")
print("It helps you analyze energy consumption, compare incandescent vs. LED efficiency, and project replacement timelines.")
print("Select a lightbulb type from the following options:")

print("1. Incandescent (60W)")
print("2. Halogen (43W)")
print("3. LED (9W)")


bulb_choice = input("Enter the number corresponding to your bulb choice (1, 2, or 3): ")
daily_hours = float(input("Enter average daily usage in hours (e.g., 5.5): "))
electricity_rate = float(input("Enter your electricity rate in $/kWh (e.g., 0.15): "))
while True:
    if bulb_choice == "1":
        wattage = 60
        rated_lifespan_hours = 1000
        bulb_type = "Incandescent"
    elif bulb_choice == "2":
        wattage = 43
        rated_lifespan_hours = 2500
        bulb_type = "Halogen"
    elif bulb_choice == "3":
        wattage = 9
        rated_lifespan_hours = 25000
        bulb_type = "LED"
    else:
        wattage = 0
        rated_lifespan_hours = 0
        bulb_type = "Unknown"
    loop=input("Would you like to calculate the lifespan of your bulb? (yes/no): ").lower()
    if loop == "yes":
        break
if wattage > 0 and daily_hours > 0:
    kwh_per_day = (wattage * daily_hours) / 1000
    annual_cost = kwh_per_day * 365 * electricity_rate
    lifespan_years = rated_lifespan_hours / (daily_hours * 365)
    
    print(f"Selected Bulb: {bulb_type} ({wattage}W)")
    print(f"Estimated Annual Operating Cost: ${annual_cost:.2f}")
    print(f"Expected Lifespan: {lifespan_years:.1f} years under current usage patterns.")
    
    if daily_hours >= 8:
        print("Usage Category: Heavy Usage — Expect faster wear and earlier replacement intervals.")
    elif daily_hours >= 4:
        print("Usage Category: Moderate Usage — Balanced efficiency and lifespan.")
    else:
        print("Usage Category: Light Usage — High energy savings and long service lifespan.")

else:
    print("Invalid selection or usage hours entered. Please rerun the program and provide valid inputs.")
   
 #The Graphing Part
import os
import matplotlib.pyplot as plt
script_dir = os.path.dirname(os.path.abspath(__file__))
wattage = []
lifespan = []

with open("wattage.txt", "r") as f_watt, open("lifespan.txt", "r") as f_life:
    f_watt.readline()
    f_life.readline()

    for w_line, l_line in zip(f_watt, f_life):
        if w_line.strip() and l_line.strip():  # ensure line is not empty
            wattage.append(float(w_line.strip()))
            lifespan.append(float(l_line.strip()))
 
