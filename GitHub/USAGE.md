# GitHub MCP Server Usage Guide

This guide provides examples of how to use the GitHub MCP server tools with Claude.

## Available Tools

The GitHub MCP server provides the following tools:

1. `search_repositories`: Search for GitHub repositories
2. `create_repository`: Create a new GitHub repository
3. `get_file_contents`: Get contents of a file or directory
4. `push_files`: Push multiple files in a single commit
5. `create_issue`: Create a new issue
6. `create_pull_request`: Create a new pull request
7. `fork_repository`: Fork a repository
8. `create_branch`: Create a new branch
9. `list_commits`: Get list of commits of a branch
10. `list_issues`: List issues in a repository
11. `update_issue`: Update an existing issue
12. `add_issue_comment`: Add a comment to an issue
13. `search_code`: Search for code across repositories
14. `search_issues`: Search for issues and pull requests
15. `search_users`: Search for GitHub users
16. `get_issue`: Get details of a specific issue
17. And many more...

## Usage Examples

Here are some examples of how to ask Claude to use these tools:

### Searching Repositories

```
Can you search for repositories related to "machine learning" on GitHub?
```

### Creating a Repository

```
Please create a new GitHub repository called "my-project" with a description "A test project for Claude".
```

### Getting File Contents

```
Can you show me the README.md file from the repository "username/repo-name"?
```

### Creating an Issue

```
Please create an issue in my repository "username/repo-name" with the title "Bug in login functionality" and description "The login button doesn't work when clicked multiple times".
```

### Searching Code

```
Can you search for code that uses "useState" in React components across GitHub?
```

## Advanced Usage

### Working with Multiple Files

You can ask Claude to create or update multiple files in a single operation:

```
Please create a simple React application in my "my-project" repository with the following files:
- src/App.js: A basic React component
- src/index.js: The entry point
- public/index.html: The HTML template
```

### Complex Workflows

You can also ask Claude to perform more complex workflows:

```
Can you help me fork the repository "username/awesome-project", create a new branch called "feature/add-documentation", add a comprehensive README.md file, and then create a pull request back to the original repository?
```

## Search Query Syntax

### Code Search
- `language:javascript`: Search by programming language
- `repo:owner/name`: Search in specific repository
- `path:app/src`: Search in specific path
- `extension:js`: Search by file extension
- Example: `q: "import express" language:typescript path:src/`

### Issues Search
- `is:issue` or `is:pr`: Filter by type
- `is:open` or `is:closed`: Filter by state
- `label:bug`: Search by label
- `author:username`: Search by author
- Example: `q: "memory leak" is:issue is:open label:bug`

### Users Search
- `type:user` or `type:org`: Filter by account type
- `followers:>1000`: Filter by followers
- `location:London`: Search by location
- Example: `q: "fullstack developer" location:London followers:>100`
