# Montanahproject
Working with Data and Code A2



CODE:
Global variable to keep track of the current screen
current_screen = "welcome"

def setup():
    size(400, 300)

def draw():
    background(255)
    if current_screen == "welcome":
        draw_welcome_screen()
    elif current_screen == "options":
        draw_options_screen()
    elif current_screen == "tritanopia_art":
        draw_tritanopia_artwork()
    elif current_screen == "deuteranopia_art":
        draw_deuteranopia_artwork()
    elif current_screen == "protanopia_art":
        draw_protanopia_artwork()

def draw_welcome_screen():
    textSize(32)
    textAlign(CENTER, CENTER)
    fill(0)
    text("Welcome to Art for All!", width / 2, height / 3)
    
    fill(100, 150, 255)
    rect(width / 2 - 50, height / 2 + 20, 100, 40, 10)
    fill(255)
    textSize(16)
    text("Continue", width / 2, height / 2 + 40)

def draw_options_screen():
    textSize(24)
    textAlign(CENTER, CENTER)
    fill(0)
    text("Select your type of colourblindness", width / 2, height / 4)
    
    options = ["Deuteranopia", "Protanopia", "Tritanopia"]
    for i, option in enumerate(options):
        fill(100, 150, 255)
        rect(width / 2 - 100, height / 2 + i * 50 - 20, 200, 40, 10)
        fill(255)
        textSize(16)
        text(option, width / 2, height / 2 + i * 50)

def mousePressed():
    global current_screen
    if current_screen == "welcome":
        if (width / 2 - 50 < mouseX < width / 2 + 50) and (height / 2 + 20 < mouseY < height / 2 + 60):
            current_screen = "options"
    elif current_screen == "options":
        options = ["Deuteranopia", "Protanopia", "Tritanopia"]
        for i, option in enumerate(options):
            if (width / 2 - 100 < mouseX < width / 2 + 100) and (height / 2 + i * 50 - 20 < mouseY < height / 2 + i * 50 + 20):
                if option == "Tritanopia":
                    current_screen = "tritanopia_art"
                    redraw()  # Ensure draw() is called to render the artwork
                elif option == "Deuteranopia":
                    current_screen = "deuteranopia_art"
                    redraw()  # Ensure draw() is called to render the artwork
                elif option == "Protanopia":
                    current_screen = "protanopia_art"
                    redraw()  # Ensure draw() is called to render the artwork
    elif current_screen in ["tritanopia_art", "deuteranopia_art", "protanopia_art"]:
        # Check if back button is clicked
        if (width - 100 < mouseX < width - 20) and (height - 40 < mouseY < height - 10):
            current_screen = "options"  # Go back to options screen
            redraw()  # Ensure draw() is called to render the options screen

def draw_tritanopia_artwork():
    background(255)
    strokeWeight(2)
    
    # Color palette suitable for tritanopia
    colors = [
        color(0, 0, 0),          # Black
        color(255, 0, 0),        # Red
        color(255, 165, 0),      # Orange
        color(255, 255, 0),      # Yellow
        color(0, 128, 0),        # Green
    ]
    
    # Draw static lines and shapes
    for i in range(200):
        stroke(colors[i % len(colors)])
        x1 = random(width)
        y1 = random(height)
        x2 = random(width)
        y2 = random(height)
        line(x1, y1, x2, y2)
    

    draw_back_button()
    noLoop()  # Stop the draw loop to make it static

def draw_deuteranopia_artwork():
    background(255)
    strokeWeight(2)
    
    # Color palette suitable for deuteranopia (blue and gold)
    colors = [
        color(0, 0, 255),        # Blue
        color(255, 215, 0),      # Gold
    ]
    
    # Draw static lines and shapes
    for i in range(200):
        stroke(colors[i % len(colors)])
        x1 = random(width)
        y1 = random(height)
        x2 = random(width)
        y2 = random(height)
        line(x1, y1, x2, y2)


    draw_back_button()
    noLoop()  # Stop the draw loop to make it static

def draw_protanopia_artwork():
    background(255)
    strokeWeight(2)

    # Color palette suitable for protanopia (shades of green)
    colors = [
        color(34, 139, 34),      # Forest Green
        color(0, 128, 0),        # Green
        color(124, 252, 0),      # Lawn Green
        color(0, 255, 0),        # Lime
        color(50, 205, 50),      # Lime Green
    ]

    # Draw static lines and shapes
    for i in range(200):
        stroke(colors[i % len(colors)])
        x1 = random(width)
        y1 = random(height)
        x2 = random(width)
        y2 = random(height)
        line(x1, y1, x2, y2)

    draw_back_button()
    noLoop()  # Stop the draw loop to make it static

def draw_back_button():
    fill(255, 100, 100)
    rect(width - 100, height - 40, 80, 30, 10)  # Smaller button in the bottom corner
    fill(255)
    textSize(14)
    textAlign(CENTER, CENTER)
    text("Back", width - 60, height - 25)  # Center text on the button
