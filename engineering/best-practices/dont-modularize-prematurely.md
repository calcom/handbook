# Don't modularize prematurely

The reason why you should not split files if they're not being used in more than one place is because it can lead to unnecessary complexity and maintenance overhead. If a file is only being used in one place, there is no need to split it into multiple files. This can make it harder to navigate and understand the codebase.

On the other hand, splitting functions and components as much as possible can be beneficial. It can help with code organization, reuse, and testability. By breaking down large components into smaller ones, you can create a more modular and flexible codebase. This can make it easier to maintain and evolve the code over time.

Collocating related code in the same file can also improve code organization and readability. If you have related code scattered across multiple files, it can be harder to understand how everything fits together.

In summary, the decision to split files or not should be based on whether it improves code organization, readability, and maintainability. It's okay to split functions and components as much as possible, but don't split files unnecessarily. Collocating related code in the same file can also be helpful.
