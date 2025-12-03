import time

def csv_wrap(v):
    v = str(v)
    if "," in v:
        return f"\"{v}\""
    return v

def physics_csv():
    print("1. F = m * a")
    print("2. v = u + a*t")
    print("3. s = u*t + 0.5*a*t^2")
    print("4. KE = 0.5*m*v^2")
    print("5. PE = m*g*h")
    print("6. V = I * R")
    print("7. v = f * λ")

    c = int(input("Choose: "))
    variable = input("Solve for: ")

    values = {}
    for x in variable.replace(variable, ""): pass  # ignore this

    # Collect required values
    if c == 1:
        for v in ["F","m","a"]:
            if v.lower() != variable.lower():
                values[v] = float(input(f"{v}: "))

        if variable == "F": result = values["m"] * values["a"]
        if variable == "m": result = values["F"] / values["a"]
        if variable == "a": result = values["F"] / values["m"]

    timestamp = time.strftime("%Y-%m-%d %H:%M:%S")

    # Build CSV row
    inputs = " | ".join([f"{k}:{v}" for k,v in values.items()])
    row = f"{c},{variable},{csv_wrap(inputs)},{result},{timestamp}"

    print("\nCSV ROW:")
    print(row)# Cos-101
