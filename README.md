# Montanahproject
NAME: ART FOR ALL EYES
Working with Data and Code A2

## General Information:
My artistic code composition aims to address the limited availability of art for visually impaired individuals, specifically those with color vision deficiencies, which affect an estimated 300 million people worldwide. These include Deuteranopia (green light perception loss), Protanopia (red light perception loss), and Tritanopia (limited blue and green light perception). Through extensive research, my artwork is specifically catered to each type of color blindness, ensuring accessibility for all. Accessibility in digital platforms, such as webpages and apps, is often addressed through features like adjustable fonts, sizes, and alt text, and my project will contribute to this by producing an art piece accessible to people with vision impairments using Python's coding environment. Python, with its rich community, libraries, and tools, will enable me to create a simple, reproducible artwork while allowing for experimentation that would be challenging to achieve manually.

### Technologies Used:
Processing.com (MacIOS)
Python


#### Features
The code allows click between seeing all 3 artworks ! compare how you periceve each image differently !
Even non-vision impaired individuals are able to see art designs for the visually impaired


##### Screenshots:
<img width="398" alt="Screen Shot 2024-11-07 at 6 11 54 pm" src="https://github.com/user-attachments/assets/8423b927-8c4a-42ab-a399-f782b5cf5c14">
<img width="402" alt="Screen Shot 2024-11-07 at 6 11 49 pm" src="https://github.com/user-attachments/assets/993fe9c9-2354-412a-b53d-e3478a13f2fe">
<img width="411" alt="Screen Shot 2024-11-06 at 2 00 14 pm" src="https://github.com/user-attachments/assets/7133db85-86f6-4a59-a44d-1585e3a97543">
<img width="412" alt="Screen Shot 2024-11-06 at 2 00 26 pm" src="https://github.com/user-attachments/assets/64332537-acef-4e17-9194-0a995a2c225d">
<img width="411" alt="Screen Shot 2024-11-06 at 2 00 20 pm" src="https://github.com/user-attachments/assets/8cbe348e-5f06-4d5d-b4e5-ee49e2ca43e0">

###### SETUP:
1. Install Processing
First, you'll need to install the Processing IDE, which is the main environment for running your sketches.

Go to the Processing website:
https://processing.org/download/

Download the macOS version:
Choose the correct version for macOS. This will download a .zip file.

Extract the ZIP file:
Once the download is complete, double-click the .zip file to extract the folder.

Move Processing to Applications:
Drag the extracted Processing folder into your Applications folder for easy access.

Open Processing:
Open the Processing IDE from your Applications folder. It should launch with a default "Java mode."

2. Install Python Mode for Processing
Open Processing IDE:
If it's not already open, start Processing from the Applications folder.

Switch to Python Mode:

In the Processing IDE, at the top-right corner, there is a dropdown where it says Java. Click on it.
From the dropdown menu, select Python. This will activate Python Mode in the IDE.
If you don’t see the Python option in the dropdown, it means you’ll need to install the Python Mode library.

3. Install Python Mode (If Needed)
If Python Mode is not installed by default, follow these steps:

Go to the Processing IDE’s Contribution Manager:
In the Processing IDE, go to Sketch > Import Library... > Add Library....
Search for Python Mode:
In the Contribution Manager window, type “Python” into the search bar.
Install Python Mode:
Find Python Mode in the list, click on it, and then click Install.
This will download and install Python Mode, enabling you to write Python code in Processing.

4. Verify Python Mode Installation
Once Python Mode is installed:

Switch to Python Mode (if not already done):
In the Processing IDE, ensure the dropdown in the top-right corner reads Python.

enter code 

Run the sketch:
Click the Run button (the triangle icon), and you should see the Processing window pop up, displaying a simple interactive sketch.


###### USAGE:

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

# project status 
    COMPLETE 

## ROOM FOR IMPROVEMENT:
I would have liked to have created a colourblind quiz, in which users can take the quiz to find out if they have protanopia, dueternopia or tritanopia. However the colourblind quiz consists of very precise artworks to differentiate shades/ colours. At this stage of my coding progress i did not have the knowledge to execute this succesfully. So instead this Art for All design assumes that indviduals know their type of colourblindess already, or for those who are interesested on art in this particular topic. 

### ACKNOWLEDGES:
https://www.pythoncheatsheet.org/cheatsheet/control-flow
UTS CANVAS MODULES AND TUTORIALS 
