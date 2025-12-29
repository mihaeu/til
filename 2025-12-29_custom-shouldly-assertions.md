## Custom Shouldly assertions

Using C# extensions one can easily build custom assertions suitable for one's domain by e.g. leveraging the Shouldly DSL.

Create a class as an extension, e.g. `public static class MyCustomShouldlyExtensions` and then create a method following the Shouldly style e.g. `public static void ShouldXYZ(this ActualObject, int expectedParameterOne)`.

Use normal logic (i.e. if statements etc.) to test what you want to test for. The big benefit of this approach is that you can then throw custom assertions which in the future help detect the problem. Use `throw new ShouldAssertExceptions(yourDetailedMessageString);` so that Shouldly renders this in your test output.

Here's an example:

```
Expected absence counts (Create: 1, Update: 1, Delete: 0)
but was (Create: 0, Update: 3, Delete: 0)

Details:

Create Absences (0):
  (none)

Update Absences (3):
  - 2040-01-01 (FirstHalfAbsence) to 2040-01-03 (SecondHalfAbsence)
  - 2040-01-04 (FirstHalfAbsence) to 2040-01-05 (SecondHalfAbsence)
  - 2040-01-05 (FirstHalfAbsence) to 2040-01-06 (SecondHalfAbsence)

Delete Absences (0):
  (none)
```
