### Splash Screen
```
BEGIN splashScreen

DISPLAY splashscreen

INPUT(Button_Clicked)
IF Button_Clicked == start:
    START Game
ELIF Button_Clicked == options:
    OPEN options_menu
ELIF Button_Clicked == quit:
    QUIT game
ENDIF

END splashScreen
```

### Pause Menu
```
BEGIN pauseMenu
DISPLAY Menu
INPUT(Button_Hovered)
IF Button_Hovered == options:
    INPUT(Button_Clicked)
    If Button_Clicked == X:
    OPEN options_Menu
        INPUT(Button_Clicked)
        If Button_Clicked == Z:
        CLOSE options_Menu

ELIF Button_Hovered == Inventory:
    INPUT(Button_Clicked)
    If Button_Clicked == X:
    OPEN inventory
        INPUT(Button_Clicked)
        If Button_Clicked == Z:
        CLOSE inventory
ELIF Button_Hovered == character:
    INPUT(Button_Clicked)
    If Button_Clicked == X:
    OPEN characterMenu
        INPUT(Button_Clicked)
        If Button_Clicked == Z:
        CLOSE characterMenu
ELIF INPUT(Button_Clicked)
    If Button_Clicked == Z:
    CLOSE Menu
ENDIF
END pauseMenu

END pauseMenu
```
### Save and Load
```
BEGIN saveLoad
DISPLAY Save-Load menu
INPUT(Button_Hovered)
IF Button_Hovered == Load:
    INPUT(Button_Pressed)
    IF Button_Pressed == X:
        INPUT(Save_File)
        IF Save_File == saveFile1:
        LOAD saveFile1

        ELIF Save_File == saveFile2:
        LOAD saveFile2

        ELIF Save_File == saveFile3:
        LOAD saveFile3

        ELIF Save_File == saveFile4:
        LOAD saveFile4

IF Button_Hovered == Save:
    INPUT(Button_Pressed)
    IF Button_Pressed == X:
        INPUT(Save_File)
        IF Save_File == saveFile1:
        SAVE saveFile1

        ELIF Save_File == saveFile2:
        SAVE saveFile2

        ELIF Save_File == saveFile3:
        SAVE saveFile3

        ELIF Save_File == saveFile4:
        SAVE saveFile4
ENDIF

END saveLoad
```
### Movement
```
BEGIN movement
INPUT(Key)
IF Key == W or up:
    MOVEPLAYER up
ELIF Key == S or down:
    MOVEPLAYER down
ELIF Key == A or left:
    MOVEPLAYER left
ELIF Key == D or right:
    MOVEPLAYER right
ENDIF
END movement
```
### Next Room
```
BEGIN nextRoom
IF Player is touching Border:
    GOTO NextRoom
ENDIF
END nextRoom
```
### Battle
```
BEGIN battle
DISPLAY battleMenu
INPUT(Button_pressed)
IF Button_Pressed == Attack:
    SHOW moves
    INPUT(SelectedMove)
    IF SelectedMove == Move1:
        DO move1
    ELIF SelectedMove == Move2:
        DO move2
    ELIF SelectedMove == Move3:
        DO move3
    ELIF SelectedMove == Move4:
        DO move4
ELIF Button_Pressed == Spells:
    SHOW spells
    INPUT(SelectedSpells)
    IF SelectedSpells == Spell1:
        DO spell1
    ELIF SelectedSpells == Spell2:
        DO spell2
    ELIF SelectedSpells == Spell3:
        DO spell3
    ELIF SelectedSpells == Spell4:
        DO spell4
ELIF Button_Pressed == Characters:
    SHOW Characters
    INPUT(Selected_Characters)
    IF Selected_Characters == Character1:
        SWITCHTO Character1
    ELIF Selected_Characters == Character2:
        SWITCHTO Character2
    ELIF Selected_Characters == Character3:
        SWITCHTO Character3
ELIF Button_Pressed == Runaway:
    QUIT battle

IF enemy is killed:
    FINISH battle
ENDIF
END battle
```