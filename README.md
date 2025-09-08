# corporate-systems
### My project for university, third semester, subject: corporate systems
---
The file 'Program.cs' contains the solution of 1 practical workbook.  

#### Implemented limitations for the calculator:
- dividing by 0
  implemented a restriction for division by 0 operations
  ```csharp
    case "/":
      if (num2 == 0)
      {
          throw new DivideByZeroException("Error: Division by zero is not allowed!");
      }
      result = num1 / num2;
      break;
  ```

- maximum of 5 decimal places
    ```csharp
    if (input.Contains('.'))
                {
                    string[] parts = input.Split('.');
                    if (parts.Length > 1 && parts[1].Length > 5)
                    {
                        Console.WriteLine("Warning: More than 5 decimal places detected. Truncating to 5 decimal places.");
                        input = parts[0] + "." + parts[1].Substring(0, 5);
                    }
                }
    ```

- the output value is between -10_000_000 and 10_000_000
    ```csharp
    if (result < -10000000 || result > 10000000)
                        {
                            throw new OverflowException($"Error: Result {result} is out of range (-10,000,000 to 10,000,000)!");
                        }
    ```
---
#### Possible developer errors when writing and debugging code.
- Strange handling of empty input. If you just press Enter instead of a number, the method will return 0. This is not obvious to the new users. (Странная обработка пустого ввода. Если просто нажать Enter вместо числа, метод вернёт 0. Это неочевидно для новых пользователей.)

- If you enter letters, the program will crash: The ReadNumberWithLimit method does not check if the input is actually a number. If the user enters "hello", the program will crash with an error. (Если ввести буквы, то программа сломается: Метод ReadNumberWithLimit не проверяет, является ли ввод числом. Если пользователь введёт "hello", программа завершится с ошибкой.)

- When errors occur, the user does not get a clear message about what exactly went wrong. (При возникновении ошибок пользователь не получает понятного сообщения о том, что именно пошло не так.)