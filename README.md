## Your Name:


# CIDM 3312 Lab 9: Middleware and Logging

## Task 0
This lab has several short answer questions to answer in this `README.md` file. Make sure you answer all questions as you progress through the lab assignment.

1. Open up VS Code. Create a new ASP.NET Core project using the `webapp` template with the following terminal command: `dotnet new webapp`

2. Open `Startup.cs` and **delete** all the code within the `Configure()` method.

3. Run your project with Run => Run Without Debug (CTRL+F5) or `dotnet run`.

4. Visit the website. What do you see? Why?

    **Replace this text with your response.**

5. Look in the Debug Console or Terminal of VS Code. Do you notice the log entries displayed? Copy and paste one of them here:

    **Replace this text with the copy/pasted log entry.**

6. Stop your project. If started with `dotnet run`, press CTRL+C at the terminal. If started with CTRL+F5, use the stop button.

## Task 1: Add Some Middleware
1. In `Startup.cs` in the `Configure()` method add a single piece of middleware using the code: 
    ```
    app.UseWelcomePage();
    ```

2. Run your project and visit the site in a web browser. What happens? Why?

    **Replace this text with your response.**

3. Stop your project.

## Task 2: Serve Some Static Files
1. Create `example.html` in the `wwwroot` folder. Write some simple html for this page.

2. Add `app.UseStaticFiles();` middleware after `app.UseWelcomePage();`

3. Run your project and navigate to http://localhost:5000/example.html.

4. Why is the welcome page still showing?

    **Replace this text with your response.**

5. Alter your code so that the content from `example.html` displays when you navigate to it and run your project again. The Welcome Page should still display for all other requests.

## Task 3: Welcome to Error Town
1. You no longer need to display the Welcome Page - alter your code so that it no longer displays.

2. Add the following Razor Page middleware at the end of the `Configure()` method.
   ```
   app.UseRouting();
   
   app.UseEndPoints(endpoints =>
   {
         endpoints.MapRazorPages();
   });
   ```

3. Visit the site again. What does this middleware do for the main page? The example.html page?

      **Replace this text with your response.**
      
4. Open `Index.cshtml.cs` and write some code that will generate an error. This should be easy for you guys, but here's an example. Put this code inside the `OnGet()` method.
   ```
   Object b = null;
   b.ToString();
   ```

5. Run your project. How is the error displayed? Does example.html still work?

      **Replace this text with your response.**
      
6. Add error handling middleware `app.UseExceptionHandler("/Error");`. Place this code above all other middleware.

7. Run your project. How is the error displayed now?

      **Replace this text with your response.**

8. Replace the error handling middleware with `app.UseDeveloperExceptionPage();` middleware.

9. Run your project again. How is the error displayed now?

      **Replace this text with your response.**

10. Why do you think the error handling middleware is placed first?

      **Replace this text with your response.**

11. Which error handling middleware should be used in development?

      **Replace this text with your response.**
 
## Round 4: Logging
1. Add logging by modifying the `OnGet()` method within `Index.cshtml.cs`:
   ```
   public void OnGet()
   {
      Object b = null;
      if (b == null) _logger.LogWarning("Object is null!");
      else b.ToString();
   }
   ```
   
2. Run your project and fild the log in the Debug Console or Terminal.

3. Submit your assignment to GitHub.
