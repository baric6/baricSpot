# C# testing console program

Once everything is installed it is time to test

#### Create a console program

```
dotnet new console -n MyFirstApp
```

```
cd MyFirstApp
```

```
dotnet run
```

The output in the console will be **hello world**

#### Edit the Program.cs

when you open Program.cs you should see a basic

```
Console.WriteLine("Hello, World!");
```

This is your entry point for your logic, if you want to change it to make it do something replace above with

```
Console.WriteLine("What is your name?");
string? name = Console.ReadLine(); // Reads user input
Console.WriteLine($"Hello, {name}! Today is {DateTime.Now:D}");
```

this will ask you for your name in the console, wait for input and output

```
Hello, baric! and the date 
```
