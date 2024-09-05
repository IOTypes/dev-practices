

## Coding Standards

* **Code Style**: Follow the [ESLint](https://eslint.org/docs/latest/use/getting-started) rules configured in the project. Before committing, run yarn lint to check for any issues.
  
* **Commenting Code**: All code should be well-commented to ensure clarity for other developers. Use comments to explain the purpose of complex logic, the reasoning behind specific decisions, and any non-obvious code sections.
  
* **Component Structure**: Adhere to the component structure as outlined in our project. Reusable components should be placed in the components directory, while page-specific components should reside in the pages directory.
  
* **Naming Conventions**: Use meaningful and consistent naming conventions for components, functions, and variables.
  
* **Cyclocomplexity**: Ensure that the [cyclocomplexity](https://www.perforce.com/blog/qac/what-cyclomatic-complexity) of functions and methods remains below 10. This helps maintain code readability and reduces the risk of introducing errors in complex logic
