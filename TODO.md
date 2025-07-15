The goal on them will be to:
- Assess what's in place currently (e.g., on the AI Backend codebase we have some checks, although I don't know how comprehensive they are)
- Propose what should be added in each of them to ensure we reach production-ready code and software development "good practices"
- Establish and implement CI/CD pipelines and pre-commit hooks (e.g., ensure development in branches, pushing to main not allowed, linting and code formatting, bumpversion/versioning)
- Finally, define github actions to deploy on Azure

There are several persons actively developing in them, I can introduce you to them. With your help, my goal is to define a set of "rules" we will always follow, irrespective of the type of project or programming language, to ensure hig-quality standards

Documentation on the project is available at: https://www.notion.so/attercop/Wholepal-Supplier-Build-9a8297fada8f49ce9ad2413ae062d289

Regarding the list I outlined before, I would add, enforcer developers to always branch and developed features in branches. To have a main branch, which is protected, which only can receive merges from another branch, which let's call develop . Thus the workflow will be, main and develop start sync, developer branches from develop , the feature us developed and testes and merged into develop. Once that that feature, and others are done, they can be merged into main. Develop will have a CI/CD to deploy into Azure development environment and main to production one
