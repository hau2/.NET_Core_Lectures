
# Section 6 Interview Questions

## What is Controller?
A **Controller** is a class used to group a set of action methods. Action methods perform operations when a request is received and return the `IActionResult` to be sent as a response to the browser.

### Key Tasks of Controller:
- Reading requests (query strings, request body, cookies, headers, etc.)
- Request validation
- Invoking models (business logic)
- Creating ViewModel or DTO objects
- Sending DTO objects to views

A controller class should have the suffix `Controller` (e.g., `HomeController`) or apply the `[Controller]` attribute.

## What is an Action Method?
An **Action Method** is a public method in a controller class. It executes in response to an HTTP request with the following restrictions:
- Must be public
- Cannot be overloaded (unless using different HTTP methods)
- Cannot be static

## Types of Action Results in ASP.NET Core:
- **IActionResult**: Represents the result of an action method.
- **ActionResult**: Default implementation of `IActionResult`.
- **ContentResult**: Returns text results.
- **EmptyResult**: Executes without returning content.
- **JsonResult**: Formats an object as JSON.
- **PartialViewResult**: Renders a partial view.
- **ViewResult**: Renders a full view.
- **ViewComponentResult**: Renders a view component.
- **StatusCodeResult**: Sends a specific HTTP status code.
- **UnauthorizedResult**: Sends HTTP 401 status.
- **BadRequestResult**: Sends HTTP 400 status.
- **NotFoundResult**: Sends HTTP 404 status.
- **ObjectResult**: Sends object data as response.
- **FileResult**: Sends file content as response.
- **RedirectToActionResult**: Redirects to a specific action method (HTTP 301/302).
- **LocalRedirectResult**: Redirects to a local URL (within the domain).
- **RedirectResult**: Redirects to a local or external URL (HTTP 301/302).

## What is HttpContext?
`HttpContext` encapsulates HTTP-specific information about individual HTTP requests. It can be accessed using `ControllerBase.HttpContext` and contains properties like `Items`, `Request`, `Response`, `Session`, and `User`.
