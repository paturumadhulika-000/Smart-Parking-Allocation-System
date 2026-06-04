SMART PARKING ALLOCATION SYSTEM
CODE:

SMART PARKING ALLOCATION SYSTEM USING CSP

slots = [
    {"slot": "S1", "size": "Small", "distance": 10},
    {"slot": "S2", "size": "Small", "distance": 20},
    {"slot": "M1", "size": "Medium", "distance": 15},
    {"slot": "L1", "size": "Large", "distance": 5}
]
vehicles = [
    {"name": "Ambulance", "size": "Large", "priority": 1},
    {"name": "Faculty Car", "size": "Small", "priority": 2},
    {"name": "VIP Car", "size": "Medium", "priority": 2},
    {"name": "Student Car", "size": "Small", "priority": 3},
    {"name": "Visitor Car", "size": "Small", "priority": 3}
]
vehicles.sort(key=lambda x: x["priority"])
allocated = []
waiting = []
print("=" * 55)
print("     SMART PARKING ALLOCATION SYSTEM")
print("=" * 55)
print("\nVehicle Allocation Process")
print("-" * 55)
for vehicle in vehicles:
    compatible_slots = []
    for slot in slots:
        if slot["size"] == vehicle["size"]:
            compatible_slots.append(slot)
    if compatible_slots:
        nearest_slot = min(
            compatible_slots,
            key=lambda x: x["distance"]
        )
        allocated.append({
            "vehicle": vehicle["name"],
            "slot": nearest_slot["slot"]
        })
        print(
            f"{vehicle['name']} "
            f"(Priority {vehicle['priority']}) "
            f"--> {nearest_slot['slot']}"
        )
        slots.remove(nearest_slot)
    else:
        waiting.append(vehicle["name"]
print(
            f"{vehicle['name']} --> Waiting List"
        )
print("\n")
print("=" * 55)
print("FINAL ALLOCATION")
print("=" * 55)
print(f"{'Vehicle':<20}{'Slot'}")
print("-" * 55)
for item in allocated:
    print(f"{item['vehicle']:<20}{item['slot']}")
print("\nWaiting Vehicles:")
if waiting:
    for vehicle in waiting:
        print(vehicle)
else:
    print("None")
print("\nParking Status")
print("-" * 55)
occupied = [x["slot"] for x in allocated]
for slot in ["S1", "S2", "M1", "L1"]:
    status = "Occupied" if slot in occupied else "Free"
    print(f"{slot} : {status}")
print("\nConstraints Applied")
print("-" * 55)
print("1. Size Matching")
print("2. Vehicle Priority")
print("3. Nearest Distance")
print("4. One Vehicle Per Slot")
