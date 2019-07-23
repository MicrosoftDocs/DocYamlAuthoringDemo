## Declaring and Initializing Strings  
 You can declare and initialize strings in various ways, as shown in the following example:  
  
```csharp-interactive
// Declare without initializing.
string message1;
Console.WriteLine(message1);

// Initialize to null.
string message2 = null;
Console.WriteLine(message2);

// Initialize as an empty string.
// Use the Empty constant instead of the literal "".
string message3 = System.String.Empty;
Console.WriteLine(message3);

//Initialize with a regular string literal.
string oldPath = "c:\\Program Files\\Microsoft Visual Studio 8.0";
Console.WriteLine(oldPath);

// Initialize with a verbatim string literal.
string newPath = @"c:\Program Files\Microsoft Visual Studio 9.0";
Console.WriteLine(newPath);

// Use System.String if you prefer.
System.String greeting = "Hello World!";
Console.WriteLine(greeting);

// In local variables (i.e. within a method body)
// you can use implicit typing.
var temp = "I'm still a strongly-typed System.String!";
Console.WriteLine(temp);

// Use a const string to prevent 'message4' from
// being used to store another string value.
const string message4 = "You can't get rid of me!";
Console.WriteLine(message4);

// Use the String constructor only when creating
// a string from a char*, char[], or sbyte*. See
// System.String documentation for details.
char[] letters = { 'A', 'B', 'C' };
string alphabet = new string(letters);
Console.WriteLine(alphabet);
```
  
 Note that you do not use the [new](#main) operator to create a string object except when initializing the string with an array of chars.  
  
 Initialize a string with the System.String.Empty constant value to create a new System.String object whose string is of zero length. The string literal representation of a zero-length string is "". By initializing strings with the System.String.Empty value instead of [null](#main), you can reduce the chances of a System.NullReferenceException occurring. Use the static System.String.IsNullOrEmpty%28System.String%29 method to verify the value of a string before you try to access it.  
  
## Immutability of String Objects  
 String objects are *immutable*: they cannot be changed after they have been created. All of the System.String methods and C# operators that appear to modify a string actually return the results in a new string object. In the following example, when the contents of `s1` and `s2` are concatenated to form a single string, the two original strings are unmodified. The `+=` operator creates a new string that contains the combined contents. That new object is assigned to the variable `s1`, and the original object that was assigned to `s1` is released for garbage collection because no other variable holds a reference to it.  
  
```csharp-interactive
string s1 = "A string is more ";
string s2 = "than the sum of its chars.";

// Concatenate s1 and s2. This actually creates a new
// string object and stores it in s1, releasing the
// reference to the original object.
s1 += s2;

System.Console.WriteLine(s1);
// Output: A string is more than the sum of its chars.
```
  
 Because a string "modification" is actually a new string creation, you must use caution when you create references to strings. If you create a reference to a string, and then "modify" the original string, the reference will continue to point to the original object instead of the new object that was created when the string was modified. The following code illustrates this behavior:  
  
```csharp-interactive
string s1 = "Hello ";
string s2 = s1;
s1 += "World";

System.Console.WriteLine(s2);
//Output: Hello
```
  
 For more information about how to create new strings that are based on modifications such as search and replace operations on the original string, see [How to: Modify String Contents](#main).  
  
## Regular and Verbatim String Literals  
 Use regular string literals when you must embed escape characters provided by C#, as shown in the following example:  
  
```csharp-interactive
string columns = "Column 1\tColumn 2\tColumn 3";
//Output: Column 1        Column 2        Column 3

string rows = "Row 1\r\nRow 2\r\nRow 3";
/* Output:
  Row 1
  Row 2
  Row 3
*/

string title = "\"The \u00C6olean Harp\", by Samuel Taylor Coleridge";
//Output: "The Æolean Harp", by Samuel Taylor Coleridge
```
  
 Use verbatim strings for convenience and better readability when the string text contains backslash characters, for example in file paths. Because verbatim strings preserve new line characters as part of the string text, they can be used to initialize multiline strings. Use double quotation marks to embed a quotation mark inside a verbatim string. The following example shows some common uses for verbatim strings:  
  
```csharp-interactive
string filePath = @"C:\Users\scoleridge\Documents\";
//Output: C:\Users\scoleridge\Documents\

string text = @"My pensive SARA ! thy soft cheek reclined
    Thus on mine arm, most soothing sweet it is
    To sit beside our Cot,...";
/* Output:
My pensive SARA ! thy soft cheek reclined
   Thus on mine arm, most soothing sweet it is
   To sit beside our Cot,... 
*/

string quote = @"Her name was ""Sara.""";
//Output: Her name was "Sara."
```
  
## String Escape Sequences  
  
|Escape sequence|Character name|Unicode encoding|  
|---------------------|--------------------|----------------------|  
|\\'|Single quote|0x0027|  
|\\"|Double quote|0x0022|  
|\\\\ |Backslash|0x005C|  
|\0|Null|0x0000|  
|\a|Alert|0x0007|  
|\b|Backspace|0x0008|  
|\f|Form feed|0x000C|  
|\n|New line|0x000A|  
|\r|Carriage return|0x000D|  
|\t|Horizontal tab|0x0009|  
|\U|Unicode escape sequence for surrogate pairs.|\Unnnnnnnn|  
|\u|Unicode escape sequence|\u0041 = "A"|  
|\v|Vertical tab|0x000B|  
|\x|Unicode escape sequence similar to "\u" except with variable length.|\x0041 = "A"|  
  
> [!NOTE]
>  At compile time, verbatim strings are converted to ordinary strings with all the same escape sequences. Therefore, if you view a verbatim string in the debugger watch window, you will see the escape characters that were added by the compiler, not the verbatim version from your source code. For example, the verbatim string @"C:\files.txt" will appear in the watch window as "C:\\\files.txt".  
  
## Format Strings  
 A format string is a string whose contents can be determined dynamically at runtime. You create a format string by using the static System.String.Format%2A method and embedding placeholders in braces that will be replaced by other values at runtime. The following example uses a format string to output the result of each iteration of a loop:  
  
```csharp
class FormatString
{
    static void Main()
    {
        // Get user input.
        System.Console.WriteLine("Enter a number");
        string input = System.Console.ReadLine();

        // Convert the input string to an int.
        int j;
        System.Int32.TryParse(input, out j);

        // Write a different string each iteration.
        string s;
        for (int i = 0; i < 10; i++)
        {
            // A simple format string with no alignment formatting.
            s = System.String.Format("{0} times {1} = {2}", i, j, (i * j));
            System.Console.WriteLine(s);
        }

        //Keep the console window open in debug mode.
        System.Console.ReadKey();
    }
}
```
  
 One overload of the System.Console.WriteLine%2A method takes a format string as a parameter. Therefore, you can just embed a format string literal without an explicit call to the method. However, if you use the System.Diagnostics.Trace.WriteLine%2A method to display debug output in the Visual Studio **Output** window, you have to explicitly call the System.String.Format%2A method because System.Diagnostics.Trace.WriteLine%2A only accepts a string, not a format string. For more information about format strings, see [Formatting Types](#main).  
  
## Substrings  
 A substring is any sequence of characters that is contained in a string. Use the System.String.Substring%2A method to create a new string from a part of the original string. You can search for one or more occurrences of a substring by using the System.String.IndexOf%2A method. Use the System.String.Replace%2A method to replace all occurrences of a specified substring with a new string. Like the System.String.Substring%2A method, System.String.Replace%2A actually returns a new string and does not modify the original string. For more information, see [How to: Search Strings Using String Methods](#main) and [How to: Modify String Contents](#main).  
  
```csharp-interactive
string s3 = "Visual C# Express";
System.Console.WriteLine(s3.Substring(7, 2));
// Output: "C#"

System.Console.WriteLine(s3.Replace("C#", "Basic"));
// Output: "Visual Basic Express"

// Index values are zero-based
int index = s3.IndexOf("C");
System.Console.WriteLine(index);
// index = 7
```
  
## Accessing Individual Characters  
 You can use array notation with an index value to acquire read-only access to individual characters, as in the following example:  
  
```csharp-interactive
string s5 = "Printing backwards";

for (int i = 0; i < s5.Length; i++)
{
    System.Console.Write(s5[s5.Length - i - 1]);
}
// Output: "sdrawkcab gnitnirP"
```
  
 If the System.String methods do not provide the functionality that you must have to modify individual characters in a string, you can use a System.Text.StringBuilder object to modify the individual chars "in-place", and then create a new string to store the results by using the System.Text.StringBuilder methods. In the following example, assume that you must modify the original string in a particular way and then store the results for future use:  
  
```csharp-interactive
string question = "hOW DOES mICROSOFT wORD DEAL WITH THE cAPS lOCK KEY?";
System.Text.StringBuilder sb = new System.Text.StringBuilder(question);

for (int j = 0; j < sb.Length; j++)
{
    if (System.Char.IsLower(sb[j]) == true)
        sb[j] = System.Char.ToUpper(sb[j]);
    else if (System.Char.IsUpper(sb[j]) == true)
        sb[j] = System.Char.ToLower(sb[j]);
}
// Store the new string.
string corrected = sb.ToString();
System.Console.WriteLine(corrected);
// Output: How does Microsoft Word deal with the Caps Lock key?
```
  
## Null Strings and Empty Strings  
 An empty string is an instance of a System.String?displayProperty=fullName object that contains zero characters. Empty strings are used often in various programming scenarios to represent a blank text field. You can call methods on empty strings because they are valid System.String?displayProperty=fullName objects. Empty strings are initialized as follows:  
  
```csharp
string s = String.Empty;  
```  
  
 By contrast, a null string does not refer to an instance of a System.String?displayProperty=fullName object and any attempt to call a method on a null string causes a System.NullReferenceException. However, you can use null strings in concatenation and comparison operations with other strings. The following examples illustrate some cases in which a reference to a null string does and does not cause an exception to be thrown:  
  
```csharp-interactive
static void Main()
{
    string str = "hello";
    string nullStr = null;
    string emptyStr = String.Empty;

    string tempStr = str + nullStr;
    // Output of the following line: hello
    Console.WriteLine(tempStr);

    bool b = (emptyStr == nullStr);
    // Output of the following line: False
    Console.WriteLine(b);

    // The following line creates a new empty string.
    string newStr = emptyStr + nullStr;

    // Null strings and empty strings behave differently. The following
    // two lines display 0.
    Console.WriteLine(emptyStr.Length);
    Console.WriteLine(newStr.Length);
    // The following line raises a NullReferenceException.
    //Console.WriteLine(nullStr.Length);

    // The null character can be displayed and counted, like other chars.
    string s1 = "\x0" + "abc";
    string s2 = "abc" + "\x0";
    // Output of the following line: * abc*
    Console.WriteLine("*" + s1 + "*");
    // Output of the following line: *abc *
    Console.WriteLine("*" + s2 + "*");
    // Output of the following line: 4
    Console.WriteLine(s2.Length);
}
```
  
## Using StringBuilder for Fast String Creation  
 String operations in .NET are highly optimized and in most cases do not significantly impact performance. However, in some scenarios such as tight loops that are executing many hundreds or thousands of times, string operations can affect performance. The System.Text.StringBuilder class creates a string buffer that offers better performance if your program performs many string manipulations. The System.Text.StringBuilder string also enables you to reassign individual characters, something the built-in string data type does not support. This code, for example, changes the content of a string without creating a new string:  
  
```csharp
System.Text.StringBuilder sb = new System.Text.StringBuilder("Rat: the ideal pet");
sb[0] = 'C';
System.Console.WriteLine(sb.ToString());
System.Console.ReadLine();

//Outputs Cat: the ideal pet
```
  
 In this example, a System.Text.StringBuilder object is used to create a string from a set of numeric types:  
  
```csharp-interactive
class TestStringBuilder
{
    static void Main()
    {
        System.Text.StringBuilder sb = new System.Text.StringBuilder();

        // Create a string composed of numbers 0 - 9
        for (int i = 0; i < 10; i++)
        {
            sb.Append(i.ToString());
        }
        System.Console.WriteLine(sb);  // displays 0123456789

        // Copy one character of the string (not possible with a System.String)
        sb[0] = sb[9];

        System.Console.WriteLine(sb);  // displays 9123456789
    }
}
```
  
## Strings, Extension Methods and LINQ  
 Because the System.String type implements System.Collections.Generic.IEnumerable%601, you can use the extension methods defined in the System.Linq.Enumerable class on strings. To avoid visual clutter, these methods are excluded from IntelliSense for the System.String type, but they are available nevertheless.
  
## Related Topics  
  
* foo
* bar
* baz