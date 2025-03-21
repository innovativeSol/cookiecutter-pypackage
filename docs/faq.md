# FAQ

???+ Question
    # Why github workflow `release & publish` failed?
    We have used a github action `heinrichreimer/github-changelog-generator-action` to
    generate change log automatically for your project. However, this action requires
    some configuration.

    Goto .github/workflows/release.yml (in your project folder), find the following:
    ```
        - name: generate change log
        uses: heinrichreimer/github-changelog-generator-action@v2.1.1
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          issues: true
          issuesWoLabels: true
          pullRequests: true
          prWoLabels: true
          unreleased: true
          addSections: '{"documentation":{"prefix":"**Documentation:**","labels":["documentation"]}}'
          #sinceTag: v0.1.1
          output: CHANGELOG.md
    ```
    uncomment `#sinceTag` line and given an existed tag name in your project. If 
    there's none, you have to create one now.

???+ Question
    # Why not travis CI?
    Travis CI is a great service, however, github actions is super convenient, less configuration , better integration. Less configuration, less error prone.

???+ Question
    # Why not read the docs?
    Same reason as above. Git pages is convenient than read the docs, it requires no further configuration, except access token. As to read the docs, you need to write v2 config file, plus several settings on web pages.

???+ Question
    # Why mkdocs over sphinx?
    reStructured Text and Sphinx is way to tedious, though powerful. With extension, 
    you'll find almost all features are available in mkdocs, in a neat and productive 
    way. Poetry and Markdown, are the two key factors driven me develop this template.

???+ Question
    # What are the configuration items?

    Here is a list:

    ```
    ## Templated Values

    The following appear in various parts of your generated project.

    full_name  
    Your full name.

    email  
    Your email address.

    github_user_or_org_name  
    Your GitHub user or organization name where the new package repository will be hosted.

    dev_aws_region
    The AWS region for the dev/test CodeArtifact repository. Defaults to us-east-1

    dev_aws_codeartifact_domain
    The name of the dev/test CodeArtifact domain.

    dev_aws_codeartifact_repository
    The name of the dev/test CodeArtifact repository.

    prod_aws_region
    The AWS region for the production CodeArtifact repository. Defaults to us-east-1

    prod_aws_codeartifact_domain
    The name of the production CodeArtifact domain.

    prod_aws_codeartifact_repository
    The name of the production CodeArtifact repository.

    project_name  
    The name of your new Python package project. This is used in
    documentation, so spaces and any characters are fine here.

    project_slug  
    The namespace of your Python package. This should be Python
    import-friendly. Typically, it is the slugified version of
    project_name.

    project_short_description  
    A 1-sentence description of what your Python package does.

    repository_name
    The GitHub repository name. Defaults to the project_slug with the underscores (_) turned to hyphens (-). 

    version  
    The starting version number of the package.

    ## Options

    The following package configuration options set up different features for your project.
    
    use_pytest
    If you choose yes, then Cookiecutter will include unit PyTest unit tests.

    command_line_interface  
    Whether to create a console script using Python Fire. Console script
    entry point will match the project_slug. Options: ["fire", "No
    command-line interface"]

    create_author_file
    If you choose yes, then Cookiecutter will include an AUTHORS.md file for acknowledging contributors.

    open_source_license
    Selects an open source license for the package. Options: ["MIT", "BSD-3-Clause", "ISC", "Apache-2.0", "GPL-3.0-only", "Not open source"]

    docstrings_style
    one of `google, numpy, rst`. It's required by flake8-docstrings.

    install_precommit_hooks
    If you choose yes, then Cookiecutter will attempt to install pre-commit hooks for you.

    ```

    except above settings, for CI/CD, you'll also need configure gitub repsitory secrets
    at page repo > settings > secrtes, and add the following secrets:

    - DEV_CODEARTIFACT_ROLE_ARN (Required for AWS access. May already be set as an organization secret.)
    - PROD_CODEARTIFACT_ROLE_ARN (Required for AWS access. May already be set as an organization secret.)
