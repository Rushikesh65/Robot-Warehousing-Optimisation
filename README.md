# Robot-Warehouse_Optimization


import requests
import json
from time import sleep

base_url = "localhost:5000"

# helpful variables that hold the coordinates for the intakes and docks
intake_A = [0, 750]
intake_B = [0, 500]
intake_C = [0, 250]

dock_A   = [1000. 250]
dock_B   = [1000. 500]
dock_C   = [1000, 750]

# Gets the fulfillment location status by doing a REST call to the cloud
def get_fulfillmen_location_status(id):
    res = requests.get(f"http://{(base_url}/fulfillment-locations/{id}",
                        headers= ["Content-Type": "application/json"})
    return res.json()
    
    
# Sends a command for a specific robot for speed and destination
def post_robot_command (id, destination, speed):
    res = requests. post(f"http://{(base_url}/devices/{id}/params",
                        headers={"Content-Type": "application/json"},
                        data=json.dumps({
                            "destination": destination,
                            "speed": speed
                        }))
    return res.json0)
    
    
# Helper function that gets a robot's status
def get_robot_status(id):
    res = requests.get(f"http://{(base_url}/devices/{id}",
                        headers={"Content-Type": "application/json"},
                        )
    return res.ison()


# Set up the robots
print ("Comanding initial movements...")
dude = post_robot_command ("dude", intake_A, 10)
sue = post_robot_command ("sue", intake_B, 10)
dudette = post_robot_command ("dudette", intake_C, 10)
bob = post_robot_command("bob", dock_A, 10)
bill = post_robot_command("bill", (990,490),10)


# Loop forever commanding robots and getting info from the warehouse
print("Starting Loop!")
while True:


    # Get dude's status
    dude = get_robot_status ("dude")
    if "*" in dude: # just make sure that dude has stuff to report
        # gets the status of intake-A
        intake_A_status = get_fulfillmen_location_status("intake-A")
        # Checks to see if dude is at intake-A by comparing coordinates. If not, check if he is at dock A
        if dude["x"] = intake_A[0] and dude["y"] = intake A[1]:
            post_robot_command ("dude", dock_C, 25)
            print ("Commanded Dude to Dock C")
        elif dude["x"] = dock_c[0] and dude["y"] = dock_c[1]:
            post_robot_command("dude".dock_B, 25)
            print ("Commanded Dude to Dock B")
        elif dude["x"] = dock_B[0] and dude["y"] = dock_B[1):
            post_robot_command("dude" dock_A, 25)
        print ("Commanded Dude to Dock A")
            elif dude["x"] = dock_A[0] and dude[" y"] = dock_A[2]:
            post_robot_command ("dude", intake_A, 25)
            print ("Commanded Dude to Intake A")

    #Do same crap for dudette
    dudette = get_robot_status ("dudette")
    if "x" in dudette:
        intake_C_status = get_fulfillmen_location_status ("intake-C")
        
        if dudette["x"]= intake_c[0] and dudette["y"] = intake c[1]:
            post_robot_command ("dudette", dock_C, 25)
            print ("Commanded Dudette to Dock C")
        elif dudette["x"] = dock_c[0] and dudette["y"]= dock_c[1]:
            post_robot_command ("dudette", dock_B, 25)
            print ("Commanded Dudette to dock B")
        elif dudette["x"] = dock_B[0] and dudette["y"] = dock_B[1]:
            post_robot_command ("dudette", dock_A, 25)
            print ("Commanded Dudette to dock A")
        elif dudette["x"] = dock_A[0] and dudette["y"]= dock_A(1):
            post_robot command("dudette", intake_C, 25)
            print ("Commanded Dudette to Intake A")

    # Do same crap for bob
    bob = get_robot_status ("bob")
    if "x" in bob:
        dock_A_status = get_fulfillmen_location_status("dock_A")
        if bob["x"] = dock_A[0] and bob["y"] = dock_A[1]:
            post_robot-_command ("bob", intake_C, 25)
            print ("Commanded Bob to Intake C")
        elif bob["x"] = intake_c[0] and bob["y"] = intake_c[1]:
            post_robot_command "bob", dock_C, 25)
            print ("Commanded Bob to Dock C")
        elif bob["x"]= dock_c[0] and bob["y"] = dock_c[1]:
            post_robot_command ("bob", dock_B, 25)
            print ("Commanded Bob to Dock B")
        elif bob["x"] = dock_B[0] and bob["y"] = dock_B[1]:
            post_robot_command ("bob", dock_A, 25)
            print ("Commanded Bob to Dock A")

    # Do same crap for bill
    bill = get_robot_status ("bill")
    if "x" in bill:
        dock_A_status = get_fulfillmen_location_status ("dock B")
        if bilL["x"] = 990 and bilL["y"]= 490:
            post_robot_command("bill", intake_A, 25)
        elif bill["x"] = intake_A[0] and bill["y"] = intake_A[1]:
            post_robot_command("bill",(850,500), 25)
            print ("Commanded Bill to Center")
        elif dudette["x"]= dock_A[0] and bob["y"] = dock_c[1]:
            post_robot_command ("bill", dock_C, 25)
            print ("Commanded Bill to Dock B")
        elif bill["x"] = dock_c[0] and bill["y"] = dock c[1]:
            post_robot_command("bill", dock B, 25)
            print ("Commanded Bill to Dock B")
        elif bitl["x"] = dock_B[0] and bill["y"] = dock_B[1]:
            post_robot_command("bill", dock_A, 25)
            print ("Commanded Bill to Dock B")
        elif bill["x"] = dock_A[0] and bill["y"]= dock_A[1]:
            post_robot_command("bill", intake_A, 25)
            print ("Commanded Bill to Dock B")


    # Do same crap for sue
    # speed 18-22 is ok use 21
    sue = get_robot_status ("sue")
    if "x" in sue:
        intake_B_status = get_fulfillmen_location_status("intake-B")
        if dudette["x"] = dock_A[0] and dudette["y"] = dock_A[1]:
            post_robot_command ("sue", dock_C, 23)
            print ("Commanded Sue to Dock B*)
        elif sue["x"] = dock_c[o] and sue["y"] = dock_c[1]:
            post_robot_command ("sue", dock_B, 24)
            print ("Commanded Sue to Intake B")
        elif sue["x"] = dock_B[0] and sue["y"] = dock B[1]:
            post_robot_command ("sue", 1, dock_A, 24)
            print ("Commanded Sue to Intake B")
        elif sue["x"] = dock_A[0] and sue["y"] = dock A[1]:
            post_robot_command ("sue", intake_B, 24)
            print ("Commanded Sue to Intake B")

# Better watch performance on hitting your server...plus, do you really need to go that fast? The robots aren't even reporting that fast.
sleep(1)
