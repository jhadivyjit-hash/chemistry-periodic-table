import tkinter as tk from tkinter import messagebox import math

=========================

PERIODIC TABLE DATA

=========================

name, symbol, atomic number, shells, uses, fun fact

ELEMENTS = [ ("Hydrogen", "H", 1, [1], "Rocket fuel", "Lightest element"), ("Helium", "He", 2, [2], "Balloons", "Does not burn"), ("Lithium", "Li", 3, [2,1], "Batteries", "Can float on water"), ("Beryllium", "Be", 4, [2,2], "Aircraft parts", "Very strong metal"), ("Boron", "B", 5, [2,3], "Glass making", "Used in borax"), ("Carbon", "C", 6, [2,4], "Diamonds and life", "Forms millions of compounds"), ("Nitrogen", "N", 7, [2,5], "Fertilizers", "Makes up most of air"), ("Oxygen", "O", 8, [2,6], "Breathing", "Supports combustion"), ("Fluorine", "F", 9, [2,7], "Toothpaste", "Most reactive element"), ("Neon", "Ne", 10, [2,8], "Neon signs", "Glows red-orange"), ("Sodium", "Na", 11, [2,8,1], "Salt", "Reacts strongly with water"), ("Magnesium", "Mg", 12, [2,8,2], "Fireworks", "Burns with white flame"), ("Aluminium", "Al", 13, [2,8,3], "Foil and cans", "Lightweight metal"), ("Silicon", "Si", 14, [2,8,4], "Computer chips", "Used in electronics"), ("Phosphorus", "P", 15, [2,8,5], "Fertilizers", "Glows in dark"), ("Sulfur", "S", 16, [2,8,6], "Medicines", "Smells like rotten eggs"), ("Chlorine", "Cl", 17, [2,8,7], "Water cleaning", "Greenish gas"), ("Argon", "Ar", 18, [2,8,8], "Light bulbs", "Noble gas"), ("Potassium", "K", 19, [2,8,8,1], "Fertilizers", "Very soft metal"), ("Calcium", "Ca", 20, [2,8,8,2], "Bones and teeth", "Essential for humans"), ]

Add placeholder elements up to 118

atomic_num = 21 while atomic_num <= 118: ELEMENTS.append(( f"Element {atomic_num}", f"E{atomic_num}", atomic_num, [2,8,18,32], "Scientific research", "Interesting chemical element" )) atomic_num += 1

=========================

WINDOW SETUP

=========================

root = tk.Tk() root.title("Interactive Periodic Table Explorer") root.geometry("1200x750") root.configure(bg="#06121f")

selected_element = ELEMENTS[0]

=========================

INFO PANEL

=========================

info_frame = tk.Frame(root, bg="#10243d", width=350) info_frame.pack(side="right", fill="y")

name_label = tk.Label(info_frame, text="", font=("Arial", 24, "bold"), fg="cyan", bg="#10243d") name_label.pack(pady=15)

info_text = tk.Label( info_frame, text="", justify="left", font=("Arial", 13), fg="white", bg="#10243d", wraplength=300, ) info_text.pack(padx=10)

=========================

ATOM CANVAS

=========================

canvas = tk.Canvas(info_frame, width=320, height=320, bg="#08131f", highlightthickness=0) canvas.pack(pady=20)

=========================

DRAW ATOM

=========================

def draw_atom(shells): canvas.delete("all")

center_x = 160
center_y = 160

# nucleus
canvas.create_oval(130,130,190,190, fill="cyan", outline="white", width=2)
canvas.create_text(160,160,text="Nucleus", fill="black", font=("Arial", 10, "bold"))

orbit_gap = 40

for shell_index, electrons in enumerate(shells):
    radius = orbit_gap * (shell_index + 1)

    # orbit circle
    canvas.create_oval(
        center_x-radius,
        center_y-radius,
        center_x+radius,
        center_y+radius,
        outline="cyan"
    )

    for e in range(electrons):
        angle = (2 * math.pi * e) / electrons
        ex = center_x + radius * math.cos(angle)
        ey = center_y + radius * math.sin(angle)

        canvas.create_oval(ex-6, ey-6, ex+6, ey+6, fill="yellow")

=========================

SHOW ELEMENT INFO

=========================

def show_element(element): name, symbol, atomic, shells, uses, fact = element

name_label.config(text=f"{name} ({symbol})")

info = (
    f"Atomic Number: {atomic}\n\n"
    f"Symbol: {symbol}\n\n"
    f"Uses: {uses}\n\n"
    f"Fun Fact: {fact}"
)

info_text.config(text=info)

draw_atom(shells)

=========================

PERIODIC TABLE BUTTONS

=========================

left_frame = tk.Frame(root, bg="#06121f") left_frame.pack(side="left", fill="both", expand=True)

heading = tk.Label( left_frame, text="Interactive Periodic Table", font=("Arial", 28, "bold"), fg="white", bg="#06121f" ) heading.pack(pady=10)

button_frame = tk.Frame(left_frame, bg="#06121f") button_frame.pack()

row = 0 col = 0

for element in ELEMENTS: name, symbol, atomic, shells, uses, fact = element

btn = tk.Button(
    button_frame,
    text=f"{atomic}\n{symbol}",
    width=7,
    height=3,
    font=("Arial", 10, "bold"),
    bg="#123456",
    fg="white",
    activebackground="cyan",
    command=lambda el=element: show_element(el)
)

btn.grid(row=row, column=col, padx=3, pady=3)

col += 1

if col > 9:
    col = 0
    row += 1

=========================

START APP

=========================

show_element(ELEMENTS[0])

root.mainloop()