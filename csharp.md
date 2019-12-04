# C# Reference

## String Formatting

`String.Format("{0} {1}", arg1, arg2)`

## Declaring an array with values ahead of time

`string[] names = new string[] { "Alice", "Bernadette", "Calli" };`

## Looping through elements of an array

```
foreach ( string name in names )
{
  Console.WriteLine(name);
}
```

## String concatenation

```
string name = "Nicholas";
name += " Bennett";
```

## Converting string to integer

```
string number = "5";
int n;
_ = int.TryParse(number, out n);
```

## ArrayLists

```
using System.Collections;
ArrayList stuff = new ArrayList();
stuff.Add("23");
stuff.Add(3);
foreach ( var item in stuff )
{
  Console.WriteLine(String.Format("{0} (type: {1})", item, item.GetType()));
}
```
