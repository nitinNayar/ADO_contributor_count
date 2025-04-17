# Azure DevOps Contributors Counter

A Python script to fetch and analyze unique contributors across all repositories in an Azure DevOps organization and project.

## Description

This script connects to Azure DevOps and generates a report of all unique contributors who have made commits across repositories within a specified time period. It provides both a summary view and detailed breakdown by repository.

## Features

- Fetches contributors from all repositories in a project
- Supports custom time period analysis
- Generates detailed JSON output
- Provides both summary and detailed contributor information
- Handles pagination for large repositories
- Includes error handling and connection testing

## Prerequisites

- Python 3.x
- `requests` library
- Azure DevOps Personal Access Token (PAT)

### Required Azure DevOps Permissions

Your PAT token needs the following permissions:
- Code (Read)
- Graph (Read)
- Git (Read)
- Project and Team (Read)

## Installation

1. Clone this repository or download the script
2. Install the required dependencies:
   ```bash
   pip install requests
   ```

## Usage

1. Set your Azure DevOps Personal Access Token as an environment variable:
   ```bash
   export AZURE_PERSONAL_ACCESS_TOKEN='your_pat_token_here'
   ```

2. Run the script with the required parameters:
   ```bash
   python ado_contributor_count.py <organization_name> <project_name> <number_of_days> <output_filename>
   ```

### Parameters

- `organization_name`: Your Azure DevOps organization name
- `project_name`: The project name within the organization
- `number_of_days`: Number of days to look back for contributors
- `output_filename`: JSON file to store the output

### Example

```bash
python ado_contributor_count.py my-org my-project 30 contributors.json
```

## Output

The script generates a JSON file with the following structure:

```json
{
  "organization": "organization_name",
  "project": "project_name",
  "date": "YYYY-MM-DD",
  "number_of_days_history": number_of_days,
  "total_contributors": total_count,
  "total_repositories": repo_count,
  "repositories": [
    {
      "name": "repo_name",
      "contributors": contributor_count,
      "contributor_emails": ["email1@example.com", "email2@example.com"]
    }
  ],
  "all_contributor_emails": ["email1@example.com", "email2@example.com"]
}
```

## Troubleshooting

If you encounter issues:

1. Verify your PAT token is correct and not expired
2. Confirm the organization and project names are correct
3. Ensure your PAT token has all required permissions
4. Check if you can access the project in your browser
5. Review the error messages and debug output provided by the script

## License

This project is open source and available under the MIT License. 
