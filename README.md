# Duality Code Conventions
## Last Updated: 4/9/24
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
