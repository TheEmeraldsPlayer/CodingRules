# Duality Code Conventions
## Last Updated: 5/9/24
**This readme is to standardise the project. Please adhere to the rules that this project applies to and fix any errors you come across. In the event that you feel a certain rule should be changed/omitted, please propose it to the owner to consider changes.**
## 1. Script Rules
### 1.1 Class Summaries
Every class that is created should have a brief summary on what it does, to give the reader a quick rundown/refresher on what it does.
Please make sure that the summary can be readable at a glance and make new lines if the line is too long.
Example: When creating class `InputController`, the brief summary is as follows:
```c#
  ...

  /// <summary>
  /// InputController will handle ALL inputs from any source.
  /// If any scripts requires an input,
  /// it will go through input controller (unless it is a button)
  /// </summary>
  public class InputController : MonoBehaviour
  {

  ...
```
### 1.2 Code Commenting
Please comment your code on what you are doing, especially for really complicated code that takes in references from elsewhere.
Try to comment all functions usages that are not Unity built-in, especially those that may seem ambigiuous.
Example: When writing in `InputController`, the comments are as follows:
```c#
    ...

    //Setup singleton to receive input
    public static InputController instance;

    //List of axis's that has already been pressed
    private List<string> axisPressed;

    private void Awake()
    {
        //check for duplicate instances
        if (instance != null && instance != this)
        {
            Destroy(instance);
        }
        instance = this;
    }

    //Checks if input is pressed
    public bool IsAxisPressed(string axis)
    {
        return (Input.GetAxis(axis) != 0);
    }

    //Checks if input is held
    public bool IsAxisHeld(string axis)
    {
        return (Input.GetAxis(axis) != 0);
    }

    ...
```
### 1.3 Accessor Priority ( Functions )
Accessors have their own priorities.
This section is the guidelines on how to order your functions based off of the accessor types.
The order is as follows:
1. Unity built-in functions (Start,Awake etc..)
2. Public functions
3. Protected Functions
4. Private Functions
Example:
```c#
  ...

  private void Awake
  {
  ...
  }

  public void PublicFunc()
  {
  ...
  }

  protected void ProtectedFunc()
  {
  ...
  }

  private void PrivateFunc()
  {
  ...
  }

  ...
```
### 1.4 Accessor Priority ( Variables )
Accessors have their own priorities.
This section is the guidelines on how to order your variables based off of the accessor types.
The order is as follows:
1. SerializeField
2. Public Variables
3. Protected Variables
4. Private Variables
Example:
```c#
...

[SerializeField] private int variable;

public float health;

protected bool hasInit;

private int selfTimer;

...
```
### 1.5 Line limit
Lines that get too long will be hard to read in one shot.
Industry standards are around 80 characters per line, but I'm more lenient and increase the limit to 120 characters per line.
Move the overflowing characters to the next line and add an indent to it.
Example:
```c#
// This is wrong!!
VeryVeryVeryVeryLongFunction(VeryVeryVeryVeryLongVariable).VeryVeryVeryVeryLongAttirbute = VeryVeryVeryVeryLongVariable;

//This is correct!!
VeryVeryVeryVeryLongFunction(VeryVeryVeryVeryLongVariable).VeryVeryVeryVeryLongAttirbute
 = VeryVeryVeryVeryLongVariable;
```
