# carbon-footprint
Design a solution that helps individuals understand, track, and reduce their carbon footprint through simple actions and personalized insights.
class EcoTrack:
    def __init__(self):
        self.total_carbon = 0

    def transport_emission(self, km, vehicle):
        emission_factors = {
            "car": 0.21,
            "bus": 0.08,
            "train": 0.04,
            "bike": 0.0,
            "walk": 0.0
        }

        carbon = km * emission_factors.get(vehicle, 0)
        self.total_carbon += carbon
        return carbon

    def electricity_emission(self, units):
        carbon = units * 0.82
        self.total_carbon += carbon
        return carbon

    def food_emission(self, diet_type):
        diet_factors = {
            "meat": 7,
            "vegetarian": 4,
            "vegan": 2
        }

        carbon = diet_factors.get(diet_type, 0)
        self.total_carbon += carbon
        return carbon

    def suggestions(self):
        print("\nPersonalized Suggestions:")
        
        if self.total_carbon > 50:
            print("- Use public transport more often.")
            print("- Reduce meat consumption.")
            print("- Save electricity by switching off appliances.")
        elif self.total_carbon > 20:
            print("- Try cycling or walking for short trips.")
            print("- Switch to energy-efficient devices.")
        else:
            print("- Great job! Keep maintaining sustainable habits.")

    def show_report(self):
        print(f"\nYour Total Carbon Footprint: {self.total_carbon:.2f} kg CO2")
        self.suggestions()


# Run Program
tracker = EcoTrack()

# Transport input
km = float(input("Enter distance traveled (km): "))
vehicle = input("Enter vehicle type (car/bus/train/bike/walk): ").lower()
tracker.transport_emission(km, vehicle)

# Electricity input
units = float(input("Enter electricity used (kWh): "))
tracker.electricity_emission(units)

# Food input
diet = input("Enter diet type (meat/vegetarian/vegan): ").lower()
tracker.food_emission(diet)

# Final Report
tracker.show_report()
