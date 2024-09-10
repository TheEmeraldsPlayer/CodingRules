# Project Rules
## Last Updated: 10/9/24
**This readme is to standardise the project. Please adhere to the rules that this project applies to and fix any errors you come across. In the event that you feel a certain rule should be changed/omitted, please propose it to the owner to consider changes.**
## 1. Script Rules
### 1.1 Class Summaries
Every class that is created should have a brief summary on what it does, to give the reader a quick rundown/refresher on what it does.
Please make sure that the summary can be readable at a glance and make new lines if the line is too long.
OPTIONAL: If you want to leave some sort of date of signature or additional information behind on the summary you can do it.
Example: When creating class `InputController`, the brief summary is as follows:
```c#
  ...

  /// <summary>
  /// InputController will handle ALL inputs from any source.
  /// If any scripts requires an input,
  /// it will go through input controller (unless it is a button)
  /// Made by SomeGuy on 5/9/24
  /// Last updated by AnotherGuy on 6/9/24
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

  private void Awake()
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
VeryVeryVeryVeryLongFunction(VeryVeryVeryVeryLongArgument).VeryVeryVeryVeryLongAttribute = VeryVeryVeryVeryLongVariable;

//This is correct!!
VeryVeryVeryVeryLongFunction(VeryVeryVeryVeryLongArgument).VeryVeryVeryVeryLongAttribute
 = VeryVeryVeryVeryLongVariable;
```
## 2. Github Rules
### 2.1 Branching out
Once you start branching out into your own branches, do take note of the naming of the branch so that it is easier to identify certain branches.
It makes tracking of projects easier (in case a rollback is required).
The formatting of the branches is as follows:

**VERSION_NAME_DATE(DD/MM/YYYY)_BRANCHNUM**

Wrong: `my_branch`

Correct: `1_User_05092024_1`

### 2.2 Commit Messages
Commit messages are important to know what was change during that commit. Try to make small commits at a time.
In the event there are other files committed along with the main file, just label it as "Minor Updates"
Importing Assets can just be labelled as what you imported inside
The format of the commits is as follows:

**ACTION FILECHANGED, DESCRIPTION, OTHERS**

Wrong: `Committed`

Correct: `Updated InputController, Added Button Pressed Function, Minor Bug fixes to Chatbox`

### 2.3 Files Committed
I know this is common sense, but please make sure with others that you are not modifying the same script with them, or else you will have merge conflicts.
There are possible solutions to this if you want to go around this problem.
1. Just wait for the other person to push their changes and privately pull from their branch to continue modifying the script
2. Just tell them what to do on their side of the computer or code it in their computer (if both of you are physically there)

### 2.4 Main
Main must ALWAYS be a working verison of the game in case of sudden rollbacks. Don't ever merge main with the latest version if it is not working!!
This is very important please note this!!
If main was thought to be working but ran into a crash halfway during playtesting, ALWAYS revert back to the original, and figure out the problem from a different branch.
